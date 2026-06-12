---
title: "Dell Inspiron 700m blacklisted?"
date: 2010-04-23
forum: General Help
---

### Post by bubblehead74 on 2010-04-23
I tried Live Session of 10.04 RC on Dell Inspiron 700m with zero success. The boot up finishes with black screen after 1min. Quick search revealed this:

[https://lists.ubuntu.com/archives/lucid-changes/2010-March/007390.html](https://lists.ubuntu.com/archives/lucid-changes/2010-March/007390.html)

drm/i915: blacklist lid status: Sony VGN-BX196VP, Dell Inspiron 700m

Does this mean that 10.04 will not work with 700m?

---

### Post by jeebustrain on 2010-04-27
I'm having the same issue... I just got one of these for my wife and wanted to install Lucid on it. A Karmic live CD works just fine, but I cannot get any graphics (outside of safe mode) to work with Lucid. I used the alternate CD and I did a text based install and manually installed gnome and x11.

I'd love to see an example xorg.conf file from a working version of it so I can use it... I notice that it never actually builds the file properly. I tried taking the template and modifying that, but I'm a little green when it comes to that file and I haven't been able to figure out what I need yet.

---

### Post by jeebustrain on 2010-04-27
After doing some research, it seems that in older versions, we had to use the 915resolution package in order to make things work properly. It appears that has been incorporated into the stock Intel driver. Maybe when I get home from work, I'll mess with that a bit.

---

### Post by jeebustrain on 2010-04-27
I emailed the guy who made that post to try and get some clarification

---

### Post by ajdonesky on 2010-04-29
I haven't done anything more that try to run the live CD, and can confirm that it just sits on a blank screen. I ran the disk check, and booted it in my MacBook Pro and my disk is fine.

So it looks like we have a issue with the 700m

---

### Post by jeebustrain on 2010-04-30
Tonight, I tried a final release of Lucid and got the same results. I put Karmic on a couple nights ago (without issue) and just kicked off the upgrade process. Let's see if I can blow this thing up.

---

### Post by jeebustrain on 2010-04-30
FYI - DON'T try this. It's a waste of your time. I let the upgrade run over night and this morning, I came down to reboot it after it finished. I'm in the same state as before - blank screen right after GRUB.


Looks like this lappy toppy is staying at 9.10. This sucks, now I have to just start all over with it.

---

### Post by jeebustrain on 2010-04-30
OK - it's definitely an issue with the kernel version. I went to the GRUB menu at boot and the old kernel was still there. I booted that and everything works. 

I'm going to test this configuration to see what kind of success I have.

---

### Post by kmand on 2010-04-30
Same results for me. Worked on beta 3, but RC and Final give black screen.

Has anyone submitted a bug report?

---

### Post by amir.khosroshahi on 2010-04-30
I am affected with a similar problem on my Dell Inspiron 6400 with ATI Mobiliy Radeon X1400 graphics hardware. I've just upgraded from 9.10 to 10.04.

Could this be the same issue as discussed here?

---

### Post by RnFstRuckHrd on 2010-04-30
Spent a few hours yesterday watching my upgrade creep towards completion... Once it did I found myself here as well. I jumped into the support channels for ubuntu and kubuntu late last night and no body would come near to dealing with my issue except one fellow who said "that sux!" I have been trying to ask if this is problem that will be fixed in a future update but cannot get a response from anyone. 

I did not think to see if the kernel vers. had been changed and thus have already formatted with a fresh install of 9.10. It seems we are all stuck here for the time being.

For the record, my Dell Inspiron 530S upgraded "okay." Seems to be working fine but the graphics a bit buggy. e.g. the sliding down k-Menu is glitchy, the sliding out of the plasma widget "adder" is glitchy as well. Every fourth or fifth time I open Kmail or Kontact it crashes, but the crash handler will not say that until I try and run a different program or reboot.

---

### Post by twrock on 2010-05-01
Adding "i915.modeset=1" to the end of the commandline when booting the Live CD should solve this and get you into full screen mode. But read this all the way through.

Here are the first steps:
1. When you see the purple box with the little keyboard and person, hit a key to enter options.
2. Choose your language.
3. Verify you have chosen "Try Ubuntu without any changes."
4. Press F6.
5. Press Esc to get out of the menu that pops up.
6. Go to the end of the commandline (with arrow keys if necessary) and type: "i915.modeset=1" (no quotes).
7. Hit Enter and pray hard.

If you receive an error message at this point that says "Ubuntu is running in low graphics mode." Click OK, and then choose to "Troubleshoot the error". Then choose to "Edit the configuration file". Change "vesa" to "intel" and click ok. Then I "closed", "cancelled" and the hit "Restart X". 

That got me into live mode with full screen support. Once there, I installed as usual.

At reboot, I hit "e" at the GRUB menu screen (post #15 below explains holding down both shift keys to get into the GRUB menu at boot), and added "i915.modeset=1" at the end of the line with "quiet splash". Then hit Ctrl-X to finish booting. It all went off without a hitch.

Now you need to edit your GRUB config to make that change permanent. To edit your GRUB config, open terminal and type this command:
```
sudo gedit /etc/default/grub
```
Add "i915.modeset=1" to this line and save:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
Update GRUB in terminal by this command:
```
sudo update-grub
```
Reboot.

As always, YMMV. If you find something I wrote in error, please let me know. Incidentally, I got all of this info from a collection of other people's posts in this forum. Thanks everyone!

---

### Post by RnFstRuckHrd on 2010-05-01
First off, thanks so much to twrock for compiling those steps for us!

Just ran through these steps on my Dell Inspiron 700M and here is where I am at...
All is fine up until step 7 - after hitting enter (and praying) I never get a notice about starting in "low graphics mode" :confused:. Fortunately, the LiveCD session continues to boot up just fine and I reach the desktop. If it matters or not - I went to the display settings console and sure enough,  the resolution is set to 1200x800 @ 65.3 Hz refresh rate (all good here).

But, since I never get the prompt about "low graphics mode" I am unable to change the config file that twrock mentions. If there is another way to do it manually (via Konsole, let me know!) So just for kicks I restarted the xerver (sudo /etc.init.d/kdm). The screen went black and then the KDE reloaded properly.

I installed the OS from the LiveCD session and then rebooted (here is where things go awry). As the boot begins I am ready with my finger on the "e" key but no grub screen shows up. I have tried this multiple times tapping the "esc" key as well but nothing comes of it. All I have is a black terminal cursor for a few moments, and then a very pixelated and poorly colored Kubuntu splash screen appears for about two seconds and then the display goes black. :(

Any thoughts on why my LiveCD session and installation are running differently? And why do I not have a grub screen on reboot? Thanks again for everyone that is working on this! I will be sure to report back if I figure anything else out.   ](*,)

---

### Post by twrock on 2010-05-02
Dang. I even went and did a complete reinstall to try to work that out so it was "reproducible". Hmmm, I'm not sure why we are getting different results. Any possibility it is related to me running GNOME and you running KDE? I'm not a real hacker, so all of this is guess work for me.  I'm not sure what to tell you. 

One other possibility I can think of is that there might be some difference between booting from the CD and from a USB stick. I set up the USB stick to allow for changes to be written to the remaining space. So is it possible all my other attempts left something on that USB stick that make it different from a "standard" installation? I don't know.

However, here are some links to other threads I've been posting in and/or following. These two threads helped me find my solution, so maybe there will be info there for you as well.

[http://ubuntuforums.org/showthread.php?t=1463294&page=4](http://ubuntuforums.org/showthread.php?t=1463294&page=4)
[http://ubuntuforums.org/showthread.php?t=1465883](http://ubuntuforums.org/showthread.php?t=1465883)

Here's a link for  a wiki that might help too.

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Using Workaround A in that Wiki was what got me going the first time around. But I'm thinking that wasn't actually necessary, and I didn't do that for my latest install. 

I'm a bit lost on why you can't get to the GRUB menu at boot. I don't have any machines that are not set up as dualboot, so all of my computers show the GRUB menu on boot. I'm sure there is some simple way of getting into GRUB, but I don't know what it is.

Oh, and I'll drop another thing here for my own reference later (and maybe it'll help someone else too?). I can make the change from "vesa" to "intel" in xorg.conf this way in a terminal:

```
sudo gedit /etc/X11/xorg.conf
```

If nothing else, let me encourage you to keep believing it is actually possible to run Ubuntu 10.04 on a Dell 700m. :)

---

### Post by jeebustrain on 2010-05-02
FYI - if you hold down both shift keys when you boot (I generally start @ POST to make sure I don't miss it), you'll get the GRUB menu.


I'll have to give this a shot when I get a chance. I just pulled my 700m apart tonight to replace the speaker wires in the display (this was second hand and all the friction of opening/closing over the years broke one of the wires).

---

### Post by twrock on 2010-05-02
> **jeebustrain said:**
> FYI - if you hold down both shift keys when you boot (I generally start @ POST to make sure I don't miss it), you'll get the GRUB menu.


I'll have to give this a shot when I get a chance. I just pulled my 700m apart tonight to replace the speaker wires in the display (this was second hand and all the friction of opening/closing over the years broke one of the wires).

Hey, I did that same repair a while back. Not a broken wire problem, just blown speakers. I had two laptops' speakers go out at the time a while back. There was a bug in Ubuntu that had this unbelievably loud shutdown beep, and I am completely convinced that was the cause. (I did finally figure out how to shut that off, but not before the speakers were damaged on both machines.)

Nice to know how to get into the GRUB menu. I'll go back and edit that post above where I gave the wrong method.

---

### Post by RnFstRuckHrd on 2010-05-02
great news ladies and gents!!!
Thanks to twrocks walk-through and jeebustrain's info on getting to grub menu (when not dual booting) - my Dell 700M is now successfully booting in Lucid (Kubuntu) on its own! I am still not sure if you need to run the LiveCD session and install from there, or if you can simply follow twrocks instructions except for installing directly from the CD at booting. I will give this a shot and let you all know for the sole reason that it will save a step. 

Thank you all so much for the rapid responses and useful feedback - so glad all of us 700M users can now enjoy the new LTS. 

BTW - I saw others made a comment about repairing the broken speaker wires in the 700M. If you are reading this article you are probably aware of the issue and most of you have probably already had them break. I just repaired mine a month ago and fixed them using the walk-through in this article:
[http://www.lukemiller.org/journal/2006/06/broken-speaker-wires-on-dell-700m.html](http://www.lukemiller.org/journal/2006/06/broken-speaker-wires-on-dell-700m.html)
I have never soldered anything before and I was able to do this in about 20 mins, it is quite simple. Whats best is I only spent $8 plus tax on the cheapest soldering kit at the local Radioshack. I know this shoudl be in another thread but figured I would toss it out since it came up.

Best of luck to you all and I will be sure to report back tomorrow after trying out the install w/out going through Live session first \\:D/

---

### Post by twrock on 2010-05-02
> **RnFstRuckHrd said:**
> great news ladies and gents!!!
Thanks to twrocks walk-through and jeebustrain's info on getting to grub menu (when not dual booting) - my Dell 700M is now successfully booting in Lucid (Kubuntu) on its own!

"I love it when a plan comes together!" :-D
Nice to hear it does work on more than one machine.
I still have no idea why I got that error message about low resolution. It seems no one else is seeing that. So my guess at this point is that for the Dell 700m, the only really necessary step is to add i915.modeset=1 at boot, however one goes about doing that. Probably this would hold true for any machine using the same graphics chip (Intel 855GM).

---

### Post by bubblehead74 on 2010-05-02
Guys, can I do this using Wubi installation?

---

### Post by alphafer on 2010-05-02
I should have checked before running the upgrade but now my Dell 700m has this black screen. 

I hope this issue is resolve soon. I really don't want to reinstall the previous version and setup my laptop from scratch.

Any ideas of how to fix this?

---

### Post by RnFstRuckHrd on 2010-05-02
Alphafer - If you are not dual booting, then hold both SHIFT keys down as soon as your BIOS screen pops up during boot. Keep holding the SHIFT keys until the grub menu comes up. Once it does, hit "e" and on the upcoming screen look for the line that ends with "...quiet splash". Add "i915.modeset=1" to the end of that line so it looks like this...
"...quiet splash i915.modeset=1". It *should* boot up fine but cross your fingers[-o<. Once it boots up - edit your grub file so that this change is permanent and occurs automatically every time you boot. To edit the grub file, open a terminal and run 
```
sudo gedit /etc/default/grub
```once your text editor opens up, find this line...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and make it look like this...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
Now, save the text file and close it. In that terminal you had open, update the grub so the change takes effect by running...
```
sudo update-grub
```
Now go ahead and reboot your machine and see if it boots up fine on its own.
Let us all know if that works as this will allow any other 700M users that already boot to K/Ubuntu to upgrade without having to do a fresh install.

---

### Post by RnFstRuckHrd on 2010-05-02
As promised I tried doing a fresh install today *with out* first  running the LiveCD session. It all went just fine! That being the case I  will just make one last list of steps - but all the credit should be  going to twrock, as he is the one that really compiled all of this.

I know this is A LOT of steps but I am trying to make it *very* clear and simple so no one is left in the dust. We have all been there;)
So...for everyone else that is trying to do a *FRESH* install of  Kubuntu 10.04 on the Dell Inspiron 700M...

1. Put in your install CD and reboot

2. The *Kubuntu* CD should take you directly to the install options window where you must first select your language, so select it. The *Ubuntu* CD on the other hand shows a little keyboard and human figure, when you see this - hit any key to reach the install options and select your language.

3. using the arrow keys, hi-light the Install K/Ubuntu option (DO NOT select it yet)

4. Press F6 - a small menu will popup. Hit "esc" to remove the menu

5. Now along the bottom of the screen is a line that ends in "quiet splash". add the following to the end of that line, "i915.modeset=1". It will look like this "...quiet splash i915.modeset=1" (Note: the elipses will not be there, it represents the rest of the text in that line!)

6. Hit Enter to begin the installation - you should then get the typical install prompts/dialogues and the install slideshow.

7. Now reboot when the prompt telling you to do so comes up. (you will have to remove the CD, it will tell you when to do that).

8. Are you dual booting? *IF SO* then hit "e" when the grub menu comes up and move to the next step. *IF NOT* then start pressing down (and holding) both shift keys simultaneously as soon as your machine starts to boot up. This will bring you to the grub menu where you can hit "e".

9. In this grub menu screen, look for the line ending in "...quiet splash" and make it look like this "...quiet splash i915.modeset=1" (again the elipses just represent the other text that is already there!)

10. Hit CTRL + X to boot

11. Once your computer boots up then edit your grub file so that your machine will boot up properly on its own every time. To do this, open a terminal.

12. In the terminal window, run the following command
```
sudo gedit /etc/default/grub
```
(Note - gedit is the standard editor for GNOME on Ubuntu, I you are running KDE then the editor is most probably kate)

13. Add "i915.modeset=1" to this line so it looks like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

14. Now save the file and close it.

15. Now update the grub so these changes take effect. In that terminal that is still open run...
```
sudo update-grub
```16. Now reboot and see if your machine starts backup normally and all on its lonesome!

Once again - I am merely re-posting what twrock and jeebustrain have already put together with a few nuggets I figured out about not having to run the LiveCD session.
To that point - if these steps DO NOT work for you then try the steps that twrock posted and see if that works. As always - post if you have any issues/obstacles with as much info as possible. Thanks again everyone for the help - making this post as we speak from my Dell Inspiron 700M running Kubuntu 10.04 Lucid Lynx!!!
\\:D/

---

### Post by twrock on 2010-05-02
RnFstRuckHrd, looks great. For the complete noob, you might want to mention opening a terminal at step 12 (or 11) in which to type that commandline.

Incidentally, I had my 700m up and running most of the last day and a half, and everything seems to be working just fine for me.

---

### Post by RnFstRuckHrd on 2010-05-03
twrock - glad to hear your 700M is firing on all cylinders again. And thanks for the tip on clarifying step 12 - it should now be readily usable to even the newest of linux users (hopefully ;-)).

---

### Post by ejarg7 on 2010-05-03
Finally installed 10.04 on my old 700m.  Those instructions were excellent.  The only thing that didn't work out for me was I couldn't do direct install, it crashed for some reason. I could install through the LiveCD session though.  Updated the grub and it's working fine now.  Thanks for all the tips! :D

Just realized I've got one problem now.  I can't seem to get any video to play.  Installed codecs and all, but whenever I try to open a video file, it crashes.  I mean the whole OS crashes, not just the application.  I am seeing some sort of Ubuntu BSOD here.  Anyone having the same problem?

---

### Post by kmand on 2010-05-03
> **ejarg7 said:**
> 
Just realized I've got one problem now.  I can't seem to get any video to play.  Installed codecs and all, but whenever I try to open a video file, it crashes.  I mean the whole OS crashes, not just the application.  I am seeing some sort of Ubuntu BSOD here.  Anyone having the same problem?

I'm in the same situation. If I run a media player on an mpg file (for example mplayer), the video never shows, just a momentary blue screen in the window, then some flashing like the Xserver is trying to restart, and then it hangs black screen, not answering pings.

---

### Post by RnFstRuckHrd on 2010-05-03
I just tried to play a few different video files on my 700M to test this out...

playing the .avi file in either DragonPlayer or VLC causes a crash that I hoped was just the plasma workspace- but unfortunately I cannot raise krunner either. After a few brief moments my screen goes dark and all is idle.

playing a .mkv file in either player causes the same crash (figured as much but just wanted to see)

Unfortunately I am unable to play any DVDs (using VLC) and yes I have verified the libdvdread4 is installed, as is libdvdcss, w32codecs and the ubuntu-restricted-extras package. Not sure if this is related but I am curious to see if a DVD will cause the same crash. Can anyone else get a dvd to play and report back with some info?

Perhaps there is some other config file for outputting graphics (from media players) that can be adjusted to i915 as well? I know absolutely nothing about that but it would be the first solution I would try if I even new where to look for it!

Glad we have the OS running but playing video files is a capability that I am sure most users want or need. Hopefully it will get figured out - thats all I have. I know its not helpful, sorry!
-Cheers

---

### Post by kmand on 2010-05-03
With mplayer you use the "-vo" option to select the video driver. The default is "xv" using the Xvideo extension needed for hardware acceleration (scaling, etc). This is what crashes the machine in 10.4 with i915.modeset=1.

If you use the -vo option "x11" which does it all in software, no crash. Its the xvideo support using the video overlay adapter thats the problem.

---

### Post by dixon151 on 2010-05-03
I'm also having a problem with 10.04 on my 700m. I did an upgrade to 10.04 from 9.10 without realizing what problems lay ahead. After reading the previous comments on this thread. I was able to boot into 10.04 by selecting kernal version 2.6.31-21 then editing the last option to quiet splash i915.modeset=1. But after logging into ubuntu i tried to edit and save the changes to the grub. with sudo gedit /etc/default/grub but when i enter the command there is nothing in the text file. any thoughts cause right now i have to manually enter the grub changes everytime i want to boot up.

---

### Post by RnFstRuckHrd on 2010-05-03
kmand - could you please be a bit more specific on how to change the driver setting? Do you know if this fix is applicable only to mplayer or to other media players as well (vlc, totem, dragonplayer)? Thanks!

|break|

dixon151 - Are you you dual-booting?

---

### Post by dixon151 on 2010-05-03
no i am not dual booting

---

### Post by kmand on 2010-05-03
> **RnFstRuckHrd said:**
> kmand - could you please be a bit more specific on how to change the driver setting? Do you know if this fix is applicable only to mplayer or to other media players as well (vlc, totem, dragonplayer)? Thanks!


Each media player has different options for the video output driver. On mplayer its "-vo x11". I didn't see a similar one on vlc.

However, you disable XVideo globally in /etc/X11/Xorg.conf

Add

Section "Extensions"
    Option "XVideo"  "disable"
EndSection


You may have to reboot. It doesn't seem to reread it on each login.

You can see if it worked with "xdpyinfo" which will list the extensions that are enabled. Also "xvinfo" will show "No Adapters".

That said its not a satisfactory workaround except on low res videos. The 700m doesn't have enough horsepower to do smooth high def video in software without the XVideo option (and barely then).

---

### Post by ejarg7 on 2010-05-03
> **kmand said:**
> 
However, you disable XVideo globally in /etc/X11/Xorg.conf

Add

Section "Extensions"
    Option "XVideo"  "disable"
EndSection


Sorry, I'm kinda new to this and am just trying to get everything working.

I remember searching for the xorg.conf file yesterday but it's not there.  Is it supposed to be there or we have to just create that file and put it in the X11 folder?

---

### Post by kmand on 2010-05-03
> **ejarg7 said:**
> Sorry, I'm kinda new to this and am just trying to get everything working.

I remember searching for the xorg.conf file yesterday but it's not there.  Is it supposed to be there or we have to just create that file and put it in the X11 folder?

Sorry, I shouldn't have capitalized Xorg, its /etc/X11/xorg.conf.

---

### Post by RnFstRuckHrd on 2010-05-04
Thanks kmand - I will give that a shot and see how it works for vlc and dragon player.

Another interesting (but frustrating) bit of information. I recently acquired a Logitech QuickCam for Notebooks Pro to use for skype calling friends. The came worked fine in 9.10 (although it did not play nice with the version of skype I had). Anyways, in 10.04 I can plug the camera in via usba nd it seems to be recognized. However, as soon as a program such as cheese or skype try to use the webcam for video input - I get the same crash as I do when playing the video files. I am going to go ahead and assume that this has to do with the graphics on the 700M and not with the webcam itself.

---

### Post by njee on 2010-05-04
To get totem up and running for me I found that I could go into the terminal and type

gstreamer-properties

then go to the video tab, and under video output select

X Window System (no XV)

I had to do something similar I think in Karmic, because I found that on the 700m videos started lagging after a few minutes. However on Karmic I found that I could play them in VLC (setting the output to no XV in VLC's options) and that didn't seem to slow down. No sure if this applies to Lucid.

---

### Post by ejarg7 on 2010-05-04
> **kmand said:**
> Sorry, I shouldn't have capitalized Xorg, its /etc/X11/xorg.conf.

I can't seem to find the xorg.conf file anywhere.  It's just not there.  Is there any way I can get a good copy of the file and just put it in the X11 folder?  Thanks.

---

### Post by twrock on 2010-05-04
> **ejarg7 said:**
> I can't seem to find the xorg.conf file anywhere.  It's just not there.  Is there any way I can get a good copy of the file and just put it in the X11 folder?  Thanks.

If you are using Ubuntu (GNOME), type this in the Terminal and see what you get.
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by ejarg7 on 2010-05-04
Hi twrock, I did sudo gedit /etc/X11/xorg.conf and it's an empty file.  I searched the X11 folder and there's no xorg.conf file.  There is however, xorg.conf.failsafe in that folder. I copied and pasted its contents here:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fbdev"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by twrock on 2010-05-04
Hmm, well, as far as I can see, the only difference between what you have there and mine is "fbdev" in yours is "intel" in mine. But I have no idea why you don't have the standard xorg.conf file.

On a completely different note, I don't have any further time this week to work on any of this. Hopefully someone will get this mess sorted out and we can really use this latest LTS version on our 700m's. But until then, I'm downgrading to something I know will work.

Good luck everyone.

---

### Post by RnFstRuckHrd on 2010-05-04
Well, one step in the right direction. Thanks njee for your two cents. In VLC player go to
tools --> Preferences --> In bottom left corner toggle "show Settings" to "all" --> expand the video tab --> select "output modules".
There is a drop-down menu here and mine was set to default. I selected x11 video output and clicked save.

I can now play .avi and .mkv files juts fine now! 

webcam still crashes (as the above fix only effect vlc). I cannot find an option like that for webcam output in cheese or Skype. Anyone know of a way to change those settings in other programs like that?

---

### Post by RnFstRuckHrd on 2010-05-04
dixon151 - Are you needing to hold down the shift keys to get to your  grub menu or do you see the grub every time you boot? I am just unclear  about why/how you are selecting your kernel version. Once at the grub  screen - the only thing you should do is press "e" to get to the grub  options menu. Could you just be a bit more clear on what you are doing at the grub screen?

As for editing the grub file - first double check that command is being put into the terminal correctly. Also be sure that gedit is your text editor installed before using the command with gedit. For example, I boot in Kubuntu so my text editor of choice is kate. Therefore, sub "kate" in place of "gedit" in that command to open up my grub config file.

If all of that checks out and the grub config file still comes up completely blank, then I am as lost as you :confused:. I am not sure why that would be or the best way to fix it, but I am confident others in here know. Let us know if you figure anything else out!

---

### Post by ejarg7 on 2010-05-05
> **RnFstRuckHrd said:**
> Well, one step in the right direction. Thanks njee for your two cents. In VLC player go to
tools --> Preferences --> In bottom left corner toggle "show Settings" to "all" --> expand the video tab --> select "output modules".
There is a drop-down menu here and mine was set to default. I selected x11 video output and clicked save.

I can now play .avi and .mkv files juts fine now! 



Hey, thanks for the tip!  It worked for me too!  I still wish they'd fix this for real soon though.  Like you said, other applications that attempt to play any video would just crash the system. But, I can live with this as my secondary machine for now.  Thanks everyone!;)

---

### Post by twrock on 2010-05-08
Wow, two weeks since this thread started, but no "official" solution yet. Bummer.

Obviously the problem is that the 700m is just too good of a machine. It should have fallen apart long ago, and shouldn't need to be supported. :D

I bought mine second hand, because I was looking for a "netbook" even before netbooks started showing up. This thing has been solid! I bought an extended battery for it a couple of years ago, and the battery life is still just great. But because it just won't break, I can't come up with any excuse to buy a new netbook.

I just installed Lucid on my other laptop (work machine; dualboot too). I gotta say that I really do like it and wish I could run it without issue on my 700m too. Hopefully some day soon.

It sucks being blacklisted. :(

---

### Post by alphafer on 2010-05-20
> **RnFstRuckHrd said:**
> Alphafer - If you are not dual booting, then hold both SHIFT keys down as soon as your BIOS screen pops up during boot. Keep holding the SHIFT keys until the grub menu comes up. Once it does, hit "e" and on the upcoming screen look for the line that ends with "...quiet splash". Add "i915.modeset=1" to the end of that line so it looks like this...
"...quiet splash i915.modeset=1". It *should* boot up fine but cross your fingers[-o<. Once it boots up - edit your grub file so that this change is permanent and occurs automatically every time you boot. To edit the grub file, open a terminal and run 
```
sudo gedit /etc/default/grub
```once your text editor opens up, find this line...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and make it look like this...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
Now, save the text file and close it. In that terminal you had open, update the grub so the change takes effect by running...
```
sudo update-grub
```
Now go ahead and reboot your machine and see if it boots up fine on its own.
Let us all know if that works as this will allow any other 700M users that already boot to K/Ubuntu to upgrade without having to do a fresh install.
Thanks [RnFstRuckHrd]("http://ubuntuforums.org/member.php?u=1063231"). I followed your instructions and my Dell 700m is up and running. I am still checking if the upgrade has caused some other issue but it is looking awesome so far.

Sorry for the late respond. 

Alphafer

---

### Post by mfhall on 2010-05-21
Using original grub

I had installed Lucid by upgrading from Karmic (after upgrading from Jaunty), not a new install.
I believe this means I am not using Grub 2 - which would explain why I don't have a /etc/default/grub file to edit, but I was able to boot from the old kernel.

All I did was edit the /boot/grub/menu.lst file to add " i915.modeset=1" after "quiet splash" as described in earlier posts.

I am booting into the new kernel without problems now. 

Now to look at the video problem ...

Is it just me, or does lucid have an extraordinary number of problems for a 'stable' release? I had quite a few headaches with a new install on a brand new box using Intel integrated video ....I'm considering dumping Ubuntu for Debian.

---

### Post by twrock on 2010-05-22
mfhall, I think the problem is that no release of Ubuntu is ever "really" stable. Because of the self-imposed six-month cycle, they are always pushing something, and likely breaking something as well.

Here's a thread that suggests a "solution", but I don't think it's going to happen. So maybe going with something like Debian is a good solution. I certainly don't know. [http://ubuntuforums.org/showthread.php?t=1472223](http://ubuntuforums.org/showthread.php?t=1472223)

My solution after working on this for a while and not finding a complete "fix" was to downgrade to Karmic and wait to see if what got broken gets fixed by the next release. Too bad. I like Lucid on my other machine, but I can't use it on this Dell 700m.

---

### Post by msntrf on 2010-06-02
I'm really disappointed!  I LOVE Lucid and I love my 700m.

---

### Post by JoelOl75 on 2010-06-03
> **kmand said:**
> Each media player has different options for the video output driver. On mplayer its "-vo x11". I didn't see a similar one on vlc.



In vlc open the player (Without opening a movie) and goto the preferences.  Click to view all options (botton left) and select Video, output modules.  Change default to opengl and click save.  Try out a movie.  If it doesn't work try x11 instead of opengl.

---

### Post by jbrid on 2010-06-09
> **twrock said:**
> So maybe going with something like Debian is a good solution.

I thought this was a kernal issue. :confused:

Does anyone know what the scope of this is? Would other non-ubuntu based linux distributions work?

---

### Post by jbrid on 2010-06-09
Thanks to the contributors of the solutions in this thread. Everything worked for me on my Dell 700m. It turned out pretty easy actually.

Cheers!:)

---

### Post by jbrid on 2010-06-12
Has anyone found a solution for the Mozilla VLC plugin? If you try to watch video, the system will crash.

---

### Post by dtakamori on 2010-07-04
fyi folks... if you update to 2.6.32-23 (the most recent update as of today) even the i915.modeset change won't help you.  I had to revert to 2.6.31 on my 700m.

---

### Post by twrock on 2010-07-18
> **dtakamori said:**
> fyi folks... if you update to 2.6.32-23 (the most recent update as of today) even the i915.modeset change won't help you.  I had to revert to 2.6.31 on my 700m.

Yep, it's tough being blacklisted. I'm sticking with Karmic for now. If somehow this gets fixed before Karmic is EOL'ed, I'll probably just stick with Ubuntu. Otherwise, I'll be looking for a new distro.

---

