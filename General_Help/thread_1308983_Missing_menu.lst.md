---
title: "Missing menu.lst"
date: 2009-11-01
forum: General Help
---

### Post by Rickspark on 2009-11-01
Hello,

Just installed Ubunto 9.10 (October 2009 release) on a Pentium III.  Runs a treat except it won't power off at system Halt.  

So as part of my efforts to resolve this, following a good amount of reading, I can see that adding this code to /boot/grub/menu.lst might provide a fix...

noacpi acpi=off
apm=on
acpi=force
apm=power_off

But there's no menu.lst file here /boot/grub

Although I've created one, surely this is no use either as somewhere else I'll need to be telling Ubunto to process the menu.lst file?

As you can see, this new user is going round in circles.  Hope you can help?

Rickspark

---

### Post by capscrew on 2009-11-01
> **Rickspark said:**
> Hello,

Just installed Ubunto 9.10 (October 2009 release) on a Pentium III.  Runs a treat except it won't power off at system Halt.  

So as part of my efforts to resolve this, following a good amount of reading, I can see that adding this code to /boot/grub/menu.lst might provide a fix...

noacpi acpi=off
apm=on
acpi=force
apm=power_off

But there's no menu.lst file here /boot/grub   Although I've created one, surely this is not use either as somewhere else I'll need to be telling Ubunto to process the menu.lst file?

As you can see, this new user is going round in circles.  Hope you can help?

RicksparkKarmic uses GRUB2 and there is no menu.1st.

See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("https://help.ubuntu.com/community/Grub2")

EDIT: and also [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://aldeby.org/blog/index.php/configure-grub2-options-and-background.html/comment-page-1")

---

### Post by retrow on 2009-11-01
Since Grub2 came out, we no longer have menu.lst file. The new kid on the block is grub.cfg

Now the funny thing about grub.cfg is that if you edit it using gedit, it won't let you save it. However if you edit it using nano, you can.

So,
```
sudo nano /boot/grub/grub.cfg
```
Plug in your code at the boot options for Kernel 2.6.31.14 and save.

---

### Post by capscrew on 2009-11-01
> **retrow said:**
> Since Grub2 came out, we no longer have menu.lst file. The new kid on the block is grub.cfg

Now the funny thing about grub.cfg is that if you edit it using gedit, it won't let you save it. However if you edit it using nano, you can.

So,
```
sudo nano /boot/grub/grub.cfg
```
Plug in your code at the boot options for Kernel 2.6.31.14 and save.

I believe this is incorrect.  The grub.cfg is automatically over written on every boot.  Read the links in the above post.

---

### Post by retrow on 2009-11-01
> **capscrew said:**
> I believe this is incorrect.  The grub.cfg is automatically over written on every boot.
No its not. I have edited out the lines for **memtest** and booting from **recovery mode**. The only time my grub.cfg got over written was when I did a kernel update and chose the option to install the package maintainers version of boot menu. I have been using grub2 since Karmic alpha5, and I can assure you that the changes stay in grub until you upgrade the kernel and authorize the updater to make automatic changes.

---

### Post by capscrew on 2009-11-01
> **retrow said:**
> No its not. I have edited out the lines for **memtest** and booting from **recovery mode**. The only time my grub.cfg got over written was when I did a kernel update and chose the option to install the package maintainers version of boot menu. I have been using grub2 since Karmic alpha5, and I can assure you that the changes stay in grub until you upgrade the kernel and authorize the updater to make automatic changes.

You are right.  The file is overwritten when there are updates only.  But the proper way to add a modification  is as stated in the community info (e.g. *[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)*) > The user can use a custom file, /etc/grub.d/40_custom, in which the user can place his own entries. This file will not be overwritten. 

---

### Post by Woulouf on 2009-11-02
Hi everybody.

I've got the same problem with 9.10. (PC don't power off at system Halt)

Capscrew say that we have to use /etc/grub.d/40_custom file to add options.

Here is the file:

> #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

So my question is: how should i insert options in this file ?

I would like to test acpi=force.

Thank you.

---

### Post by peculiar penguin on 2009-11-02
I need the noapic kernel parameter, simply added it to /etc/default/grub (GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **noapic**"), ran update-grub, done.

---

### Post by Woulouf on 2009-11-02
Hi Peculiar Penguin

Thanks for you help.

I understood that when you change this variable (GRUB_CMDLINE_LINUX_DEFAULT), grub.cfg is updated after running update-grub.

So i add options given by Rickspark. Here the solution.

1) Edit /etc/default/grub. 

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=Blue]**noacpi acpi=off apm=on acpi=force apm=power_off**[/COLOR]"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"Save the file.

2) run update-grub

3) check your grub.cfg  (/boot/grub/grub.cfg)

> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set f577f365-392f-47f2-967f-8a1f087035ef
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set f577f365-392f-47f2-967f-8a1f087035ef
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f577f365-392f-47f2-967f-8a1f087035ef ro   quiet splash [COLOR=Blue]**noacpi acpi=off apm=on acpi=force apm=power_off**[/COLOR]
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set f577f365-392f-47f2-967f-8a1f087035ef
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f577f365-392f-47f2-967f-8a1f087035ef ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
Now my pc turns off automatically.

Thanks everybody :)

---

### Post by ranch hand on 2009-11-02
I suggest first going to the link in my sig and reading the first post in the thread.  Then take a look at the first three links on it.  The first 3 are best info you are going to get and you may understand it if you read mine first.

All links are good information that was developed, or discovered, during Karmic testing.

Editing the /boot/grub/grub.cfg file is possible and extremely silly.  It is over written every time you run "update-grub".  That is how it is designed.  It is a read only file for root for a reason.

---

### Post by Woulouf on 2009-11-02
Thanks Ranch hand, i'll check this.

---

### Post by Chip13 on 2009-11-03
hi i have the some problem, but i am using xubuntu 9.10 and this quide isnt working. i had some problem under xubuntu 9.04 but there i just put the 'noacpi' and 'acpi=off' in menu.lst and it works. But now i dont know what to do.

Thanks for help.

---

### Post by ranch hand on 2009-11-03
> **Chip13 said:**
> hi i have the some problem, but i am using xubuntu 9.10 and this quide isnt working. i had some problem under xubuntu 9.04 but there i just put the 'noacpi' and 'acpi=off' in menu.lst and it works. But now i dont know what to do.

Thanks for help.
What guide is not working?

Set up a custom menu file for those difficult OS' and put the added instructions where all the rest of the instructions are.

---

### Post by Chip13 on 2009-11-05
i put lines in file and update grub .... then whet i try to shut down the pc print system is halted but the pc doesnt turn off
what should i do?

---

### Post by ranch hand on 2009-11-05
That, I am sure, has nothing to do with grub in any way.  Grub works on boot up not down.

I would wonder what else you have configured.

Did you try "Alt + SysRq + b"?

You could also pull the plug.  This is not a good thing to do but it will shut the bugger off.

---

