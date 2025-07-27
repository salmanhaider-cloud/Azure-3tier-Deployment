# Azure 3-Tier Architecture Deployment (Project)

This project demonstrates the deployment of a 3-Tier architecture on Microsoft Azure using Virtual Machines (VMs) across three separate tiers:

* **Web Tier** (Frontend)
* **App Tier** (Backend)
* **DB Tier** (Database)

---

## Project Topology

```
                +--------------------+
                |    Web Tier VM     |
                |  (Public IP + SSH) |
                +--------------------+
                         |
               (Port 5000: Python HTTP)
                         |
                +--------------------+
                |    App Tier VM     |
                | (Private IP only)  |
                +--------------------+
                         |
               (Port 5001: Python HTTP)
                         |
                +--------------------+
                |    DB Tier VM      |
                |  (MySQL Installed) |
                +--------------------+
```

---

## Technologies Used

* **Azure VMs** (Ubuntu 20.04 LTS)
* **Azure Resource Groups**
* **Azure Virtual Network + Subnets**
* **Network Security Groups (NSGs)**
* **SSH Key Authentication**
* **Python HTTP Server**
* **MySQL Database**
* **Git & GitHub for Source Control**

---

## File Structure

```
Azure3TierProject/
├── index.html      # Web Tier: HTML for Frontend
├── app.html        # App Tier: HTML served via Python HTTP
└── README.md       # Project details and structure
```

---

## How to Use

### Web Tier

1. `index.html` is served using Python:

```bash
python3 -m http.server 5000
```

### App Tier

1. SSH into Web VM, then into App VM.
2. Serve `app.html` via Python:

```bash
python3 -m http.server 5001
```

### DB Tier

1. MySQL installed on DB VM.
2. App VM connects to DB VM using private IP:

```bash
mysql -h <DB_PRIVATE_IP> -u root -p
```

---

## Notes

* Security via NSGs: Only required ports (22, 5000, 5001, 3306) are allowed.
* All internal traffic uses private IPs.
* Only Web Tier has public IP, others are private.

---

## Author

**Salman Haider**

GitHub: [salmanhaider-cloud](https://github.com/salmanhaider-cloud)
