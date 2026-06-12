---
title: "grub2 error with sabayon linux entry"
date: 2010-07-26
forum: General Help
---

### Post by poltak on 2010-07-26
Hello, yet another question from me.
This time it's about grub2 and Sabayon:
Alright, so I currently have Ubuntu 10.04, openSUSE 11.3 and Sabayon 5.3 installed (all 32 bit). I'm using grub2 (from Ubuntu) as my bootloader. Anyway, it detects openSUSE and ubuntu fine and their menu entries show up and both work. It just doesn't want to make an entry for Sabayon.

Funny thing is, when I run "update-grub2" in terminal it recognises Sabayon:
```
Found Gentoo Base System release 2.0.1 on /dev/sda7
```
It just doesn't want to create a menu entry for it :\ (and just so you're aware, though you probably already know, Sabayon is based on Gentoo, that's why it update-grub calls it Gentoo...).

Anyway, I did some googling, found some older threads, none of them really solved my problem. Then had a look at "https://wiki.ubuntu.com/Grub2#User-defined Entries" to try and manually configure the Sabayon entry.
So I came up with:
```
echo "Adding Sabayon" >&2
cat << EOF
menuentry "Sabayon Linux 5.2" {
        set root=(hd0,9)
        linux /boot/gentoo root=/dev/sda7 ro
	initrd linux /boot/gentoo
}
EOF
```
Then update-grub again.

In short, that allowed an entry to be made in grub2, except when I try to boot that, nothing happens... the grub menu just disappears and nothing happens so I have to press a few buttons to get it back.

I'm sure someone will know the answer to this. I think I'm just doing something wrong in my custom entry file. Thanks for your time :)

---

### Post by poltak on 2010-07-28
Ah, don't worry about this anymore. I worked-around it by putting the Sabayon disc back in and installing Sabayon's boot loader. It recognised all my OS's and works fine.

---

