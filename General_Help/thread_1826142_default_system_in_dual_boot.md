---
title: "default system in dual boot"
date: 2011-08-16
forum: General Help
---

### Post by magodiafano on 2011-08-16
Hello I wanna use Windows Xp as default system because this laptop is not mine.
I tried to use startup manager but it doesn't work. Do you know other way to choose the default os?
I heard about grub2 but I don't have any idea about that! do you know a simple guide? and where could I download it? I have ubuntu 11.04.

---

### Post by SidebySide on 2011-08-16
```
sudo gedit /etc/default/grub
```

[COLOR=Red]**GRUB_DEFAULT=0**[/COLOR] => the number refers to the default OS, Change it: 0, 1, 2, 3, etc.
                                       Note: 3 refers to 4th entry in grub, 2 refers to 3rd entry and so on.

**[COLOR=Red]GRUB_TIMEOUT=10[/COLOR]** => in/decrease the waiting time on grub menu.

---

### Post by stinkeye on 2011-08-16
You can edit the grub file at /etc/default/grub to change the default OS.

First you need to know the number of your XP menu entry in your grub.cfg
Copy and paste into the terminal...
```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```


Which will give you something like this...
```
glen@Natty:~$ grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
     0	Ubuntu, with Linux 2.6.38-10-generic
     1	Ubuntu, with Linux 2.6.38-10-generic (recovery mode)
     2	Ubuntu, with Linux 2.6.38-8-generic
     3	Ubuntu, with Linux 2.6.38-8-generic (recovery mode)
     4	Memory test (memtest86+)
     5	Memory test (memtest86+, serial console 115200)
     [COLOR="Magenta"]6[/COLOR]	Windows NT/2000/XP (loader) (on /dev/sda1)
```

Note the number of **your** XP menu entry.
In my case it is [COLOR="magenta"]6[/COLOR].


Now you need to edit grub.
```
gksudo gedit /etc/default/grub
```

The first part of the file should look similar to this...
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

[COLOR="Blue"]GRUB_DEFAULT=0[/COLOR]
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

Change the [COLOR="Blue"]GRUB_DEFAULT=0[/COLOR] line to **your** menu entry number for XP.
eg in my case if I wanted XP as the default OS I would change the line to
GRUB_DEFAULT=[COLOR="Magenta"]6[/COLOR]
Save the file and then run 
```
sudo update-grub
```
Done.

[COLOR="Red"]Edit[/COLOR] I was a bit slow but you should have all the info you need now.

---

### Post by Mark Phelps on 2011-08-16
That will work until the number of entries in the GRUB menu changes -- which will put you back to doing this again.

For a more permanent fix, edit the grub file indicated by stinkeye, but instead of changing the number on the DEFAULT line, replace that number with the text from the grep command output, and wrap that text in double-quotes (because it contains blanks)

Thus, for example, using stinkeye's info again, instead of the line 

GRUB_DEFAULT=6

You would have:

GRUB_DEFAULT="Windows NT/2000/XP (loader) (on /dev/sda1)"

Doing it this way, you can add and delete GRUB lines without changing the default.

---

