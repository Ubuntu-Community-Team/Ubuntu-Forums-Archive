---
title: "Grub 2 Won't Use My Theme"
date: 2011-09-19
forum: General Help
---

### Post by Tikabu on 2011-09-19
I followed the guide to set up a theme on my Ubuntu 11.04 but i only get a basic looking GRUB screen. See attached picture

Can anyone help please
Thanks

---

### Post by drs305 on 2011-09-19
> **Tikabu said:**
> I followed the guide to set up a theme on my Ubuntu 11.04 but i only get a basic looking GRUB screen. See attached picture

Can anyone help please
Thanks

When I've gotten a screen such as the one you mentioned it was because Grub 2 hadn't found the theme or there was something which prevented it from being used. When you run 'sudo update-grub' see if the terminal provides a message indicating it found the theme file.

---

### Post by Tikabu on 2011-09-19
I am sorry if i am not suppose to use this thread as support but i don’t know where else i can go.

This is my out put when I run the *sudo update-grub*

```

Generating grub.cfg ...
Found theme: /boot/grub/themes/ubuntu/theme.txt
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP on /dev/sda1
done

```I don't see any error message
Thanks

---

### Post by drs305 on 2011-09-19
> **Tikabu said:**
> I am sorry if i am not suppose to use this thread as support but i don&#8217;t know where else i can go.

This is my out put when I run the *sudo update-grub*

```

Generating grub.cfg ...
**Found theme: /boot/grub/themes/ubuntu/theme.txt**

```I don't see any error message
Thanks

That was the line I was referring to. Grub 2 is finding your theme so that is not the problem.

As far as the support question, generally we prefer users start their own threads. Since I'm a moderator, if you wish I can move our posts to a new thread with a title such as "Grub 2 Won't Use My Theme" or something like that. Having your own thread will ensure the advice is specific to your situation and may be read more often than posts in this thread.

*Mod Note: New thread created.*

---

### Post by Tikabu on 2011-09-19
Ok can you please move it then

This is the first time i am posting i don't know how to move it.

thanks

---

### Post by towheedm on 2011-09-22
As stated in the guide, if the gfxmenu theming engine does not find even one element of your theme or if there is some mistake in your theme definition file, it will display the text screen

Can you post the contents of your theme.txt file?

---

### Post by Tikabu on 2011-09-23
Here is my theme.txt

```

# GRUB2 gfxmenu Ubuntu Demo Theme
# The Definitive Guide to Theming GRUB2,
# using the ubuntu1 demo theme from http://www.gibibit.com
# Designed for 640x480 resolution

# Global Property
title-text: "GRUB2 Demo Theme"
title-font: "DejaVu Sans Regular 12"
title-color: "B08458"
#message-font: "DejaVu Sans Regular 12"
#message-color: "#FFFFFF"
#message-bg-color: "#020202"
desktop-image: "desktop.png"
desktop-color: "#000000"
#terminal-box="terminal_*.png"
#terminal-font="Fixed Regular 13"

# Show the boot menu
+ boot_menu {
left = 15%
top = 37%
width = 70%
height = 42%
item_font = "DejaVu Sans Bold 14"
item_color = "#B08458"
selected_item_color = "#FFFFFF"
item_height = 32
item_padding = 0
item_spacing = 3
}

```Thanks

---

### Post by towheedm on 2011-09-23
Line #9 should be:
```
title-color: "#B08458"
```You left out the '#' before the color value.

If that does not help, please post the output from:
```
ls -l /boot/grub/{themes/ubuntu1,fonts}
```Finally, did you create your own fonts or did you use the ones from the .tar.gz file you downloaded?

NOTE:  Natty uses GRUB 1.99.  I have not tested with 1.99.  If you find any discrepencies with 1.99, I'dd appreciate a PM, thanks.  My next re-write will surely include 1.99 and most likely whatever stable release is out at that time.  I'm presently working on an in-depth tutorial for theming metacity.

---

### Post by Tikabu on 2011-09-27
I fixed the missing '#' but now when i reboot i just get a black screen.  I don't get any selection for the os i want to boot into.

Thanks

---

