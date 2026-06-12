---
title: "Remote Access to Home Folder"
date: 2011-11-03
forum: General Help
---

### Post by Jaybyrrd on 2011-11-03
Say I want to be able to login and gain access to my home folder so that I can pull documents from it from anywhere, what would be the best and safest solution?

---

### Post by WorMzy on 2011-11-03
Ssh.

---

### Post by mjuhasz on 2011-11-03
+1

Install the ssh package (which is a metapackage for the openssh server and client) and then you have password based access on default port 22 to your machine. You can access your files with sftp, scp, Nautilus (Connect to server option), etc.

For better security you can change the default port and disable password base access and use key based access instead.

Remember to forward the ssh port if you are behind NAT (e.g. using a router).

---

### Post by Jaybyrrd on 2011-11-03
How do I access it from a Windows machine?

---

### Post by Script Warlock on 2011-11-03
you can use filezilla for windows

---

### Post by Jaybyrrd on 2011-11-03
Alright thanks! :)

---

### Post by papibe on 2011-11-03
You can also use [WinSCP]("http://winscp.net/eng/index.php") in windows.

Regards.

---

