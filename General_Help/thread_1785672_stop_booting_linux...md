---
title: "stop booting linux.."
date: 2011-06-18
forum: General Help
---

### Post by nos09 on 2011-06-18
hey guys, i've got a question - "how do i stop linux to boot !?!"

i know it sounds really funny like why would i need to do that !? but see, my 7yr old cousin is here at my home and he's just you know - a very annoying kid who likes to play around with stuff and doesnt really care about privacy and the problems is he's little sensitive so i cant really tell him to stop on his face !! lol

so all i wanna know is how do i stop my pc from booting into linux and still keeping it just like it is and having an option to fix it later (he's here for two days !)

would it work if i copy the kernel on my thumbdrive and then delete it ? i searched the google but they are all answering about how to start booting into linux !! lol 

anyway thanks !

---

### Post by deserthowler on 2011-06-18
Have you reset the login screen so that it requires username and password?

Earl

---

### Post by amauk on 2011-06-18
Why get complicated?
Just remove the power chord
No power, no boot

---

### Post by nos09 on 2011-06-18
thats not easy !! lol
he's a smart kid, i have to make it like a complete black screen ... or he'll be on my back and telling me to turn it on !

---

### Post by WorMzy on 2011-06-18
Remove your hard drive or make grub try to load to a non-existent kernel.

Personally though, I'd just change my password to something a 7 year old couldn't guess. ;)

---

### Post by nos09 on 2011-06-18
> **WorMzy said:**
> Remove your hard drive or make grub try to load to a non-existent kernel.

Personally though, I'd just change my password to something a 7 year old couldn't guess. ;)

i know ... but the problems is if he get access in to the GUI then he'll be going to ask the password ! and if i don tell him he's going to cry .. hahahaahaha so i have to pretend that system is broken or something !! 

and i know it sounds really funny but .. lol

and thanks for giving advice guys for this kind of stupid problems ! i appreciate it.

---

### Post by idoitprone on 2011-06-18
Edit you grub.cfg file to introduce minor faults. This way the edit is a simple fix from the grub menu.

Go to the menu press "e" , fix whatever you did and press "b" . You can even change the problem like booting to the wrong partition or cannot find kernel lol.

pratice yourself, it not that hard to use grub menu to edit entries that are already there



When you manually edit and boot up grub, 

```
sudo mv /boot/grub/grub.cfg /boot/grub/grub.cfg.errors
```this to keep the errors

```

sudo update-grub
```way to fix the errors

when you want to leave 

```
sudo mv /boot/grub/grub.cfg.errors  /boot/grub/grub.cfg
``````


menuentry "My Default Karmic" {
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set cb201140-52f8-4449-9a95-749b27b58ce8
    linux        /boot/vmlinuz-2.6.31-11-generic root=UUID=cb201140-52f8-4449-9a95-749b27b58ce8 ro   quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
    }

```for example you change the partition number, not grub cannot find the boot files
```


menuentry "My Default Karmic" {
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set cb201140-52f8-4449-9a95-749b27b58ce8
    linux        /boot/vmlinuz-2.6.31-11-generic root=UUID=cb201140-52f8-4449-9a95-749b27b58ce8 ro   quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
    }






```

---

### Post by nos09 on 2011-06-18
> **idoitprone said:**
> Edit you grub.cfg file to introduce minor faults. This way the edit is a simple fix from the grub menu.

Go to the menu press "e" , fix whatever you did and press "b" . You can even change the problem like booting to the wrong partition or cannot find kernel lol.

pratice yourself, it not that hard to use grub menu to edit entries that are already there



When you manually edit and boot up grub, 

```
sudo mv /boot/grub/grub.cfg /boot/grub/grub.cfg.errors
```this to keep the errors

```

sudo update-grub
```way to fix the errors

when you want to leave 

```
sudo mv /boot/grub/grub.cfg.errors  /boot/grub/grub.cfg
``````


menuentry "My Default Karmic" {
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set cb201140-52f8-4449-9a95-749b27b58ce8
    linux        /boot/vmlinuz-2.6.31-11-generic root=UUID=cb201140-52f8-4449-9a95-749b27b58ce8 ro   quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
    }

```for example you change the partition number, not grub cannot find the boot files
```


menuentry "My Default Karmic" {
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set cb201140-52f8-4449-9a95-749b27b58ce8
    linux        /boot/vmlinuz-2.6.31-11-generic root=UUID=cb201140-52f8-4449-9a95-749b27b58ce8 ro   quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
    }






```

thanks man it helped !

---

### Post by idoitprone on 2011-06-18
Remember I only recommend editing grub.cfg file if it only temporary. When there is a grub update or whatever, you may have to redo the faults, if you have not saved a backup. I would tell you have to edit 10_linux script, but fixing that script will be a pain in the ***. 


if you want to maintain the same faults

i recommend change the mv to cp

sudo mv /boot/grub/grub.cfg.errors  /boot/grub/grub.cfg

sudo cp /boot/grub/grub.cfg.errors  /boot/grub/grub.cfg

---

