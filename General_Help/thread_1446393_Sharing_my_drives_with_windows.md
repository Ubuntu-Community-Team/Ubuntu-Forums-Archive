---
title: "Sharing my drives with windows"
date: 2010-04-04
forum: General Help
---

### Post by cancer10 on 2010-04-04
Hi

A couple of questions

1) I want to share my drives with other users using windows XP, please tell me what settings do I have to make in my Ubuntu machine.

2) In windows, when we want to access a shared drive, we go to Run > and type \\192.168.1.10 to access the shared drives of the pc having that IP. In the same way how do I access the drives of another user having either ubuntu or windows?



Many thanks in advance for your help.



Thanks

---

### Post by gzarkadas on 2010-04-04
1. You will have to install the Samba server package from the Synaptic Package Manager and setup your shares.  Since the settings depend on what and how is to be shared, it is best to first read the config files, assess your needs and post about any specific issues that you will encounter.  There is plenty of documentation available, see for example  [http://www.samba.org/samba/docs/man/Samba-Guide/](http://www.samba.org/samba/docs/man/Samba-Guide/).

2. The way you describe is protocol-dependent (SMB/CIFS) and thus it will work regardless of the type of the box you want to access.

---

### Post by cancer10 on 2010-04-04
Hi

In package manager, when i search for Samba, it shows me huge list, I am confused which one of them should I install?

Pls see the attached screenshot and help me



Thanks

---

### Post by gzarkadas on 2010-04-04
I have put a checkmark besides each package (samba,samba-doc, samba-doc-pdf); see attached image.

---

### Post by cancer10 on 2010-04-04
Any idea why I am getting the attached error when trying to select the First marked installation (marked by you in ur screenshot)?

---

### Post by gzarkadas on 2010-04-04
Select also the `samba-common' package, a few lines below; I had the feeling it should be included automatically by the 'samba' package, but perhaps it is not.

---

### Post by HermanAB on 2010-04-04
Also go to the Samba.org web site and read The Official Howto.

---

### Post by cancer10 on 2010-04-04
Hi


Now getting a new error as attached

---

### Post by 3rdalbum on 2010-04-04
When you're getting errors like this, first go to System > Administration > Software Sources and check that Main, Restricted, Multiverse and Universe are enabled, and that you have security updates and backports enabled.

Then reload your package list by hitting the Reload button in Synaptic.

Probably the most useful package for you would be "system-config-samba" - it gives you a GUI for setting up the Samba server, and also pulls in the Samba server as a dependency.

As for your other question, you'd put the following into the Location bar in Nautilus:

smb:\\192.168.1.10

Just do that once and then make a bookmark. If your server system has a different Ip address every time it starts up, then either make it use a static IP address or tell Nautilus the server's computer name, rather than the IP address, like so:

smb://myserver/

---