### Post by towheedm on 2011-09-27
I'm assuming you can boot the default menu item.  Please post the output from:
```
ls -l /boot/grub/{themes/ubuntu,fonts}
```

Looking at the screenshot in your first post, I'm seeing the second menu item 'Previous Linux versions'.  Is this an entry you added manually or are you chainloading GRUB2 from GRUB legacy?

---

### Post by Tikabu on 2011-09-27
Here is the out put you were requesting

```

/boot/grub/fonts:
total 92
-rw-r--r-- 1 root root 81350 2011-09-18 13:36 7x13.pf2
-rw-r--r-- 1 root root  3206 2011-09-19 01:25 dejavu-sans-10.pf2
-rw-r--r-- 1 root root  3471 2011-09-19 01:25 dejavu-sans-12.pf2
-rw-r--r-- 1 root root  3792 2011-09-19 01:25 dejavu-sans-bold-14.pf2

/boot/grub/themes/ubuntu:
total 68
lrwxrwxrwx 1 root root    25 2011-09-18 14:02 7x13.pf2 -> /boot/grub/fonts/7x13.pf2
lrwxrwxrwx 1 root root    35 2011-09-18 14:01 dejavu-sans-10.pf2 -> /boot/grub/fonts/dejavu-sans-10.pf2
lrwxrwxrwx 1 root root    35 2011-09-18 14:01 dejavu-sans-12.pf2 -> /boot/grub/fonts/dejavu-sans-12.pf2
lrwxrwxrwx 1 root root    40 2011-09-18 22:17 dejavu-sans-bold-14.pf2 -> /boot/grub/fonts/dejavu-sans-bold-14.pf2
-rw-r--r-- 1 root root 25467 2011-09-18 01:33 desktop.png
-rw-r--r-- 1 root root  2487 2011-09-18 01:33 terminal_c.png
-rw-r--r-- 1 root root  1212 2011-09-18 01:33 terminal_e.png
-rw-r--r-- 1 root root  1537 2011-09-18 01:33 terminal_ne.png
-rw-r--r-- 1 root root   485 2011-09-18 01:33 terminal_n.png
-rw-r--r-- 1 root root  1293 2011-09-18 01:33 terminal_nw.png
-rw-r--r-- 1 root root  2447 2011-09-18 01:33 terminal_se.png
-rw-r--r-- 1 root root   687 2011-09-18 01:33 terminal_s.png
-rw-r--r-- 1 root root  2465 2011-09-18 01:33 terminal_sw.png
-rw-r--r-- 1 root root  1078 2011-09-18 01:33 terminal_w.png
-rw-r--r-- 1 root root   713 2011-09-23 19:18 theme.txt.back

```I did not add 'Previous Linux Version' to the menu it just showed up.   Also it is a fresh load of the Ubuntu 11.04 as far as i understand it comes with GRUB2 and not GRUB legacy.  Therefor it should not be chainloading but i could be wrong this is my first attempt to customize GRUB.

Thanks

---

### Post by towheedm on 2011-09-27
I'm not seeing a 't[COLOR=Blue]heme.txt[/COLOR]' file listed in [COLOR=Blue]/boot/grub/themes/ubuntu[/COLOR].  Instead you have a [COLOR=Blue]'theme.txt.back'[/COLOR] file.

