---
title: "where does ubuntu store all the route info i entered into the network manager?"
date: 2010-09-30
forum: General Help
---

### Post by firsttimeuser on 2010-09-30
trying to find where ubuntu stores all the routes i punched into the network manager GUI without any luck.

Can someone tell me where i can find the static files for the route i entered? thanks

---

### Post by gzarkadas on 2010-09-30
Network Manager stores connections in /etc/NetworkManager/system-connections. All information about each connection is stored as entries inside the corresponding file.

---

