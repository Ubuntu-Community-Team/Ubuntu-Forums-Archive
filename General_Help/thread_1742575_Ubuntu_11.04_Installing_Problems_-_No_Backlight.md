---
title: "Ubuntu 11.04 Installing Problems - No Backlight"
date: 2011-04-29
forum: General Help
---

### Post by werdnazner on 2011-04-29
I am having a problem. There is no backlight in ubuntu 11.04. I know many have these problems but I cannot find a right solution. This the only time I encountered this problem, no problems in installing 9, 10.04, and 10.10.
First, I used a CD to install natty. I boot on the CD but after seeing Ubuntu 11.04 with loading dots for less than a second my screen went blank. Then I used a live usb but there's an error something. After reading some posts, they said it is only in the backlight. So I boot using the CD and went outside to see my screen clearly and boom I saw Try Ubuntu and Install Ubuntu. I clicked Try Ubuntu. Then my screen went blank and now I cannot see anything.
What is the solution for this one?
 
My system is:
Acer Aspire 4736
Intel P7350
Mobile Intel(R) 4 Series Chipset
4GB RAM
 
Edit: I have installed Ubuntu 11.04...but what is the use if I can't see my screen

---

### Post by JohnNestea on 2011-04-29
I have the same problem. However, I discovered that if I booted 11.04 while running on battery, the display lights up normally. 

Hope that helps.

---

### Post by werdnazner on 2011-04-29
Thank you...but it does not work for me. I can make out thing until login but after logging in I cannot see anything. Please help me please. I have an assignment that needs ubuntu. I already deleted my Ubuntu 9 and 10.
Also, I tried to install ubuntu 11.04. I opted for trial, and backlight is turned on his compaq laptop.
I like to use the acpi_backlight=vendor, but how? will I type it in the screen with grub>
but when I typed and press ESC, the problem is still there.
So, I wanna try to edit the grub file after logging in but I can't see anything on my screen after logging in but if I press my power button to force turn off my screen blinks and there's backlight for about a second then it turns off.

---

### Post by l3vity on 2011-04-29
I have the exact same problem, it's some kind of error with the latest kernel from what I can tell.
You have 3 options from what it seems,

1. Use something like a flash on a camera to open up terminal and type

```
sudo setpci -s 00:02.0 F4.B-0
```2. When booting select a different kernel to use. If you instantly auto-boot into the latest, pressing SHIFT while grub loads will open the menu. I am currently using the oldest kernel, which works fine.

3. Use a cable to connect to an external monitor.

I'm a complete ubuntu noob (my first ever udgrade) but have found these various solutions around the internet.

EDIT: Have now found a way to include the setpci code into boot.

select another kernel to boot so you dont have to mess around with the camera then...
```
gksudo gedit /etc/rc.local
```
this will probably be blank except some comments and an EXIT 0 at the bottom. Between the comments and the exit line, add
```
setpci -s 00:02.0 F4.B-0
```

You should now boot, after grub the backlight will go out, but should turn back on before log in.

---

### Post by souldr0p on 2011-04-29
I have an Aspire 5734z-4512, and I dual boot windows xp, everything looks fantastic until ubuntu boots...then no backlight...I don't get it...but will try the battery power thing to see if anything happens....using a flashlight to use this sucker is killin me..

---

### Post by souldr0p on 2011-04-29
> **souldr0p said:**
> I have an Aspire 5734z-4512, and I dual boot windows xp, everything looks fantastic until ubuntu boots...then no backlight...I don't get it...but will try the battery power thing to see if anything happens....using a flashlight to use this sucker is killin me..
 
Yeah, back to the xp side...no go....used a flashlight..no settings seem to turn the backlight on...it's like the backlight starts out on, then something loads before the ubuntu logo appears, and boom, it's black...  I haven't found a fix, but I'm going to try a few million things out and see which one works...

---

### Post by souldr0p on 2011-04-29
Before I upgraded, I had 10.10...so I got the flashlight out trying to install gnome again to see if that helps, cause unity looks pretty cool....but I really can't see it....and my cursor tracks faster than I thought....have to go slow...

---

### Post by souldr0p on 2011-04-29
> **souldr0p said:**
> Before I upgraded, I had 10.10...so I got the flashlight out trying to install gnome again to see if that helps, cause unity looks pretty cool....but I really can't see it....and my cursor tracks faster than I thought....have to go slow...

