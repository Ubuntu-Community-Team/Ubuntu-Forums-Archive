---
title: "Where to change network default workgroup name"
date: 2009-07-05
forum: General Help
---

### Post by healee on 2009-07-05
I have ubuntu 8.04.1 LTS Desktop Edition installed.  Where can I change the workgroup to something else instead of the default?

I would appreciate if somebody would tell me where I can get information regarding how to access Linux or ubuntu in this case from Windows XP or Vista.  Do I need to set the directory on Linux or ubuntu as shared beforehand?

Has ubuntu desktop edition got firewall installed by default?

---

### Post by credobyte on 2009-07-05
Workgroup name can be changed there ( assuming that Samba is already installed ) :
```
/etc/samba/smb.conf
```

---

### Post by wojox on 2009-07-05
Do you have samba installed?

[http://us3.samba.org/samba/](http://us3.samba.org/samba/)

ufw uncomplicated firewall is installed by default but diabled.

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by swerdna on 2009-07-05
The default firewall is "ufw" = "uncompliacted firewall". It's installed in a disabled state.

You might find a primer for Samba useful. Here's one that includes firewall configuration, how to make shares, how to join a workgroup, how to set passwords and so on:
[Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by healee on 2009-07-07
I have only installed the default ubuntu system with the desktop edition CD.  I have not installed anything extra.  Somehow I can see the shared directory of the all the Windows system of other computers on the local network as well those on the same computer by entering the name of the workgroup and the password.  I have checked the etc directory and couldn't see any samba directory.  Now I wonder how I can see the files in the Window without samba installed.

---

### Post by swerdna on 2009-07-07
> **healee said:**
> I have only installed the default ubuntu system with the desktop edition CD.  I have not installed anything extra.  Somehow I can see the shared directory of the all the Windows system of other computers on the local network as well those on the same computer by entering the name of the workgroup and the password.  I have checked the etc directory and couldn't see any samba directory.  Now I wonder how I can see the files in the Window without samba installed.

If there's no directory "samba" at /etc/samba, then go to System --> Administration --> Synaptic Package Manager and install or check these: smbclient, libsmbclient, samba-common, nautilus-share and samba. Most should be installed by default except perhaps "samba". But check them all.

---

### Post by healee on 2009-07-09
I did dpkg -l | egrep "samba|smbclient|nautilus-share" and found nothing.  I brought up Synaptic Package Manager, searched for samba, marked libsmbclient, samba, samba-common and smbclient.  I applied marked changes and installed.
After all these I ran dpkg -l | egrep "samba|smbclient|nautilus-share" again but found nothing.  I checked /etc directory and there was no samba installed.  Do I need to do anything else to get samba going?  I must have missed something.

While dpkg -l | egrep "samba|smbclient|nautilus-share" found nothing I did sudo /etc/init.d/samba status it said * SMBD is running.  No samba entry was found in etc directory though.  Can somebody explain to me what is going on?

---

### Post by swerdna on 2009-07-09
> **healee said:**
> I did dpkg -l | egrep "samba|smbclient|nautilus-share" and found nothing.  I brought up Synaptic Package Manager, searched for samba, marked libsmbclient, samba, samba-common and smbclient.  I applied marked changes and installed.
After all these I ran dpkg -l | egrep "samba|smbclient|nautilus-share" again but found nothing.  I checked /etc directory and there was no samba installed.  Do I need to do anything else to get samba going?  I must have missed something.

While dpkg -l | egrep "samba|smbclient|nautilus-share" found nothing I did sudo /etc/init.d/samba status it said * SMBD is running.  No samba entry was found in etc directory though.  Can somebody explain to me what is going on?

The packages have not all installed. Check again in System --> Admin --> Synaptic. Search on samba. The indicator is a green filled square if it installed. Check all the others too for the green square.

Check also in synaptic --> Settings --> repositories. The first four main, universe, restricted and multiverse are (usually) enabled by default.

---

### Post by swerdna on 2009-07-09
Actually, I'm speaking about 9.04. Just noticed yours is different. But your 8.04 would have similar principles.

Check here for the apt-get version: [https://help.ubuntu.com/8.04/serverguide/C/installing-samba.html](https://help.ubuntu.com/8.04/serverguide/C/installing-samba.html)

---

### Post by healee on 2009-07-10
Thanks for your help.  I have read the recommended page and re-did "sudo apt-get install samba smbclient" and "sudo apt-get install smbfs" again and again. However I can't find any samba file in the /etc directory.  So I can't change the workgroup to match that of the Windows systems.  I can see the files of all the Windows partitions on the same computer where the ubuntu is installed.

After disabling the firewall at the ubuntu I can see the Windows systems on other computer on the same physical network from ubuntu.  Having selected the same workgroup of ubuntu on the Windows network I can see the ubuntu system however I can't access the ubuntu file system from Windows computer even though I have entered the same username and password I access the ubuntu system.  Is it because I don't have publicly shared directory on ubuntu file system?  What shall I do from here?  Also how can I enable the ufw but still allow sharing files between ubuntu file system and Windows system on other computers in the same network?

---

### Post by swerdna on 2009-07-10
When you looked in System --> Admin --> Synaptic, what colour was the marker box beside the package "samba"?

> However I can't find any samba file in the /etc directory. It's not actually a file. It's a directory and inside that directory is the file (smb.conf). Try that approach. If you can't see the directory samba inside directory /etc, I'll be flummoxed.

---

### Post by healee on 2009-07-10
I thank you for your patience and tolerance.  I have found it at long last.  It was my stupidity because I didn't scroll up the window when I did a "ls /etc" on the Terminal.  I realized my mistake when I went to Places - > Computer.

---

### Post by swerdna on 2009-07-11
> **healee said:**
> I thank you for your patience and tolerance.  I have found it at long last.  It was my stupidity because I didn't scroll up the window when I did a "ls /etc" on the Terminal.  I realized my mistake when I went to Places - > Computer.

Well all is looking better for you I hope.

---

