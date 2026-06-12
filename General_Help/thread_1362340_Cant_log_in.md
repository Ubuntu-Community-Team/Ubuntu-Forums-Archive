---
title: "Cant log in"
date: 2009-12-23
forum: General Help
---

### Post by Brainy142 on 2009-12-23
I am currently having trouble logging in on my computer, I will get to the log in window, then I will try to log in, the screen will go black, then I will be back at the log in menu.

What works: Root
Creating a new account (however changing the resolution prevents me from logging in after I log out/restart)
I can access my home in other accounts

What doesn't work: Display is now listed as unknown
switching window managers
making a new account and changing the home to my old account (I get 2 errors when starting)

Any help would be appreciated.

---

### Post by lavinog on 2009-12-23
You say creating a new account works?
I would use the new account and just move your files from the old account to the new.
You will need to add the new user to the admins group.

---

### Post by Brainy142 on 2009-12-23
problem is when I change the resolution and log out I cant log back in.

(I lower the resolution as I dont want to stress my internal video card aka. It tries running it at 1600x1080 as I have a high res CRT)
(and yes before you ask the linux support for my drivers suck aka no 3d 2d works nice though)

If I am able to make another account, Is there any way to send my firefox addons as It will be a pain to configure all my apps again

---

### Post by lavinog on 2009-12-23
What are you changing the resolution from and to?
Does it happen if you change it to any resolution...what happens if you change it to 800x600?

Could you be trying to change the resolution to something that your monitor cannot handle.
Is your monitor widescreen?

---

### Post by Brainy142 on 2009-12-23
The monitor handles the resoution fine (I'm going from 1600x1080 to 1152x864)

---

### Post by Brainy142 on 2009-12-23
I'm going to try it again.

---

### Post by Brainy142 on 2009-12-23
It seems to be working for now but had the same problem before I reinstalled ubuntu and it randomly quit working and then would work and so on and so forth where it got to the point It would take 5-6 log-ins to work. I've tried different window managers but they all have this issue (except for xterm)

any idea on the source of the issue?

---

### Post by lavinog on 2009-12-23
it could be a problem with the video drivers. What card do you have?

---

### Post by Brainy142 on 2009-12-23
Internal via thing... pretty old.... (I'm running a amd athlon xp 2000+ cpu for comparison)

Here we go VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

---

### Post by lavinog on 2009-12-23
you could try:
```

lshw -c video

```

---

### Post by Brainy142 on 2009-12-23
VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266
lol I just googled for that command after I posted.

---

### Post by Brainy142 on 2009-12-23
that command spit out more stuff

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=255 mingnt=4
       resources: memory:e1000000-e107ffff memory:d8000000-dfffffff(prefetchable) memory:e0000000-e000ffff(prefetchable)

---

### Post by lavinog on 2009-12-23
here is a bug report that involves your card: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vesa/+bug/414330](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vesa/+bug/414330)  It may not be the same issue, but it does seem to have some information.
When you get kicked back to the login screen, try to login with the other user and post your Xorg.0.log file (accessable with the log file viewer in system>admin)

---

### Post by Brainy142 on 2009-12-23
I'l get a log right now then
*log file has been posted

---

