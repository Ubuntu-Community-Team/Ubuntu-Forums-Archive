---
title: "Ubuntu Desktop Wont Load"
date: 2011-07-23
forum: General Help
---

### Post by Jicks on 2011-07-23
Hey guys, 

I have been an avid reader of the Ubuntu Forums but I think this is my first post. 

I recently began using Ubuntu 11.04, having a dual boot setup alongside Windows 7. Everything worked perfectly fine until the last update of Ubuntu occurred. After the update I rebooted my system (as you do) to "Ubuntu, with Linux 2.6.38-10-generic."

When I do this it does one of two things: a) the Terminal loads and the cursor sits there blinking boringly achieving nothing and doing nothing the OS does not get very far into loading. Or b) A number of checks run automatically then pause and it goes nowhere and I'm left with a screen full of System checks. 

So, what I do is I load a previous version of Ubuntu "Ubuntu, with Linux 2.6.38-8-generic" and this loads no trouble.

I am wondering if anybody has had a similar issue, or if anyone knows any troubleshooting I could follow to determine what is the issue.

Thanks

---

### Post by Jicks on 2011-07-26
Been searching for a while through the forums and google and still struggling to find any solutions to the issue. Is it possible to revert back to an older version of Ubuntu without having to choose it at the boot screen, so it doesn't load the newest every time?

Thanks

---

### Post by 2F4U on 2011-07-26
Maybe the problem is due to graphics drivers. Are you using proprietary graphics drivers, for example for an ATI or nVidia card?

---

### Post by Jicks on 2011-07-26
Using an Nvidia card, however, I installed the required driver when I first installed Ubuntu. Maybe if the driver isn't compatible with the newest version? But I don't think it would be causing the issue...

Is there anyway to determine what may be causing the issue? Maybe a command I could type?

---

### Post by 2F4U on 2011-07-26
You can look into the system log files and also into .xsession-errors, which is located in your home directory.

---

### Post by Mr Nemo on 2011-07-26
I've also had problems with the new kernel (still doing some testing, but I'm pretty sure its the new kernel). I've had a load of problems with ubuntu getting stuck during boot and a lot of graphical freezes. If it is the kernel, just continue using the older kernel that should solve the problem. Reinstalling ubuntu probably won't solve the problem in this case.

EDIT: I also have an NVIDIA card

---

### Post by Jicks on 2011-08-25
Hey guys,

Well after being away for a while I came back and started fiddling round.

I managed to fix the problem. Although I don't really understand what I did technically so if anyone could explain exactly what I have done I would appreciate that.

I had to update my Nvidia drives, so the first problem I came to when trying to update them was doing it as the root user (I'm assuming this is the administrator). I managed to fix that with:
```
sudo sh abc.run
```

Then had to disable the X server (which I don't understand what it does or is but I found how to stop it and start it)

So I did Ctrl Alt F1 and got into tty1, logged in, and typed

```
sudo service gdm stop
sudo sh abc.run
```

Installed the driver on  Linux **2.6.38-8**

So I rebooted my computer into  Linux **2.6.38-11**
Simply followed the same steps as going into tty1,
reinstalled the graphics drivers and the desktop booted and now everything is working.... so far

---

