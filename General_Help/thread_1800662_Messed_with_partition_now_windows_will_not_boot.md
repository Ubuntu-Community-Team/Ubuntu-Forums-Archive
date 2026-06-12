---
title: "Messed with partition now windows will not boot"
date: 2011-07-09
forum: General Help
---

### Post by l0fls on 2011-07-09
ok, so im in a bit of a jam. I had a dual boot backtrack 5 with windows 7, i had no need for the backtrack partition anymore so i deleted the backtrack partition and extended the windows NTFS to take up all free space, now my computer boots to grub but it will not boot into windows. i am currently in the process of creating a ubuntu live cd to do the following to repair the windows Master boot record
> sudo apt-get insall lilo
sudo lilo -m /dev/sda mbr

im going to do that and as soon as i get booted into the linux live cd i will check this forum again please help me out guys :P much appreciated

---

### Post by spiky001 on 2011-07-09
If your just going to use windows there is an option on the windows disc to fix the mbr

---

### Post by Rubi1200 on 2011-07-09
If you are going to use the commands to install lilo then please make sure you use the right syntax. It is not only good practice to do so, it will also not confuse less experienced users who may be looking at this thread:

> sudo apt-get [COLOR=Red]insall[/COLOR] lilo
sudo lilo -[COLOR=Red]m[/COLOR] /dev/sda mbr                      It should be this:

```
sudo apt-get [COLOR=Blue]install[/COLOR] lilo
sudo lilo -[COLOR=Blue]M[/COLOR] /dev/sda mbr
```lilo will complain and throw warnings up but you can ignore them since all you want is to get it installed to the MBR.

See man lilo for the differences between the usage of lowercase m and uppercase M:
[http://manpages.ubuntu.com/manpages/natty/en/man8/lilo.8.html](http://manpages.ubuntu.com/manpages/natty/en/man8/lilo.8.html)

Good luck!

---

