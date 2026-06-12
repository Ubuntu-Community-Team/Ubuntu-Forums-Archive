---
title: "Is my Installation corrupted?"
date: 2011-06-24
forum: General Help
---

### Post by radiosgalore on 2011-06-24
I upgraded from Ubuntu 10.04 via an old CD then right to 10.10 and 11.04 a few months back. Immediately there were issues.

Unity wouldnt work despite getting a command line off another forum. right-clicking the desktop and the tab to adjust the display settings was missing. the latest update removed google chrome and knocked me off the internet. I'm also unable to access the little internet icon on the panel to see whats going on. I know almost nothing about command lines so please keep it simple. i'm using an old 10.04 live CD to post this btw. 

thanks in advance. really should stop messing but i never learn

---

### Post by Esspwebbb on 2011-06-24
This problem may be due to any virus attack.There are many useful anti-virus software available in the market .Try any one and get rid of this problem.

---

### Post by dino99 on 2011-06-24
if you can get the grub menu (hold "shift" key down at bios end process to see it) then boot on "recovery mode" and select "repair packages"

if it fail, then better to do a clean install again

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by radiosgalore on 2011-06-24
i can't get online to download anything. as for the GRUB menu isnt that only when you have multiple operating systems? this is 100% linux

I tried to download a copy of 11.04 and burn to CD while it was still a beta to show my brother and it refused to do so. Also refused to let me install meaning i had to wipe 10.10, install 10.04 via CD and upgrade twice to 11.04. Not sure if i was using the wrong link or version or what

---

### Post by dino99 on 2011-06-24
grub is needed of course, as its the bootloader (all Os on earth need one)

---

### Post by haqking on 2011-06-24
> **Esspwebbb said:**
> This problem may be due to any virus attack.There are many useful anti-virus software available in the market .Try any one and get rid of this problem.

Viruses are not a major issue in Linux as is widely known, there are some out there but Linux and its security model is not as susceptible to them as Windows environments.

Virues are rare in the Linux World, as for AV software, you mention there are lots out there, yes for Windows, for Linux there are not too many mainly because they are not needed that often, the main players being Avast and ClamAv in the linux world.

None of his problems are likely to be Virus related, his issues appear to be more a case of corrupt packages that are in need of repair or a fresh install

---

### Post by dino99 on 2011-06-24
> **Esspwebbb said:**
> This problem may be due to any virus attack.There are many useful anti-virus software available in the market .Try any one and get rid of this problem.

:( :( virus are mainly in front of the computer, between chair & lid :) :)

---

### Post by radiosgalore on 2011-06-24
> **dino99 said:**
> :( :( virus are mainly in front of the computer, between chair & lid :) :)

in my case oh yes. I will insist on messing with things i don't understand properly. right lets see if i can get something done 

*crosses fingers*

---

### Post by radiosgalore on 2011-06-24
hmmmm well... got to where is said GRUB menu loading then gave me an out of range message. Did the same when I tried to upgrade direct from 10.10 to 11.04 beta as it was then. Hence me having to get rid of the lot and use my old 10.04 CD. even CTRL+ALT+F3 didnt get me into the command line this time. Used to give the same out of range message then auto-correct and load the GUI. Now it doesnt even do that

---

### Post by JKyleOKC on 2011-06-24
Since you are running from a 10.04 live CD, the quickest way to make the machine functional again would be to simply re-install 10.04 as a clean install -- assuming that you do not have anything on the drive that you want to keep. You could then download the 11.04 ISO file, burn it to disk, and re-install that.

The problems of being unable to download, or to burn the disk, would be totally separate from those you now have, and probably would be simpler to solve.

Your description of the current situation suggests that you do, in fact, have some corrupted files. It's not totally uncommon when upgrading to new major versions over existing installs, and the 11.04 version includes some very major changes. In such a case, locating and fixing the damaged areas might well be an extremely slow operation!

---

### Post by radiosgalore on 2011-06-24
thing is what of this out of range message? it seems to be a common issue. I don't want to go through all that bother and just have the same issue. There was a solution on this forum listed [here]("http://ubuntuforums.org/showthread.php?t=1744490&highlight=grub+range") but I only understood part of it and it requires the ability to get into the command line. This has not been possible now and when i used the software centre to force an upgrade to 11.04 Beta as it was then. it just rebooted after the install and immediately screwed up

---

### Post by haqking on 2011-06-24
> **dino99 said:**
> :( :( virus are mainly in front of the computer, between chair & lid :) :)

ha ha well said, yep the most common virus is PEBKAP ;-)

---

### Post by JKyleOKC on 2011-06-24
The "out of range" message is probably generated in your monitor itself rather than in the computer, and in any case indicates that the signals being fed to the monitor are outside the range that it is able to accept. There's no indication whether the signal involved is the vertical sync, the horizontal sync, the dot frequency, or the refresh rate -- it could be any of them.

All these signals are generated by the video driver, and when you get that message it usually means that the video driver is not compatible with your monitor. However that's not always the case. Modern monitors send information back to the driver software during the boot process, and if that information isn't exactly what the driver expects, it may not be interpreted correctly -- resulting in an out of range situation. I have exactly that situation here, and have had to work around it.

All recent versions of Ubuntu rely on automatic detection of monitor and video card characteristics, rather than using the xorg.conf file, and this can lead to such situations. However the software will use an xorg.conf file if it exists, rather than the automatic detection. That's what I had to do: create a file with the correct data.

