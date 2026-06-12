---
title: "Customize GRUB2 installed on USB (no /etc folder)"
date: 2011-03-01
forum: General Help
---

### Post by your_average_bro on 2011-03-01
I'm kind of new to the whole GRUB2 business, where I learned I could boot multiple ISO using the loopback feature.

I have 4 or 5 ISOs and GRUB2 configured on a flash drive that boot fine, thats not the problem. The problem is I cannot customize it.

I used the following commands to install GRUB2 on my flash drive, using an Ubuntu 10.10 Live CD.

> grub-install --force --no-floppy --root-directory=/usb(/usb was my mounted location).

It created one folder on the root of my flash drive, which was called 'grub'.
There was no /etc folder created.
I've managed to set it up, all my ISOs boot fine, and GRUB2 boots fine.

However, all of the customization tutorials online say I need to edit /etc/05_debian_theme, but I don't have one; all the setup did was create a /boot folder, not a /etc folder.

Should I just make a /etc folder or what?
Thanks a lot.

---

### Post by your_average_bro on 2011-03-01
Wow. 
Didn't realize the thread would get buried this fast.
Anybody know how?

---

### Post by towheedm on 2011-03-01
Is there a 05_debian_theme file or even a grub.d directory in the /boot directory?

Ah just read the post properly.  grub-install installes the bootloader only.  How did you update grub's boot menu?

---

### Post by your_average_bro on 2011-03-01
^ Nope.
Just /boot/grub, and in that is the grub.cfg file and a bunch of assorted .mod files.
You think I installed it wrong? Those options look solid to me.

My bad for not making the tag [all variants], it doesnt really apply to just Ubuntu, but I'm new to this forum, so my bad.

EDIT: Sorry I didn't read your whole post.
I edited the menu by making my own grub.cfg file, was I supposed to do that? :/
How would I go about reinstalling it the right way?

---

### Post by towheedm on 2011-03-01
No actually nothing is wrong with doing that.  The reason it's not really recommended, is because every thime you do an update-grub command, whatever changes you made manually to grub.cfg gets lost.

Since you did not really install grub from a package, the configurations files will not be present in the stick.  Obviously, you know what to edit in the grub.cfg file for the menu.  So that may be one option open to you.  I will create a simple theme in my VM and post the appropriate lines for you to change.  Give me 10 mins or so, I hope.

BTW, what version of grub is on the stick and are you looking at graphical themes or just the normal text themes?

---

### Post by your_average_bro on 2011-03-01
> **towheedm said:**
> No actually nothing is wrong with doing that.  The reason it's not really recommended, is because every thime you do an update-grub command, whatever changes you made manually to grub.cfg gets lost.

Since you did not really install grub from a package, the configurations files will not be present in the stick.  Obviously, you know what to edit in the grub.cfg file for the menu.  So that may be one option open to you.  I will create a simple theme in my VM and post the appropriate lines for you to change.  Give me 10 mins or so, I hope.

BTW, what version of grub is on the stick and are you looking at graphical themes or just the normal text themes?

Is there any way to get a 'full' install onto a USB stick?
I dont really understand. 
I thought you made 'themes' by editing files such as 05_debian_theme that would normally be in /etc, which is not present.

Is there some kind of command that will install grub2 "fully" onto my flash drive?
Thanks for your help though, greatly appreciated.

**EDIT:** Don't know what version of grub is on the stick. I ran grub-install from an Ubuntu 10.10 LiveCD, so, I would guess 1.9.8.
Also, I'm looking to edit the font, perhaps, and definitely a background image; not too fancy.

**EDIT2: **Hopefully even the size of the boot menu, itself, and the border of the boot menu.
Also, change the text that appears (such as press 'e' to edit, etc etc.)

Thanks again.

---

### Post by towheedm on 2011-03-01
Here's the section you need to add to grub.cfg:

```
### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a8736a80-5ea3-4f15-8c85-69183d8ea6aa
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###
```Explanation:

1.  The first insmod part_msdos you may need or not, depending on your MBR.
2.  insmod ext2, you may need to change.
3.  set root='(hd0,msdos1)' you will need to change.
4.  Create a directory[COLOR=Blue] /usr/share/images/desktop-base/[/COLOR] and put your image into it.  Preferable name it moreblue-orbit-grub.png.  If you give it another name, change it in the above code snipet also.  Also, if it's a jpg file, change** insmod png** to** insmod jpg**.
5.  Set your text color in set menu_color_normal.  It is foreground/background color.
6.  Set color of the selected menu item in set menu_color_highlight.

