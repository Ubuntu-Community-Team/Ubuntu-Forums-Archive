---
title: "Widescreen grub menu"
date: 2010-05-12
forum: General Help
---

### Post by inso_741 on 2010-05-12
I'm using lucid x86_64.
I tried changing the grub menu resolution and it works fine on 1024x786 and 1280x1024 but since my monitor is a widescreen lcd
i tried the native resolution which is 1440x900 which gives a message "Frequency out of range" during boot after bios post...
but then after 10 secs ubuntu boots w/o any problems...also I get the same problem with 1280x800 so i'm guessing it doesn't support wide screen resolutions...is there a workaround?..............I've a GTX260 if that helps...:confused:
Edit: I'm using nouveau....

---

### Post by warfacegod on 2010-05-12
Check to see if there is a "Stretch Screen" option in your BIOS.

---

### Post by inso_741 on 2010-05-12
No, there isn't...its a DX58SO
although my monitor has that option......to stretch 4:3 content which I've disabled as it looks ugly

---

### Post by inso_741 on 2010-05-13
bump

---

### Post by inso_741 on 2010-05-13
btw 'hwinfo --framebuffer' returns this
: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.wJE+Nfe8JS0
  Hardware Class: framebuffer
  Model: "NVIDIA BIOS-P/N@N5659-2"
  Vendor: "NVIDIA Corporation"
  Device: "BIOS-P/N@N5659-2"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xd1000000-0xd1dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by inso_741 on 2010-05-13
this is what I found in grub2 wiki:
#GRUB_GFXMODE=640x480
Uncomment (remove '#' from beginning of the line) to change (increase) resolution of your boot loader. Use one of classic (4:3 rate):
GRUB_GFXMODE=640x480 (is used if isn't here a proper value)
GRUB_GFXMODE=800x600
GRUB_GFXMODE=1024x768
GRUB_GFXMODE=1600×1200
or make experiments with some others nonstandarts like widescreen (16:10 ratio in my case), here is list of most of commonly use Display resolution:
GRUB_GFXMODE=640x400
GRUB_GFXMODE=800x500
GRUB_GFXMODE=1024x640
GRUB_GFXMODE=1280x800
GRUB_GFXMODE=1680x1050
If you don't know what modes are supported by your graphics card, go to the grub command line and run 'vbeinfo'. It will list all available modes. (You might need to run 'insmod vbe' first if the vbe module isn't loaded yet)

---

### Post by ryan858 on 2010-05-13
Do all the WS modes not work? Have you tried 1680x1050?

---

