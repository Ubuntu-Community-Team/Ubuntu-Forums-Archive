---
title: "A Beginner's Guide to Theming GRUB2"
date: 2010-07-19
forum: General Help
---

### Post by towheedm on 2010-07-19
Would you like to learn to theme GRUB2?  Now, when I say theme GRUB2, I don't mean to simply add a wallpaper and change the text's colors.  I'm talking about adding graphics, different fonts, scrollbar, progress bar etc.  Check out the attached file for a screenshot of what's possible.

Interested?  Well it's all explained in my latest tutorial 'A Beginner's Guide to Theming GRUB2'.  It's a 37 page PDF document that explains it all.  Of course, 37 pages complete with screenshots and a sample theme is quite a lot to post.  So it's all in my tutorial available here:

[COLOR=Blue][http://www.mediafire.com/?amub1vfdyfhj7v2](http://www.mediafire.com/?amub1vfdyfhj7v2)[/COLOR] (This is obsolete, but is still there)

Edit:  Apparently, 4shared.com now requires you to login or register before downloading files.  For this reason, I have moved the file from there and have published it from my Ubuntu One account.

The 2nd and 3rd editions are now available for download here:
[http://ubuntuone.com/2EslXTLj5s2zzbeYKx17wJ](http://ubuntuone.com/2EslXTLj5s2zzbeYKx17wJ)

This now covers GRUB v1.99 for the following distros:
[LIST]
[*]Arch Linux 2011.08.19 using GRUB     1.99-5
[*]Debian Squeeze using GRUB     1.99-14 from Debian Wheezy
[*]Debian Wheezy using GRUB 1.99-14
[*]Fedora 14 (Laughlin) and Fedora     15 (Lovelock) using GRUB 1.99-13.fc16 from Fedora 16
[*]Fedora 16 (Verne) using GRUB     1.99-13.fc16
[*]LinuxMint 10 (Julia) using GRUB     1.99-12ubuntu5-1linuxmint1 from LinuxMint 12
[*]LinuxMint 12 (Lisa) using  GRUB     1.99-12ubuntu5-1linuxmint1
[*]Mandriva 2011.0 (Turtle) using     GRUB 1.99
[*]openSUSE 11.3 (Teal) and     openSUSE 11.4 (Celadon) using GRUB 1.99-8.7.2 from openSUSE 12.1
[*]openSUSE 12.1 (Asparagus) using     GRUB 1.99-8.7.2
[*]Sabayon 7 using GRUB 1.99
[*]Slackware Linux 13.37  using     GRUB 1.99
[*]Ubuntu 10.04 (Lucid), 10.10     (Maverick) and 11.04 (Natty) using GRUB 1.99-12ubuntu3 from Ubuntu     11.10
[*]Ubuntu 11.10 (Oneiric) using     GRUB 1.99-12ubuntu5
[*]VectorLinux 7.0 using GRUB 1.99
[/LIST]
It includes instructions to upgrade to GRUB 1.99 from the repos of the respective distros.

I have left the 2nd edition, which covers GRUB 1.98, in the tar archive.

Please feel free to post any comments or questions about it in this thread.

You may post your themes here:
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)

Happy GRUB2 Theming.:

---

### Post by K.Mandla on 2010-07-23
Moved to General Help.

---

### Post by hansdown on 2010-07-23
Thanks, towheedm.

This looks interesting.

---

### Post by towheedm on 2010-07-23
> **hansdown said:**
> Thanks, towheedm.

This looks interesting.

Most welcome.  Please let me know how it works out for you, any bugs etc.

---

### Post by towheedm on 2011-06-09
The 2nd edition is now available for download at:
[http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html](http://www.4shared.com/file/lFCl6wxL/grub_guidetar.html)

It now includes Ubuntu and Variants (Karmic, Lucid and Maverick), Debian  6.0, Sabayon 5.5, openSUSE 11.3, Fedora 14 and LinuxMint 10.

It also includes many other customization to the boot menu.

---

### Post by towheedm on 2011-11-22
For those using a separate /boot partition and having problems getting their themes to display, here is a very simple/quick fix:

Copy the unicode font to /boot/grub:```

sudo cp /usr/share/grub/unicode.pf2 /boot/grub/

```You may also need to add the following line to [COLOR=Blue]/etc/default/grub[/COLOR]:
```
GRUB_FONT_PATH=/boot/grub
```Finally, update GRUB's configuration file.

---

### Post by Anomandaris on 2011-12-02
Hey, I've just moved from Ubunutu 10.04 to Lubuntu 11.10 (so I'm using Grub 1.99-12ubuntu5), and I've got a couple of questions:

[LIST]
[*]Am I correct in believing that "Modify /etc/grub.d/00_header" (pg19 of the guide) should be skipped, as for Grub 1.98+20100804?
[*]Is there anything (that you know of) I should be aware of that is significantly different when using Grub 1.99? (Yes, I do realise the guide was not written for 11.10 and Grub 1.99...)
[/LIST]

---

### Post by towheedm on 2011-12-03
Yes, you must skip this and continue on to '*Adding More Menu Items*'.

If you have a separate /boot partition then check the post above yours.  This may have been fixed in GRUB 1.99 but I am not sure if it's been applied by all distros.

Also, have a look at this thread first:
[http://ubuntuforums.org/showthread.php?t=1846754](http://ubuntuforums.org/showthread.php?t=1846754)

If you have a 'Previous Linux Versions' menu item, selecting it may not necessarily show a themed screen.

Note also, that the keypresses lags.  This lag increaes as the number of menu items increases.

You can also post your themes here:
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)

I have left Ubuntu in favor of Debian.  While I do not monitor the forums as I did, I still remain a member, so feel free to post any support questions to this thread or you may also PM me.

Hope you find the guide useful.

I'm about to start the 3rd edition which will certainly include 1.99.  This will be completed early next year.  Keep your subscription to this thread as I'll post to it when I've uploaded it.

OK, here's rather quick way to know, whether or not the themes will display properly.  Download one of the themes from the post above and install it.  If it displays, you're good to go.  If not post back.

---

### Post by Anomandaris on 2011-12-03
Thanks for the help!

OK, so approximate steps I have needed to take to get the basic theme in your guide running: (pretty much as for 1.98+20100804)

[LIST=1]
[*]Copy 08_gfxmenu to /etc/grub.d/
[*]Put theme resources in /boot/grub/themes/theme_name
[*]Add GRUB_THEME=path_to_theme.txt to /etc/default/grub.d
[*]Run sudo update-grub
[*]Reboot
[/LIST]
 
More info/Oddities:

[LIST=1]
[*]I switched to Virtual Box just so I could test things quickly and to avoid any real risk. I then had some bizarre issues with failing to reach the login screen after a reboot (from the OS menu, with the VM power button, and even with killing the VM...) which have... gone away. This bothers me (that the problem just stopped happening) but I'm not going to chase it unless it comes back. Hopefully not GRUB related.
[*]The console area replaces parts of the background and menu items once a menu item has been selected. This looks horrible. Is there any way around this?
[*]The "Previous Linux Versions" option is indeed not themed (default white on black) if you descend into it. Is there a way to get this themed too?
[*]Neither the memtestx86+ options nor the "Previous Linux Versions" options have a [FONT=Courier New]--class[/FONT] by default
[*][FONT=Courier New]sudo update-grub[/FONT] prints [FONT=Courier New]Found theme: path/to/theme.txt[/FONT] twice - maybe something to do with the new submenu?
[*]Plymouth seems to have only sometimes work. Not necessarily anything to do with GRUB or themes, but I am a sucker for eyecandy.
[*]I didn't set up a separate /boot partition so I can't tell you anything useful about that.
[*]Parts of your "Customising The Menu Items" section seem like they might not be the same for the 1.99 config files - I'll investigate this later.
[*]I haven't tried the install script yet.
[/LIST]
 
I'm looking forward to your guide v3~

---

### Post by dcstar on 2011-12-03
Gee, it looks a bit like BURG but with a lot more stuffing around to achieve the same outcome.

---

### Post by Anomandaris on 2011-12-03
> **dcstar said:**
> Gee, it looks a bit like BURG but with a lot more stuffing around to achieve the same outcome.
[http://askubuntu.com/questions/11863/why-doesnt-burg-replace-grub/20187#20187](http://askubuntu.com/questions/11863/why-doesnt-burg-replace-grub/20187#20187)

Besides, some of us enjoy learning how to do things the hard way.

---

### Post by CryptAck on 2011-12-03
> **Anomandaris said:**
> 
Besides, some of us enjoy learning how to do things the hard way.

+1

What fun is there in life if you always take the easy route! :)

---

### Post by towheedm on 2011-12-04
> OK, so approximate steps I have needed to take to get the basic theme in your guide running: (pretty much as for 1.98+20100804)

[LIST=1]
[*]Copy 08_gfxmenu to /etc/grub.d/
[/LIST]
More info/Oddities:
[FONT=Courier New]
    5.  sudo update-grub[/FONT] prints [FONT=Courier New]Found theme: path/to/theme.txt[/FONT] twice - maybe something to do with the new submenu?


That's because you copied [COLOR=Blue]08_gfxmenu[/COLOR] to [COLOR="Blue"]/etc/grub.d[/COLOR].  You only need this for GRUB2 prior to 1.98+20100804.  Remove [COLOR="Blue"]08_gfxmenu[/COLOR] from [COLOR="Blue"]/etc/grub.d[/COLOR].

> 2. The console area replaces parts of the background and menu items once a menu item has been selected. This looks horrible. Is there any way around this?


Could you post a screenshot.  This sounds like the terminal window.

> 3. The "Previous Linux Versions" option is indeed not themed (default white on black) if you descend into it. Is there a way to get this themed too?

I'll look at this in the 3rd Edition.  I'm not sure if it's GRUB2 or Ubuntu's release of GRUB2.  Certainly GRUB 1.99-14 from Debian does not generate a Sub-menu (Previous Linux Version) menu item.  This is done in [COLOR="Blue"]/etc/grub.d/10_linux[/COLOR].  You may remove the lines of code that produces it in the meantime if you wish.  I recommend you comment out the lines instead of deleting them.

> 4. Neither the memtestx86+ options nor the "Previous Linux Versions" options have a --class by default


As I said in my previous post, have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1846754](http://ubuntuforums.org/showthread.php?t=1846754)

> 6. Plymouth seems to have only sometimes work. Not necessarily anything to do with GRUB or themes, but I am a sucker for eyecandy.


What video card are you using?  Do you have [COLOR="Teal"]GRUB_GFXPAYLOAD_LINUX[/COLOR] set in your [COLOR="Blue"]/etc/default/grub[/COLOR] file?

> 8. Parts of your "Customising The Menu Items" section seem like they might not be the same for the 1.99 config files - I'll investigate this later.


Some of GRUB2 env vars have changed between 1.98 and 1.99 so some of that section may not necessarily work with 1.99.

> ....but I am a sucker for eyecandy.

Then you may also like the 'Customizing GDM' section in my other tutorial:
[http://www.mediafire.com/file/2yimyo3ow3t/ubuntu_customization.tar.gz](http://www.mediafire.com/file/2yimyo3ow3t/ubuntu_customization.tar.gz)

---

### Post by Anomandaris on 2011-12-05
> **towheedm said:**
> That's because you copied [COLOR=Blue]08_gfxmenu[/COLOR] to [COLOR=Blue]/etc/grub.d[/COLOR].  You only need this for GRUB2 prior to 1.98+20100804.  Remove [COLOR=Blue]08_gfxmenu[/COLOR] from [COLOR=Blue]/etc/grub.d[/COLOR].
  Ah. Oops. Thanks for pointing that out.

> **towheedm said:**
> 
Could you post a screenshot.  This sounds like the terminal window.
  OK, so it is definitely the terminal window. It's a black box if I  don't theme the terminal window, otherwise it has the appropriate borders etc.  It's still pretty undesirable. Unfortunately I only worked that out *after* my  previous post. I can still post a screenshot if you want, but it'll have  to wait a few hours (I'm not at home right now.) Any way around it that you know of? Have I missed something obvious again?

> **towheedm said:**
> 
As I said in my previous post, have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1846754](http://ubuntuforums.org/showthread.php?t=1846754)
  Sorry, I should have made it clear that that was purely informative - I did look at that thread the first time and had no problems sorting it out.

> **towheedm said:**
> 
What video card are you using?  Do you have [COLOR=Teal]GRUB_GFXPAYLOAD_LINUX[/COLOR] set in your [COLOR=Blue]/etc/default/grub[/COLOR] file?
  The machine in question is a laptop with a Mobility Radeon HD5450. I am not using the FGLRX drivers, although I was at one point. [COLOR=Teal]GRUB_GFXPAYLOAD_LINUX[/COLOR] is not set. [COLOR=Teal]GRUB_GFXMODE[/COLOR] is set to 1366x768.

> **towheedm said:**
> 
Some of GRUB2 env vars have changed between 1.98 and 1.99 so some of that section may not necessarily work with 1.99.
 Sorry, I still haven't had a chance to test that out yet.

> **towheedm said:**
> 
Then you may also like the 'Customizing GDM' section in my other tutorial:
[http://www.mediafire.com/file/2yimyo3ow3t/ubuntu_customization.tar.gz](http://www.mediafire.com/file/2yimyo3ow3t/ubuntu_customization.tar.gz) Thanks! I'll check it out.[URL="http://Thanks%21%20I%27ll%20check%20it%20out.%3Cbr%20/%3E"]
[/URL]

---

### Post by towheedm on 2011-12-05
You cannot get rid of the terminal window.  You'll always get a black box if it's not themed.  The terminal window is used to show any messages from GRUB.  It also provides the command-line area.

I have never used the fglrx drivers.  I use the proprietary nVidia drivers.  I also never got Plymouth to display properly at all times.  But with Debian, no Plymouth....woo hoo ! :)

Oh...you're not using the fglrx drivers.  I installed Natty on my sister's desktop with an on-board  ATI Radeon  but also never got Plymouth to display properly with the proprietary drivers.  It only works with the fglrx drivers.

You can try setting GRUB_GFXPAYLOAD_LINUX=keep in /etc/default/grub and see if that works.  Note, when I did this it caused the system to hang between Plymouth and GDM unless I set my GRUB timeout to > 30secs and let the time expire.  I worked around this by using the now deprecated vga=VGAMODE kernel command line option.  If you decide to try either, verify that the Linux framebuffer will work with the selected mode.

---

### Post by towheedm on 2011-12-05
I've been saving this for the 3rd Edition, but here it is not fully tested:

You may have a background image in the terminal box.  There are two possible ways:

1.  Set the center slice of the terminal to whatever image you want to use as the background.  It should be scaled accordingly.  If you do this, make sure that update-grub does not show 'Found Background Image...'

2. Set a background image manually by adding:
```
GRUB_BACKGROUND=/path/to/image
```to /etc/default/grub.  Make sure the image is readable by GRUB.  This image is not scaled.

Well it seems that the first method does not work.  The terminal window is always rendered with a black background.  However, the second method works but the image appears to be scaled to the resolution set for GRUB and then cropped to fit the dimensions of the terminal window with the origin being the upper-left corner of the image.

---

### Post by Anomandaris on 2011-12-09
> **towheedm said:**
> 
You can try setting GRUB_GFXPAYLOAD_LINUX=keep in /etc/default/grub and  see if that works.  Note, when I did this it caused the system to hang  between Plymouth and GDM unless I set my GRUB timeout to > 30secs and  let the time expire.  I worked around this by using the now deprecated  vga=VGAMODE kernel command line option.  If you decide to try either,  verify that the Linux framebuffer will work with the selected  mode.
No luck. I guess I'll have to try the FGLRX drivers.

> **towheedm said:**
> I've been saving this for the 3rd Edition, but here it is not fully tested:

You may have a background image in the terminal box.  There are two possible ways:

1.  Set the center slice of the terminal to whatever image you want to use as the background.  It should be scaled accordingly.  If you do this, make sure that update-grub does not show 'Found Background Image...'

2. Set a background image manually by adding:
```
GRUB_BACKGROUND=/path/to/image
```to /etc/default/grub.  Make sure the image is readable by GRUB.  This image is not scaled.

Well it seems that the first method does not work.  The terminal window is always rendered with a black background.  However, the second method works but the image appears to be scaled to the resolution set for GRUB and then cropped to fit the dimensions of the terminal window with the origin being the upper-left corner of the image.
Thanks - that's certainly something I can work with (in my quest for less of a visual clash once the option is selected). Is there any way to change the size of the terminal box? Or reposition it?

---

### Post by towheedm on 2011-12-09
> **Anomandaris said:**
> No luck. I guess I'll have to try the FGLRX drivers.


Thanks - that's certainly something I can work with (in my quest for less of a visual clash once the option is selected). Is there any way to change the size of the terminal box? Or reposition it?

Not unless you wamt to modify the source code.  As it is, the size of the terminal box is set to 70% of the screen's size set by GRUB_GFXMODE and it's position is centered on the screen.

---

### Post by Anomandaris on 2011-12-09
> **towheedm said:**
> Not unless you want to modify the source code.  As it is, the size of the terminal box is set to 70% of the screen's size set by GRUB_GFXMODE and it's position is centered on the screen.
I think I'll make do with taking the centre 70% of the theme background image, putting it into the top left corner of the full-sized background image used by GRUB_BACKGROUND, and then arranging the menu icons and text so that nothing is partially cut off by the terminal box (i.e. either an entry is fully visible or not at all when the terminal box plasters itself on top).

It's a rather crude "solution", inflexible and hardly portable, but it'll do for now.

---

### Post by c.cobb on 2011-12-22
Hi towheedm,
Thanks for such a great theming tutorial. I'm just starting to experiment with this, and have a couple of questions before I start changing things. 

It's tough to find good theme examples (besides yours). I did find several at kde-look.org, including [this very nice one]("http://kde-look.org/content/show.php/Da+Vinci?content=93952"). However, it's packaged up in a cpio archive called "message," which includes all of the theme elements. I didn't see anything like this in your guide or in the [Theme File Format doc]("http://grub.gibibit.com/Theme_format") -- is this an alternative mechanism, or is this old/obsolete? Seems like a nice way to go, as the setup is very simple, as noted at the above link:

> Simple installation guide: Place the "message" file in your /boot/grub/ directory and change your grub config file to contain "gfxmenu /boot/grub/message" at the top of the file.Second question: I notice in the first screen shot at the above link that there is a separation in the menu, but I don't see the way to make this work. Is this easy to do? Haven't figured out how to do this in the standard Grub2 menu either, and it drives me nuts not to have some control over the spacing. 
Thanks again,

---

### Post by towheedm on 2011-12-22
That theme at kde-look is for grub-legacy and not GRUB2.  It is not compatible.  Of course, you can take the elements of the theme (background, fonts, etc) and make a GRUB2 theme from it.

Have a look at this thread for a couple more themes:
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)

Towards the end of the guide is a theme installation script which makes installing your theme quite simple.  It starts on Pg 50 of the guide.

The theme format manual at grub.gibibit.com is for the most parts obsolete and not maintained anymore.  It's good for a quick reference of the theme elements.  The properties of the theme elements have changed considerable from what's there.

You cannot have menu separation as the one shown on the theme at kde-look in the GRUB2 themes.  The most you can do at this time is to specify the spacing between menu items.  You might consider posting a feature request to the GRUB devs.

---

### Post by towheedm on 2012-04-08
I have just uploaded the 3rd Edition to my guide.  This now covers GRUB v1.99 for the following distros:
[LIST]
[*]Arch Linux 2011.08.19 using GRUB     1.99-5
[*]Debian Squeeze using GRUB     1.99-14 from Debian Wheezy
[*]Debian Wheezy using GRUB 1.99-14
[*]Fedora 14 (Laughlin) and Fedora     15 (Lovelock) using GRUB 1.99-13.fc16 from Fedora 16
[*]Fedora 16 (Verne) using GRUB     1.99-13.fc16
[*]LinuxMint 10 (Julia) using GRUB     1.99-12ubuntu5-1linuxmint1 from LinuxMint 12
[*]LinuxMint 12 (Lisa) using  GRUB     1.99-12ubuntu5-1linuxmint1
[*]Mandriva 2011.0 (Turtle) using     GRUB 1.99
[*]openSUSE 11.3 (Teal) and     openSUSE 11.4 (Celadon) using GRUB 1.99-8.7.2 from openSUSE 12.1
[*]openSUSE 12.1 (Asparagus) using     GRUB 1.99-8.7.2
[*]Sabayon 7 using GRUB 1.99
[*]Slackware Linux 13.37  using     GRUB 1.99
[*]Ubuntu 10.04 (Lucid), 10.10     (Maverick) and 11.04 (Natty) using GRUB 1.99-12ubuntu3 from Ubuntu     11.10
[*]Ubuntu 11.10 (Oneiric) using     GRUB 1.99-12ubuntu5
[*]VectorLinux 7.0 using GRUB 1.99
[/LIST]
It includes instructions to upgrade to GRUB 1.99 from the repos of the respective distros.
The download link is the same as in post #1:
_[http://ubuntuone.com/2EslXTLj5s2zzbeYKx17wJ](http://ubuntuone.com/2EslXTLj5s2zzbeYKx17wJ)_

---

### Post by luke91 on 2012-06-13
Looks like a great guide but I have Ubuntu 12.04 installed and the guide only states up to 11.10. Would the guide still work for the newest version of Ubuntu?

---

### Post by towheedm on 2012-06-13
> **luke91 said:**
> Looks like a great guide but I have Ubuntu 12.04 installed and the guide only states up to 11.10. Would the guide still work for the newest version of Ubuntu?

Yes it would.

---

### Post by hal8000 on 2012-11-01
This is a great guide.
I'm using Ubuntu 12.10 which now uses grub 2.00

After reading revision3 thought I'd try the script to install the demo menu,
however it fails will following error (displayed in red) :


sudo ./install.sh 
Could not locate "/etc"/default/grub.

I have a feeling there is a problem in eiether the sed script to locate the patch as message shows /etc as  /etc"

or is it because I'm using Ubuntu 12.10?
Thanks in advance.

---

### Post by towheedm on 2012-11-01
Could you post the output of:
```
grep ^sysconfdir $(sudo which grub-mkconfig)
```

Thanks for the feedback.

---

### Post by hal8000 on 2012-11-03
Sorry for delay output from grep:


hal@Orac:~$ grep ^sysconfdir $(sudo which grub-mkconfig)

sysconfdir="/etc"

---

### Post by towheedm on 2012-11-06
Here is the patched install.sh script.   There were several other changes to GRUB 2.00 grub-mkconfig script.

I've also included it in the main download archive.

---

### Post by hal8000 on 2012-11-07
Thanks a lot Towheed.

OK, I have it working but there were a few problems.
First off I ran the new install script from my downloads directory
and it copied all the files from ~/Downloads into /boot/grub/themes/demo ?

I then read the document again and this time moved the script to ~/Documents
 and it installed but again no theme?

I have a look at /etc/default/grub   contents below:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
--snip--

export GRUB_COLOR_NORMAL="light-blue/black"
export GRUB_COLOR_HIGHLIGHT="white/black"
GRUB_BACKGROUND=/boot/grub/themes/demo/terminal-background-workaround.png

GRUB_THEME=/boot/grub/themes/demo/theme.txt

#UNNAMED_OPTION=""
[COLOR="Red"]export GRUB_MENU_PICTURE="/boot/grub/themes/demo/demo/gnu-linux-color-wallpaper.png"[/COLOR]
GRUB_FONT="/boot/grub/unicode.pf2"


From the above it became clear that there is another demo directory within demo.

I change the other paths to include demo/demo  ran update-grub and now have the demo theme , but no icons.

I've had some practise with burg so am currently looking at this, for now
the contents of /boot/grub/themes/demo:

ls /boot/grub/themes/demo -l
total 5612
-rw-r--r-- 1 root root     608 Nov  7 17:13 00_header-01.patch
-rw-r--r-- 1 root root    4162 Nov  7 17:13 10_linux-arch-01.patch
-rw-r--r-- 1 root root    4465 Nov  7 17:13 10_linux-debian-mandriva-sabayon-01.patch
-rw-r--r-- 1 root root    4466 Nov  7 17:13 10_linux-fedora-01.patch
-rw-r--r-- 1 root root    4399 Nov  7 17:13 10_linux-mint-01.patch
-rw-r--r-- 1 root root    4602 Nov  7 17:13 10_linux-opensuse-01.patch
-rw-r--r-- 1 root root    4452 Nov  7 17:13 10_linux-slackware-01.patch
-rw-r--r-- 1 root root    4232 Nov  7 17:13 10_linux-ubuntu-01.patch
-rw-r--r-- 1 root root    4447 Nov  7 17:13 10_linux-vector-01.patch
-rw-r--r-- 1 root root   12403 Nov  7 17:13 30_os-prober-01.patch
-rw-r--r-- 1 root root   13497 Nov  7 17:13 30_os-prober-ubuntu-01.patch
-rw-r--r-- 1 root root    1646 Nov  7 17:13 40lsb-01.patch
-rw-r--r-- 1 root root    5267 Nov  7 17:13 90linux-distro-01.patch
-rw-r--r-- 1 root root    5303 Nov  7 17:13 90linux-distro-opensuse-01.patch
drwxr-xr-x 2 root root    4096 Nov  7 17:13 demo
-rw-r--r-- 1 root root 5600124 Nov  7 17:13 grub2_theming_guide_3rd_edition.pdf
-rw-r--r-- 1 root root     440 Nov  7 17:13 grub-mkconfig-01.patch
drwxr-xr-x 2 root root    4096 Nov  7 17:13 icons
-rwxr-xr-x 1 root root    6376 Nov  7 17:13 install.sh


There is another demo folder which contains theme.txt so I was correct to modify /etc/default/grub

I'm not sure if this is down to changes in Ubuntu 12.10 but it is working and a very nice improvement over the default Ubuntu 12.10 grub theme.

---

### Post by hal8000 on 2012-11-07
Hi Towheed,
This is a very good guide to theming grub2.


I have read the guide in Ubuntu 12.10 and am suggesting a few comments that may be helpful:

I'm using Document Read 3.6 on  Ubuntu 12.10 at screen resolution of 1280x1024. The menu pages do not correspond to pages within document. These comments refer to pages in the document (not displayed by menu):


Page 34 Theme
I would include words to the effect of:

Each grub2 theme is  selected by a reference in /etc/default/grub
Each grub2 theme is stored within its own directory inside /boot/grub/themes/



Page 38 Global Property
I would include another comment, words to the effect of:

Global properties are set defined by the file theme.txt which must be included for each grub2 theme.

---

### Post by towheedm on 2012-11-07
The guide is dependent on you following through the previous steps.  At the end of the **Demo Theme** chapter, you should have in /boot/grub/themes/demo:
```
7x13.pf2                       sb_th_c.png
arch-24.png                    sb_th_n.png
caribbean_sunset_200.jpg       sb_th_s.png
center.png                     select_c.png
debian-24.png                  select_e.png
dejavu-sans-10.pf2             select_ne.png
dejavu-sans-12.pf2             select_n.png
dejavu-sans-bold-14.pf2        select_nw.png
desktop.png                    select_se.png
gentoo-24.png                  select_s.png
gnu-linux-color-wallpaper.png  select_sw.png
kubuntu-24.png                 select_w.png
linuxmint-24.png               terminal-background.png
menu_bkg_c.png                 terminal-background-workaround.png
menu_bkg_e.png                 terminal_c.png
menu_bkg_ne.png                terminal_e.png
menu_bkg_n.png                 terminal_ne.png
menu_bkg_nw.png                terminal_n.png
menu_bkg_se.png                terminal_nw.png
menu_bkg_s.png                 terminal_se.png
menu_bkg_sw.png                terminal_s.png
menu_bkg_w.png                 terminal_sw.png
opensuse-24.png                terminal_w.png
progress_bar_c.png             theme.txt
progress_highlight_c.png       tick.png
sabayon-24.png                 tux.png
sb_fr_c.png                    ubuntu-24.png
sb_fr_n.png                    ubuntu-glow-24.png
sb_fr_s.png                    windows-24.png
icons
```And under /boot/grub/themes/demo/icons:
```
arch.png    gnu-linux.png      opensuse.png  slackware.png
debian.png  LICENSES           osx.png       submenu.png
fedora.png  linuxmint.png      recovery.png  ubuntu.png
gentoo.png  mandrivalinux.png  sabayon.png   windows.png
```

Now, at the start of the **Distributing Your Theme** chapter, the first command:
```
mkdir ~/grub-themes ; cp -r --no-preserve=ownership <grub_dir>/themes/demo ~/grub-themes/ ; cp ~/Documents/grub_guide/ed3/install.sh ~/grub-themes/demo/
```
creates a grub-themes directory in your /home directory and copies the /boot/grub/themes/demo directory and the ~/Documents/grub_guide/ed3/install.sh file to it.

Follow the steps in the rest of the chapter.

If you did not follow each step up to this point, the install script may fail.  This should help with testing the demo theme:
```
mkdir ~/grub-themes
cd ~/grub-themes
cp -r ~/Documents/grub_guide/ed3/demo .
cd demo
cp -r ~/Documents/grub_guide/ed3/icons .
cp ~/Documents/grub_guide/ed3/install.sh .
sudo rm -r /boot/grub/themes/demo
sudo ./install.sh
```
This will install the demo themes and icons to /boot/grub/themes and set the variables GRUB_BACKGROUND and GRUB_THEME in the /etc/default/grub configuration file.  It will also run update-grub to generate the new /boot/grub/grub.cfg file.

[COLOR=Red]export GRUB_MENU_PICTURE="/boot/grub/themes/demo/demo/gnu-linux-color-wallpaper.png"[COLOR=Black] is not set by the install script.

Thanks for the suggestions in your other posts.
[/COLOR][/COLOR]

---

### Post by hal8000 on 2012-11-08
Thanks a lot for your help.

I have another suggestion for testing grub2 themes without rebooting:

grub-emu


I tried grub-emu and it gave me an error relating to a video driver I do not use, so maybe someone else needs to install grub-emu.


I followed your instructions and can confirm that it works perfectly. Thank you for all the hard work you have shared with
the Community. 
In next few weeks I will have a go at a custom theme myself.

---

### Post by edkmho on 2013-05-05
Hi Towheed,

I am new to Ubuntu. This is my first Ubuntu installation.

I am trying to get the grub theme to work on my newly installed Ubuntu Gnome 13.04 and the terminal windows keep popping up after selection. I did try to patch the 00_header but not successful. 


Please help me to get rid of the terminal windows after selection is being made. 

Below is my grub file from /etc/default/grub :
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Ubuntu"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="2"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768
GRUB_THEME=/boot/grub/themes/demo/theme.txt

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#GRUB_SAVEDEFAULT="false"

GRUB_BACKGROUND=/boot/grub/themes/demo/terminal-background-workaround.png

Below is my 00_header file :
#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"

prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"
grub_lang=`echo $LANG | cut -d . -f 1`

export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"

. "${datarootdir}/grub/grub-mkconfig_lib"

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=auto ; fi

if [ "x${GRUB_DEFAULT_BUTTON}" = "x" ] ; then GRUB_DEFAULT_BUTTON="$GRUB_DEFAULT" ; fi
if [ "x${GRUB_DEFAULT_BUTTON}" = "xsaved" ] ; then GRUB_DEFAULT_BUTTON='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT_BUTTON}" = "x" ] ; then GRUB_TIMEOUT_BUTTON="$GRUB_TIMEOUT" ; fi

cat << EOF
if [ -s \$prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
EOF
if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
   set default="${GRUB_DEFAULT_BUTTON}"
else
   set default="${GRUB_DEFAULT}"
fi
EOF
else
    cat <<EOF
set default="${GRUB_DEFAULT}"
EOF
fi
cat <<EOF

if [ x"\${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "\${prev_saved_entry}" ]; then
  set saved_entry="\${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "\${boot_once}" ]; then
    saved_entry="\${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "\${have_grubenv}" ]; then if [ -z "\${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
EOF
if [ -n "${GRUB_VIDEO_BACKEND}" ]; then
    cat <<EOF
  insmod ${GRUB_VIDEO_BACKEND}
EOF
else
# If all_video.mod isn't available load all modules available
# with versions prior to introduction of all_video.mod
cat <<EOF
  if [ x\$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
EOF
fi
cat <<EOF
}

EOF

serial=0;
gfxterm=0;
for x in ${GRUB_TERMINAL_INPUT} ${GRUB_TERMINAL_OUTPUT}; do
    if [ xserial = "x$x" ]; then
	serial=1;
    fi
    if [ xgfxterm = "x$x" ]; then
	gfxterm=1;
    fi
done

if [ "x$serial" = x1 ]; then
    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
	grub_warn "$(gettext "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used.")"
	GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
fi

if [ "x$gfxterm" = x1 ]; then
    if [ -n "$GRUB_FONT" ] ; then
       # Make the font accessible
       prepare_grub_to_access_device `${grub_probe} --target=device "${GRUB_FONT}"`
    cat << EOF
if loadfont `make_system_path_relative_to_its_root "${GRUB_FONT}"` ; then
EOF
    else
	for dir in "${pkgdatadir}" "`echo '/boot/grub' | sed "s,//*,/,g"`" /usr/share/grub ; do
	    for basename in unicode unifont ascii; do
		path="${dir}/${basename}.pf2"
		if is_path_readable_by_grub "${path}" > /dev/null ; then
		    font_path="${path}"
		else
		    continue
		fi
		break 2
	    done
	done
	if [ -n "${font_path}" ] ; then
    cat << EOF
if [ x\$feature_default_font_path = xy ] ; then
   font=unicode
else
EOF
                # Make the font accessible
		prepare_grub_to_access_device `${grub_probe} --target=device "${font_path}"`
    cat << EOF
    font="`make_system_path_relative_to_its_root "${font_path}"`"
fi

if loadfont \$font ; then
EOF
	    else
    cat << EOF
if loadfont unicode ; then
EOF
	    fi
	fi

    cat << EOF
  set gfxmode=${GRUB_GFXMODE}
  load_video
  insmod gfxterm
EOF

# Gettext variables and module
if [ "x${LANG}" != "xC" ] ; then
  cat << EOF
  set locale_dir=\$prefix/locale
  set lang=${grub_lang}
  insmod gettext
EOF
fi

cat <<EOF
fi
EOF
fi

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_input ${GRUB_TERMINAL_INPUT}
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_output ${GRUB_TERMINAL_OUTPUT}
EOF
  ;;
esac

if [ "x$gfxterm" = x1 ]; then
    if [ "x$GRUB_THEME" != x ] && [ -f "$GRUB_THEME" ] \
	&& is_path_readable_by_grub "$GRUB_THEME"; then
	gettext_printf "Found theme: %s\n" "$GRUB_THEME" >&2

	prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_THEME"`
	cat << EOF
insmod gfxmenu
EOF
	themedir="`dirname "$GRUB_THEME"`"
	for x in "$themedir"/*.pf2 "$themedir"/f/*.pf2; do
	    if [ -f "$x" ]; then
		cat << EOF
loadfont (\$root)`make_system_path_relative_to_its_root $x`
EOF
	    fi
	done
	if [ x"`echo "$themedir"/*.jpg`" != x"$themedir/*.jpg" ] || [ x"`echo "$themedir"/*.jpeg`" != x"$themedir/*.jpeg" ]; then
	    cat << EOF
insmod jpeg
EOF
	fi
	if [ x"`echo "$themedir"/*.png`" != x"$themedir/*.png" ]; then
	    cat << EOF
insmod png
EOF
	fi
	if [ x"`echo "$themedir"/*.tga`" != x"$themedir/*.tga" ]; then
	    cat << EOF
insmod tga
EOF
	fi
	    
	cat << EOF
set theme=(\$root)`make_system_path_relative_to_its_root $GRUB_THEME`
export theme
EOF
    elif [ "x$GRUB_BACKGROUND" != x ] && [ -f "$GRUB_BACKGROUND" ] \
	    && is_path_readable_by_grub "$GRUB_BACKGROUND"; then
	gettext_printf "Found background: %s\n" "$GRUB_BACKGROUND" >&2
	case "$GRUB_BACKGROUND" in 
	    *.png)         reader=png ;;
	    *.tga)         reader=tga ;;
	    *.jpg|*.jpeg)  reader=jpeg ;;
	    *)             gettext "Unsupported image format" >&2; echo >&2; exit 1 ;;
	esac
	prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_BACKGROUND"`
	cat << EOF
insmod $reader
background_image -m stretch `make_system_path_relative_to_its_root "$GRUB_BACKGROUND"`
EOF
    fi
fi

make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ]; then
  set timeout=${GRUB_RECORDFAIL_TIMEOUT:--1}
else
  set timeout=${2}
fi
EOF
}

if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
echo else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
echo fi
else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
fi

if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ] && [ "x$GRUB_BUTTON_CMOS_CLEAN" = "xyes" ]; then
    cat <<EOF
cmosclean $GRUB_BUTTON_CMOS_ADDRESS
EOF
fi

# Play an initial tune
if [ "x${GRUB_INIT_TUNE}" != "x" ] ; then
  echo "play ${GRUB_INIT_TUNE}"
fi

if [ "x${GRUB_BADRAM}" != "x" ] ; then
  echo "badram ${GRUB_BADRAM}"
fi

Thanks.

---

### Post by towheedm on 2013-05-05
Simply put, you cannot get rid of the terminal window.  It's part of the GRUB source code.

Also, if you followed the 3rd Edition (which you should use now), from Page 69 of the Guide:
> A background image is never shown if we are using GRUB's graphical theme
because GRUB_THEME takes precedence over GRUB_BACKGROUND. Before a background
image is shown in the terminal window, we must remove this precedence. This is set in GRUB's
/etc/grub.d/00_header script as shown below:

The patch only allows you to apply a background image to the temrinal window, not remove it all together.

---

