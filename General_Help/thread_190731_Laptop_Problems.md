---
title: "Laptop Problems"
date: 2006-06-06
forum: General Help
---

### Post by mapage on 2006-06-06
I have a Toshiba Tecra M4 tablet/laptop computer that I have installed Ubuntu on.  For the most part I am very happy to have scrubbed that Microsoft virus off of it, but I am having a couple of problems that I hope someone here can help me with.

Like a lot of people, I can't seem to make it suspend/wakeup correctly. Is there anyone out there that has this working? If so, how? Hibernate doesn't work either.  When I suspend, the power lights stay on as do the fans and it never actually powers down.  I have to hold the switch to get it to shut off and then when it starts back up it doesn't restore.  Most of the time it boots normally, but last time I got a blank black screen and nothing would work.

I can't switch screen resolutions in X. This includes jumping to a virtual terminal (ctrl-alt f1-f6) The screen blanks and won't easily comeback. (ctrl-alt-f7 then ctrl-alt-backspace seems to bring it back )

I've added additional screen resolutions to the xorg.conf but I am stuck at the default 1400x1050 no matter what I do.

Also, another weird problem I've been having is that if I restart my computer, I get error messages that the video driver isn't receiving interupts from the video card or that the driver isn't responding when X tries to start.  I can get the exact error message if anyone cares to see it.  If I shut the computer down completely then X starts normally.

I think I may have multiple issues here, but they could all be symptoms of one greater problem.

Thanks for the time.

 - Matt

---

### Post by givré on 2006-06-06
[QUOTE=mapage]Is there anyone out there that has this working? If so, how? Hibernate doesn't work either.[/QUOTE]
Yeh it's work perfectly for me, but it's really depend of the hardware. Try to fill a big there [https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug) with your caracteristic 
[QUOTE=mapage]
I can't switch screen resolutions in X. This includes jumping to a virtual terminal (ctrl-alt f1-f6) The screen blanks and won't easily comeback. (ctrl-alt-f7 then ctrl-alt-backspace seems to bring it back )
[/QUOTE]
What is your graphic card?

---

### Post by mapage on 2006-06-06
GeForce Go 6600  I have the Nvidia drivers installed. (1.0-8762)

---

### Post by givré on 2006-06-06
Did you follow that howto
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
Also, i found something about nvidia and suspend
[https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend)

---

### Post by mapage on 2006-06-06
Yeah...  The nvidia driver seems to be fine.  At least accelerated 3d works.

I tried what was mentioned in the second link, but it didn't work.  The suspend-to-ram (like it said) doesn't work.  Same behavior with the black screen.  

Suspend to disk was a little different.  The screensaver immediately came on, the screen blinked a couple times and then I got the unlock screen dialog.

---

### Post by givré on 2006-06-06
[QUOTE=mapage]
Suspend to disk was a little different.  The screensaver immediately came on, the screen blinked a couple times and then I got the unlock screen dialog.[/QUOTE]
Good, that's how it should work.

For the other problem, can't really say, you should try reconfiguring xorg
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mapage on 2006-06-06
I don't think suspend to disk is supposed to work that way...  It never actually powered down.

---

### Post by H.E. Pennypacker on 2006-06-06
> When I suspend, the power lights stay on as do the fans and it never actually powers down

Suspend is the Windows equivalent of Stand by.  It doesn't mean that you're turning off the computer.  It simply means that you are limiting the number of resources you are using.  The lights are supposed to stay on, because the system did not shut down or otherwise turn off.

Why doesn't hibernation work?  Click on the red shut-down button on your right top corner, and select Hibernate.  What happens when you do that?  Ideally, when you select hibernate, the system will take a minute to store the session (so that the next time you start, everything's back to normal), and then it will turn off the system (desktop, laptop, etc.).  The next time you want to use your computer, you press the power-button, and once again, select Ubuntu from the GRUB list, and after you log-in to Ubuntu, the session is re-loaded.

---

