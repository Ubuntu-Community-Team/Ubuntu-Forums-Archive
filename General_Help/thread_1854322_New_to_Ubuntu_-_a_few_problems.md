---
title: "New to Ubuntu - a few problems"
date: 2011-10-04
forum: General Help
---

### Post by leunam12 on 2011-10-04
Hi, I'm slowly trying to move away from Windows and I installed Ubuntu 11.04 on a second drive on my PC. My other drive still has Widows in it. I'm experiencing a few problems with Ubuntu.

1- Ubuntu won't boot unless I invoke the BIOS boot menu and select the second drive.

2- When the second drive is selected I get an "out of range" message on my monitor, this lasts for about 30 seconds, then I get a purple screen and Ubuntu starts.

3- If I suspend or Hibernate I can't come back all I get is a black screen and I have to hard-reset by holding the power button.

4- Fonts are blurry by default, so after a few hours reading stuff on different websites i managed to install MS fonts and and adjust for sharpness, it worked the first time but now it's sharp on some areas of the screen and blurry on others.

5- I can't type the apostrophe unless I open the keyboard preferences and remove the default keyboard and select the USA keyboard (the default is USA alternate or something like that), every time I boot I have to do the same procedure.

6- I haven't figured out a way to adjust my Wacom tablet, it works but I don't know how to configure it

I guess that's it; please, let me know if it's better to open a separate thread for each one of these questions, I'm not very experienced on forums. 

my system is a Compaq presario SR1630NX with an AMD 64 3500+ processor. 2 Gigs of ram. Video card: ATI RS480                       Radeon Xpress 200G Series.

Thanks
*

---

### Post by westie457 on 2011-10-04
> **leunam12 said:**
> Hi, I'm slowly trying to move away from Windows and I installed Ubuntu 11.04 on a second drive on my PC. My other drive still has Widows in it. I'm experiencing a few problems with Ubuntu.

1- Ubuntu won't boot unless I invoke the BIOS boot menu and select the second drive.

2- When the second drive is selected I get an "out of range" message on my monitor, this lasts for about 30 seconds, then I get a purple screen and Ubuntu starts.

3- If I suspend or Hibernate I can't come back all I get is a black screen and I have to hard-reset by holding the power button.

4- Fonts are blurry by default, so after a few hours reading stuff on different websites i managed to install MS fonts and and adjust for sharpness, it worked the first time but now it's sharp on some areas of the screen and blurry on others.

5- I can't type the apostrophe unless I open the keyboard preferences and remove the default keyboard and select the USA keyboard (the default is USA alternate or something like that), every time I boot I have to do the same procedure.

6- I haven't figured out a way to adjust my Wacom tablet, it works but I don't know how to configure it

I guess that's it; please, let me know if it's better to open a separate thread for each one of these questions, I'm not very experienced on forums. 

my system is a Compaq presario SR1630NX with an AMD 64 3500+ processor. 2 Gigs of ram. Video card: ATI RS480                       Radeon Xpress 200G Series.

Thanks
*

1, In the bios set the default drive to the Ubuntu drive. Then open a terminal and type in ```
sudo update-grub
``` that should sort things to enable dual-booting and a Grub menu.

2,3,&4 could possibly be graphics card issues. Atm cannot find the required link, will edit when found unless someone else posts it.

5 In Preferences > Keyboard Choose the one you want to keep, remove all others and click apply system-wide.

Hope this helps.

                     -----------------------------------------------------------------

Found the link [here]("http://ubuntuforums.org/showthread.php?t=1743535")

