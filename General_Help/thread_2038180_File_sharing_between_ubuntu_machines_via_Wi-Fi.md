---
title: "File sharing between ubuntu machines via Wi-Fi"
date: 2012-08-06
forum: General Help
---

### Post by community on 2012-08-06
Hai everyone
            I need to share files between two computers working on Ubuntu 12.04.Please give me the detailed steps from the very beginning.Because I tried in several ways but failed to share. Whether creating an Ad-hoc network is the basic thing as in Windows? Do I need any of the programs like FTP,Samba,NFS,OpenSSH,..? Is it possible to share files without installing these programs? Help me please...

---

### Post by nothingspecial on 2012-08-07
Hi

Install openssh-server then on a workspace with a clear desktop go to the global menu and click File > Connect to server

[ATTACH]222359[/ATTACH]

Fill the details in like so

[ATTACH]222360[/ATTACH]

Where server is the ip address of the other machine and username and password are an account on the other machine. Once connected you can add a bookmark in the file browser.

That's it.

---

