---
title: "IPtables blocking internet access"
date: 2011-04-07
forum: General Help
---

### Post by PCaddicted on 2011-04-07
Hello,
I've installed the Firestarter GUI for the IPtables Firewall.I have outbound traffic policy permissive(blacklisting traffic).I launched Chromium(my only navigator) and the browser was unable to connect to the Internet(thus it couldn't display Google homepage).I disabled IPtables and everyhing was OK again.Does this firewall have an issue or is it so secure that it doesn't allow me to access the Internet?Any idea how could I fix this problem?
Also...if I enable it and just set it deny/reject inbound traffic,will I have any problems?
OS:Ubuntu 10.10 Maverick Meerkat

---

### Post by Frogs Hair on 2011-04-07
I know that application has not been updated for a long time . If you have not set any rules with Firestarter I would remove it and install Firewall Configuration from the software center you want a simple GUI for IPtables.

If you have set any special rules with Firestarter you will need the application to undo the changes.

---