Try renaming this file:
```
sudo mv /boot/grub/themes/ubuntu/theme.txt.back /boot/grub/themes/ubuntu/theme.txt
```Also, make sure the previous missed hashed (#) was added.

---

### Post by Tikabu on 2011-09-28
Yes that is usually theme.txt but I had to change it so that I could boot into my computer because after i fixed '#' problem.  I would not get a grub menu at all.  what i got is just a black screen with nothing on it so i named it to theme.txt.back so that i can boot up the computer.

Thanks

---

### Post by towheedm on 2011-09-28
As I said previously, I have not tested on 1.99.  There may have been some changes to the theming engine.  I'll install Natty tomorrow and test it.

In the meantime, if you can please uncomment the following lines and try again:

```
#message-font: "DejaVu Sans Regular 12"
#message-color: "#FFFFFF"
#message-bg-color: "#020202"


#terminal-box="terminal_*.png"
#terminal-font="Fixed Regular 13"
```Commenting out these lines does not affect the basic theme, but probably it was changed in 1.99.

And:
```
#terminal-box=
#terminal-font=
```should be:
```
#terminal-box:
#terminal-font:
```I'd appreciate you letting me know whether or not uncommenting the lines worked.

Finally, did not create your own PFF2 fonts (.pf2) using the grub-mkfont utility or did you use the ones from the tutorial?

---

### Post by Tikabu on 2011-09-28
I uncommented the lines you requested and fixed the two other one 'terminal-box and terminal-font'.  After i rebooted same thing just a blank screen with no GRUB option to select from.

At firs i did generate my own font but as it was not working i then switched to the fonts from the tutorial but no luck.

---

### Post by towheedm on 2011-09-28
OK, I have installed and tested with Natty on vmplayer.

As it is, vmplayer crashes with the theme.txt as is.  I got it to work by excluding 'memtest' from the menu entries.

Could you try it? Do the following:

Remove the executable bit from [COLOR=Blue]20_memtest86+[/COLOR] and update grub:
```
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub
```Remember, I tried this on a virtual machine not on my physical machine, so things may be different.

---

### Post by Tikabu on 2011-09-28
No sorry it did not work still getting a black screen with no options. :-(

Thanks

---

### Post by towheedm on 2011-09-28
What next?  Thinking......

Post your /etc/default/grub and /boot/grub/grub.cfg files.

What video card are you using?

---

### Post by towheedm on 2011-09-28
I have installed Natty on my physical machine and can confirm that the menu does not show.

Will look at what may be the cause.

---

### Post by towheedm on 2011-09-29
I have done some extensive testing over the last 4 hrs or so and I think I have found the problems.

There are two problems, one resulting from changes made to [COLOR=Blue]10_linux[/COLOR].

The first problem involves GRUB setting the default GFXMODE.  In previous versions of GRUB2, if GRUB_GFXMODE was commented out in [COLOR=Blue]/etc/default/grub[/COLOR], it was automatically set to 640x480 in [COLOR=Blue]10_linux[/COLOR].

However, this behavior has changed and if the line is commented out, GRUB now sets it to 'auto'.  I would assume, it would iterate through the list of valid vbe modes and select the first working mode.  Unfortunately for me, it selects 640x400x256, which works in text mode, but causes a black screen and a hung keyboard with gfxmenu.

A quick fix is to change the line in [COLOR=Blue]/etc/default/grub[/COLOR] from:
```
#GRUB_GFXMODE=640x480
```to:
```
GRUB_GFXMODE=640x480
```The second problem involves the [COLOR=Blue]/etc/grub.d/20_memtest86+[/COLOR] script.  Simple put, a -**-class <classname>** parameter must be appended to the end of the menuentry line in [COLOR=Blue]grub.cfg[/COLOR].  Without this, I get the same blank screen and hung keyboard even with the GFXMODE fix described above.

A simple fix is to unset the executable bit from the 20_memtest86+ file with:
```

sudo chmod -x /etc/grub.d/20_memtest86+
```Now update grub:
```
sudo update-grub
```With the above two fixes, I can now see the basic theme at 640x480, 1024x768 and 1280x1024 modes.  The last is the highest my video card is capable of.

Could you try this and let me know if it now works for you.

Again, what video card do you have installed?

I'm going to file a bug report on Launchpad (pretty sure they'll tell me to file it upstream).  I will post the bug number should you want to subscribe to and track it.

---

### Post by towheedm on 2011-09-29
Bug #862959 has been filed on Launchpad.

---

### Post by Tikabu on 2011-10-01
Sorry still no luck it did not work :(

Here is my /boot/grub/grub.cfg

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root acc2adaf-8464-4e2c-abff-c0060d1e5336
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root acc2adaf-8464-4e2c-abff-c0060d1e5336
insmod gfxmenu
loadfont ($root)/boot/grub/fonts/7x13.pf2
loadfont ($root)/boot/grub/fonts/dejavu-sans-10.pf2
loadfont ($root)/boot/grub/fonts/dejavu-sans-12.pf2
loadfont ($root)/boot/grub/fonts/dejavu-sans-bold-14.pf2
insmod png
set theme=($root)/boot/grub/themes/ubuntu/theme.txt
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root acc2adaf-8464-4e2c-abff-c0060d1e5336
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos2)'
        search --no-floppy --fs-uuid --set=root acc2adaf-8464-4e2c-abff-c0060d1e5336
        linux   /boot/vmlinuz-2.6.38-11-generic root=UUID=acc2adaf-8464-4e2c-abff-c0060d1e5336 ro   quiet splash vt.handoff=7
        initrd  /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos2)'
        search --no-floppy --fs-uuid --set=root acc2adaf-8464-4e2c-abff-c0060d1e5336
        echo    'Loading Linux 2.6.38-11-generic ...'
        linux   /boot/vmlinuz-2.6.38-11-generic root=UUID=acc2adaf-8464-4e2c-abff-c0060d1e5336 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos2)'
        search --no-floppy --fs-uuid --set=root acc2adaf-8464-4e2c-abff-c0060d1e5336
        linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=acc2adaf-8464-4e2c-abff-c0060d1e5336 ro   quiet splash vt.handoff=7
        initrd  /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos2)'
        search --no-floppy --fs-uuid --set=root acc2adaf-8464-4e2c-abff-c0060d1e5336
        echo    'Loading Linux 2.6.38-8-generic ...'
        linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=acc2adaf-8464-4e2c-abff-c0060d1e5336 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(/dev/sda,msdos1)'
        search --no-floppy --fs-uuid --set=root FC544A89544A469C
        drivemap -s (hd0) ${root}
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

