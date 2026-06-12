---
title: "where is my menu.lst?"
date: 2010-08-17
forum: General Help
---

### Post by enhu on 2010-08-17
need to edit my menu.lst but can't find it. please tell me where i can find it.

---

### Post by howefield on 2010-08-17
Used to be /boot/grub/menu.lst but if you are running a newer version of xubuntu, you might be using Grub2 which doesn't use menu.lst.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by kotnik on 2010-08-17
You've got GRUB2. Most of the stuff you could find in menu.lst is now in /etc/default/grub.

---

### Post by linux18 on 2010-08-17
/boor/grub/grub.cfg

---

### Post by earthpigg on 2010-08-17
please make sure you aren't following directions or guidelines for grub on a newer install of *buntu with grub2. they are very different, and you will almost certainly break things if you do.

---

### Post by NiGhtMarEs0nWax on 2010-08-17
/boot/grub/grub.cfg

---

### Post by enhu on 2010-08-17
got it!

the menu.lst is in the /etc/grub.d/
where we have to create a bashscript for the new entry before running update-grub

---

### Post by supershin on 2010-08-17
you run update-grub after editing menu.lst? I thought the you're suppose to save the file and just reboot. And that update-grub was a grub2 thing. You should check that out cause grub is different from grub2

---

### Post by uRock on 2010-08-17
It may help if you explain what you are trying to do to the grub menu.

---

### Post by enhu on 2010-08-17
i was to edit my config as i have also installed zenwalk in the 2nd drive.
so i tried creating a bash script naming it "11_Zenwalk.sh" and in it are these code. 

> #!/bin/sh -e
echo "Adding my custom Linux to GRUB 2"
cat << EOF
menuentry "Zenwalk" {
set root=(hd0,3)
linux /boot/vmlinuz
initrd /boot/initrd.splash
}
EOF

then i run** update-grub** to simply update the conf.

i have just successfully boot zenwalk :D

this tut help a lot
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by JKyleOKC on 2010-08-17
> **supershin said:**
> you run update-grub after editing menu.lst? I thought the you're suppose to save the file and just reboot. And that update-grub was a grub2 thing. You should check that out cause grub is different from grub2Agreed the two are quite different, but it was necessary to run update-grub with the original version also. The menu.lst file was simply a configuration file that told update-grub how to set the actual bootloader up, just as grub.cfg does for grub2. The update-grub program was rewritten for grub2 but kept its original name.

I don't know how many times I forgot to run update-grub after making a change, and wondered why the change had no effect, when I was running Hardy LTS and original grub...

---