Nope, that didn't work...but I ran aptitude update && aptitude full-upgrade -y && reboot like I normally do, and rebooted and saw an option for previous kernels....and the previous kernel works great....unity desktop...and backlight is working...is there a bug submitted on this already??  I'm going to look into this now that I can....

---

### Post by werdnazner on 2011-04-30
This morning, I went out of our house to get sunlight.I don't have any flashlight. Also, it's a good thing that I am using a laptop what if this problem showed in our desktop and I have to bring it outside hahaha.
After booting, I wondered why my backlight is not turned off because it is working as bright as the sun. Now, I can use unity. However I thought to restart my laptop to see if my problem was really solved. But after booting backlight is turned off again. So restart again but no the problem is still there.
I logged in and typed on the terminal sudo gedit /etc/default/grub and added nomodeset acpi_backlight=vendor thingy with my eyes some centimeters away from the lcd so I can see what I am clicking and typing. And wow it worked but problem is that I cannot use unity, I cannot adjust brightness, and I cannot adjust my screen size.
I also tried dropping nomodeset, but the backlight is off so I reverted it back.
Now I went to recovery mode then failsafe and restart x, and unity is working with backlight. But after hibernating, the backlight is off again but after choosing faillsafe my screen got some light but very dim.
I don't know what to do...what's the real solution
 
Edit: I tried using setpci yeah it worked but I am in recovery mode now
Edit: I tried editing rc.local so i will not use stpci everytime but it destroyed my system, now I cannot go to restart x, it gives me a loop of pressing failsafex. Then I logged in using the non-recovery mode to fix rc.local but the problem still persists. So reinstalled natty.
So i think the solution here is that:
-log in recovery mode using failsafex
-to adjust the dimlight, type sudo setpci -s 00:02.0 F4.B=0
 (the '0' after the equal sign can be adjusted with zero being the brightest and with f as no light at all)
 
cons:
-you cannot adjust the brightness by pressing fn+whateverkey
-you will enter setpci each time you log-in
 
pro:
-though tiresome to do, it is the safest way to do without the fear of changing your grub files or any system files and messing up your system
-you're screen will not be resized to 4:3

---

### Post by glococo on 2011-05-02
Hi,

The best workaround was:

Autorun "setpci -s 00:02.0 F4.B=00" each boot.

Steps:
1) edit rc.local

```
gksudo gedit /etc/rc.local
```

2) Add the command before EXIT 0

```
setpci -s 00:02.0 F4.B=00
```

3) Restart.

You should now be able to boot in UNITY where "nomodeset" was unable.
(ps: **nomodeset** is not a good solution)

---

### Post by Chris2243 on 2011-05-02
Thought I would let you know, I found this thread

[http://ubuntuforums.org/showthread.php?t=1743301]("http://ubuntuforums.org/showthread.php?t=1743301")

Using arrow keys to scroll down I added "acpi_osi=Linux kernel" (without quotes) at the bottom, press enter and then F10 to boot. I had already edited rc.local

Sorted it for me, hopefully will for you.

Chris

Edit: It doesn't work after suspend, brightness has to be turned up using function keys. Alternatively boot into a previous version, there are no issues with 2.6.35

---

### Post by souldr0p on 2011-05-12
> **glococo said:**
> Hi,

The best workaround was:

Autorun "setpci -s 00:02.0 F4.B=00" each boot.

Steps:
1) edit rc.local

```
gksudo gedit /etc/rc.local
```2) Add the command before EXIT 0

```
setpci -s 00:02.0 F4.B-0
```3) Restart.

You should now be able to boot in UNITY where "nomodeset" was unable.
(ps: **nomodeset** is not a good solution)

This is an excellent workaround that actually works.  I've had to remote into my own computer to use it..

---

### Post by euchrid on 2011-06-15
I had the same problems with an Acer Aspire 5336, and the above solution *mostly* worked for me.

At first, I thought this was a driver (Nvidia or Intel) problem, and did not even know about backlights or that they could be turned off...

I agree with glococo that 'nomodeset' was not a good solution - I found that the screen resolution was well off, impossible to put right, and rendered many programs unusable.

Putting "setpci -s 00:02.0 F4.B-0" in rc.local got the backlight on at boot, but whenever the screen shut off after inactivity, I had to enter the code in a terminal again - in the dark, reading the screen with a torch.

