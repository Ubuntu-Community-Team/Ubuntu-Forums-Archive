---
title: "Error Codes like windows in Ubuntu..???"
date: 2010-02-12
forum: General Help
---

### Post by karthick87 on 2010-02-12
In **Windows** if we get an error,there will be an error so we can easily identify the problem and we can find the solution...For example if **LAN** is disabled the error code will be **769**,if the **user name and password** is wrong we get the error code  **691**...Like that how can we identify in **Ubuntu**???

---

### Post by Grenage on 2010-02-12
You're best off looking in the logs.  The information there is, thankfully, not as generic as most windows error codes.

---

### Post by karthick87 on 2010-02-12
How to view my logs??I used to connect my connection using "sudo pon dsl-provider" if suppose mu username or my password is wrong how to find it???

---

### Post by l-x-l on 2010-02-12
> **getyourkarthick said:**
> In **Windows** if we get an error,there will be an error so we can easily identify the problem and we can find the solution...For example if **LAN** is disabled the error code will be **769**,if the **user name and password** is wrong we get the error code  **691**...Like that how can we identify in **Ubuntu**???

Wow.. you actually know what those codes mean in Windows?? My hat off to you. But in Ubuntu, the logs are located under System -> Administration -> Log File Viewer.

---

### Post by chewearn on 2010-02-12
Specifically, "System > Administration > Log File Viewer" is the Log viewer program, but the actual logs are found in "/var/log".

---

