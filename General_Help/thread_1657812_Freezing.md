---
title: "Freezing"
date: 2011-01-01
forum: General Help
---

### Post by penguinplus on 2011-01-01
I just upgraded from ubuntu 10.4 to ubuntu 10.10. But it keeps freezing. It froze 3 times. I only upgraded last night at Dec. 31 2010. Can someone please help?



Edit:  
  
   Help!!! It is freezing all the time. If I try to browse the internet and copy some fills and/or download something it freezes. It isn't a hardware problem because my mom daul boots windows on the same computer.


Edit 1/13/11: Please Help!!! It is getting really annoying. I see that people are viewing this so please help soon!!

---

### Post by penguinplus on 2011-01-14
Please!!! Please!!! Please!!! I am begging anyone to help!!! It is killing me!!! It is so annoying!!!

---

### Post by Pollox on 2011-01-15
Okay, it's been a week and no one has offered any ideas to fix this. The simple (but not fun) solution is just to reinstall Ubuntu. Backup your home folder to an external drive to save all your documents and settings. Make note of programs you have installed that you want to install again. Reinstall Ubuntu and copy your home folder back.

It might be good to test out the live cd for a bit to make sure it really just was a problem with the upgrade process and not some issue with Ubuntu 10.10 and your computer.

---

### Post by NightwishFan on 2011-01-15
Freezes specifically on file copies might be some sort of IO locking bug. Try opening System -> Administration -> Disk Utility and running the READ ONLY benchmark and see if your speeds are optimal.

I have had similar locks ups however mine were related to Compiz and Nvidia. Try disabling Compiz.

---

### Post by penguinplus on 2011-01-15
I really don't want to reinstall. Like I WiLL NEVER reinstall. I only have a ubuntu 9.1 disc and it takes to long to upgrade. I made the settings none in animation settings. It still freezes.

---

### Post by NightwishFan on 2011-01-15
You might have had a bad install then, check the disk you used doing this method, if any files "fail" then thats probably why, disk was damaged.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the files are fine, then open System->Administration->Log File Viewer, go to the "dmesg" and when it freezes, after it is done locking up, check the bottom of the log to see why.

---

### Post by Pollox on 2011-01-15
> **penguinplus said:**
> I really don't want to reinstall. Like I WiLL NEVER reinstall. I only have a ubuntu 9.1 disc and it takes to long to upgrade. I made the settings none in animation settings. It still freezes.

You should definitely continue following NightwishFan's advice on troubleshooting you're problem, but I do want to point out to you that you can get the latest Ubuntu cd sent to you for free from Canonical: [https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/"), if for some reason you can't make a cd yourself. You may find it handy to at least have it around should you ever want to boot from a live cd with a newer kernel, install on a new computer, share with a friend, etc.

---

### Post by NightwishFan on 2011-01-16
If you want to get sent or buy a free CD try to ensure it is 10.04 LTS "Lucid Lynx". That release is perfect for long term fully supported use. :)

---

### Post by penguinplus on 2011-01-29
Ubuntu I'm using now without getting rid of my files or damaging windows xp.(I dual boot).  It freezes in KDE mode as well just is harder to freeze. can I degrade Ubuntu 10.10 and degrade to 10.4 quickly?

---

### Post by NightwishFan on 2011-01-29
Downgrading is not designed if even possible. You will have to reinstall, you can set up ubuntu to have a seperate /home partition so reinstalling is easy though.

---

### Post by yuskhanzab on 2011-01-29
i also had this prob at the first time using ubuntu..

---

### Post by NightwishFan on 2011-01-29
I am not sure of the root cause of this issue however a hard lock spells graphics drivers to me. I know you do not want to reinstall, and it might not even fix the problem. :/

---

### Post by penguinplus on 2011-01-29
I do know that if I try to change the  monitor's setting it says "Can not find monitor" I know there is a monitor I'm looking at it right now.

---

### Post by NightwishFan on 2011-01-29
Can you open Applications -> Accessories -> Terminal, and type this command (the c needs to be capital):
```
lshw -C display | grep product
```

Post the output here. It should look like this:
```
user@ubuntu:~$ lshw -C display | grep product
WARNING: you should run this program as super-user.
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
```

---

### Post by penguinplus on 2011-02-04
I get this code ```
WARNING: you should run this program as super-user.
       product: C51G [GeForce 6100]

```

---

### Post by NightwishFan on 2011-02-04
Have you enabled Nvidia's drivers in System -> Administration -> Hardware Drivers?

---

### Post by penguinplus on 2011-02-06
Yes. I had trouble in the past(ubuntu 10.4) with the windows manager, I couldn't see the tittle bar. I solved the problem by switching to the propriety drive(173) to solve the problem. But now(ubuntu 10.10) I changed to the reccomended drive but it still freezes.

---