And that's about it for a simple theme.

As for installing grub on the stick, you may be able to do that  using dpkg.  I have never tried using it to re-configure package though.  Maybe I should try, may come in haby someday.

Let me know if the above works for you.

---

### Post by your_average_bro on 2011-03-01
Wow.
Thanks a lot.

So I can basically just make an /etc/05_debian_theme, and follow tutorials online no problem?

Thanks a lot bro.

---

### Post by towheedm on 2011-03-01
Not really.  If you make a /etc/05_debian_theme file, to get it into the grub.cfg file you will need to do issue the update-grub command.  But since you do not have the grub package installed on the stick, it will not work.  In your case add the snipet directly into you grub.cfg file as you did for the menu items.

---

### Post by your_average_bro on 2011-03-02
Didn't boot for me.
Gave me an error: could not find (uuid number listed).

Im gonna start up Ubuntu, find MY device UUID, then replace it, and see if it works.
I think you might have used your UUID and forgot to mention to change it.
I'll edit this post if it works or not.

Also, I don't really want a /usr/ directory on the root of my flash drive, so I changed the directory to /boot/grub/bg.png, hope that'll work.

Main priority is getting it booted though; will edit this post if changing the uuid does it.

---

### Post by your_average_bro on 2011-03-02
K.
Got it to boot by changing the UUID, now it boots to GRUB no problem.
Still no theme though. :/

Ive even made the directory just as you said with the /usr
Heres my grub.cfg file, in full.

> ### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod sdb1
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set AEF1-D314
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

menuentry "Password & Registry Editor" {
loopback loop /boot/iso/password-edit-new.iso
linux (loop)/VMLINUZ. rw vga=normal  --
initrd (loop)/INITRD.CGZ 
}

menuentry "GParted 0.8.0-1" {
loopback loop /boot/iso/gparted-live-0.8.0-1.iso
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=/boot/iso/gparted-live-0.8.0-1 toram=filesystem.squashfs --
initrd (loop)/live/initrd.img 
}

menuentry "Ubuntu 10.10" {
loopback loop /boot/iso/ubuntu-10.10.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.10.iso noeject noprompt --
initrd (loop)/casper/initrd.lz 
}

menuentry "Boot & Nuke 2.2.6" {
loopback loop /boot/iso/dban-2.2.6.iso
linux (loop)/DBAN.BZI nuke="dwipe" silent  --
}


Boots to the default black & white after saying 'error: file not found' for about a millisecond.

