---
title: "PC crashes after switching to Nvidia GFX. What to do?"
date: 2010-10-14
forum: General Help
---

### Post by TheForumTroll on 2010-10-14
Hello.

My old ATI 4850 graphic card died and since everyone keeps saying that Nvidia is the way to go in Linux I got myself a brand spanking new Gainward GeForce GTX 460 *"Golden Sample - Goes Like Hell"*. Yay! Switching from ATI to Nvidia caused me a lot of problems with drivers and crashes though so I decided to reinstall as I have been upgrading Ubuntu for some time now and I guess it couldn't hurt to start from scratch. 

Well, it didn't help. This is what my screen looks like:

[[IMG]http://imgur.com/xsNmGs.jpg[/IMG]](http://imgur.com/xsNmG.jpg)

I don't mind the purple colours in Ubuntu but this is a bit too much :(

I can still move the mouse pointer around but I cannot *do *anything except hard reset. Any ideas? :confused:

Everything worked just fine with the ATI card and the new card also works 100 % in Windows 7. So far it seems to work without the driver activated but I really would like it to work.

---

### Post by TBABill on 2010-10-14
Have you removed all the open source and ATi drivers in Synaptic and checked to make sure all necessary nVidia files are installed?

---

### Post by Refalm on 2010-10-14
After you tried TBABill's suggestion, and that didn't work, you can try this one:
[http://ubuntuforums.org/showpost.php?p=9965364&postcount=9](http://ubuntuforums.org/showpost.php?p=9965364&postcount=9)

---

### Post by TheForumTroll on 2010-10-14
I gave up trying to fix the issue with changing gfx brand and reinstalled Ubuntu. So my installation is 100 % default with all updates.


I will give the beta drivers a try. :)

---

### Post by TheForumTroll on 2010-10-14
Nu luck with the beta drivers. It still crashes after a few minutes use. Any other ideas or should i post a bug in launchpad?

---

### Post by sendblink23 on 2010-10-14
That is very odd, allot of people have that card working 100% fine on ubuntu 10.10 using the standard - System > Administration > Additional Drivers

Something must be acting quite odd on your motherboard if its making your card have strange odd behaviors on Ubuntu

Even my neighbor has a 470 and its working fine with the same driver I mentioned on a fresh install of 10.10.

---

### Post by TheForumTroll on 2010-10-14
Yes I couldn't understand it either. All my hardware have been working fine in Ubuntu as far as I can recall except some small problems with 3D acceleration in newer releases while I used an ATI card. That was why I chose the Nvidia card this time as they have always worked for me.


I was sure the problem was something with swapping from ATI to Nvidia but since a format didn't work I have no idea what can cause this.

Some further details:
When it crashes I can still move the mouse (looks funny though) but nothing works. I cannot even turn on/off CAPS lock or switch to a terminal. Only the reset button does anything at all.

I'll have a look in the logs and post if I find anything strange.



**UPDATE**:
Forgot to add that the GTX 465 and 470 use the old Nvidia GF100 chip. Mine use the newer GF10**4**. Don't know it it matters but it could be something since it looks like a gfx driver problem.

---

### Post by sendblink23 on 2010-10-14
> **TheForumTroll said:**
> Yes I couldn't understand it either. All my hardware have been working fine in Ubuntu as far as I can recall except some small problems with 3D acceleration in newer releases while I used an ATI card. That was why I chose the Nvidia card this time as they have always worked for me.


I was sure the problem was something with swapping from ATI to Nvidia but since a format didn't work I have no idea what can cause this.

Some further details:
When it crashes I can still move the mouse (looks funny though) but nothing works. I cannot even turn on/off CAPS lock or switch to a terminal. Only the reset button does anything at all.

I'll have a look in the logs and post if I find anything strange.

Here is a random suggestion... do you have another motherboard or a friend on which you could test out installing 10.10 with *Your graphic card on his computer... to see if it happens as well - or do you have a friend who has another 460 to test it out on your computer.

Its extremely odd if it works perfectly in Windows it should work fine on Ubuntu the same card.. so I am certain teh card isn't the issue... but that is why I'm suggesting teh above just to rule out if its the card odd behavior on ubuntu.. or if its your motherboard causing the odd behavior on ubuntu with another 460

*just read your update... no clue... that maybe does do a difference :/

---

### Post by TheForumTroll on 2010-10-14
I will see if I can find someone who can help me test the card. Would a LiveCD do the trick I wonder? 

I'll go dig in the logs now.

---

### Post by TheForumTroll on 2010-10-14
No much to see. Here is every single error I could find that happend around the time it crashed:

```

gdm-simple-greeter[1608]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
gdm-session-worker[1613]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
NetworkManager[1108]: <error> [1287094279.459260] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
NetworkManager[1108]: <error> [1287094279.469904] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
modprobe: FATAL: Module index: unexpected error: EOF#012Try re-running depmod

```

I can't see any errors with gfx drivers.

---

### Post by cascade9 on 2010-10-14
OK, this is weird, I thought I had seen a similar thread. Post this on both so you can both see the others problem, maybe that will help your troubleshooting

[http://ubuntuforums.org/showthread.php?t=1595509](http://ubuntuforums.org/showthread.php?t=1595509)

---

### Post by legionarius on 2010-10-15
[gorbalad]("http://ubuntuforums.org/member.php?u=1167165") and me have solved this problem installing Ubuntu drivers taken from nvidia official site Take a look here: [http://ubuntuforums.org/showthread.php?t=1595509](http://ubuntuforums.org/showthread.php?t=1595509)

After downloading the drivers on the desktop I've written (as I've been suggested to do) this:
sudo chmod 777 ~/Desktop/NVIDIA-Linux-x86_64-260.19.12.run
sudo servive gdm stop
cd ~/Desktop
sudo ./NVIDIA-Linux-x86_64-260.19.12.run
sudo reboot

Thank you cascade9 for the link :)  I hope everyone can solve this probelm.

---

### Post by TheForumTroll on 2010-10-17
Thank you for your post! I will try it as soon as possible. 

Right now I cannot test it as I accidentally bumped my harddrive so hard that it is now saying the "click of death" sound :( 

Will mark as SOLVED when my new drive arrive and I have tested the solution.

---

