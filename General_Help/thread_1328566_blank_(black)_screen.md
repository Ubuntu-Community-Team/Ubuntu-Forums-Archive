---
title: "blank (black) screen"
date: 2009-11-16
forum: General Help
---

### Post by laytek on 2009-11-16
Hello,

Just upgraded a Dell Dimension 2400 to Karmic. I believe this machine has the 82845g chipset. First reboot after upgrade went normally. Turned machine off for the night, and today I get nothing but a blank (black) screen. The keyboard is unresponsive, and there is no mouse pointer. I can push the power button and command a normal shutdown.

Any suggestions?

LayTek

---

### Post by hwttdz on 2009-11-16
During shutdown do you see messages on the screen?  Do you see messages on the screen during bootup?  Do you see a grub boot menu?

---

### Post by laytek on 2009-11-16
Thanks you for your reply hwttdz.

During startup, I see the POST, then grub, then the new Karmic ubuntu emblem. After several seconds, the Karmic emblem goes away, and single (text underline, I believe) cursor shows in the upper left corner of the screen. After several more seconds, the cursor disappears leaving me with a blank screen. Nothing during shutdown at all.

LayTek

---

### Post by hwttdz on 2009-11-16
Can you select failsafe kernel during grub stage?  Often a simple "sudo apt-get update" "sudo apt-get upgrade" fixes problems like this. Otherwise maybe try to grab a "dmesg" output from the failsafe one.  If you're using a dual boot to do this you can, dmesg > file.txt.  Then move file.txt to your alternate os partition.

---

### Post by laytek on 2009-11-16
Again thanks, hwttdz.

I booted using the 2.6.31-14-generic kernel in recovery mode. Updated, but nothing to upgrade. Tried booting using the 2.6.28-16-generic kernel with no luck. Tried again with the 31-14-generic kernel, again with no luck. Also, the computer no longer responds to the single push of the power button as before. I am having to shutdown by holding the power button for about 6 seconds.

Karmic is the only OS installed.

LayTek

---

### Post by hwttdz on 2009-11-16
What's the output of "dmesg"?

---

### Post by laytek on 2009-11-16
Took me a while.

This is a dmesg output when I booted using the 2.6.31-14-generic kernel in recovery mode. I used dmesg > dmesg.odt, scp to another machine and am attaching it to this post. Had to use .odt to get past file limit size. Change to .txt if desired.

Thanks,
LayTek

---

### Post by JUSTINBEAIRD on 2009-11-17
> **laytek said:**
> Hello,

Just upgraded a Dell Dimension 2400 to Karmic. I believe this machine has the 82845g chipset. First reboot after upgrade went normally. Turned machine off for the night, and today I get nothing but a blank (black) screen. The keyboard is unresponsive, and there is no mouse pointer. I can push the power button and command a normal shutdown.

Any suggestions?

LayTek


I Have the same computer and the same blank screen problem after upslash it just goes blank

my fix was 

as soon as your computer boots hold down shift so you don't miss grub menu then go to 
(recovery mode) and then to root remove xsplash and ubuntu-xsplash-artwork using the command line 
or
type gdm or startx I cant remember then use synaptic to remove them :) then restart

and for kubuntui I had same problem and noticed it dont use xsplash
so i was poking around and seen usplash-theme-ubuntu and kubuntu-artwork-usplash where both installed and I think they where both running at same time on top of each other causing errors
so I removed kubuntu-artwork-usplash and I have no problems now

in short my guess is
xsplash is not starting gdm correctly on intel cards or others 
and
kubuntu is runing 2 themes or maybe 2 usplash instances at the same and not starting X correctly

sorry for spelling I am half asleep 
please tell me if this helped you or anyone else

and why does (recovery mode) have complete root access without a password is this a bug?

---

### Post by laytek on 2009-11-17
JUSTINBEAIRD, thanks for your reply.

I started the computer using recovery mode, dropped to a root console and removed xsplash as you suggested. During the next restart, I am sorry to report that I saw no differences. The same artwork showed on the screen and the computer still refuses to boot.

I read an article last night, "[Hey Ubuntu, Stop Making Linux Look Bad]("http://www.linux-mag.com/cache/7600/1.html")" that summarizes my feelings about these upgrades. I know I don't have the most advanced equipment, and the 82845g chipset has always been a problem, but to render the computer unusable is not part of the linux heritage.

LayTek

---

### Post by JUSTINBEAIRD on 2009-11-17
> **laytek said:**
> JUSTINBEAIRD, thanks for your reply.

I started the computer using recovery mode, dropped to a root console and removed xsplash as you suggested. During the next restart, I am sorry to report that I saw no differences. The same artwork showed on the screen and the computer still refuses to boot.

I read an article last night, "[Hey Ubuntu, Stop Making Linux Look Bad]("http://www.linux-mag.com/cache/7600/1.html")" that summarizes my feelings about these upgrades. I know I don't have the most advanced equipment, and the 82845g chipset has always been a problem, but to render the computer unusable is not part of the linux heritage.

LayTek

go to (recovery mode) then root and type gdm and see if it boots if it does remove ubuntu-xsplash-artwork then try rebooting and see if it boots normaly if not i will post my bios settings also as i have the same desktop and it may matter

also a ton of bug fixes just came through try installing them and cross your fingers 

and you know just as well as me that our  desktop's are crappy :)

