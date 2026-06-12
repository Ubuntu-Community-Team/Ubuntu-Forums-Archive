---
title: "Error Message, Won't Network"
date: 2006-05-02
forum: General Help
---

### Post by jrgillam on 2006-05-02
I just installed a dual boot OsX, Ubuntu setup on my iBook g4. When I enter my username and password to login, I get the following error message: 

*"Could not look up internet address for ubuntumac.* (the name of my computer) *This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding ubuntumac to the file /etc/hosts."*

I then get a choice to either "try again" or "login anyway" (or something to that effect.) When I choose try again nothing happens, and when I override and login, it logs in, but won't let me open the network configuration window. 

Any help would be much appreciated.

---

### Post by bugme on 2006-05-02
Have you tried adding ubuntumac to the file /etc/hosts?

---

### Post by jrgillam on 2006-05-02
Well, no, erm, how would I go about doing that?

---

### Post by bugme on 2006-05-03
/etc/hosts is a file/folder.
Click on places > computer > file system (double click) then look for a folder called etc, then hosts and add the line ubuntu mac in the file /etc/hosts
it should be added like this, for example,
Paragraph 1
ubuntumac
or if it is irregular add it where it would seem to go.
Also, you might need to be in root, search the ubuntu wiki for **root**
and click on the entry that sais something like **enable root login**.

---

### Post by jrgillam on 2006-05-07
I found the document "hosts," but when I open it, it's in read only format, and it seems I don't have the permissions to edit it. I tried to setup a root login, as described [https://wiki.ubuntu.com/RootSudo?action=show&redirect=Sudo]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=Sudo"), but it didn't work. It said something like "no such directory." Note: I'm completely in the fog when it comes to Terminal, sudo, su, etc. 

Also, I'm still having no luck with network/ethernet. My geek friend determined that my ethernet port is not being recognized but ubuntu, and he recommended a reinstall, with an ethernet cable plugged into the port. Any ideas?

---

