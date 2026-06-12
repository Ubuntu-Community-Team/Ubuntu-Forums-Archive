---
title: "ATI/flgrx issues"
date: 2011-09-30
forum: General Help
---

### Post by siff on 2011-09-30
Good day all

Recently ran into an issue with 11.04. I don't know if it's been posted at all as i have not had time to look (been trying to fix system issues).

Long story short:

Dual boot Win7 (64)/Ubuntu 11.04 (2.6.39.03xxxx)(32)
ATI Radeon HD 6310
Toshiba C650-D (AMD flavor)


Initially under 2.38 Gen, i was able to get Compiz working the way i had it in 9.10. Since updating the distro/kernel to 2.6.39.03xxxx i've had a few issues (ie Winn FF not working, and Radeon not using proprietary drivers). 
I have purged fglrx and then tried to re install the Catalyst suite but for some reason Jockey gives me an error trying to install and i get a mdio gdio error when i boot using 2.6.39.03xxxx and it locks up and i have to ctrl+alt+del.
If i revert and log on using 2.6.38 Generic under Failsafe everything works like magic under Classic with no Proprietary drivers but who wants to use Failsafe all the time?
I have tried just about everything i've read up but to no avail short of updating to kernel 3.0 rc2 or formatting the partition and staring over again (not really desired since i'll have to do a complete install.

Any suggestions or a thread i can follow to update properly and get everything working again? o_0

---

### Post by seawolf167 on 2011-09-30
Take a look at these two links and see if they help at all:
[How to ]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")purge and reinstall the driver plus some troubleshooting
[How to ]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")for the ATI binary driver

---

### Post by siff on 2011-09-30
I've tried the first (which led the to mdio error and 2.6.39 halts with a kernel panic) and i did the 2nd as well. Both did not produce any reasonable results.
I did do a complete purge of flgrx and then tried the install off the 2nd link. Still nothing (made sure i had the bases covered before i tried re installing Catalyst).

Any other thoughts?

---

### Post by Claus7 on 2011-10-01
Hello,

which is the catalyst suite you are trying to install? Mind you that the latest one might not be the best option.

Regards!

---

### Post by siff on 2011-10-03
I'm pulling it right from the latest build off the AMD site. I'm pretty positive that it's 11.9 though. Not too sure. I'll have to check again tonight and repost.

---

### Post by seawolf167 on 2011-10-03
What if instead of installing the proprietary drive suite you use the driver from System -> Administration -> Hardware Drivers? (Power Button -> System Settings -> Additional Drivers in 11.04)

The bonus here is that you don't have to re-install the drivers every time your kernel is updated.

---

### Post by siff on 2011-10-07
Yeah i tried that too. It seems that since i upgraded to 2.6.39.xxx that's where all the issues started.

I can't even boot to the old 2.6.38 kernel at all (have to use failsafe). I still get the persisting mdio error that goes to black screen after i start up.

---

### Post by Claus7 on 2011-10-07
Hello,

do you have any broken packages? From what you mention it seems that something went wrong during your updates.
You could try:
sudo apt-get update

to see if anything is wrong. I do not want to hassle, but I think that a fresh new installation might save you from a lot of trouble.

Regards!

---

### Post by siff on 2011-11-08
Hey all


I finally got everything working. Last Friday my machine finally posted properly and i did a full upgrade to Oneiric.
I searched around a bit and i found that fglrx was indeed the cause (as i was using the stock drivers and not the open source).

So here is what i did step by step for those having the same issue with ATI Radeon 6X HD series cards:

1.Upgrade to Oneiric (11.10)
2.Restart
3.Install Gnome Panel (sudo apt-get install gnome-panel) from Terminal
4.Restart
5.Logon using Gnome Classic and then head to the following page:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
6.Assuming you followed the guide implicitly, install Compiz Config Icon from sources.
7.Select Indirect Rendering (as this will restart Gnome automatically now,thank you dev teams!).
8.Enjoy all of your desktop effects!

Notes/caveats:
I found that every time a reboot occurs you have to turn Compiz Config Icon back on and switch over/back to Indirect rendering. You will have to go through Catalyst(Administrative) to fix the tearing issue (as Wobbly Windows looks poor without it turned on).There is also an issue with your distro not coming out of screen saver mode which forces you to restart. As a temporary measure (and until there is a time you have to fix it), switch your monitor to Never in power management and it should be fine.
This worked for me and i was hoping to have this posted up in plain view for anyone having the same issue.

---

### Post by Mk1Softie on 2011-11-09
Hi all,

Thanks for the posts - got catalyst 11.10 working [sort of] on a Radeon HD 6450.

Anyone seen this problem with catalyst/fglrx?

Can login OK once only, as any user, and logout.  Cannot log back in to an X session.

Attempt to login a second time as the same user locks the X display [lightDM screen removes its "password" box, but the backdrop does not change].

Attempt to login as a different user gets further: the user wallpaper appear, but the Unity bits [top bar & launcher] do not.

Switch to a text session Ctrl-Alt-[1-6], login & "ps -ef" shows the "compiz" process from the first login is still present.

Killing the "/usr/bin/gnome-session" process, as either user, brings back the lightdm login screen, but does not allow another login.

Cannot "kill -9" the compiz process, and "compiz --replace --display :0", with or without "sudo", reports "display not found".

Note:
(1) Some userIDs are below 1000 [needed 'cos my NAS won't accept UIDs above 999].  This does odd things (user name next to the clock is ''[invalid UTF-8]'', accounts not shown by lightdm), but the logout/login problem also happens with accounts 1000 and up.

(2) Have two machines [Acer desktop with the HD6450 & EeePC netbook], and this only happens with the desktop, so I assume it is driver-related.

---

