---
title: "Strangest graphics problem (Nvidia)"
date: 2009-09-15
forum: General Help
---

### Post by garthecho on 2009-09-15
I've just installed an Nvidia 9500 gt and all is well.  The problem is for some reason on *only* the first boot of the day my wife gets low graphics mode when logging into her profile. After a restart she gets in just fine.  To make things even more confusing my profile works on first boot every time. Wanted to see if you guys had any opinions.

---

### Post by steveneddy on 2009-09-15
Only a suggestion:

Try reinstalling the video driver

or

go down one version of video driver.

My .02

---

### Post by garthecho on 2009-09-15
Thanks for replying.  I am on the third installation and second version of the video driver.

---

### Post by garthecho on 2009-09-15
So far I've made sure all settings are correct in the BIOS, tried both KDM and GDM, tried copying my nvidia-settings-rc file to my wifes home folder, and went through installing different driver versions.  Nothings successful so far.

Once it's logged in everything is perfect, 3D and all.  I started to think that the card must have to warm up or something but then why would my session log in right the first time?  It's got me beat.:(

---

### Post by steveneddy on 2009-09-17
It's a long shot, and after this I don't what direction you should go in, but go to the Users and Groups section of the Administrator area and see if she is privileged to use 3d acceleration.

---

### Post by garthecho on 2009-09-17
Yeah she is.  That was one I haven't thought of yet though.:)

---

### Post by steveneddy on 2009-09-17
More long shots:

Are there two nvidia drivers installed on the system?

It probably wouldn't boot if there was but I had to ask.

Which driver is installed according to the Hardware Drivers application under Administration?

---

### Post by garthecho on 2009-09-17
Right now I'm using 185.18.14 from the Nvidia site as any later driver version wont let me detect my TV.  I initially installed 185.18.36, then tried upgrading to the 190 beta drivers (all from the Nvidia site).  I found a post on another forum that recommended 185.18.14 to get the TV out working so I settled with that one.  None of the installs gave any errors and the problem has persisted through all the driver versions.

---

### Post by garthecho on 2009-09-19
Well, I finally got out of bed to see this problem for myself (I work nights and she's on days.), and noticed that it goes to low graphics when trying to load gdm, not when logging into her profile.  The message reads "Your screen and graphics could not be detected correctly, you'll have to configure these yourself." 
If I ignore that, go to a console and /etc/init.d/gdm restart it will load with no problems.
I also can't find any errors in any log files.

---

### Post by garthecho on 2009-09-20
Today I booted straight into Windows 7 to rule out there being a problem with the hardware and there were no problems.  Rebooted to Ubuntu and the problem still happened.  It's definitely in my configuration somewhere.

---

### Post by steveneddy on 2009-09-30
Set up another user just to see if the problem exists with that user profile, also.

If not, erase her old profile and make this her new profile.

---

### Post by Giblet5 on 2009-09-30
Try invoking the nvidia tool: ```
sudo nvidia-settings
``` and set up the resolution the way you like it, then save the resulting Xorg config file (from the "nvidia-settings Configuration" screen, "Save Current Configuration" button. Save as /etc/X11/xorg.conf

Then, restart Xorg to verify met expectations ```
sudo /etc/init.d/gdm restart
```.

That should definitely fix it.

---

### Post by steveneddy on 2009-10-01
> **Giblet5 said:**
> Try invoking the nvidia tool: ```
sudo nvidia-settings
``` and set up the resolution the way you like it, then save the resulting Xorg config file (from the "nvidia-settings Configuration" screen, "Save Current Configuration" button. Save as /etc/X11/xorg.conf

Then, restart Xorg to verify met expectations ```
sudo /etc/init.d/gdm restart
```.

That should definitely fix it.

But xorg.conf is used by all users.

The problem is that only one user on the machine has the issue while the main user's video is OK.

---

### Post by garthecho on 2009-10-03
Well, thanks for all the suggestions but I gotta report that an update to Karmic beta has fixed the issue.

---

