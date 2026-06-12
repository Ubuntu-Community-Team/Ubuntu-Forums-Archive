---
title: "have to restart CUPS every reboot"
date: 2010-04-07
forum: General Help
---

### Post by ayoitzrimz on 2010-04-07
Hi, I have a problem with printing.

Everytime I reboot, I must manually restart CUPS using sudo /etc/init.d/cups restart in order for my printer to be recognized.

Any way to remedy this? I see that CUPS is already listed in my bootup manager and I dont know any other solutions.

Thanks!!

---

### Post by Ozdemon on 2010-04-21
> **ayoitzrimz said:**
> Hi, I have a problem with printing.

Everytime I reboot, I must manually restart CUPS using sudo /etc/init.d/cups restart in order for my printer to be recognized.

Any way to remedy this? I see that CUPS is already listed in my bootup manager and I dont know any other solutions.

Thanks!!

Me too.  I am on 9.10 and the problem is a few weeks old.

[Update]  - Seems to be fixed on 10.04

---

### Post by Jacroe on 2010-05-04
I'm having this problem now too on 10.04. But once it's restarted I'm good.

---

### Post by ames89 on 2010-05-04
same problem here T.T

---

### Post by ames89 on 2010-05-04
> **Jacroe said:**
> I'm having this problem now too on 10.04. But once it's restarted I'm good.
  same here :\ sorry the repost

---

### Post by dilldappe on 2010-05-05
Hi, same over here on a fresh 10.04 install. i tried several hints from the german ubuntu forums but nothing seems to solve the problem.

Does anyone know how lucid starts services? The rc-entries are not used anymore as far as i understand.

greetz

---

### Post by Jacroe on 2010-05-07
This was solved for me with the latest updates. Did it work for anybody else?

---

### Post by voodoo_child on 2010-05-08
I have this problem also, with a clean installation of 10.04. I can't see my USB printer, and troubleshooting tells me that 'The CUPS Print spooler does not appear to be running...'

I did not have the problem with 9.10 

Does anyone have a solution? Restarting CUPS in the terminal works temporarily, but is not a viable solution because I am not the user of the computer, it is a non-technical family member. 

Thanks

---

### Post by jkeatley on 2010-05-19
The cups service is dependent upon starting the avahi-daemon and samba daemons before it can start itself. You must make sure that avahi-daemon and samba are installed.  It should either be made an install dependency, or the dependency should be broken.

I had this problem, and after studying the rc script, determined the dependency and sure-enough, did not have it installed. It is not one of the newer upstart services. I installed samba (I already had avahi) and restarted, and it was running when it finished rebooting.

---

### Post by sir_robert007 on 2010-05-23
> **jkeatley said:**
> The cups service is dependent upon starting the avahi-daemon and samba daemons before it can start itself. You must make sure that avahi-daemon and samba are installed.  It should either be made an install dependency, or the dependency should be broken.

I had this problem, and after studying the rc script, determined the dependency and sure-enough, did not have it installed. It is not one of the newer upstart services. I installed samba (I already had avahi) and restarted, and it was running when it finished rebooting.

Yeah I also had this same problem. Would have to start CUPS manually every time I rebooted my machine. Installed Samba and CUPS now starts on its own like it should, although I don't see why CUPS would need Samba to start.

---

### Post by mickier on 2010-05-25
[QUOTE=jkeatley;9329015]The cups service is dependent upon starting the avahi-daemon and samba daemons before it can start itself. 

HMMM. so THIS may explain why my laptop is FINE, and my wife's is irritating needing cups restarted after every boot-up..!! 

I'll try it! thanks for the great IDEA:KS

---

### Post by fro1269 on 2010-06-06
does anybody have a resolution for this? i didnt have this issue until I performed the latest updates. Once i restart cups it works fine.. I already have both Samba and CUPS installed.. I am running 10.04

---

### Post by Morbius1 on 2010-06-06
Give this a shot: [http://ubuntuforums.org/showthread.php?t=1500806](http://ubuntuforums.org/showthread.php?t=1500806)

Post #4

---

### Post by fro1269 on 2010-06-06
> **Morbius1 said:**
> If you can't resolve this by removing and adding the printer and if the problem is that you have to restart cups at every boot then I would suggest the following:

Create a script:[FONT=sans-serif]
[/FONT]```
gksu gedit /etc/network/if-up.d/cups
```With this content:
```
#!/bin/sh
service  cups restart

```Save the file and make it executable:
```
sudo chmod +x /etc/network/if-up.d/cups
```Reboot


thanks for pointing me towards that thread, post #4 fixed it right away. i posted it above for those of  you too lazy to click the link
:)

---

