---
title: "Stopping System V runlevel compatibility?"
date: 2011-07-19
forum: General Help
---

### Post by ojdon on 2011-07-19
Hi there, I've just installed gNatty 11.04 on my machine the first thing I've done is to update via the terminal:

> sudo apt-get update && sudo apt-get upgrade

All seemed fine but when I've gone to restart it gets stuck at this message while booting:

> Stopping System V runlevel compatibility

I've reinstalled but the problem is still occurring, Any help?

---

### Post by GolemdX on 2011-07-19
bump. this is a pretty serious problem, and I'm now getting it as well.

EDIT: so far, all things point to it being an graphics driver problem. will try this topic: [http://ubuntuforums.org/showthread.php?t=1744681](http://ubuntuforums.org/showthread.php?t=1744681)

EDIT2: maybe change the topic title to something related to 'boot hang after upgrade'? 'Stopping System V runlevel compatibility' isn't directly related to the problem...

EDIT3: How does pressing Control+Alt+F1, logging in, and running 'startx' work for you?

---

### Post by ojdon on 2011-07-20
But I'm running on an intel gma chipset. Would that still be a problem then?

---

### Post by GolemdX on 2011-07-20
it could possibly still be related to that... but maybe less of a chance now.

have you tried running startx?

---

### Post by ojdon on 2011-07-21
Yes I have, but it goes into fallback mode, I've also tried to downgrade xorg-server-video packages in Synaptic but it doesn't help. =\

---

### Post by mr.scotty on 2011-08-11
Same for me. An hour ago Ubuntu (natty 11.04) asked me for a dist upgrade and I allowed it ... big mistake ... now Ubuntu hang at "Stopping System V runlevel compatibility".
So I switched to the recovery console and tried vesa and radeon driver instead of fglrx, but no change.
Starting the x-server by startx makes the machine crashing totally.
My setup:
ubuntu 11.04
radeon 5570
radeon 5450

Since 9.04 ubuntu gets form version to version more instable..

---

### Post by crgutierrez on 2011-10-14
same problem
same intel chip

---

### Post by joneberger on 2011-10-14
Same difficulty.

Last night I got the option to upgrade distribution from 11.04 to 11.10.  So, I gave it that option and then staggered off to bed.

This morning I found the install stalled at installing a fonts package.  I finally killed the graphical installer and rebooted to a busted install (as warned!).  I moved to tty1, logged in, and called for the upgrades/updates.

After what seems like hours of pulling files, the machine reboots and hangs at the same error of "System V runlevel compatibility" being stopped.  I switch to tty1 and issue "startx".  The machine slowly loads Ubuntu Unity.  So far, twice, I've been asked to enter my keyring password at this step.

I, too, am running an Intel chipset.

---

### Post by vin1983 on 2011-10-14
I get the same problem. The update manager prompted me to update and wasted 20 hours of my life :(

I am really stuck.

Thanks a lot for any clue.

---

### Post by catmandog on 2011-10-14
What a pain. Acer desktop aspire x1700

11.10 upgrade stuck

Did the alt+ctrl+f1 then sudo startx worked -thanks

Then hit the upgrade center followed the partial upgrade.

On issue with the upgrade the netcomm wifi dongle lost connection 

Must say thankfully the iPad connected to Internet found this how to forum.

 I wish the upgrade would run a hardware test first..

I just hope all the computers I installed ubuntu have upgrades turned off..ahh

---

### Post by catmandog on 2011-10-14
Note: partial upgrade did not work -still got the V runlevel issues.

Even better sudo startx just gives me a black screen 

Crtl alt f1 gives no protocol specified

---

### Post by effenberg0x0 on 2011-10-14
@mr.scotty Search for my name plus ATI and you'll find a post with complete instructions for ATI.

@Other guys (intel)
```
sudo mv ~/.Xauthority.conf ~/.Xauthority.conf.old
sudo mv /etc/x11/xorg.conf /etc/x11/xorg.conf.backup
sudo killall /usr/bin/X
sudo service lightdm stop
sudo service lightdm start
```

Makes any difference?

Regards,
Effenberg

---

### Post by catmandog on 2011-10-15
From spending a few hours on this

Im just going to do the old

[http://www.youtube.com/watch?v=QGnsYuWS0xY](http://www.youtube.com/watch?v=QGnsYuWS0xY)[SIZE=1]
How-to Re-Install Ubuntu Linux 10.10 or 10.04 to Upgrade or Downgrade Linux Tutorial[/SIZE]

just dont have the time.

Thanks for all the help and comments. 

Next time this is a upgrade, do the live disk first. :P:popcorn:

---

### Post by ReZeeR on 2011-10-15
> @mr.scotty Search for my name plus ATI and you'll find a post with complete instructions for ATI.

@Other guys (intel)
 	Code:
 	sudo mv ~/.Xauthority.conf ~/.Xauthority.conf.old sudo mv /etc/x11/xorg.conf /etc/x11/xorg.conf.backup sudo killall /usr/bin/X sudo service lightdm stop sudo service lightdm start 
Makes any difference?

Regards,
Effenberg

It helped in a way, now i can successfully 'startx' but the original problem still remains

---

### Post by marcmolla on 2011-10-15
Same problem after 11.10 upgrade.

I can start the X system with startx (from tty 1) and work normally.
I can't start the system in safe mode because I've lost the menu where I could choice the kernel.
I tried also to remove the restricted driver (fglrx) but the result was the same...

Any ideas?

Thx!
Marc

---

### Post by marcmolla on 2011-10-15
My problem is solved by installing:
lightdm-gtk-greeter

It seems that version 11.10 replace gdm by lightdm start manager and because the version upgrade didn't install the greeter package, the new lightdm didn't work.

Four hours lost due to this silly issue :(

---

### Post by joneberger on 2011-10-15
This worked perfectly for me.  Thanks.

Jon

---

### Post by marrtys on 2011-10-16
worked for me too,
go to Ubuntu Software Centre > search ''lightdm'' > more info > add-ons > install "unity-greeter".
Problem solved
Thanks

---

### Post by Stepway on 2011-10-17
Hi another  gma chipset - on Dell 12 mini same problem! Rather than update, mine cuts in on the usb install. So the fix doesn't work at this stage.
It won't even run 11.10 from the flash drive. It stops during the Ubuntu 11.10 purple screen, has a brief message that begins with "B43-phyo error firmware file B43/uncode15.fw " then I end up with the  "Stopping System V runlevel compatibility screen"  
Should add 11.04 is fine. Any ideas?:confused:

---

### Post by IanVaughan on 2011-10-29
Got it working thanks to  marcmolla and > **marrtys said:**
> 
go to Ubuntu Software Centre > search ''lightdm'' > more info > add-ons > install "unity-greeter".
Problem solved
Thanks
After install it asks which greater you want, gdm or lightdm, I choose gdm, as thats what I wanted.

See also [http://ubuntuforums.org/showthread.php?p=11407278](http://ubuntuforums.org/showthread.php?p=11407278)

---

### Post by Stepway on 2011-10-30
Never did get to install from the flash drive, :( However I did a clean install of 11.04 (from a flash drive) & then upgraded to 11.10 from there. A bit strange, but it worked fine. I was expecting to apply a fix others used here.....no need. Even the standard graphics driver works in Unity for the 1st time! A first for a gma 500 I think!  :P

---

### Post by rrgalvao on 2011-11-02
> **marcmolla said:**
> My problem is solved by installing:
lightdm-gtk-greeter

It seems that version 11.10 replace gdm by lightdm start manager and because the version upgrade didn't install the greeter package, the new lightdm didn't work.

Four hours lost due to this silly issue :(
Solved for me too. Thank you all.

---

### Post by dc.ricardo on 2011-11-27
See if you have lightdm and lightdm-gtk-theme.
Installing gdm package helps.
Run dpkg-reconfigure gdm.

---

### Post by dbos on 2011-12-14
I think it's just what you see when X11 fails to start during the boot process. I just had the same issue but it had nothing to do with my chipset or graphics card. I went to the terminal with Ctrl-Alt-F1 and tried startx (which failed with some errors). I did have a bunch of fglrx errors from my nVidia graphics card (one for each PCI port), but under that was an error about being unable to write a keyboard configuration file. I then remembered that I was out of disk space. Freeing up some resolved the problem completely for me. I think the nVidia errors were just because it was scanning every PCI port for devices.

Hopefully this stops someone from needlessly reinstalling their OS or anything drastic like that over something so basic.

---

### Post by citricguy on 2012-01-16
Happens on Server installs as well, even without GUI running or even installed.

---

### Post by edony44 on 2012-01-26
Happens on server reboot too after update ,does somebody found a solution?

---

### Post by Turtle.net on 2012-02-14
> **edony44 said:**
> Happens on server reboot too after update ,does somebody found a solution?

Something is messing up the GDM conf.
As dc.radio suggested it, just running 
```
sudo dpkg-reconfigure gdm
```
did the trick for me.
Problem solved for me ... but doesn't explain why a server install without GUI should be affected.

---

### Post by ilongbow on 2012-04-13
gdm? but I do not have gdm installed on a server
I am hitting an issue on Natty x86_64 running inside Virtual Box - does not look to be a problem related to video drivers.

---

### Post by ant0n10 on 2012-04-17
same problem here, I'm installing from scratch, no GUI but I'm getting 

Stopping System V runlevel compatibility 

and hangs

EDIT: using 12.1 beta and it's working fine.

---

### Post by LeEmo86 on 2012-06-16
I hit this issue on 12.04 LTS for a different reason and wanted to share in case someone else had the same problem.

My issue was due to an incorrect mounting of a large storage drive. I tried to move a large amount of data to this drive and instead of the data going to the physical drive which -should have been- mounted /mnt/mountpoint the data was transferred to /mnt/mountpoint as a directory in my root filesystem, i.e. on my operating system's physical drive which did not have the capacity to cope with this. 

Therefore when trying to boot I was hitting the above issue because there wasn't enough physical space left on the operating system drive to boot properly.

I fixed it by <Ctrl> + <Alt> + <F1>, logging in and removing the files from the operating system disk by hand.

---

### Post by nuclearj on 2012-06-19
> **LeEmo86 said:**
> I hit this issue on 12.04 LTS for a different reason and wanted to share in case someone else had the same problem.

My issue was due to an incorrect mounting of a large storage drive. I tried to move a large amount of data to this drive and instead of the data going to the physical drive which -should have been- mounted /mnt/mountpoint the data was transferred to /mnt/mountpoint as a directory in my root filesystem, i.e. on my operating system's physical drive which did not have the capacity to cope with this. 

Therefore when trying to boot I was hitting the above issue because there wasn't enough physical space left on the operating system drive to boot properly.

I fixed it by <Ctrl> + <Alt> + <F1>, logging in and removing the files from the operating system disk by hand.

I had this same problem - when trying to log in it would just go back to the log in screen.  I'll try this out.

---

### Post by Bagustrix on 2012-06-24
Solved by using dpkg-configure lightdm or gdm.
It works for me.

---

### Post by aspacelot on 2012-07-31
> **dbos said:**
> I think it's just what you see when X11 fails to start during the boot process. I just had the same issue but it had nothing to do with my chipset or graphics card. I went to the terminal with Ctrl-Alt-F1 and tried startx (which failed with some errors). I did have a bunch of fglrx errors from my nVidia graphics card (one for each PCI port), but under that was an error about being unable to write a keyboard configuration file. I then remembered that I was out of disk space. Freeing up some resolved the problem completely for me. I think the nVidia errors were just because it was scanning every PCI port for devices.

Hopefully this stops someone from needlessly reinstalling their OS or anything drastic like that over something so basic.

Thanks a ton! You were right- this was my problem exactly. I had a Mint install on VMWare (Fusion on a 2011 MBA) and couldn't figure out why it wouldn't boot for the life of me. Turns out, I had have Dropbox on my install and synchronization of services on it filled the drive and wouldn't let it boot.

Thanks a ton- just a simple rm of some shared picture folders and I'm back at it. :-)

---

### Post by funicorn on 2012-08-02
> **aspacelot said:**
> Thanks a ton! You were right- this was my problem exactly. I had a Mint install on VMWare (Fusion on a 2011 MBA) and couldn't figure out why it wouldn't boot for the life of me. Turns out, I had have Dropbox on my install and synchronization of services on it filled the drive and wouldn't let it boot.

Thanks a ton- just a simple rm of some shared picture folders and I'm back at it. :-)

that's too bad. when doing this you really should assign disk quota to dropbox

---

### Post by whit on 2012-08-05
Just ran into that error on a 12.04 system, where I have things set not to boot into a GUI. Going to a different terminal allowed me to startxfce4 and things are normal except for that first terminal session being hung at "Stopping System V runlevel compatibility". 

Is some upgrade trying to overcome my lack of desire to have any GUI start on boot? (It's not that I don't use one. It's just that over the years I've learned it's the last thing to want a system to immediately go to.)

---

### Post by quadoss on 2012-09-07
I had removed gnome-core and then started to see this issue and by using <Ctrl> + <Alt> + <F1> and then sudo startx reinstalled gnome core and got to the login screen again.

---

