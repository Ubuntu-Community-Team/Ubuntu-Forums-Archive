---
title: "recover /dev/sda"
date: 2011-01-04
forum: General Help
---

### Post by haggus on 2011-01-04
I accidentally gparted /dev/sda not it looks like msdos partition. I hope I can recover the home folder to another drive but I don't know how. Am I screwed here or can someone help me out I'm running a live cd right now. I had all my pictures video and documents I even had family vacations on there. I haven't written anything else to it. Any help at all to rescue me would be appreciated.

Thanks

---

### Post by dino99 on 2011-01-04
recovering tools:

[http://www.cgsecurity.org/wiki/Main_Page](http://www.cgsecurity.org/wiki/Main_Page)

---

### Post by haggus on 2011-01-04
> **dino99 said:**
> recovering tools:

[http://www.cgsecurity.org/wiki/Main_Page](http://www.cgsecurity.org/wiki/Main_Page)

Is there a livecd method I'm sorry but I really need some hand holding to get through this one.

Thanks

---

### Post by haggus on 2011-01-04
> **haggus said:**
> Is there a livecd method I'm sorry but I really need some hand holding to get through this one.

Thanks

I have gotten this far

ubuntu@ubuntu:~$ sudo parted /dev/sda
GNU Parted 1.8.9
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) rescue 0 25000000000
Information: A ext3 primary partition was found at 32.3kB -> 241GB.  Do you want
to add it to the partition table?
Yes/No/Cancel? Yes                                                        
(parted) quit                                                             
Information: You may need to update /etc/fstab.

---

### Post by haggus on 2011-01-04
Well I managed to restore the partiton and the folders which is good I can backup all my /home to another drive. Which I should have in the first place. Now If I can figure out how to restore grub I might be able to rescue this system since the /boot/grub/menu.lst is still there I just have to find a way to restore the MBR on /dev/sda. How is everyone else's day going?

Thanks

---

### Post by haggus on 2011-01-04
OK so I have now backed up my home folder. I'm back into Ubuntu 10.04 LTS. I had trouble with grub from the terminal. root (hd0,0) showed hd0,0 but setup (hd0) gave me an error 17. After playing with the live cd all day I finally tried a lilo install and now I have my original system back and recovered all of my files. They were never gone just my boot loader was pooched. Well that's enough troubleshooting for one day I'm done ):P

code:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

