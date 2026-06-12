---
title: "Ununtu 9.10, Grub 2 dualboot with BT4: HELP"
date: 2009-12-29
forum: General Help
---

### Post by Cerox Rex on 2009-12-29
I'm in need of som dier help, I'v Installed BT4 on a seperate partisjon after i'v installed ubuntu. I didnt allow BT4 to install a bootloader.

Then i added BT4 to grub.conf manually and restarted tried to load BT4 but discovered i had forgotten to put /boot before the kernel img file. Fixed that.

Now i get this funny thing when trying to load BT4. and it drops me to a "initramfs" -bash thingy! 

It simply just tells me it "Gives up waiting for the root-filesystem!" Evrything thath spams up on my screen seems fine untill i get this stupid thingy.

Any Ideas as tho what this migth be? 

Heres the part of grub.conf wich is supposed to load BT4!


```
menuentry "Bactrack 4" {
	irecordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	linux	/boot/vmlinuz-2.6.29.4
	initrd	/boot/initrd.img-2.6.29.4
}
```

---

### Post by Cerox Rex on 2009-12-29
Anyone who can help?

---

### Post by roadkilla on 2010-03-17
this is probably one of my most surprising experiences with Linux, all you need to do is do run **sudo update-grub2** and the grub2 os-prober
will locate BackTrack 4 as Ubuntu 8.10 and will add the entries needed accordingly in **grub.cfg**... ;)
pretty good improvement IMO

good luck!

---

### Post by Scrubru on 2010-03-19
[FONT=Verdana]I installed BT4 in hd(0,1) without boot loader.  Then I installed Ubuntu in hd(0,0) and had the grub installed in MBR, Master Boot Record.  BT4 was recognized as ubuntu 8.10 but it gave me the initramfs shell, and "gave up waiting for root device".

I created a file called "10_backtrack" in /etc/grub.d/ with the instruction of the Ubuntu wiki, [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2), it was like this

[/FONT][FONT=Verdana]```
echo "Backtrack 4" >&2
cat << EOF
menuentry "BackTrack 4" {
        set root=(hd0,1)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrid.img
}
EOF
```

After running "update-grub2" the entry "BackTrack 4" was added.
This time BackTrack did boot up, but neither the touchpad nor the mouse could be used.  I could only use the keyboard.
Any ideas?

[/FONT][FONT=Verdana]
[/FONT]

---

### Post by mmlinx on 2011-02-23
@[Scrubru]("http://ubuntuforums.org/member.php?u=982369"): 

Thanks your entry worked fine for me :D
keyboard and mouse work too.

---