Heres a screenshot in QEMU:
[http://i52.tinypic.com/zmh1l4.jpg](http://i52.tinypic.com/zmh1l4.jpg)

---

### Post by towheedm on 2011-03-02
My apologies.  Yes, you have to change the UUID also.  And yes, the image file can be in any directory of the stick.

---

### Post by towheedm on 2011-03-02
The third line insmod sdb1  should be insmod ext2 or whatever file-system the stick was formatted in.  sdb1 is a device not a file-system.

End of Line 7: bg.png;then should be  bg.png ; then (a space before and after the semi-colon).

---

### Post by your_average_bro on 2011-03-02
> **towheedm said:**
> The third line insmod sdb1  should be insmod ext2 or whatever file-system the stick was formatted in.  sdb1 is a device not a file-system.

End of Line 7: bg.png;then should be  bg.png ; then (a space before and after the semi-colon).

There is a space between the 2.
Changed it back to ext2 (thought maybe that was the problem).

Still get the half-a-millisecond 'error:file not found' before it boots to the original black and white.

UGHH. Any suggestions? Why would it say file not found? What file?

---

### Post by your_average_bro on 2011-03-02
Forgot to post my current grub.cfg

> ### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set AEF1-D314
insmod png
if background_image /boot/grub/bg.png ; then
set color_normal=white/black
set color_highlight=white/black
else
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

menuentry "Password & Registry Editor" {
loopback loop /boot/iso/password-edit-new.iso
linux (loop)/VMLINUZ. rw vga=normal  --
initrd (loop)/INITRD.CGZ 
}

menuentry "GParted 0.8.0-1" {
loopback loop /boot/iso/gparted-live-0.8.0-1.iso
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia 

findiso=/boot/iso/gparted-live-0.8.0-1 toram=filesystem.squashfs --
initrd (loop)/live/initrd.img 
}

menuentry "Ubuntu 10.10" {
loopback loop /boot/iso/ubuntu-10.10.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.10.iso 

noeject noprompt --
initrd (loop)/casper/initrd.lz 
}

menuentry "Boot & Nuke 2.2.6" {
loopback loop /boot/iso/dban-2.2.6.iso
linux (loop)/DBAN.BZI nuke="dwipe" silent  --
}


Thats about it.
Booting with no background, black background, white text.

Upon booting in QEMU, I can see for about a half a millisecond 'error: file not found' at least thats what I think it says; I've tried to prt-scr it, but its too fast.

---

### Post by towheedm on 2011-03-02
Is there a png.mod file in the /boot/grub directory?  Also check the permission of the bg.png file.  It should be -rw-r--r--, owner should be root.
Will play around with these in a bit and see what happens.

---

### Post by towheedm on 2011-03-02
OK, so the permissions on the bg.png file did not make any difference.  But, png.mod must be in the /boot/grub/ directory, or else you get the un-themed menu.

You may also want to look at the** set root='(hd0,msdos1)' line.  **Is grub seeing the stick as hd0?

Just some advice, you should wrap your code around CODE tags instead of QUOTE tags.  Some mods may take offence to this in other posts.

---

### Post by your_average_bro on 2011-03-04
> **towheedm said:**
> OK, so the permissions on the bg.png file did not make any difference.  But, png.mod must be in the /boot/grub/ directory, or else you get the un-themed menu.

You may also want to look at the** set root='(hd0,msdos1)' line.  **Is grub seeing the stick as hd0?

Just some advice, you should wrap your code around CODE tags instead of QUOTE tags.  Some mods may take offence to this in other posts.

My bad.
Thanks for your help with all of this.

There is a "png.mod" in /boot/grub.
Also, I have no idea how to tell whether or not grub is seeing the stick as hd0; how can I go about doing so?

Once again, thanks for your assistance in my issue.

---

### Post by your_average_bro on 2011-03-04
Forgot to check permissions on that bg.png file; will do right now.

---

### Post by your_average_bro on 2011-03-04
Nothing yet.
Theres a png.mod in /boot/grub
Still not sure about the hd0 thing, get back to me as soon as your can.

---

### Post by towheedm on 2011-03-04
What file-system did you use to format the stick, or exactly how did you format it?

Some of your screenshots show you are booting from Windows, using wubi?

---

### Post by towheedm on 2011-03-05
Ok so I finally got it to work, from a stick.  Now I understand a little more of grub.  This is what you need to do:

1.  Copy the [COLOR=Blue]unicode.pf2[/COLOR] font file from your [COLOR=Blue]/usr/share/grub/[/COLOR] directory (Maverick installation) to the[COLOR=Blue] /boot/grub/[/COLOR] directory on the stick.

2.  Make sure the following files are present in the[COLOR=Blue] /boot/grub/[/COLOR] directory on the stick:
     - [COLOR=Blue]unicode.pf2[/COLOR]
     - [COLOR=Blue]png.mod[/COLOR]
     - [COLOR=Blue]vbe.mod[/COLOR]
     - [COLOR=Blue]vga.mod[/COLOR]
     - [COLOR=Blue]gfxterm.mod[/COLOR]
     -  [COLOR=Blue]part_msdos.mod[/COLOR]
     - [COLOR=Blue]fat.mod [/COLOR](because I'm almost certain the stick was formatted using the fat32 fs)
     - your background image ([COLOR=Blue]bg.png[/COLOR])

3.  If it exists, delete the file [COLOR=Blue]/boot/grub/grubenv[/COLOR] from the stick

4.  Paste the following code snipet at the beginning of the[COLOR=Blue] /boot/grub/grub.cfg[/COLOR] file (delete what was added from the previous posts):
```
insmod part_msdos
insmod fat
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set <your stick's UUID>
loadfont /boot/grub/unicode.pf2
set gfxmode=1024x768
insmod vbe
insmod vga
insmod gfxterm
terminal_output gfxterm
insmod png
if background_image /boot/grub/bg.png ; then
    set color_normal=white/black
    set color_highlight=magenta/black
else
    set menu_color_normal=white/black
    set menu_color_highlight=black/light-gray
fi

```Of course, the following are assumed:
- the stick has an msdos MBR (most likely so, unless you explicitly changed it) > insmod part_msdos
- the stick has a fat32 file-system > insmod fat
- you are booting from the USB boot device from your BIOS's boot menu and that[COLOR=Blue] /boot/grub/[/COLOR] is in the first partition > set root='(hd0,msdos1)'.
- your graphics card supports the 1024x768 mode > set gfxmode=1024x768.  Change to suit your needs.

Good.  I've tried this on a stick and it works for me, given the above condition.  So now I'm a bit sleepy as it's 3am local time.

Post back and let me know if you succeeded.

---

### Post by your_average_bro on 2011-03-05
Windows is the only OS on my HD.
I was running Ubuntu 10.10 from a LiveCD, (trying without installing).
My flash drive was formatted as FAT32 (as recommended by many sites for GRUB2) through Windows.
I'm gonna try **everything** you just suggested.
I suppose those grub files will be in the root of the LiveCD.
Will post back with results.

Thanks for everything.

**EDIT:** 
So /usr was not on the root of the LiveCD, I'm gonna try booting from the LiveCD and it's probably gonna be in 'File System', where I can then copy all those files to my flash drive, then proceed.

I have a working QEMU emulator on Windows that works with flash drive, but I cant seem to get QEMU to boot my flash drive.
I run ```
qemu /dev/sdb1
```, and it hangs on 'booting from hard drive', so I'll probably just end up booting Windows once the files are copied.

---

### Post by your_average_bro on 2011-03-05
Oh. My. God.
Bro, your the ******* man.

It completely works.
Booted to my background image, with a new font.

Any way I can change the title text (GNU GRUB1.9.8, etc) at the top?
Also, how can I change the size of the boot menu itself?
And, how can I remove the text at the bottom?

Do those ^ require the /etc folder, or can they also be done from the grub.cfg file?
Thanks for all the help, your a lifesaver. Can I give rep?

---

### Post by towheedm on 2011-03-05
Can I give rep?  Don't understand.  Explain.

As for the other stuff, quite simply, no you can't.  These are hard-coded into grub and cnnot be changed this way.  To really customize grub the NICE way, you need to use the gfxmenu theming engine.  The link at the beginning of the following has my tutorial for that:

[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

You will need to have [COLOR=Blue]gfxmenu.mod[/COLOR] in your[COLOR=Blue] /boot/grub/[/COLOR] directory for this to work for you.  Here's a quick screen-shot:

NOTE:  This was written for Karmic and Lucid.  I am presently re-writing it to include Maverick because there are some slight differences.   If you are going to attempt this, PM me and I'll give you a heads-up on the few differences.

---

### Post by your_average_bro on 2011-03-05
> **towheedm said:**
> Can I give rep?  Don't understand.  Explain.

As for the other stuff, quite simply, no you can't.  These are hard-coded into grub and cnnot be changed this way.  To really customize grub the NICE way, you need to use the gfxmenu theming engine.  The link at the beginning of the following has my tutorial for that:

[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

You will need to have [COLOR=Blue]gfxmenu.mod[/COLOR] in your[COLOR=Blue] /boot/grub/[/COLOR] directory for this to work for you.  Here's a quick screen-shot:

Will that link work for my setup? (no /etc folder)
Thanks.

And some forums allow users the option to give 'reputation points' to another user, usually if they succeeded or helping them with a problem, or posted a kick-*** tutorial, etc.

---

### Post by towheedm on 2011-03-05
Don't this this forums does that, I have never seen it anyway.  And yes, no need for /etc/.  See my edit to post #25.

---

### Post by your_average_bro on 2011-03-05
Guess I'll go ahead and attempt that.
I'll be using my Ubuntu 10.10 LiveCD I suppose, so I believe you'll have to tell me the "differences" in the tutorial.

Thanks.

---

### Post by towheedm on 2011-03-05
No probs.  Will compile a list and post it in the thread with the link.  Let me know how it goes.  Remember the live CD does not keep your changes, so you'll have to save them tp apply to your stick.

---

### Post by your_average_bro on 2011-03-05
The tutorial modifies files in the /etc directory.
Guess I'll have to wait for that list.

---

### Post by towheedm on 2011-03-05
Ay ya yay........forgot bout that.  Ok, so why not do a wubi install in windows and proceed from there?  Then apply the grub.cfg to your stick.  Oh, while you get your images together I'll check out what needs to be done to grub.cfg for your situation, will be sometime later.

---

### Post by your_average_bro on 2011-03-05
> **towheedm said:**
> Ay ya yay........forgot bout that.  Ok, so why not do a wubi install in windows and proceed from there?  Then apply the grub.cfg to your stick.  Oh, while you get your images together I'll check out what needs to be done to grub.cfg for your situation, will be sometime later.

I dont understand. 
How can I modify the /etc directory of a hard drive install of Ubuntu, then copy **just** the grub.cfg created from doing that, apply it to my stick, and expect everything to work?

And there **is** a grub/etc directory on the LiveCD, but I still dont understand how modifying /etc files **outside** of my stick will work for my stick.

---

### Post by towheedm on 2011-03-05
Once you get into the live desktop from the live CD (Try ubuntu without installing) you can do anything as though it was a regular install, except that those changes will not be saved across boots.  You must save the changed files to a directory on your HD (windows).

And the grub.cfg generated from the live desktop, will most likely have to modified slightly to work with the stick.

---

### Post by your_average_bro on 2011-03-05
> **towheedm said:**
> Once you get into the live desktop from the live CD (Try ubuntu without installing) you can do anything as though it was a regular install, except that those changes will not be saved across boots.  You must save the changed files to a directory on your HD (windows).

And the grub.cfg generated from the live desktop, will most likely have to modified slightly to work with the stick.

I get the part about saving the changed files to my HD, but why do I need ubuntu to 'generate a grub.cfg'?

---

### Post by towheedm on 2011-03-05
No you really don't.  It just makes it easier than doing it manually.

---

### Post by towheedm on 2011-03-05
Ok, put your theme together with all the graphics etc, do not install or modify anything.  This is one of the differences with the version of grub in Maverick, no need to modify any files in /etc/grub.d/.

---

### Post by your_average_bro on 2011-03-05
> **towheedm said:**
> No you really don't.  It just makes it easier than doing it manually.

This is very confusing.
So all it is to theme grub2 like I want it is to add a few lines of text to grub.cfg?

So, to avoid all confusion, cant you just tell me what to add in grub.cfg to change, say, the height and width of the boot menu, add a border, remove the text, etc?

I dont see why I need to modify /etc files when I'm not going to be using them anyway.

---

### Post by towheedm on 2011-03-05
Ok bro.....give me a few hours, I'll put something together for you that you can just add to your stick and then modify to suit your needs.

---

### Post by your_average_bro on 2011-03-05
> **towheedm said:**
> Ok bro.....give me a few hours, I'll put something together for you that you can just add to your stick and then modify to suit your needs.

I love you.

---

### Post by towheedm on 2011-03-05
> **your_average_bro said:**
> I love you.

Thanks for the love, now show your love by learning to theme grub.:D

OK so here it is.  To install do the following:

1.  Extract the archive.  I've created a it in zip format so you should be able to do it from windows.
2.  Delete everything that was previously added to[COLOR=Blue] /boot/grub/grub.cfg[/COLOR] file on the stick.
3.  Add the lines from the[COLOR=Blue] grub_code_snipet.txt[/COLOR] file to the beginning of the[COLOR=Blue] grub.cfg[/COLOR] file.
4.  Create a[COLOR=Blue] /boot/grub/themes/[/COLOR] directory on the stick and copy the extracted directory [COLOR=Blue]/ubuntu1/[/COLOR] into the themes directory.

Boot from the stick and see your new grub gfx theme.

Check out the tutorial if you want to modify the theme.

---

### Post by your_average_bro on 2011-03-05
> **towheedm said:**
> Thanks for the love, now show your love by learning to theme grub.:D

OK so here it is.  To install do the following:

1.  Extract the archive.  I've created a it in zip format so you should be able to do it from windows.
2.  Delete everything that was previously added to[COLOR=Blue] /boot/grub/grub.cfg[/COLOR] file on the stick.
3.  Add the lines from the[COLOR=Blue] grub_code_snipet.txt[/COLOR] file to the beginning of the[COLOR=Blue] grub.cfg[/COLOR] file.
4.  Create a[COLOR=Blue] /boot/grub/themes/[/COLOR] directory on the stick and copy the extracted directory [COLOR=Blue]/ubuntu1/[/COLOR] into the themes directory.

Boot from the stick and see your new grub gfx theme.

Check out the tutorial if you want to modify the theme.

What color modes does the wallpaper feature?
Tried to make an 8-bit RGB gradient on Photoshop and it came out with like... layers instead of a gradient.

---

### Post by towheedm on 2011-03-05
8-bit = 256 colors.  Photoshop is probably dithering to show gradients.  Try a 16 bit RGB.  Also, check the gfxmode=line in grub.cfg and make sure grub supports this mode for your video card.  To check the modes grub suuport:

-  Press 'c' from grub's menu to get to grub's command-line
-  Enter vbeinfo to get a list of modes grub supports.
- Enter 'exit' to return to the menu

I'm assuming then that the basic gfxmenu worked for you?

---

### Post by your_average_bro on 2011-03-05
> **towheedm said:**
> 8-bit = 256 colors.  Photoshop is probably dithering to show gradients.  Try a 16 bit RGB.  Also, check the gfxmode=line in grub.cfg and make sure grub supports this mode for your video card.  To check the modes grub suuport:

-  Press 'c' from grub's menu to get to grub's command-line
-  Enter vbeinfo to get a list of modes grub supports.
- Enter 'exit' to return to the menu

I'm assuming then that the basic gfxmenu worked for you?

hmm.. I'm planning on using this on various computers, so what would be the best 'universal fit'.
I'm gonna be designing a whole theme based on this ^.

16-bit didnt work either, gave me some CRAZY thing.
Guess I'll have to settle with solid colors, nbd.
When everything is done, I'll post it here.
I'm gonna assume that 1024x768 will work for most computers made like after 06, right?

---

### Post by towheedm on 2011-03-06
My PC is 2000-2002 and it works with 1280x1024, so yes 1024x768 should work.  It must be the format of the png file created by Photoshop.  Does it allow you to set different parameters for the png file?  I use GIMP without problems.

You can also specify the color depth for the gfxmode:
1024x768x8 = 8-bits
1024x768x16 = 16-bits.

Try with 640x480 for testing and once you get it working properly then try different settings.

---

### Post by your_average_bro on 2011-03-06
> **towheedm said:**
> My PC is 2000-2002 and it works with 1280x1024, so yes 1024x768 should work.  It must be the format of the png file created by Photoshop.  Does it allow you to set different parameters for the png file?  I use GIMP without problems.

You can also specify the color depth for the gfxmode:
1024x768x8 = 8-bits
1024x768x16 = 16-bits.

Try with 640x480 for testing and once you get it working properly then try different settings.

I guess GRUB2 hates gradients. I have a brand new laptop with an AMD Vision HD Graphics card, and I've tried both 8-bit and 16-bit images; still blocking it up. Ended up going with a solid color and added some Winter Breeze brushes to make it look half-decent (probably not final).

I also ended up 'hard-coding' the boot menu border into the wallpaper, then using the left, top, and item-spacing to define where it is.
Ended up coming out nice-looking.

If anyones wondering what font I used, its Pupcat, size 60.
I had to play with item_height to get it to display the font without cutting the top entry off, but other than that, your directions worked great.

Only thing is, the directions on how to compile fonts in your PDF guide are wrong.

Its ```
sudo grub-mkfont --verbose --size=SIZE HERE --range=0x0-0x7F --output="OUTPUT HERE" /FONT LOCATION HERE(case sensitive).
```I want to thank you for all your help, I know this took a long time, but its fukcing awesome, and now I have a USB Swiss-Army-Knife, lol.

Heres a screen of it in QEMU:
[http://i55.tinypic.com/t5j789.jpg](http://i55.tinypic.com/t5j789.jpg)

I also have another question.
I know this probably isnt possible, but I did mention how I want to use it with different computers.

I wanted to know if it was possible to add menu entries that could "detect" if the computer I'm running it on had, say, a Windows partition. It would then display that Windows entry, and allow to boot. Like, adding 'set root='(hd0,1)' isnt going to work with all computers, and I was wondering if GRUB2 could detect that.

Also, if that's possible, is it also possible for GRUB2 to detect a CD drive, so it could say 'Boot from CD/DVD Drive". I know those are pointless questions, cause I could just change the boot order in the BIOS, but it would be nice to know.

I know the Offline NT Password & Registry Editor detects "candidate Windows" partitions, (I believe it searches for the /WINDOWS/system32 directory).

ANYWAY, I appreciate your help. I think I might go update the graphics mode to 1280x720 if your '02 comp even handles that; cause this is going to be my utility flash drive now.

---

### Post by towheedm on 2011-03-06
> I guess GRUB2 hates gradients.I don't think so.  If you look at the screen-shot in one of the previous posts, you will see that the background have gradients.  If you look carefully, you'll also notice that the center slice of the menu background even has transparency because you can see the background showing through it slightly.  So again, it has got to be something in the format of the png file you're creating.

> Only thing is, the directions on how to compile fonts in your PDF guide are wrong.

Its
     ```
sudo grub-mkfont --verbose --size=SIZE HERE --range=0x0-0x7F --output="OUTPUT HERE" /FONT LOCATION HERE(case sensitive). 
```This is the instruction to compile one of the fonts from the tutorial:
```
sudo grub-mkfont --verbose --range=0x0-0x7F --size=10 --output=”/boot/grub/fonts/dejavu-sans-10.pf2 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf

```What's wrong here?

> I wanted to know if it was possible to add menu entries that could  "detect" if the computer I'm running it on had, say, a Windows  partition. It would then display that Windows entry, and allow to boot.  Like, adding 'set root='(hd0,1)' isnt going to work with all computers,  and I was wondering if GRUB2 could detect that.Well grub does that when you issue the[COLOR=Red] update-grub [/COLOR]command.  It may be possible to do it in real time.  Have a look at /etc/grub.d/30_os-prober.  You may need to become a bit familiar with bash scripting.  There are lots of tutorial out there on Google.

> Also, if that's possible, is it also possible for GRUB2 to detect a CD drive, Well there's an iso9660.mod file in /boot/grub, so it might be possible.  I'm not quite sure how grub designates a CD drive though, sc0 ?

 > I think I might go update the graphics mode to 1280x720 if your '02 comp even handles that
1280x720 is 16:9 aspect ratio, my monitor is 4:3, so it is pointless for me to do this.

---

### Post by your_average_bro on 2011-03-07
> **towheedm said:**
> I don't think so.  If you look at the screen-shot in one of the previous posts, you will see that the background have gradients.  If you look carefully, you'll also notice that the center slice of the menu background even has transparency because you can see the background showing through it slightly.  So again, it has got to be something in the format of the png file you're creating.

What's wrong here?

For my gradient issues, I just ended up changing grub.cfg to "insmod tga" and I just made 24-bit TGAs in Photoshop; saves a **lot** of hassle.

And as for your PDF tutorial, the MediaFire link (grub2_theming.pdf) **does** have an error in the grub-mkfont code.

Instead of '--verbose', '--range', and '--size', you use '-verbose', '-range', and '-size', which does not work.

Heres a screenshot of what I'm talking about:
[http://i51.tinypic.com/23ixxlh.png](http://i51.tinypic.com/23ixxlh.png)

As for the resolution; I figured most computers nowadays are widescreen.
I went with 1280x768. It worked , even though it wasnt one of the resolutions listed by 'vbeinfo'.
My laptop is 16:9, default res being 1366x768, and the 1280x768 BG scales up nicely when booted. Even tested it on my Dimension 3000, with a 4:3 monitor, and it still looked not bad.

QEMU, for some reason, was distorting the wallpaper, for example, making the menu border I hardcoded stretch. Booting from BIOS into my drive was what it should be, non-distorted, and the border matched up with the menu.

I thought that was kind of strange; why would QEMU distort my wallpaper.

**EDIT:** This is solved, btw. Not sure how to change the tag.
Thanks for all your help, I love my GRUB now. (;

---

### Post by towheedm on 2011-03-07
My apologies, you are so correct.  I never even noticed that.  Thanks a lot, will certainly correct it in the re-write.

Mark thread solved:  Tread Tools > Mark Solved

---

