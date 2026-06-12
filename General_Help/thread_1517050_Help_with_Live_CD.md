---
title: "Help with Live CD"
date: 2010-06-24
forum: General Help
---

### Post by Viperman0986 on 2010-06-24
I have followed the instructions on this website :  [http://samiux.blogspot.com/2010/05/howto-fix-blank-screen-on-ubuntu-1004.html](http://samiux.blogspot.com/2010/05/howto-fix-blank-screen-on-ubuntu-1004.html)

I am having the problem of blank screen on startup using an intel integrated gpu in ubuntu 10.04.  However, with the live cd, the computer boots up fine.  I need the computer to be able to display properly without the live cd.

I need help with some of the steps in that link.  How do I mount the hard drive at the "place" like it states I should do:
[I]
[B]Step b :
After bootup, mount the hard drive at the "Place".[/B][/I] 

I just need someone to clarify the steps that link is suggesting I do.

Thank you.

---

### Post by Viperman0986 on 2010-06-25
if anyone doesnt understand what my problem is with the live cd, please just ask. 

bump

---

### Post by hansdown on 2010-06-25
Hi Viperman0986.

The way they word that, is somewhat cryptic.

In the top corner of the screen, click "places", then click on the drive that your install is on.

---

### Post by Viperman0986 on 2010-06-25
> **hansdown said:**
> Hi Viperman0986.

The way they word that, is somewhat cryptic.

In the top corner of the screen, click "places", then click on the drive that your install is on.


wow, that was REALLY cryptic.  Thanks for deciphering it!:lolflag:

---

### Post by hansdown on 2010-06-25
> **Viperman0986 said:**
> wow, that was REALLY cryptic.  Thanks for deciphering it!:lolflag:

No problem.

Hope all goes well.

---

### Post by Viperman0986 on 2010-06-26
Hansdown,

thanks for the help, ive been trying to get 10.04 on this system since its release LOL

Here's an update if it makes any sense cause i need some sleep....:(

well, it was going well... So long story short, Ive been dealing with intel 865G integrated graphics issues since 9.10 and until today I havent been able to boot to desktop.  YAY, little success!! I found a work around but am having trouble editing the grub. Well, I edit it in terminal like the website says to but idk how to exit and save....i try "^X" but its a nogo. idk what to do..Unlike the website above, I am not using the live cd so i didnt have to mount the HDD yet.  Not sure if thats the problem. 

So to FINALLY boot into desktop I used this post to config the xorg file but mabe i screwed it up...lol
[http://ubuntuforums.org/showthread.php?t=1465883&page=4](http://ubuntuforums.org/showthread.php?t=1465883&page=4)

To tell you the truth, i dont even know if this is a real work around cause im being forced to use a crt cause my lcd says "out of range" and goes to sleep.  Im thinking that once I get 10.04 working on the  old crt properly, then i should be able to tackle the lcd issue.

any thoughts?

I'm willing to start over if you think its necessary.  This was a clean install as well, I wiped Karmic off and it wasnt an upgrade.

Also, Ive ran Update Manager and it downloaded ALL 203 updates since 10.04 was released and hasnt helped yet.

-Vip

---

### Post by hansdown on 2010-06-26
It's a good idea, to have an active internet connection, when installing, because some packages will be installed.

You should be using the 

```
xserver-xorg-video-intel
```

driver. It is the same one for my onboard graphics.

What is the make and model of your lcd monitor?

---

### Post by Viperman0986 on 2010-06-26
the lcd i am using is some company named X2gen...:P  Srry but this computer is for my parents and they are pretty cheap lol

-I'll try to download the package u suggested.

---

### Post by Viperman0986 on 2010-06-26
i just realized that we do have a sharp aquos lcd tv that i can try to hook it up on if it makes a difference?  Let me know if you think that will help.

thanks

---

### Post by Viperman0986 on 2010-06-26
> **hansdown said:**
> It's a good idea, to have an active internet connection, when installing, because some packages will be installed.

You should be using the 

```
xserver-xorg-video-intel
```driver. It is the same one for my onboard graphics.

What is the make and model of your lcd monitor?


I just typed "xserver-xorg-video-intel in synaptic and for me its saying i have both "intel" and "i740" installed.

Also i noticed when i typed in "xserver-xorg-video" a lot of other things were installed as well. is that normal?

---

### Post by hansdown on 2010-06-26
> **Viperman0986 said:**
> the lcd i am using is some company named X2gen...:P  Srry but this computer is for my parents and they are pretty cheap lol

-I'll try to download the package u suggested.

Can you pick it out, here?

[http://www.fixya.com/support/x2gen](http://www.fixya.com/support/x2gen)

One of the problems with one 19" X2gen monitors, was a bad invertor.

---

### Post by hansdown on 2010-06-26
> **Viperman0986 said:**
> I just typed "xserver-xorg-video-intel in synaptic and for me its saying i have both "intel" and "i740" installed.

Also i noticed when i typed in "xserver-xorg-video" a lot of other things were installed as well. is that normal?

The i740 is for a different chipset.

I suspect, that most of those are not needed.

---

### Post by Viperman0986 on 2010-06-26
> **hansdown said:**
> Can you pick it out, here?

[http://www.fixya.com/support/x2gen](http://www.fixya.com/support/x2gen)

One of the problems with one 19" X2gen monitors, was a bad invertor.


The model of my monitor is MW19R but i know that the monitor is working properly.  I've used it for booting into windows recently so hardware isnt faulty, not yet at least!

For the display drivers, I removed the intel i970 driver and the vesa driver and it seems we are getting somewhere!  I do not see a desktop but here is a list in order of what I see, one set for the LCD monitor and the other set for the CRT monitor.

When connected to LCD
1. Bios
2. flashing "_" on the top left of the screen
3. "Out of Range" message
4. monitor goes to sleep and I do not see desktop
5. I press the power button and hit "enter" on keyboard and computer shuts down successfully. Nothing is displayed.

When connected to CRT
1. Bios
2. Flashing "_" on the top left of the screen
3. there is NO "out of range" message, it just goes to sleep
4. again no desktop is displayed
5. when I press the power button and hit "enter" on keyboard, monitor wakes up and displays UBUNTU splash image before shutting down.

Now the only way ive been able to boot into desktop until now is using these steps when connected to CRT, these steps do not work when connected to LCD
1. hold down shift after bios loads
2. at GRUB menu hit "e"
3. second to last line, delete "quiet splash" and insert "i915.modeset=0"
4. Ctrl + X to restart
5. ubuntu desktop boots up after text is displayed!

Thanks again Hansdown!

---

### Post by Viperman0986 on 2010-06-26
I forgot to mention that i was worried that I screwed up the xorg.conf file so I did a complete reinstall of 10.04.  I typed this into terminal "cat /etc/X11/xorg.conf" and its stating that "no such file or directory"!!!!

I researching how to fix that now as well!

---

### Post by Viperman0986 on 2010-06-26
> **Viperman0986 said:**
> The model of my monitor is MW19R but i know that the monitor is working properly.  I've used it for booting into windows recently so hardware isnt faulty, not yet at least!

For the display drivers, I removed the intel i970 driver and the vesa driver and it seems we are getting somewhere!  I do not see a desktop but here is a list in order of what I see, one set for the LCD monitor and the other set for the CRT monitor.

When connected to LCD
1. Bios
2. flashing "_" on the top left of the screen
3. "Out of Range" message
4. monitor goes to sleep and I do not see desktop
5. I press the power button and hit "enter" on keyboard and computer shuts down successfully. Nothing is displayed.

When connected to CRT
1. Bios
2. Flashing "_" on the top left of the screen
3. there is NO "out of range" message, it just goes to sleep
4. again no desktop is displayed
5. when I press the power button and hit "enter" on keyboard, monitor wakes up and displays UBUNTU splash image before shutting down.

Now the only way ive been able to boot into desktop until now is using these steps when connected to CRT, these steps do not work when connected to LCD
1. hold down shift after bios loads
2. at GRUB menu hit "e"
3. second to last line, delete "quiet splash" and insert "i915.modeset=0"
4. Ctrl + X to restart
5. ubuntu desktop boots up after text is displayed!

Thanks again Hansdown!


Here is an update to this post.  I figured out how to update grub and save the file.  All i had to do was hit Ctrl +X to exit and save changes to grub then sudo update-grub.  So now everything is running smoothly with the CRT monitor. I see a desktop and splash images and everything!!!!:guitar:
So now moving on to having ubuntu displaying correctly on LCD!!!

Here is an update of what i see when connected to the LCD monitor:

1. Bios
2. Flashing "_" at top left
3. Ubuntu splash image flashes for a couple seconds the way its supposed to.
4. Monitor "out of range" message and monitor goes to sleep
5.  Cannot see desktop nothing is displayed.
6.  I hit the power button since I know the computer is booted to desktop but just not displaying it!
7. Press enter on keyboard, still nothing is displayed yet
8. Monitor wakes up and displays Ubuntu splash screen again before shutting down correctly.

So the only problem with the LCD is the desktop not being displayed!!!!!

I REALLLY hope its a simple fix...lol
 
thanks,

-VIp

---

### Post by hansdown on 2010-06-26
> **Viperman0986 said:**
> I forgot to mention that i was worried that I screwed up the xorg.conf file so I did a complete reinstall of 10.04.  I typed this into terminal "cat /etc/X11/xorg.conf" and its stating that "no such file or directory"!!!!

I researching how to fix that now as well!

I think the way to access it has been changed.

See this thread.

[http://www.uluga.ubuntuforums.org/showthread.php?t=634435](http://www.uluga.ubuntuforums.org/showthread.php?t=634435)

The recommended resolution for this monitor, is 1280x768.

The optimum, is 1440x900.

Stick with the first, for now.


[http://www.google.com/search?client=ubuntu&channel=fs&q=optimum+resolution+for+x2gen+MW19R+&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=optimum+resolution+for+x2gen+MW19R+&ie=utf-8&oe=utf-8)

---

### Post by Viperman0986 on 2010-06-26
> **hansdown said:**
> I think the way to access it has been changed.

See this thread.

[http://www.uluga.ubuntuforums.org/showthread.php?t=634435](http://www.uluga.ubuntuforums.org/showthread.php?t=634435)

The recommended resolution for this monitor, is 1280x768.

The optimum, is 1440x900.

Stick with the first, for now.


[http://www.google.com/search?client=ubuntu&channel=fs&q=optimum+resolution+for+x2gen+MW19R+&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=optimum+resolution+for+x2gen+MW19R+&ie=utf-8&oe=utf-8)

hmm, thanks for the info 

according to this, looks like they got rid of that file all together in 9.10 so i need to create one for that resolution?

[http://superuser.com/questions/141802/where-is-xorg-conf-in-ubuntu-10-04](http://superuser.com/questions/141802/where-is-xorg-conf-in-ubuntu-10-04)

---

### Post by hansdown on 2010-06-26
> **Viperman0986 said:**
> hmm, thanks for the info 

according to this, looks like they got rid of that file all together in 9.10 so i need to create one for that resolution?

[http://superuser.com/questions/141802/where-is-xorg-conf-in-ubuntu-10-04](http://superuser.com/questions/141802/where-is-xorg-conf-in-ubuntu-10-04)

If you follow this, it should work.

[http://www.uluga.ubuntuforums.org/showthread.php?t=634435](http://www.uluga.ubuntuforums.org/showthread.php?t=634435)

---

### Post by Viperman0986 on 2010-06-26
> **hansdown said:**
> If you follow this, it should work.

[http://www.uluga.ubuntuforums.org/showthread.php?t=634435](http://www.uluga.ubuntuforums.org/showthread.php?t=634435)

alright, so i tried to run the command "sudo dpkg-reconfigure -phigh xserver-xorg" after ctrl +alt +F1 but it says my login is incorrect.  Is there a different default password that I dont know about?

---

### Post by Viperman0986 on 2010-06-26
good news....Finally GOT a full startup to work on the LCD!!!! Ive restarted about 5 times, fully shut down and restarted twice and its working great!  All i had to do was mess with the resolutions while the crt was connected.   Then I clicked on the "Detect Monitors" button in preferences.

One final nuisance is that when ubuntu is at the desktop, the image is off center so i have to hit the "auto" adjust button on my lcd in order for it to center up.  I have to do that everytime it boots up.  

Any ideas Hansdown?

---

### Post by hansdown on 2010-06-26
Good job Viperman0986!

I admire your persistence.

I'll check, but that one is new for me.

Great work!

---

### Post by Viperman0986 on 2010-06-26
> **hansdown said:**
> Good job Viperman0986!

I admire your persistence.

I'll check, but that one is new for me.

Great work!


well, having someone to shoot ideas with definitely helped!!!  

seriously, thanks a bunch!!!!:p

---