### Post by mapage on 2006-06-07
What I want the computer to do when I click the suspend button is the same as what it does in Windows when I click the suspend button.  The entire system powers down except for the ram.  The power light should slowly strobe on and off while it is in suspend/standby or whatever-you-want-to-call-it mode.  When I hit the power button or open the laptop lid, it should come back to life and return me to the screen I was looking at when I hit suspend or closed the laptop lid.

What it IS doing is blanking my screen and making it so I have to either kill X if I'm lucky or shutting off power to the laptop by holding the power switch.  Not exactly useful.

Here is what happens when Hibernate is selected after clicking the red button.
Screen fades
screensaver comes on
screen goes blank
disk spins for a while
screen flickers
disk spins some more
the login screen comes up as if the screen were locked and I moved the mouse
It never powers down at all.

---

### Post by givré on 2006-06-07
Sorry guy, i didn't really read clearly what you said, it was late :rolleyes: 
And what done sudo dpkg-reconfigure xserver-xorg ?

---

### Post by mapage on 2006-06-07
Haven't done that...  Will it break the nvidia driver install at all?

---

### Post by givré on 2006-06-08
Check this howto:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
> 5) If you have problems with the Resolution and/or Refresh rate of your display, please do the following steps OR follow this excellent guide by Heimo HOWTO: change resolution/refresh rate in Xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