---

### Post by OneMixDJ on 2009-11-17
> **laytek said:**
> 
I read an article last night, "[Hey Ubuntu, Stop Making Linux Look Bad]("http://www.linux-mag.com/cache/7600/1.html")" that summarizes my feelings about these upgrades. I know I don't have the most advanced equipment, and the 82845g chipset has always been a problem, but to render the computer unusable is not part of the linux heritage.
LayTek

Although the article may relate to any frustration you may feel, I think we should focus on the problem at hand. 

Because if we were to shift the focus from your problem to the article itself, even I, who still considers myself a noob compared to others here, would find it way too easy to rip every claim made by the author to shreds due to its inaccuracy. ;)

I had a similar problem with my T22 Stinkpad after installing 8.04 and did a few reboots until it came up. Once it came up, I ran the command to try to fix any broken packages (apt-get -f install). After that I did my first slew of upgrades before bringing it up to 8.10. It happens once in blue moon but extremely seldom and not repetitive.

Were you upgrading from 9.04?

Also, may I request a txt version of the provided output?

---

### Post by laytek on 2009-11-17
> go to (recovery mode) then root and type gdm and see if it boots

Well, very interesting. I booted using the 2.6.31-14-generic kernel in recovery mode and dropped to a root shell with networking. I typed gdm, and the system finished loading. I was able to log into my desktop. Everything seemed to work, except the original Karmic background is gone. Of course the latter is no big deal.

I was able to catch a brief text message displayed in the console after typing "gdm" and before the desktop came up. It said:

> WARNING: Unable to find users: no seat-id found

There is a [_bug report_]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/433928") on this subject that describes my symptoms. I don't understand everything on the page, but it appears that there is no one assigned to fix this bug.

The first attempt to reboot from a cold start after all of the above was successful. Ahhh, the system is working. Unfortunately, that first restart is the only one that has worked. xsplash and ubuntu-xsplash-artwork have been removed and the system has been updated.

Thanks for everyone's help so far. You send suggestions and I will keep trying!
LayTek

---

### Post by JUSTINBEAIRD on 2009-11-19
> **laytek said:**
> Well, very interesting. I booted using the 2.6.31-14-generic kernel in recovery mode and dropped to a root shell with networking. I typed gdm, and the system finished loading. I was able to log into my desktop. Everything seemed to work, except the original Karmic background is gone. Of course the latter is no big deal.

I was able to catch a brief text message displayed in the console after typing "gdm" and before the desktop came up. It said:



There is a [_bug report_]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/433928") on this subject that describes my symptoms. I don't understand everything on the page, but it appears that there is no one assigned to fix this bug.

The first attempt to reboot from a cold start after all of the above was successful. Ahhh, the system is working. Unfortunately, that first restart is the only one that has worked. xsplash and ubuntu-xsplash-artwork have been removed and the system has been updated.

Thanks for everyone's help so far. You send suggestions and I will keep trying!
LayTek




today the my whole system is screwed it gets to the desktop and shows the panel at the top and bottom and stops the mouse shows continuing loading but nothing else ever loads everything is locked up but the mouse :(

and the blank screen thing happens in Debian stable and testing also

---

### Post by Scott753 on 2009-11-19
Hello, I've been having the same problem with the black screen, exactly the same. My problem is that the root with networking wasn't working, so i just kept typing gdm. 

Finally, my desktop loaded.

Also, before it finally loaded, I also got the two panels with the mouse symbol for working on several tries.


This is really frustrating, because it's all so random. Why did gdm work this time and not any of the previous times? I did everything exactly the same. 

You wouldn't think that would be the case for a computer, which is supposed to be governed by a set of rules right? I mean, it's not like it throws a die everything to determine if it will boot or not.
Anyway, I don't know how to remove xsplash, if you think that would help. So, if anyone has any advice on how I can avoid the black screen in the future, please let me know. I

(I won't be rebooting again for a long, long time)

---

### Post by laytek on 2009-11-20
This problem seems to be affecting relatively few of us. I suspect (but really don't know) that this is chipset specific. In the rush to be the newest and the best, stability and thorough testing become less important. I know my equipment is old and accordingly I have reloaded Jaunty on the computer.

I am sorry that I am unable to provide a better solution, and the community doesn't seem to know the answer either. I wish I had the skill to tackle the bug (there is still no one assigned to address the problem) and give back to the community. In the mean time, I have gotten what I paid for.

LayTek

---

### Post by deathspal on 2009-11-21
Thank you guy for this thread.... I was having the exact same issue on my JVC Vivtor interlink mini note... I found that I could load from console with gdm. I did not have xsplash installed but I looked further and found I had usplash, probably from and old Ubuntu-studio install. I removed it and I'm in!!!!  thanks for the clues!!!

---

### Post by heyted on 2009-12-01
Instead of removing xsplash and all that other stuff, the following worked with my dell dimension 2400:

1.  In /etc/default/grub:
Change 
#GRUB_GFXMODE=640x480
to
GRUB_GFXMODE=1024x768
(possibly another resolution)

2.  In /etc/grub.d/00_header:
add 
set gfxpayload=keep
right after
set gfxmode=${GRUB_GFXMODE}

3.  Update grub:
sudo update-grub

grub.cfg should have:
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi

---

### Post by Lutin on 2010-01-04
Thanks, that worked for me. :-)

---