#menuentry 'Gentoo' --class gentoo {
#       set root='(hd0,1)'
#}

#menuentry 'Sabayon' --class sabayon {
#       set root='(hd0,1)'
#}

#menuentry 'Microsoft Windows XP Professional' --class windows {
#       set root='(hd0,1)'
#}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###


```The video card that i have in my laptop is a nvidia Quadro FX 1500M
Thanks for all the work you have been putting into this problem.  I really appreciate it.

---

### Post by towheedm on 2011-10-01
> Thanks for all the work you have been putting into this problem.  I really appreciate it     You are most welcome.  I would really like to figure this one out.  I have not gotten any reply from the bug report and doubt very much I'll ever.  All of my previous bug reports concerning gfxmenu have gone unanswered.

From some further testing I've done, it seems that all menu items must belong to a class.  The difference between my grub.cfg and yours is you have a 'Previous Linux Versions' menu entry.  There is no class assignment to it.  Although it takes you to a sub-menu, it is just another menu entry in the main menu.

Try commenting the following lines directly from grub.cfg:
```
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos2)'
        search --no-floppy --fs-uuid --set=root acc2adaf-8464-4e2c-abff-c0060d1e5336
        linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=acc2adaf-8464-4e2c-abff-c0060d1e5336 ro   quiet splash vt.handoff=7
        initrd  /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos2)'
        search --no-floppy --fs-uuid --set=root acc2adaf-8464-4e2c-abff-c0060d1e5336
        echo    'Loading Linux 2.6.38-8-generic ...'
        linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=acc2adaf-8464-4e2c-abff-c0060d1e5336 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.38-8-generic
}
}
```[COLOR=Red]
Do not update grub after editing this file directly.[COLOR=Black]

If that works, change the submenu line to:
[/COLOR][/COLOR]```
submenu "Previous Linux versions" --class menuitem {
```and try again.

I'm pretty sure the problem here is with the modes offered by the video card.

---

### Post by Tikabu on 2011-10-01
It worked now i see the menu
Thanks

I have a question I have this windows that pups up after i select an option.  Do you know what that is

Thanks again for all you hard work

---

### Post by towheedm on 2011-10-01
That's the terminal window.  It's properties are set with the following global property items:
Borfers - terminal-box:
Font: terminal-font

OK, now every time you update grub you must delete or add a --class clause to the submenu item.  I'll look at 10_linux sometime soon and post a permanent fix for both 10_linux and 20_memtest86+.

If you have any further problems with the guide please post them on '[The Beginner's Guide to Theming GRUB]("http://ubuntuforums.org/showthread.php?t=1534689")' thread.  That way, I'm sure I won't miss it since I don't look at the new posts these days.

---

### Post by towheedm on 2011-10-02
Here's the permanent fix for [COLOR=Blue]10_linux[/COLOR] and [COLOR=Blue]20_memtest86+[/COLOR].

Open [COLOR=Blue]10_linux[/COLOR] and find this line towards the end of the file (line 214):
```
echo "submenu \"Previous Linux versions\" {"
```Change it to:
```
echo "submenu \"Previous Linux versions\" --class menuitem {"
```Save the changes.

Open [COLOR=Blue]20_memtest86+[/COLOR] and locate this line (line 27):
```
menuentry "Memory test (memtest86+)" {
```Change it to:
```
menuentry "Memory test (memtest86+)" --class memtest {
```Save the changes and update grub.

Now you won't have to manually edit [COLOR=Blue]grub.cfg[/COLOR] everytime to update it.

Note:  If you select the 'Previous Linux versions' menu item, you will be taken to an un-themed screen.  The theme file format must have changed to include sub menu theming.

This I'll look into in the the re-write.

---

### Post by Tikabu on 2011-10-05
I implemented the changes you mad and the one for the 10_linux worked fine but the one for the 20_memtest86+ did not work.

I noticed that there is another line starting with menuentry should that one have class added to it.

Thanks

---

### Post by towheedm on 2011-10-05
> **Tikabu said:**
> I implemented the changes you mad and the one for the 10_linux worked fine but the one for the 20_memtest86+ did not work.

I noticed that there is another line starting with menuentry should that one have class added to it.

Thanks

Which line is this?  There was only one menuentry line in my 20_memtest86*.  Could you paste the section with the line?

---

### Post by towheedm on 2011-10-05
Ok, my mistake.  The second menuentry line:
```
menuentry "Memory test (memtest86+, serial console 115200)" {
```must also have a class parameter:
```
menuentry "Memory test (memtest86+, serial console 115200)" --class memtest {
```Sorry for that.

---

### Post by Tikabu on 2011-10-10
Thanks towheedm for all your hard work every thing is working now.

Thanks Again

---

### Post by towheedm on 2011-10-10
You are welcome.  Glad to hear it's working now.  I'll certainly include it in my next re-write for 1.99 or 2.0 (if there's ever one).  If you have any further problems with the guide, please feel free to post and PM me the thread's link, or post in the GRUB guide tutorial thread that you posted in initially.

I've also filed a bug report on GRUB's bugzilla but nothing yet.

OK back to my Metacity theming tutorial now.

---

### Post by mdc098523 on 2011-12-28
I am using Ubuntu 10.04 (Lucid) with GRUB 1.98-1ubuntu12 and trying to do theming using Towheed Mohammed's "Definitive Guide to Theming -2nd edition."  The GRUB version I have may not be compatible per Toweed's disclaimer page but I thought I would try it anyway.  When I enter the "update-grub" command I get the following message :

 xxx@xxx-laptop:~$ sudo update-grub
[sudo] password for xxx: 
Generating grub.cfg ...
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
/etc/grub.d/08_gfxmenu_theme: 2: 2: not found


I am also including my file permission info below:
xxx@xxx-laptop:~$ sudo grub-probe -t device /boot/grub/
/dev/sda5
----------------------------------------------------------
xxx@xxx-laptop:~$ sudo grub-probe -t fs_uuid /boot/grub/
814c7dde-4bb6-4a11-b323-cb97ac1f29e0
----------------------------------------------------------
xxx@xxx-laptop:~$ ls -l /etc/grub.d/
total 40
-rwxr-xr-x 1 root root 4457 2011-12-20 20:11 00_header
-rwxr-xr-x 1 root root 1205 2011-12-22 09:32 08_gfxmenu_theme
-rwxr-xr-x 1 root root 4843 2011-04-27 05:28 10_linux
-rwxr-xr-x 1 root root  918 2010-03-23 04:37 20_memtest86+
-rwxr-xr-x 1 root root 6605 2011-04-27 05:28 30_os-prober
-rwxr-xr-x 1 root root  418 2011-12-20 20:29 40_custom
-rw-r--r-- 1 root root  483 2009-10-23 19:44 README
-----------------------------------------------------------
xxx@xxx-laptop:~$ ls -l /boot/grub/fonts/
total 112
-rw-r--r-- 1 root root 100153 2011-12-19 13:12 7x13.pf2
-rw-r--r-- 1 root root   3206 2011-12-19 13:05 dejavu-sans-10.pf2
-rw-r--r-- 1 root root   3471 2011-12-19 13:06 dejavu-sans-12.pf2
-rw-r--r-- 1 root root   3792 2011-12-19 13:09 dejavu-sans-bold-14.pf2
-----------------------------------------------------------------------

xxx@xxx-laptop:~$ ls -l /boot/grub/themes/ubuntu
total 68
lrwxrwxrwx 1 root root    25 2011-12-27 20:33 7x13.pf2 -> /boot/grub/fonts/7x13.pf2
lrwxrwxrwx 1 root root    35 2011-12-27 20:32 dejavu-sans-10.pf2 -> /boot/grub/fonts/dejavu-sans-10.pf2
lrwxrwxrwx 1 root root    35 2011-12-27 20:32 dejavu-sans-12.pf2 -> /boot/grub/fonts/dejavu-sans-12.pf2
lrwxrwxrwx 1 root root    40 2011-12-27 20:33 dejavu-sans-bold-14.pf2 -> /boot/grub/fonts/dejavu-sans-bold-14.pf2
-rw-r--r-- 1 root root 25467 2011-12-17 14:47 desktop.png
-rw-r--r-- 1 root root  2487 2011-12-17 14:47 terminal_c.png
-rw-r--r-- 1 root root  1212 2011-12-17 14:47 terminal_e.png
-rw-r--r-- 1 root root  1537 2011-12-17 14:47 terminal_ne.png
-rw-r--r-- 1 root root   485 2011-12-17 14:47 terminal_n.png
-rw-r--r-- 1 root root  1293 2011-12-17 14:47 terminal_nw.png
-rw-r--r-- 1 root root  2447 2011-12-17 14:47 terminal_se.png
-rw-r--r-- 1 root root   687 2011-12-17 14:47 terminal_s.png
-rw-r--r-- 1 root root  2465 2011-12-17 14:47 terminal_sw.png
-rw-r--r-- 1 root root  1078 2011-12-17 14:47 terminal_w.png
-rwxr-xr-x 1 root root   767 2011-12-21 08:40 theme.txt
---------------------------------------------------------------------------

Can someone help me with this???

---

### Post by towheedm on 2011-12-29
Did you change the prefix=/usr line in the 08_gfxmenu_theme file?

Could you unset the executable bit from 08_gfxmenu_theme and re-run update-grub, does it still give the error?

---

### Post by mdc098523 on 2011-12-29
Thanks for responding so quickly, Towheed.
 did_ **not **_change the prefix=/usr line in the 08_gfxmenu_theme file.  The file indicated that it should only be deleted for Sabayon 5.5 users. I unset the executable bit from 08_gfxmenu_theme and re-ran **update-grub**. See below for the results....

xxx@xxx-laptop:~$ sudo chmod -x /etc/grub.d/08_gfxmenu_theme
xxx@xxx-laptop:~$ ls -l /etc/grub.d/
total 40
-rwxr-xr-x 1 root root 4457 2011-12-27 20:12 00_header[B]
-rw-r--r-- 1 root root 1205 2011-12-22 09:32 08_gfxmenu_theme[/B]
-rwxr-xr-x 1 root root 4843 2011-04-27 05:28 10_linux
-rwxr-xr-x 1 root root  918 2010-03-23 04:37 20_memtest86+
-rwxr-xr-x 1 root root 6605 2011-04-27 05:28 30_os-prober
-rwxr-xr-x 1 root root  418 2011-12-20 20:29 40_custom
-rw-r--r-- 1 root root  483 2009-10-23 19:44 README

xxx@xxx-laptop:~$ sudo update-grub
Generating grub.cfg ...
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Found linux image: /boot/vmlinuz-2.6.32-37-generic
Found initrd image: /boot/initrd.img-2.6.32-37-generic
Found linux image: /boot/vmlinuz-2.6.32-36-generic
Found initrd image: /boot/initrd.img-2.6.32-36-generic
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda3
done

---

### Post by towheedm on 2011-12-29
Great!  We know now there's a 'possible' problem with 08_gfxmenu_theme, but there is also another problem.  So 10_linux, 20_memtest and 30_os-prober seems to be working fine.  But firsrt, can you boot the other menu entries?

I'm assuming you did the 00_header modifications.  If so, could you revert the modified file from the backup (you did create the backup?) and see if the 'No path or device specified' error goes away when you run update-grub.

---

### Post by mdc098523 on 2011-12-29
I can boot into either Ubuntu or Windows 7 from the GRUB 1.98 menu.  Is that what you mean? After replacing the "00_header" in /usr/grub.d/ with the original version from my backup, the update-grub ran to completion. See below.  I then rebooted the system and the GRUB menu had reverted to the original black screen with white lettering for the menu.  I think the only changes that I had made to "00_header" was to comment out the lines you said to delete in your "Grub2 Theming Guide" but I will compare my file with the one you have in your Appendix.

xxx@xxx-laptop:~$ sudo update-grub 
Generating grub.cfg ...
Found theme: /boot/grub/themes/ubuntu/theme.txt
Found linux image: /boot/vmlinuz-2.6.32-37-generic
Found initrd image: /boot/initrd.img-2.6.32-37-generic
Found linux image: /boot/vmlinuz-2.6.32-36-generic
Found initrd image: /boot/initrd.img-2.6.32-36-generic
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35 update-grub
[sudo] password for lee: my-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda3
done

---

### Post by mdc098523 on 2011-12-29
Since my last post worked with the original "00_header" and the excute permission taken off "08_gfxmenu_theme, I decided to compare "08_gfxmenu_theme" with yours.  I found that, when I copied the file from your "Theming Guide" appendix, I accidently copied the line numbers which definitely caused some bad problems.  Now, with the"08_gfxmenu_theme" line numbers removed and the execute permission restored, I got the results below:   I will look at the file again to see if there is an extra EOF statement.

xxx@xxx-laptop:~$ sudo update-grub
Generating grub.cfg ...  
Found theme: /boot/grub/themes/ubuntu/theme.txt
/etc/grub.d/08_gfxmenu_theme: 43: Syntax error: end of file unexpected (expecting "fi")

---

### Post by towheedm on 2011-12-29
The complete 08_gfxmenu_theme file is included in the downloaded archive.  Simply follow the tutorial and copy the file to /etc/grub.d/, no need to rewrite it from the pdf file, it's there just for reference.

---

### Post by mdc098523 on 2011-12-30
Wow!  It works great now!  I had failed to extract the files from your "grub_guide.tar.gz" archive. I just copied  the "08_gfxmenu_theme from your .pdf file and apparently messed it up.  Your new menu is great compared to the boring basic Grub menu.  Thank you very much for your expert help, Towheed.  I hope I can find time soon to continue with the other enhancements outlined in you Grub2 Theming Guide....

---

### Post by towheedm on 2011-12-30
You're most welcome.  Glad to know it works for you.  3rd edition out soon, covering GRUB 1.99.

Check out this link for a couple of themes or to post your own themes:
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)

---

### Post by cecilpierce on 2012-05-06
@towheedm

Is it possible to use burg themes in grub ?

---

### Post by towheedm on 2012-05-06
I never used BURG, but I'm pretty sure they won't work in GRUB.  While it will certainly look quite different, you should be able to use the graphics to create a GRUB2 theme.

---

### Post by cecilpierce on 2012-05-07
Your right, I tried adding some things from burg to grub and it didn't work so well.

I don't know much on howto, but its fun to try, and break things

:lolflag:

---