When it asks you about your graphic card select it manually (don't do autodetect).

Select the "advanced" when it asks you about the refresh rate (make sure you know the horizontal and vertical refresh rate supported by your monitor (try in google or if you have a manual of the monitor) OR use "autodetect" (the easy one).

It will ask you your desired resolutions, select the ones you need by pressing the SPACEBAR.

If you don't know how to answer the other questions you can use the suggested answers (which will work) by pressing ENTER (without typing anything).

After you finish, log out and press CTRL+ALT+BACKSPACE

Log in and see if everything is displayed correctly and if your card is well detected. 

EDIT:the excellent howto he speak about is there [http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

### Post by mapage on 2006-06-08
Did the reconfig.  All it appears to have bought me is that I can now switch to 1280x1024 instead of being stuck at 1400x1050.

---

### Post by testube_babies on 2006-06-08
[QUOTE=mapage]...includes jumping to a virtual terminal (ctrl-alt f1-f6) The screen blanks and won't easily comeback. (ctrl-alt-f7 then ctrl-alt-backspace seems to bring it back)...[/QUOTE]

This is a common problem on nVidia laptops.  Check out this thread for a possible fix (it worked for me):
[http://www.ubuntuforums.org/showthread.php?t=127277](http://www.ubuntuforums.org/showthread.php?t=127277)

---

### Post by mapage on 2006-06-08
That worked.  One down, several more to go...  *Sigh*

---

### Post by 23meg on 2006-06-08
Suspend and hibernate don't work on my Tecra M4 either. It's a kernel ACPI issue and won't be resolved unless support arrives in the kernel. You may want to try [compiling a more recent kernel]("http://www.ubuntuforums.org/showthread.php?t=157560") and see if that helps.

For changing resolutions, check [this]("http://doc.gwos.org/index.php/ChangeResolution") out.

---

### Post by mapage on 2006-06-08
Do you have any problems with your display only having one resolution?  What range do you use for vertical and horizontil refresh?  I changed those settings but it didn't give me any more resolution options.  I also added a bunch of modelines that should give something, but I still only have the original resolution for the LCD.  (Haven't worked on the external display at all.)

---

### Post by 23meg on 2006-06-08
Yes, by default I only have the native 1400x1050 selectable but I have no problems with that (non-native resolutions will always look blurred) so I didn't change anything. 

Here's my current xorg.conf "Monitor" section:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-70
        VertRefresh     43-60
EndSection

```

If you're having problems with the instructions in the guide, you may want to ask for help in [this thread]("http://ubuntuforums.org/showthread.php?t=83973").

---

### Post by cleentrax on 2006-06-08
The Ubuntu wiki helped me. Maybe it will work for you...

wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend

---

### Post by mapage on 2006-06-08
Hmm...  I think I'm going to give up on the multiple resolutions.  Not a big deal.  I am having trouble getting Cedega to work and I think it's because there isn't a display resolution available that matches what it's trying to play the games at...  if that makes any sense.  

Also going to give up on the suspend/hibernate support for the time being.  It's annoying that it works for other laptops but not the M4.

So the only other problem that I am having that was mentioned in the original post is that when I restart my computer, X won't come up.  I have to shut it down and then start the computer to get it back.  Strange.  Something is messed.  I take it you don't share that experience?  

Also, recently when the computer is shutting down, I get the xubuntu logo instead of the ubuntu logo.  Strangeness will never end, seemingly.

---

### Post by mapage on 2006-06-08
[QUOTE=cleentrax]The Ubuntu wiki helped me. Maybe it will work for you...

wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend[/QUOTE]


I think the first line of the wiki entry summarizes my experience with the entry...

NOTE: Suspend-to-RAM does not seem to work with Ubuntu Linux 6.06 "Dapper Drake" (at least not by following the directions given on this page).

:(

---

### Post by cleentrax on 2006-06-08
[QUOTE=mapage]Hmm... 

Also going to give up on the suspend/hibernate support for the time being.  It's annoying that it works for other laptops but not the M4...[/QUOTE]


Don't give up until you try the above fix from the Ubuntu Wiki.

---

### Post by cleentrax on 2006-06-08
[QUOTE=mapage]I think the first line of the wiki entry summarizes my experience with the entry...

NOTE: Suspend-to-RAM does not seem to work with Ubuntu Linux 6.06 "Dapper Drake" (at least not by following the directions given on this page).

:([/QUOTE]

The directions on the page worked in Dapper for me, but I have exactly the  same  computer as the  creator (Inspiron 8600).

---

### Post by mapage on 2006-06-09
Hmm...  I set the computer to suspend (again) and this time just let it go overnight.  At some point it did power down (power led was slowly strobing) and when I hit the power button, I saw for a split second a 'LINU' at the top of the screen.  The screen went blank and then came back with a screen full of vertical lines.  Nothing is visible through the lines and they are stable.  (Unlike the lines you get if the refresh rate is to great)

So far none of the usual key combos works (ctrl-alt-f1-f6 or ctrl-alt-bksp)  I tried blindly typing in my username/password combo in case I was sitting at the login screen.  Nothing I have done has made the hard drive twitch at all. (The led never comes on.)

In the end, I had to hold the power switch and kill it the hard way...

---

### Post by mapage on 2006-06-09
In case anyone is curious, it took about 6 minutes for the computer to completely go into standby mode.  Not exactly lightning quick.  Same story with the lines when I powered it back up.

Hibernate is behaving differently also...  The first time I selected it, nothing happened.  Screen blanked and then came back.  Didn't even lock the console like it normally does.  Second time, the screen saver came up then it switched to some sort of text mode and said that it couldn't find the swap and I should try swapon -a, the third time the same thing happened but the message was longer.  I don't know if it was the same message twice or just a longer message.  It flashes by quick enough that I can't read more than a line and I don't have a chance to print screen or copy text.  Should probably check the logs.  Anyway, after the error message the second time, the screen locked.  The second time the screen went black and the caps-lock light is blinking and the computer has become unresponsive.  I will wait ten minutes or so to see if it powers off like it does with suspend before I start trying to get my screen back.

It's strange, but I feel like this is progress.

Note:  Computer still brain dead after 10 minutes.

---

### Post by 23meg on 2006-06-09
FYI: I just compiled a 2.6.16.20 kernel and suspend and hibernate still don't seem to work on the M4.

---

### Post by 23meg on 2006-06-09
> Also, another weird problem I've been having is that if I restart my computer, I get error messages that the video driver isn't receiving interupts from the video card or that the driver isn't responding when X tries to start. I can get the exact error message if anyone cares to see it. If I shut the computer down completely then X starts normally.Try booting with the "irqpoll" kernel option.

---

