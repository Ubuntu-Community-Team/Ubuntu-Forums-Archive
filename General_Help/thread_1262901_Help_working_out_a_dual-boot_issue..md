---
title: "Help working out a dual-boot issue."
date: 2009-09-10
forum: General Help
---

### Post by sean.d on 2009-09-10
'ello,

I'm trying to figure out the best way to manage a dual boot system.  Normally not an issue, but, this particular machine has got a wireless keyboard (bluetooth w/ USB dongle).  So, i am obviously not going to be able to use that keyboard to choose an OS at startup, as it doesn't work until Windows or Linux is fully loaded.

Basically, how can i manage to choose between Windows XP and Ubuntu?

---

### Post by mhgsys on 2009-09-10
Go to the BIOS, and enable USB Legacy Support

---

### Post by sean.d on 2009-09-10
Brilliant!

That seems to have done it. Thanks.

---

### Post by mhgsys on 2009-09-10
Nice,
Your welcome


Enjoy your dual booting

---

### Post by sean.d on 2009-09-10
Well, i've got it installed, but, the Grub boot-loader isn't coming up at system startup.  Should i try (re)installing grub manually?

---

### Post by sean.d on 2009-09-11
*BUMP*

I've been trying all day to try to get my GRUB bootloader working.  This PC still boots directly into windows, as it always has.  If anyone has any ideas, i'd be more than happy to try them.

---

### Post by mhgsys on 2009-09-12
First off all,are you sure the bios is booting from the hd ubuntu is installed on?

 
If yes; there is a good  way to manually (re) install grub.


Bootup a live cd, open a terminal and do the following.

```


sudo grub

```
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```


find /boot/grub/stage1

```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```

root (hd?,?)

```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr
```


setup (hd0)

```
Finally exit the grub shell
```


quit

```

In case the bios was booting from the right disk, and you reinstalled grub on it, your ubuntu will be booting.

In case windows is located on that same disk, you can use the commands below to get the dualboot-option.

edit your /boot/grub/menu.lst and add:
```


title Windows Xp (or whatever you want to name it)
root (hd0,0)
chainloader +1

```
This should get your dual boot going.

---