Unfortunately doing this can be rather complicated, and it will very from one system to another depending on exactly what hardware you have, so I can't give you detailed instructions that will solve your problem. All we can do is lead you in what we hope is the right direction. I'll go back over all of these posts and see what other information we need to get you started...

---

### Post by radiosgalore on 2011-06-24
much appreciated. I was thinking about installing 10.04 on another partition and using that to get me started and just authenticate this account through the command line if i can get my head around it. That was i'd get an automatic GRUB menu instead of having to try to force it with the SHIFT key and can input the commands listed on that other thread. In any case i'll hold fire till you'd had a look and in the meantime borrow my brothers memory stick just in case I need to wipe the lot

---

### Post by JKyleOKC on 2011-06-24
Okay, I see that you can get to "GRUB menu loading" but then freeze up with the "out of range" message. That indicates that at least part of the problem is in the boot loader itself, which makes things more difficult.

It's possible to get access to the files on your hard disk when booted from the live CD, and fix them, but having two different versions of the system makes that trickier and I don't know exactly how to do such a fix. Instead, at this point I would boot from the live CD, use it to download the current ISO file for 11.04, and burn that to a new live CD. If you have enough RAM available, you ought to be able to do this by loading the burner program, then swapping the 10.04 CD for a blank before doing the burn. Once you have an 11.04 CD, boot from it and we can proceed from there to repair the GRUB on your hard disk so that you can get to its menu. It's fairly complicated, but each step isn't too bad...

Don't try to use that beta copy you already have; beta software always has bugs of some sort, and we're dealing with enough problems already!

---

### Post by radiosgalore on 2011-06-24
> **JKyleOKC said:**
> Okay, I see that you can get to "GRUB menu loading" but then freeze up with the "out of range" message. That indicates that at least part of the problem is in the boot loader itself, which makes things more difficult.

It's possible to get access to the files on your hard disk when booted from the live CD, and fix them, but having two different versions of the system makes that trickier and I don't know exactly how to do such a fix. Instead, at this point I would boot from the live CD, use it to download the current ISO file for 11.04, and burn that to a new live CD. If you have enough RAM available, you ought to be able to do this by loading the burner program, then swapping the 10.04 CD for a blank before doing the burn. Once you have an 11.04 CD, boot from it and we can proceed from there to repair the GRUB on your hard disk so that you can get to its menu. It's fairly complicated, but each step isn't too bad...

Don't try to use that beta copy you already have; beta software always has bugs of some sort, and we're dealing with enough problems already!

lol i know. never seem to learn do i? :P I don't have a beta CD. i googled the command line to force the software centre to find 11.04 while still in beta. that was an oops. instant out of range message and thats when I went and used the 10.04 CD i have installed that then upgraded till i had 11.04

well I have 2.3GB of ram but no disks so i think i'll download the current iso to memory stick and install that. Unless that will complicate things further? also back up the pics and music I have. its a 16GB stick so more than enough room. now maybe stupid question but an iso is a compressed file i think. Will i have to uncompress that before i port it to the memory stick or will it just extract and install?

---

### Post by JKyleOKC on 2011-06-24
No, it's not a compressed file. It's an actual image of the CD. No extraction is necessary, but you'll need to use the "make bootable USB" utility to put it on the stick correctly. Since you have files you want to save on it also, I'd simply download the ISO to the stick and then burn an actual CD from there. Use the "burn CD image" option rather than normal file writing; that will keep things bootable. A 16 GB stick is way more than needed for the ISO so you ought to have plenty of room for your other files.

---

### Post by Elfy on 2011-06-24
spam post and offtopic stuff gone

---

### Post by radiosgalore on 2011-06-24
> **JKyleOKC said:**
> ...but you'll need to use the "make bootable USB" utility to put it on the stick correctly


aaaaaah no wonder when i tried that originally with the beta it told me off. i'd just downloaded then copied direct to the memory stick then hurled abuse at it wouldnt boot. Luckily i found the information I need on the Ubuntu site and can grab a coffee before i wage war on this dumb machine. Once the install is complete and before i reboot i'll try

sudo gedit /etc/default/grub

then if i understand this correctly with this lot

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640*400

rewmove the '#' from the final line and change to a higher resolution maybe right up to 1024x768 then save

---

### Post by JKyleOKC on 2011-06-24
I think that running the "make bootable USB" utility will reformat the memory stick, losing everything already stored on it, so you may want to check that possibility out! That's why I suggested downloading to the stick but burning a CD for the actual reboot... However I'm not certain of this. Just wouldn't want to mislead you into losing all your music and files, not to mention anything your brother has on the stick...

---

### Post by radiosgalore on 2011-06-24
> **JKyleOKC said:**
> I think that running the "make bootable USB" utility will reformat the memory stick, losing everything already stored on it, so you may want to check that possibility out! That's why I suggested downloading to the stick but burning a CD for the actual reboot... However I'm not certain of this. Just wouldn't want to mislead you into losing all your music and files, not to mention anything your brother has on the stick...

well... it didnt delete anything but it refuses to install to the memory stick - with 13GB free. i'm gonna try once more reboot then re-download the iso. Gotta say this is almost the amount of trouble I had with windoze. Didnt expect Linux to play me up like this. ooooh well

---

### Post by radiosgalore on 2011-06-25
I think i got it sorted. Strangely I can run my Dock in OpenGL mode but Google earth is messed up and Unity doesn't work. But at least its working so thank you to everybody who tried to help

---

