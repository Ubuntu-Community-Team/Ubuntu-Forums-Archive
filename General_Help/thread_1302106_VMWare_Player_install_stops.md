---
title: "VMWare Player install stops"
date: 2009-10-26
forum: General Help
---

### Post by bl@ckm@ge987 on 2009-10-26
Hi,

I just installed Ubuntu 9.10 Karmic Koala because it now seems all my hardware s finally supported.

I'm trying to install VMWare Player 2.5.3. I've tried installing it using the .bundle and .rpm converted to a .deb.

For both options it stops installing at "Configuring"

This is the tutorial I'm using: 
[https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

I used the instructions here to convert the .rpm to .deb:
[https://help.ubuntu.com/community/VMware/Workstation](https://help.ubuntu.com/community/VMware/Workstation)


Here is the output from my terminal:

Installing VMware Installer 1.0
Copying files...
Configuring...
Installing VMware Player 2.5.3
Copying files...
Configuring...
Installing VMware VIX API 1.6.3
Copying files...
Configuring...
Installing VMware Player 2.5.3
Copying files...
Configuring...
Installing VMware Player 2.5.3
Copying files...
Configuring...

^^It stops doing anything at the last "Configuring..." there. I can't find the process to KILL it so I reboot my system.

Now VMWare actually does install and works fine, but this freeze or hang or whatever just really bugs me.

I've also tried installing VMWare Workstation provided by my school, and it hangs at the same spot, output is identical.

Any help is appreciated.

---

### Post by mikewhatever on 2009-10-26
If it runs and works ok after the installation, I wouldn't worry. Perhaps there is a bug in the installer, who know.

---

### Post by bl@ckm@ge987 on 2009-10-27
Well its not that it doesn't work, but for VMWare workstation, it installs the VMWare player and then the Workstation. But it can't get too the Workstation install because it stops at the Player install.

It is probably just a bug with Karmic Koala. Its no big problem, I just ued Virtualbox which seems to work a lot better then I thought.

I just wanted VMWare for one of my classes so I didn't need to reboot into Windows to use it.

Thanks anyway.

---

### Post by GadiCohen on 2009-11-07
See this: [http://communities.vmware.com/message/1357476#1357476](http://communities.vmware.com/message/1357476#1357476)

---

### Post by jhayes on 2009-11-07
same proble. new install 9.10, tried to install the downloaded .bundle file from vmware, freezes or something on the vmware player configureing part.
yes i also use virtualbox no problm, but for one of my classes i have to have vmware, as we get a vmware image  as part of a test.

---

### Post by superfly1978 on 2009-11-08
This worked for me on ubuntu 9.10 using vmware 6.5.3

[http://aldeby.org/blog/index.php/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html](http://aldeby.org/blog/index.php/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html)

---