My workaround was to create the following bashcript:
```
#!/bin/bash
sudo setpci -s 00:02.0 F4.B-0
```
I then created a keyboard shortcut for the file (I did this in Fluxbox).

However, the script has to be run as root (or sudo), so I then had to edit the sudoers file (/etc/sudoers), using 'sudo visudo' (this is the ONLY way you should edit the file).

Under the part that reads "# Allow member of the group sudo to execute any command", I added this line:
```
%usergroup ALL=(ALL) NOPASSWD: ALL
```
Replace '%usergroup' with your own group name.

The only problem with this is that now all member of the group are able to execute ALL sudo commands without entering a password. Not a problem for me, as I'm the only one using the laptop, but it can cause problems with other programs that need/use sudo or gksudo.

Supposedly, I should have been able to put the line
```
%username ALL=(ALL) NOPASSWD: /path/to/bashscript/
```
into 'sudoers', but it just wouldn't work for me - sudeors would not accept it, no matter how I changed the syntax.

Be VERY careful when editing sudoers - any mistakes will mean you can't use sudo AT ALL unless you log into a recovery session as root and edit the file through nano or vi... I found, while making sure sudoers worked, that it was best to have a file manager (Thunar, in my case) open with gksudo - that way, I was able to go back to /etc/sudoers and return it to its normal state. 

To check if the sudoers file is OK, just run 'sudo visudo', which will either return an error or allow you to edit the file (which means everything is OK). If all you get is an error, then, if you are already logged into a file manager as root/sudo or have the file open in a text editor as root/sudo, then you need to put it back to how it was.

I hope this helps someone - it is an annoying workaround for a ridiculously irritating problem. I suspect it is something in the latest kernel, as it's never happened before. Hope this helps someone else, and I hope this gets fixed in the next kernel!

---

### Post by Dipper on 2011-06-24
> **souldr0p said:**
> This is an excellent workaround that actually works.  I've had to remote into my own computer to use it..

That didn't work.  I still have no backlight.

---

### Post by travissparks1307 on 2011-08-21
This is a confirmed bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/826386]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/826386")

Head over and let the developers know it affects you. The more people who report this thing, the more likely it will be fixed in time for Oneiric Ocelot. There is another thread about this exact same thing

[http://ubuntuforums.org/showthread.php?t=1729064]("http://ubuntuforums.org/showthread.php?t=1729064")

Maybe one of the admins or moderators could merge, bump, or whatever, and help consolidate this info?

---

### Post by jibon_24 on 2011-09-12
You can use  cron job this will run the script for every 1 second. You can follow this:

1. Go to home folder & create a script at any name. For example : "display"
&& write this code:
[PHP]
#!/bin/bash
while [ true ]; do
sleep 1
sudo setpci -s 00:02.0 F4.B=0
done
[/PHP]2. Go to terminal & write:

[HTML] sudo crontab -e[/HTML]& select 2 if you first time.

3. Now write this line at the end :

[HTML]
*/1 * * * *  sudo sh /home/YOUR NAME/display
[/HTML]4. Now ctrl+O && then ctrl+x

Enjoy :popcorn:

---

### Post by atomicspin on 2011-10-24
> **l3vity said:**
> I have the exact same problem, it's some kind of error with the latest kernel from what I can tell.
You have 3 options from what it seems,

1. Use something like a flash on a camera to open up terminal and type

```
sudo setpci -s 00:02.0 F4.B-0
```2. When booting select a different kernel to use. If you instantly auto-boot into the latest, pressing SHIFT while grub loads will open the menu. I am currently using the oldest kernel, which works fine.

3. Use a cable to connect to an external monitor.

I'm a complete ubuntu noob (my first ever udgrade) but have found these various solutions around the internet.

EDIT: Have now found a way to include the setpci code into boot.

select another kernel to boot so you dont have to mess around with the camera then...
```
gksudo gedit /etc/rc.local
```
this will probably be blank except some comments and an EXIT 0 at the bottom. Between the comments and the exit line, add
```
setpci -s 00:02.0 F4.B-0
```

You should now boot, after grub the backlight will go out, but should turn back on before log in.

Thanks for this!  Is there a place I can put the same code so that when it comes back from the screensaver/display off that it will turn the backlight on again?  

Thanks!

---