Forgot about 6, Wacom Tablet. No ideas of my own. Take a look here for inspiration. [http://ubuntuforums.org/tags.php?tag=wacom+tablet](http://ubuntuforums.org/tags.php?tag=wacom+tablet)

---

### Post by Favux on 2011-10-04
Hi leunam12,

Welcome to Ubuntu forums!

As westie457 said those could be video card issues.  They may also be related to Unity.  To rule out Unity when you get to the log in screen (after you get the boot issue straightened out) there are options for Classic mode and Classic mode without effects at the bottom.  Try Classic first and see if that helps.

If it does you still may be able to use Unity if you install the AMD proprietary drivers (Catalyst) for your video chipset.  Also to give you some keywords to Google with enter in a terminal the following command:
```
lspci | grep VGA
```
The output will contain your video chipset as the system sees it.

For the Wacom tablet need to know which model.  Should be on a sticker on the bottom of the tablet.  Also the output of the following command:
```
lsusb
```
should contain a line in it with your Wacom tablet.  Post that as that will tell us the product ID.  What do you want to configure?  Things in general or something specific?

---

### Post by Mark Phelps on 2011-10-04
Notice that you have an ATI Xpress 200 -- for which there are NO restricted drivers that will work with recent versions of Ubuntu.  The open-source drivers, which were installed by default when you installed Ubuntu, are the ones that work now.

I've read that Ubuntu 11.10 has supposedly made major improvements to the open-source ATI/AMD drivers, so you might try booting from an ubuntu 11.10 CD and see if that gives you better video.

---

### Post by leunam12 on 2011-10-04
Thanks for the replies, I'm not at the Ubuntu machine now so I'm not able to test the suggestions. I am using the classic desktop and I tried to install the catalyst drivers from AMD this morning and it gave me some kind of error; I will try again.

My Wacom tablet is an Intuos 3 (the smallest one) I will post some details later. What I want to do is configure the lower button so it invokes a context menu when I press it and touch the pad; I also wnat to reduce the sensitivity area on the pad so the cursor moves faster and I don't have to move my hand so much. In other word I want to set the tablet so a smaller portion of it covers the whole screen as it is shown in the picture.

[IMG]http://www.mediafire.com/imgbnc.php/2f5d8aef224d8571c0bdc66e41bd467b881d72fdda8940d72a5c1fa979c461f86g.jpg[/IMG]

---

### Post by Favux on 2011-10-04
Sounds like Mark is correct then and the Catalyst drivers aren't available for your video chipset.  But definitely worth trying again.  Oneiric is due out in about 10 days and hopefully its OSS video driver will help.

For the Intuos3 the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") has some generic information on configuring the pad and a sample script in post #2. That would need to be modified as the HOW TO explains because your version of xsetwacom is more recent.  Also see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

For the screen mapping of the active area see the Linux Wacom Project's mediawiki:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)  The HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

Don't forget the built in manuals.  Enter in a terminal:
```
man wacom
or
man xsetwacom
```
to bring them up.

Oneiric has GNOME 3.2 which introduces the preliminary Wacom tablet cpl applet gui in System Settings.  The first version is limited and pretty much only let's you configure the stylus.  There are already more hooks for Wacom in the gnome-setting-daemon so hopefully the applet will become more capable quickly.  And with luck more hooks introduced.

---

### Post by leunam12 on 2011-10-04
> **westie457 said:**
> 1, In the bios set the default drive to the Ubuntu drive. Then open a terminal and type in ```
sudo update-grub
``` that should sort things to enable dual-booting and a Grub menu.

                     I did this, I changed the default boot drive to the Ubuntu drive (where GRUB was installed), I updated GRUB and restarted; but I still get the same results: I get a blinking cursor for about three seconds, then I get a red box with a blinking message that says "out of range"; this lasts for about twenty seconds; then I get the purple screen with Ubuntu on it and four orange dots underneath it; finally the system logs in to Ubuntu. The whole process takes less than one minute, but I never see the GRUB menu. I'm starting to think it's a video card compatibility issue.

Another thing that I tried was: I managed to extract the Ubuntu boot record and placed it on the Windows disk and edited the boot.ini file in Windows to include this option. Now if I boot from my primary disk I get the option to choose between Windows and Ubuntu, but if I choose Ubuntu all I get is a black screen with a blinking cursor and nothing happens.

Can I install GRUB on the Windows disk or will that leave me unable to boot Windows?

Thanks, for your help anyway.

---

### Post by leunam12 on 2011-10-04
> **westie457 said:**
> 
5 In Preferences > Keyboard Choose the one you want to keep, remove all others and click apply system-wide.
[]("http://ubuntuforums.org/tags.php?tag=wacom+tablet")
I have two keyboard layouts, one in English (on top) and the other in spanish; but there is a third one that always appears by itself, (USA alternate). I delete the Spanish and the alternate and keep only the USA layout and press "Apply system wide" and everything works fine, but when I reboot the **USA alternate** comes back, and, even though is not on the top, it takes over and and won't let me type apostrophes or quotation marks, the only way around it is to delete it every time I boot.

---

### Post by westie457 on 2011-10-04
> **leunam12 said:**
> I have two keyboard layouts, one in English (on top) and the other in spanish; but there is a third one that always appears by itself, (USA alternate). I delete the Spanish and the alternate and keep only the USA layout and press "Apply system wide" and everything works fine, but when I reboot the **USA alternate** comes back, and, even though is not on the top, it takes over and and won't let me type apostrophes or quotation marks, the only way around it is to delete it every time I boot.

Have you checked the language settings in System > Administration > Language Support and set the default to English (United Kingdom) in both tabs and applying System wide.

If I remember rightly I had to do this when I installed Natty. Reasonably sure I did not have to make any adjustments for Maverick.

---

### Post by leunam12 on 2011-10-08
I solved the keyboard problem by login out and choosing the keyboard layout that I wanted at login. Now that layout is always the default.

---

### Post by leunam12 on 2011-10-08
I will try the Ubuntu 11.10 to see if I have better video. Right now I've installed the catalyst driver and I lost 3D acceleration properties and the problem with the blurry fonts is not solved. However, I found a workaround: if I go to **system Settings > Monitors **and change the refresh rate to 70 instead of 60, hit apply and choose "restore previous configuration" at the prompt to go back to 60, everything gets really sharp. sometimes I have to do this twice but it always works.

---

### Post by leunam12 on 2011-10-15
Problems 1-4 were video card-related; i bought a new video card and they went away. I solved the keyboard issue re-installing Ubuntu and choosing USA as the keyboard (for some reason it defaults to USA alternate). I solved the Wacom problem with a script containing several xsetwacom commands; i set the script to run at boot time.

Thanks to all who helped me.

---

