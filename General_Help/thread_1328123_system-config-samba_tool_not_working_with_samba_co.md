---
title: "system-config-samba tool not working with samba config"
date: 2009-11-16
forum: General Help
---

### Post by lajo01 on 2009-11-16
Hi,
I have just installed samba through the Synaptics manager. During previous installations I think also the GUI config tool (system-config-samba) was installed along with samba, but not this time. (Samba version 2:3.4.0-3ubuntu5.1)

I installed the GUI tool manually (also with Synaptics) the latest version available, 1.2.63-0ubuntu4. But the GUI throws me a warning when I start it that it doesn't understand certain (quite a few) lines of the smb.conf file, after that I'm unable to make any changes to the samba configuration through the GUI tool.

Is there a mismatch between samba versions or other problems?

Other samba packages are installed, like samba-common and samba-common-bin.

---

### Post by 3rdalbum on 2009-11-16
That's interesting. Unfortunately, system-config-samba worked fine for my 9.10 server. What happens if you completely purge the Samba server packages (including configuration files), reinstall them (so your config file is clean) and run system-config-samba again?

---

### Post by lajo01 on 2009-11-16
Deleted ALL samba packages and re-installed. Now it works.
I wonder about the smb.conf file that was there, where did it come from....? Probably an example file, but why didn't system-config-samba accept it?

Well, larger mysteries than this also remains to be solved... :)

---

### Post by justinham on 2009-12-05
Same issue here.  I was able to solve it by installing three packages:

sudo apt-get install gksu
sudo apt-get install python-gtk
sudo apt-get install python-glade2

- Justin
Kubuntu 9.10

---

### Post by beterhans on 2010-03-15
same here
I'll try to reinstall it this evening.
:p

---

