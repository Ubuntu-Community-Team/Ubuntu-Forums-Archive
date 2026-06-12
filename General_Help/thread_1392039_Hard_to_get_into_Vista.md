---
title: "Hard to get into Vista?"
date: 2010-01-27
forum: General Help
---

### Post by Bellsprout on 2010-01-27
**Why does Ubuntu restart my computer when I try to go into Vista?**

I'm not too good at computer jargon so...

When I turn on my computer, I get this screen:

[IMG]http://i47.photobucket.com/albums/f170/andrew95035/Blog/grub.png[/IMG]

I have no idea which one does what but I use the first Ubuntu option and the first Windows Vista option (Is there a way to clean the GRUB up?)

Anyways, I pick the first Windows Vista option, and this pops up:

[IMG]http://i47.photobucket.com/albums/f170/andrew95035/Blog/choices.png[/IMG]

I choose Microsoft Windows Vista (is there a way to bypass this screen since in the GRUB, I already chose Vista instead of Ubuntu?)

Then it takes me to this screen:

[IMG]http://i47.photobucket.com/albums/f170/andrew95035/Blog/recovery.png[/IMG]

I choose the Repair Method and it leads me to a blue wallpaper with a recovery window working its magic. Now I'm not sure if this is supposed to happen, but I guess this wouldn't be too much of a problem if it didn't reset my computer.

Once it finishes, I come across this screen:

[IMG]http://i47.photobucket.com/albums/f170/andrew95035/Blog/loading.png[/IMG]

...and it resets my whole computer and takes me to GRUB. This doesn't happen all the time. Sometimes I can get in and sometimes I can't. I love using Ubuntu, so I hope you guys can help me out! :D

---

### Post by lindsay7 on 2010-01-27
Looks like you have the vista boot loader on two drives. One of these should start Windows the other most likely will not. Use the one that works. if it takes you to the menu that gives the option to repair or start normally, start normally. It should stop asking for the repair option after a few good start ups.  There is a way to edit the grub menu but I would just install the "Startup-Manager" from synaptic if you do not have it already and choose the correct windows options as the default.  That way you will start windows as the default and you can just choose Ubuntu to start up if you want.

---

### Post by MaindotC on 2010-01-27
> **Bellsprout said:**
> 
I have no idea which one does what but I use the first Ubuntu option and the first Windows Vista option (Is there a way to clean the GRUB up?)


It looks like you are using Grub2.  You can clean up this menu by editing /boot/grub/grub.cfg.  Here's a snippet of my grub.cfg file:
```

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.32-020632-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 3e39d2a2-5fe3-4790-8aee-e545a5fe5643
        linux   /boot/vmlinuz-2.6.32-020632-generic root=UUID=3e39d2a2-5fe3-4790-8aee-e545a5fe5643 ro$
        initrd  /boot/initrd.img-2.6.32-020632-generic
}
menuentry "Ubuntu, Linux 2.6.32-020632-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 3e39d2a2-5fe3-4790-8aee-e545a5fe5643
        linux   /boot/vmlinuz-2.6.32-020632-generic root=UUID=3e39d2a2-5fe3-4790-8aee-e545a5fe5643 ro$
        initrd  /boot/initrd.img-2.6.32-020632-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 3e39d2a2-5fe3-4790-8aee-e545a5fe5643
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=3e39d2a2-5fe3-4790-8aee-e545a5fe5643 ro   q$
        initrd  /boot/initrd.img-2.6.31-17-generic

```

As you can see, each time you install a new [kernel](http://en.wikipedia.org/wiki/Linux_kernel), which usually comes via [update-manager](https://help.ubuntu.com/community/InstallingSoftware), it will create a new entry in the grub.cfg file because sometimes you need to boot into a different kernel to utilise different features or correct problems.  It's a little difficult explaining to a novice so I'll just leave it at that.  I suggest if you don't have any problems like programs crashing, sound, video, and network interfaces working, you should use whatever is the latest kernel version - it will be at the top of the list.  As you can see, my latest version is:
```

Ubuntu, Linux 2.6.32-020632-generic

```
It's a weird number because I installed it differently.  So, let's say I wanted to remove the "Ubuntu, Linux 2.6.31-17-generic" entry because it's not the latest and I'll probably never use it.  You just edit the grub.cfg file like this:
```

#menuentry "Ubuntu, Linux 2.6.31-17-generic" {
#        recordfail=1
#        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
#       set quiet=1
#       insmod ext2
#       set root=(hd0,1)
#       search --no-floppy --fs-uuid --set 3e39d2a2-5fe3-4790-8aee-e545a5fe5643
#       linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=3e39d2a2-5fe3-4790-8aee-e545a5fe5643 ro   q$
#       initrd  /boot/initrd.img-2.6.31-17-generic
#}

```
Just put those hash marks in front and it will skip over those entries.  There are more advanced options but that's one way you can clean up that Grub.  Also, it just skips those kernel versions - they aren't actually removed from your system in the event you would need them.

I'm not yet sure about the other issues you are experiencing.

---

### Post by Finalfantasykid on 2010-01-27
Ok I can only answer about half of those questions.

For the first question, yes you can clean up the Grub menu list.  Just comment out the unwanted lines in /boot/grub/menu.lst (as root), but make sure to keep a backup of the previous one just incase you change something you don't want. (EDIT:  Ok if you are using GRUB2 like the above posted said, then you can probably ignore what I wrote)

For the second part, I am not sure why the Windows Boot loader is coming up, but you can probably get rid of this by editing Window's [BOOT.ini]("http://support.microsoft.com/kb/289022") file.  If you make the default OS the windows partition, and the timeout to be 0, then this screen should not appear.  Again, backup this file before doing any editing.

As for the other question, I have no idea what is going on there.  It could have something to do with your windows apparently being spread accross two partitions, though I have no idea.  Have you tried going to the second Vista in GRUB?

---

### Post by Bellsprout on 2010-01-31
Anybody know why my computer restarts?

---