### Post by inso_741 on 2010-05-13
sorry but my monitor doesnt support resolution greater than 1440x900:(
although I've checked 1280x800.....it gives a message frequency out of range...
i'll check other smallaller resolutions but it doesn't matter even if they do work....

---

### Post by inso_741 on 2010-05-13
vbeinfo returns a list of resolutions
but there is no widescreen res. in the list
is it possible to add a custom resloution??
the maximum possible res as reported by vbeinfo is 1600x1200
so I think it can definitely handle 1440x900........any ideas??

---

### Post by inso_741 on 2010-05-13
according to [this]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#VESA_BIOS_Extensions_.28VBE_Core.29_3.0_.5BSep._1998.5D") its possible 
but its not working for me can someone try it and confirm please???:confused:

---

### Post by inso_741 on 2010-05-13
such a BIG community and no one cares about the grub menu!!!:(
I'm a little dissapointed.....after wasting so much time I'm still were I was a day before....
the only thing I can do now is set timeout=0 and get rid of the silly menu

---

### Post by inso_741 on 2010-05-14
update: widescreen modes work in my laptop(alteast 1280x800)
now the only difference here is laptop has a digital display and my monitor is analog lcd

---

### Post by inso_741 on 2010-05-14
alright one more thing, for my laptop, 'vbeinfo' returns 1280x800 in the modes list
but 'vbeinfo' on desktop doesn't......although 'hwinfo --framebuffer' says the card supports all sorts of resolutions 
desktop - GTX260
laptop   - 8600mGT
someone help!!!!:(

---

### Post by inso_741 on 2010-05-14
I don't think anyone's gonna reply
so I'll just mark the thread solved

---

### Post by dino99 on 2010-05-14
maybe you need to add into xorg.conf, the vertical and horizontal frequencies of the screen

---

### Post by inso_741 on 2010-05-14
> **dino99 said:**
> maybe you need to add into xorg.conf, the vertical and horizontal frequencies of the screen
I don't think VBE checks xorg but thnx for the reply

---

### Post by drs305 on 2010-05-14
> **inso_741 said:**
> I don't think anyone's gonna reply
so I'll just mark the thread solved

I'd recommend you remove the 'Solved' tag for several reasons.

First, even though you haven't received a solution yet, people may still read this and come up with an answer. For instance, I've been on vacation for the past several weeks. I've been following the thread for two days and have been trying a few things to see if I could solve it. Had it been marked solved when I first returned to the forums I would not have opened the original post.

Secondly, users may open the post thinking they will find a solution to their own problem. Although posts such as this can still be beneficial in showing what *didn't* work, it's a bit misleading/disappointing to a user who may think they have finally stumbled on a solution which doesn't exist in the thread.

Leaving a post 'open' doesn't hurt anything, and you can unsubscribe if you really don't want to see it any longer. If the 'unsubscribe' link isn't available in the thread you may be able to do it from the Control Panel's Subscribed Threads section. I hope you will stick with it though.

---

### Post by inso_741 on 2010-05-14
> **drs305 said:**
> I'd recommend you remove the 'Solved' tag for several reasons.

First, even though you haven't received a solution yet, people may still read this and come up with an answer. For instance, I've been on vacation for the past several weeks. I've been following the thread for two days and have been trying a few things to see if I could solve it. Had it been marked solved when I first returned to the forums I would not have opened the original post.

Secondly, users may open the post thinking they will find a solution to their own problem. Although posts such as this can still be beneficial in showing what *didn't* work, it's a bit misleading/disappointing to a user who may think they have finally stumbled on a solution which doesn't exist in the thread.

Leaving a post 'open' doesn't hurt anything, and you can unsubscribe if you really don't want to see it any longer. If the 'unsubscribe' link isn't available in the thread you may be able to do it from the Control Panel's Subscribed Threads section. I hope you will stick with it though.

alright i'll keep the thread open(sorry to close it in the first place)...but I don't think I can provide any more information then what I already have and I did put a lot of time into it w/o any solution and now I think its time to move on to other problems........although I'll keep n eye on this thread....

anyways what do you think? is my analog monitor the problem here or is it my graphics card is it vbe 
since vbe displays wide modes on my laptop i'm a bit confused about why it doesn't list those for my desktop 
if you want I'll post some screenshots of 'vbeinfo' not screenshots but I can snap some pics with my cam.....just tell me if u need to see

---

### Post by efflandt on 2010-05-14
Even with a digitally connected monitor, grub/grub2 is only going to use modes found in **vbeinfo**, but not sure how those modes are determined.

When my laptop boots 9.10 on its 1280x800 display, the splash Ubuntu logo is round.  When 9.10 boots on my desktop w/DVI to HDMI connected 1080p HDTV, the splash Ubuntu logo is oval (1024x768 stretched). But the X login prompt on either is the correct native resolution for either computer (1280x800 on laptop and 1920x1080 on the desktop).

Of course in 10.04 there is no big round, or supposed to be round, splash symbol.

---

### Post by Cavsfan on 2010-05-14
I have mine set to my native resolution 1920 x 1200 and about any resolution will work.
My /etc/default/grub file contains this line and 32 is bit depth.
GRUB_GFXMODE=1920x1200x32
That is all that is in that file.

sudo update-grub to make the changes stick.

---

### Post by Cavsfan on 2010-05-14
This link will help. It helped me get mine setup

[U][http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/%7Eherman546/p20.html")

[/U]Even if you are not dual booting.

---

### Post by inso_741 on 2010-05-15
> **efflandt said:**
> Even with a digitally connected monitor, grub/grub2 is only going to use modes found in **vbeinfo**, but not sure how those modes are determined.

When my laptop boots 9.10 on its 1280x800 display, the splash Ubuntu logo is round.  When 9.10 boots on my desktop w/DVI to HDMI connected 1080p HDTV, the splash Ubuntu logo is oval (1024x768 stretched). But the X login prompt on either is the correct native resolution for either computer (1280x800 on laptop and 1920x1080 on the desktop).

Of course in 10.04 there is no big round, or supposed to be round, splash symbol.

thanx for the reply...can you please specify your gfx card and tell me if 'vbeinfo' lists wide resolutios for your desktop?

---

### Post by inso_741 on 2010-05-15
> **Cavsfan said:**
> I have mine set to my native resolution 1920 x 1200 and about any resolution will work.
My /etc/default/grub file contains this line and 32 is bit depth.
GRUB_GFXMODE=1920x1200x32
That is all that is in that file.

sudo update-grub to make the changes stick.

again can you please specify your gfx card??

and thanx for that awesome link!!!

---

### Post by Ginsu543 on 2010-05-15
Is it just the grub screen giving you trouble, or does your Plymouth (the screen with the Ubuntu logo and red/white "progress" dots) appear low res as well?

I too have my GRUB_GFXMODE set to 1920x1200, but you might want to add this line to your /etc/default/grub file:

```

GRUB_GFXPAYLOAD_LINUX=*width*x*height* (where *width* and *height* are the screen resolution you want)

```See if that does anything to help you. The other thing to try would be to use the nVidia restricted driver instead of Nouveau.

---

### Post by inso_741 on 2010-05-15
> **Ginsu543 said:**
> Is it just the grub screen giving you trouble, or does your Plymouth (the screen with the Ubuntu logo and red/white "progress" dots) appear low res as well?

I too have my GRUB_GFXMODE set to 1920x1200, but you might want to add this line to your /etc/default/grub file:

```

GRUB_GFXPAYLOAD_LINUX=*width*x*height* (where *width* and *height* are the screen resolution you want)

```See if that does anything to help you. The other thing to try would be to use the nVidia restricted driver instead of Nouveau.

its just grub screen........
Plymouth runs at my native resolution of 1440x900 thanx to nouveau
and I dont think restricted drivers will help because vesafb draws the grub screen or am I missing something here?

---

### Post by Ginsu543 on 2010-05-15
Have you tried changing the Grub2 splash image? Maybe making Grub2 use a splash image that is the same size as your screen resolution will force Grub2 to comply. If you want to give this a try, all you have to do is make some simple changes in your /etc/grub.d/05_debian_theme file:

```

WALLPAPER="/path_to_your_splash_image/splash_image.jpg"

```The file can also be .png and .tga, besides .jpg. Just throwing stuff at the wall, hoping something will stick. :)

---

### Post by inso_741 on 2010-05-15
> **Ginsu543 said:**
> Have you tried changing the Grub2 splash image? Maybe making Grub2 use a splash image that is the same size as your screen resolution will force Grub2 to comply. If you want to give this a try, all you have to do is make some simple changes in your /etc/grub.d/05_debian_theme file:

```

WALLPAPER="/path_to_your_splash_image/splash_image.jpg"

```The file can also be .png and .tga, besides .jpg. Just throwing stuff at the wall, hoping something will stick. :)

thats the plan actually but the image gets cropped to 4:3 resolution
and unless grub is set to use wide resolutions I don't think it will work
by the way we have the same configuration(as per your signature) so can you tell me what modes does 'vbeinfo'
lists for your machine??
also specify your monitor details....

---

### Post by inso_741 on 2010-05-15
why does 'hwinfo --framebuffer' say that all modes are available while 'vbeinfo' fails is the real question!!!
its all about Vesa Bios Extensions.....so please donot drag xorg or nouveau into the discussion....
and maybe I should try using nvidiafb instead of vesafb but I dont have much time to do that 
as I've to prepare for my exams but I'll definitely try it afterwards.........

---

### Post by Ginsu543 on 2010-05-15
Well, my monitor is the Dell UltraSharp 2407WFP with a native resolution of 1920x1200. I simply changed my GRUB_GFXMODE setting from the default 640x480 to 1920x1200, added GRUB_GFXPAYLOAD_LINUX=1920x1200 so my Plymouth screen will work with my nVidia restricted drivers, and changed the WALLPAPER= setting in /etc/grub.d/05_debian_theme to point to my splash image. And everything works as it should. I'm not sure how to get the vbeinfo, so I'm not sure what modes my video card supports (although I assume all the major ones).

---

### Post by inso_741 on 2010-05-15
> **Ginsu543 said:**
> Well, my monitor is the Dell UltraSharp 2407WFP with a native resolution of 1920x1200. I simply changed my GRUB_GFXMODE setting from the default 640x480 to 1920x1200, added GRUB_GFXPAYLOAD_LINUX=1920x1200 so my Plymouth screen will work with my nVidia restricted drivers, and changed the WALLPAPER= setting in /etc/grub.d/05_debian_theme to point to my splash image. And everything works as it should. I'm not sure how to get the vbeinfo, so I'm not sure what modes my video card supports (although I assume all the major ones).

thanx for the quick reply
here's short how-to for vbeinfo
at the grub boot menu press c to enter grub cli
at the prompt type 'vbeinfo' press enter
a list of supported modes will follow
press esc to exit

I'm guessing that you will find wide modes in that list but I cant and that is what I need to solve now the only difference in our config is my lame 19" analog lcd(yes it doesn't have a dvi-in)
I'm gonna try uvesafb and post the results here.....

---

### Post by Cavsfan on 2010-05-15
> **inso_741 said:**
> again can you please specify your gfx card??

and thanx for that awesome link!!!

(sorry been away)
I have an nvidia 9800 GT.

---

### Post by Cavsfan on 2010-05-15
Since we both have Nvidia cards, here is some info that should help:
(I am using the 195.36.14 version as shown in System > Administration > NVIDIA X Server, 
but I set the version with System > Administration > Hardware Drivers to the recommended version.)

sudo grub-mkconfig (displays all of the info about where the grub stuff is coming from)

You will see a beginning and ending line for each file involved in grub 
e.g.
### BEGIN /etc/grub.d/00_header ###
...
...
### END /etc/grub.d/00_header ###

I had to create this directory as it did not exist before - /usr/share/images/grub/
and that is where I have put my grub2 picture 1920 x 1200, what ever your native res. is will work.

sudo gedit /etc/grub.d/05_debian_theme  (this is where the grub picture and text colors are stored)
Just below these 3 commands
[COLOR=Red]# check for usable backgrounds
use_bg=true
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then[/COLOR]

you should have this line or add it:
         [COLOR=Red]for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/xxxxxx.{png,tga,jpg} ; do[/COLOR]
Where xxxxxx is your picture. I was told jpg works the best. Put the line exactly like it is above.
This file is also where you put your normal and highlight color.
The colors are right after this line:
[COLOR=Red]if background_image `make_system_path_relative_to_its_root ${bg}` ; then[/COLOR]

I have mine set to light cyan for normal and white for highlight. the 2nd color black means transparent.
These work for my picture, but might not be good for a different color picture.
    [COLOR=Red]set color_normal=light-cyan/black
    set color_highlight=white/black[COLOR=black]

For the default line, timeout and resolution - 
sudo gedit /etc/default/grub

GRUB_DEFAULT=0   (this line starts 0,1,2,3 - 3 would be the 4th line down)
GRUB_TIMEOUT=30 (display menu 30 secs. this is because I dual boot win 7 and lucid lynx)
GRUB_GFXMODE=1920x1200x32  (my resolution is defined to grub)

Here is my entire [/COLOR][/COLOR][COLOR=Red][COLOR=black]/etc/default/grub:

[/COLOR][/COLOR]```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=30
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1200x32

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```[COLOR=Red][COLOR=black]

And most important after any changes, run "sudo update-grub" or you changes will not take.
I don't know how many times I have forgotten that and the changes did not show on next boot. :(
But, even if you forget, entering that command and rebooting shows the difference.
I do hope this helps as you have been fighting this for too long.
Let me know if you need anything else.
[/COLOR][/COLOR]

---

### Post by drs305 on 2010-05-15
> **Cavsfan said:**
> 
Just below these 3 commands
[COLOR=Red]# check for usable backgrounds
use_bg=true
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then[/COLOR]

you should have this line or add it:
         [COLOR=Red]for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/xxxxxx.{png,tga,jpg} ; do[/COLOR]
Where xxxxxx is your picture. I was told jpg works the best. Put the line exactly like it is above.


The background image line quoted above is how it was written in Grub 1.97. While it may still work in Grub 1.98, which is the version used by Lucid with all the updates, the lines you have in your /etc/grub.d/05_debian_theme file may look more like this. If so, there shouldn't be a need to change these particular lines. Mixing Grub 1.97 and Grub 1.98 lines in the same configuration files may cause unexpected results:

> # this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
   WALLPAPER="[COLOR="Blue"]/usr/share/images/desktop-base/moreblue-orbit-grub.png[/COLOR]"
   COLOR_NORMAL="black/black"
   COLOR_HIGHLIGHT="magenta/black"

The path/filename in the blue font should reflect the actual path/filename of the background image you are using.

---

### Post by inso_741 on 2010-05-16
thanx for the replys but displaying a background image at grub menu is not the issue here, I've already done that successfully on my laptop.....
the issue is that vbe doesnt somehow list wide modes for my desktop 
so when I boot with a wide resloution say 1440x900 or 1280x800, the monitor says "Out of Range" only for the grub menu part of the boot process then after timeout of 10 sec it boot up the default os and everythings good after that........my guess is vesafb either displays those resolutions at frequencies less than 60Hz or greater than 74.6Hz from what my monitor says.....
I'm gonna try 'vbeinfo' on my friend's digitally connected monitor to see if it works
can someone with analog monitor conform this??? so I can finally give up on this and wait till I can afford another LCD with dvi input????:confused:

I've read a lot on VBE and I can assure you that nvidia drivers wont help me unless I want to screw up the splash
just google VBE wiki its really very informative........I've learned a lot about the booting process thanx to this "still unsolved" issue

---

### Post by drs305 on 2010-05-16
You are correct that the background issue isn't your problem. The resolutions available to Grub2 are determined by your BIOS and I believe you have been looking into that issue.

---

### Post by Cavsfan on 2010-05-16
Thanks drs305 for pointing out I have 1.97 in my 1.98 grub2!
I have 1.98 installed.

---

### Post by Cavsfan on 2010-05-16
> **drs305 said:**
> The background image line quoted above is how it was written in Grub 1.97. While it may still work in Grub 1.98, which is the version used by Lucid with all the updates, the lines you have in your /etc/grub.d/05_debian_theme file may look more like this. If so, there shouldn't be a need to change these particular lines. Mixing Grub 1.97 and Grub 1.98 lines in the same configuration files may cause unexpected results:



The path/filename in the blue font should reflect the actual path/filename of the background image you are using.

Would you know how I could obtain a copy of GRUB2 version 1.98 /etc/grub.d/05_debian_theme w/o re-installing it?
I would like to fix it back to how you mentioned.
Thanks!

And inso_741, sorry for the confusion and intruding on your post!

---

### Post by drs305 on 2010-05-16
> **Cavsfan said:**
> Would you know how I could obtain a copy of GRUB2 version 1.98 /etc/grub.d/05_debian_theme w/o re-installing it?

I've sent it to you via PM. Save it as /etc/grub.d/05_debian_theme, make it executable, change the WALLPAPER entry to point to the desired background image, then run "update-grub".

Note: You can refresh all the Grub2 default files by purging and then reinstalling grub-common (which also removes grub-pc). You actually would purge *grub-common* and then install *grub-pc* (which would also install grub-common). The downside is that if you lose your Internet connection or power while doing so you would be left without a bootable system.

---

### Post by Cavsfan on 2010-05-16
> **drs305 said:**
> I've sent it to you via PM. Save it as /etc/grub.d/05_debian_theme, make it executable, change the WALLPAPER entry to point to the desired background image, then run "update-grub".

Note: You can refresh all the Grub2 default files by purging and then reinstalling grub-common (which also removes grub-pc). You actually would purge *grub-common* and then install *grub-pc* (which would also install grub-common). The downside is that if you lose your Internet connection or power while doing so you would be left without a bootable system.

Thanks very much!!! I got it!  This one line is all I changed to be like version 1.97.
I will have version 1.98 back as soon as I get this fixed.
Thanks again! :D

---

### Post by inso_741 on 2010-05-16
I found another [thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1474799") with similar issues!!!
I'm happy I'm not alone!!!!!!haha just kiddin...

---

### Post by inso_741 on 2010-05-20
Update:
so I finally decided to ditch nouveau for a cooler, quieter case
as expected it screwed up my splash
so I tried the 'gfxpayload=keep fix' and it dint work
I wasnt surprised that it doesnt again work with wide resolutions
as the workaround just makes use of VBE to display the splash........
I dint get any time to check try it on a digitally connected monitor although I'll try in a couple of days.................

---

### Post by Cavsfan on 2010-05-20
> **inso_741 said:**
> Update:
so I finally decided to ditch nouveau for a cooler, quieter case
as expected it screwed up my splash
so I tried the 'gfxpayload=keep fix' and it dint work
I wasnt surprised that it doesnt again work with wide resolutions
as the workaround just makes use of VBE to display the splash........
I dint get any time to check try it on a digitally connected monitor although I'll try in a couple of days.................

I wish I could help as we have similar machines with Nvidia video cards. I have a 9800 GT, 
but I don't have a clue as to why you're not able to get this resolved.
I have a 1920 x 1200 GRUB2 screen which looks VERY good and everything works very well.
Are you still on Ubuntu 8.04 Hardy Heron as your profile shows. Wouldn't think that would matter, 
but since Lucid is LTS and it has been in final release, maybe upgrading to that would help. 
I am amazed with Lucid! I boot up in under 15-20 seconds including the dual boot grub screen and the login in screen. 
It totally screams! Might be worth a try! :)

---

### Post by inso_741 on 2010-05-20
I've finally updated my sig.!!!
I've been using Lucid(final x86_64) on my desktop.
I don't have this issue with my laptop i.e. it boots @ a native 1280x800(looks great)
but somehow it doesn't do so on my desktop........the only difference here is the laptop screen is digitally connected and the monitor for my desktop is analog(which I think is the problem but not confirmed yet!!!)
I'm guessing your monitor is digitally connected, am I right?

---

### Post by Cavsfan on 2010-05-20
> **inso_741 said:**
> I've finally updated my sig.!!!
I've been using Lucid(final x86_64) on my desktop.
I don't have this issue with my laptop i.e. it boots @ a native 1280x800(looks great)
but somehow it doesn't do so on my desktop........the only difference here is the laptop screen is digitally connected and the monitor for my desktop is analog(which I think is the problem but not confirmed yet!!!)
I'm guessing your monitor is digitally connected, am I right?

Yes, I have a DVI to HDMI cable. That may be it.

---

### Post by inso_741 on 2010-05-22
update : (probably the last one from my side)
I borrowed my friend's lcd which has a dvi-in...hooked it with my gtx260 and guess what 'vbeinfo' listed all the wide-screen mode supported by the monitor
so this confirms it......the issue is only with the analog displays that support wide-screen resolutions........Now that I know this I'm wondering what can I do to get it resolved??
should I file a bug report??? If yes how?....never done that before........help me guys cause I wont be getting a new monitor for a long time.......:(

---

### Post by tripmix on 2010-10-10
Well, since you can get 4:3 at both screens cant you just make the pic to emulate 16:9? Just make/edit the image in 16:9 res then scale it to 4:3 res when done. If yo make an image 1920x1080, draw a circle in the middle then scale it to 1280x1024 now when it gets stretched the circle will look round again. Simple but effective (as long as you only use it on wide displays). Example: [ATTACH]171827[/ATTACH]

---

### Post by inso_741 on 2010-10-11
now thats an idea but TBH I've no intrest in gfx....the thing that I'm lookin for is crisp white txt on black bg...;-)...thanx for the suggestion though

---

