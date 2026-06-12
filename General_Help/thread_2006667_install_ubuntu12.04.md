---
title: "install ubuntu12.04"
date: 2012-06-19
forum: General Help
---

### Post by tbrownarcher on 2012-06-19
I am trying to install ubuntu 12.04 on my desktop from ubuntu 10.10.  I get to a certain point and it tells me THERE HAS BEEN AN UNRECOVERABLE ERROR AND IT WILL NOW LOAD A DESKTOP SESSION SO THAT I MAY FIX THE PROBLEM.  (not exact wording)

Does anyone know or can tell me what to do in the desktop session.  I have no idea .

Thanks

Nate

---

### Post by wilee-nilee on 2012-06-19
> **tbrownarcher said:**
> I am trying to install ubuntu 12.04 on my desktop from ubuntu 10.10.  I get to a certain point and it tells me THERE HAS BEEN AN UNRECOVERABLE ERROR AND IT WILL NOW LOAD A DESKTOP SESSION SO THAT I MAY FIX THE PROBLEM.  (not exact wording)

Does anyone know or can tell me what to do in the desktop session.  I have no idea .

Thanks

Nate

10.10 is end of life, and you cannot go from it to 12.04.

Here is the end of life info.
[http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/](http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
[]("http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/")[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by tbrownarcher on 2012-06-19
I'm doing an erase and install.  I'm installing ubuntu 12.04 it gets to a certain spot and gives me a desktop session .. i have no idea what to do to find why it stopped.  

thanks,
Nate

---

### Post by wilee-nilee on 2012-06-19
> **tbrownarcher said:**
> I'm doing an erase and install.  I'm installing ubuntu 12.04 it gets to a certain spot and gives me a desktop session .. i have no idea what to do to find why it stopped.  

thanks,
Nate

Check that the disc is good with a md5sum check.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Make sure the disc is burned at the slowest speed.

Make sure that there is not a gpt or other setup as well.

So once the disc is confirmed good boot the cd open gparted and wipe the HD, and try the auto install if you do not know how to do a custom install.,

All this applies to a usb boot, you would just use a standard loader like unetbootin, and md5 the iso.

---

### Post by tbrownarcher on 2012-06-22
I switched gears i formatted and downloaded the ubuntu iso **(ubuntu-12.04-desktop-i386.iso)** to a 16 gig usb drive a thumb drive.  

I am trying to get it to install from the thumb drive but it gives me the message .. " no operating system" ... so now what am i doing wrong ?

thanks,
Nate

---

### Post by tbrownarcher on 2012-06-22
i tried to follow the instructions on the md5 page this is what i got in the terminal.


nate@Nate3:~$ ubuntu@ubuntu-desktop:~$ cd Downloads
ubuntu@ubuntu-desktop:~$: command not found
nate@Nate3:~$ cd ubuntu@ubuntu-desktop:~$ cd Downloads
bash: cd: ubuntu@ubuntu-desktop:~$: No such file or directory
nate@Nate3:~$ cd ..
nate@Nate3:/home$ cd ..
nate@Nate3:/$ dir
bin    dev   initrd.img  media	proc  selinux  tmp  vmlinuz
boot   etc   lib	 mnt	root  srv      usr
cdrom  home  lost+found  opt	sbin  sys      var
nate@Nate3:/$ cd cdrom
nate@Nate3:/cdrom$ ls
nate@Nate3:/cdrom$ cd ubuntu@ubuntu-desktop:~$ cd Downloads
bash: cd: ubuntu@ubuntu-desktop:~$: No such file or directory
nate@Nate3:/cdrom$ cd ..
nate@Nate3:/$ cd ubuntu@ubuntu
bash: cd: ubuntu@ubuntu: No such file or directory
nate@Nate3:/$ cd cdrom
nate@Nate3:/cdrom$ md5sum ubuntu-12.04-dvd-i386.iso
md5sum: ubuntu-12.04-dvd-i386.iso: No such file or directory
nate@Nate3:/cdrom$ md5sum ubuntu-12.04-dvd-i386.iso
md5sum: ubuntu-12.04-dvd-i386.iso: No such file or directory
nate@Nate3:/cdrom$ 



I admit I don't know a lot .  Could someone help with this?  I don't even know if i'm in the right directory.  If I'm not then how do i get there?


Thanks,
Nate

---

### Post by gordintoronto on 2012-06-22
> **tbrownarcher said:**
> I switched gears i formatted and downloaded the ubuntu iso **(ubuntu-12.04-desktop-i386.iso)** to a 16 gig usb drive a thumb drive.  

I am trying to get it to install from the thumb drive but it gives me the message .. " no operating system" ... so now what am i doing wrong ?

thanks,
Nate

Download to your hard drive, then use Unetbootin to create a bootable flash drive. If you are doing it from Windows, Pendrive Linux is another option for creating the flash drive.

During the creation of the flash drive, it might appear to stall for several minutes. It's just processing a very large file.

---

### Post by gordintoronto on 2012-06-22
> **tbrownarcher said:**
> i tried to follow the instructions on the md5 page this is what i got in the terminal.


nate@Nate3:~$ ubuntu@ubuntu-desktop:~$ cd Downloads
ubuntu@ubuntu-desktop:~$: command not found
nate@Nate3:~$ cd ubuntu@ubuntu-desktop:~$ cd Downloads
bash: cd: ubuntu@ubuntu-desktop:~$: No such file or directory
nate@Nate3:~$ cd ..
nate@Nate3:/home$ cd ..
nate@Nate3:/$ dir
bin    dev   initrd.img  media	proc  selinux  tmp  vmlinuz
boot   etc   lib	 mnt	root  srv      usr
cdrom  home  lost+found  opt	sbin  sys      var
nate@Nate3:/$ cd cdrom
nate@Nate3:/cdrom$ ls
nate@Nate3:/cdrom$ cd ubuntu@ubuntu-desktop:~$ cd Downloads
bash: cd: ubuntu@ubuntu-desktop:~$: No such file or directory
nate@Nate3:/cdrom$ cd ..
nate@Nate3:/$ cd ubuntu@ubuntu
bash: cd: ubuntu@ubuntu: No such file or directory
nate@Nate3:/$ cd cdrom
nate@Nate3:/cdrom$ md5sum ubuntu-12.04-dvd-i386.iso
md5sum: ubuntu-12.04-dvd-i386.iso: No such file or directory
nate@Nate3:/cdrom$ md5sum ubuntu-12.04-dvd-i386.iso
md5sum: ubuntu-12.04-dvd-i386.iso: No such file or directory
nate@Nate3:/cdrom$ 



I admit I don't know a lot .  Could someone help with this?  I don't even know if i'm in the right directory.  If I'm not then how do i get there?


Thanks,
Nate

You're pasting both the prompt and the command in as a command. Just copy the command.

---

### Post by tbrownarcher on 2012-06-22
> **gordintoronto said:**
> Download to your hard drive, then use Unetbootin to create a bootable flash drive. If you are doing it from Windows, Pendrive Linux is another option for creating the flash drive.

During the creation of the flash drive, it might appear to stall for several minutes. It's just processing a very large file.

Hope I'm not typting this 2 times ... sorry if i am.

I did not want to get windows involved.  I am trying to install a dedicated computer with 12.04 ubuntu.  

Can I use 10.1 ubuntu to accomplish what you described above.  Otherwise i guess I have to use windows.  

I did download onto a cd and also a thumb drive the ubuntu 12.04 iso though.

Thanks,
Nate

---

### Post by tbrownarcher on 2012-06-22
I got the 2 problems mixed up sorry ... maybe i should separate them .

this is what i get from the terminal when i try to use md5sum to verify the cdrom.  This is my attempt to get into the directory of the cdrom that has the *.iso on it.
It seems i'm in the wrong place. 

nate@Nate3:~$ cd ..
nate@Nate3:/home$ cd ..
nate@Nate3:/$ cd cdrom
nate@Nate3:/cdrom$ ls cdrom
ls: cannot access cdrom: No such file or directory
nate@Nate3:/cdrom$ ls
nate@Nate3:/cdrom$ 

Thanks,
Nate

---

### Post by gordintoronto on 2012-06-22
> **tbrownarcher said:**
> I did not want to get windows involved.  I am trying to install a dedicated computer with 12.04 ubuntu.  

Can I use 10.1 ubuntu to accomplish what you described above.  Otherwise i guess I have to use windows.  

I did download onto a cd and also a thumb drive the ubuntu 12.04 iso though.

Thanks,
Nate

I think you mean Ubuntu 10.10. It has "expired," so it does not get updates, but you might be able to install unetbootin by using Synaptic Package Manager.

You can't download directly onto a CD, so I assume you have the ISO on your hard drive. If not, copy it from the flash drive onto the hard drive.

(I ran Ubuntu 10.10 as my primary computing environment, until April 10, 2012. I'm actually using Linux Mint 13 now.)

---

### Post by gordintoronto on 2012-06-22
> **tbrownarcher said:**
> I can access the cdrom files with the gui but when i try to enter it with the terminal this is what i get i must be going to the wrong place.

nate@Nate3:~$ cd ..
nate@Nate3:/home$ cd ..
nate@Nate3:/$ cd cdrom
nate@Nate3:/cdrom$ ls cdrom
ls: cannot access cdrom: No such file or directory
nate@Nate3:/cdrom$ ls
nate@Nate3:/cdrom$ 

Thanks,
Nate

I don't think it is useful to access the files on the CDROM. However, if you really want to:
cd /media
ls

That should show you the label of the cdrom. It probably contains spaces. You can cd to it, by putting the name in quotes. Eg:
cd "Kubuntu 11.10 amd64"

Which is the label of a random CD I pulled out of my collection.

---

### Post by tbrownarcher on 2012-06-23
This is the result of trying to run md5sum on the ubuntu012.04 iso in downloads what does it mean ????




nate@Nate3:~/Downloads$ md5sum ubuntu-12.040desktop-i386.iso
md5sum: ubuntu-12.040desktop-i386.iso: No such file or directory
nate@Nate3:~/Downloads$ md5sum ubuntu-12.04-desktop-i386.iso
d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso
nate@Nate3:~/Downloads$ md5sum ubuntu-12.04-desktop-i386.iso
d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso
nate@Nate3:~/Downloads$ 

thanks,
Nate

---

### Post by tbrownarcher on 2012-06-23
I seem to have gotten into the Downloads directory but I do not know what the result of running the md5sum means .



nate@Nate3:~/Downloads$ ls
flash-plugin-10.3.183.20-release.i386.rpm  unetbootin-linux-575
ubuntu-12.04-desktop-i386.iso
nate@Nate3:~/Downloads$ md5sum ubuntu-12.040desktop-i386.iso
md5sum: ubuntu-12.040desktop-i386.iso: No such file or directory
nate@Nate3:~/Downloads$ md5sum ubuntu-12.04-desktop-i386.iso
d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso
nate@Nate3:~/Downloads$ md5sum ubuntu-12.04-desktop-i386.iso
d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso
nate@Nate3:~/Downloads$ 



Thanks,
Nate

---

### Post by tbrownarcher on 2012-06-23
I am so sorry for being redundant.  I did not intend to post a post twice or more i  did not realize i was on the second page and so i couldn't find the post and thought that i had not completed the procedure

Sorry ,
Nate

---

### Post by gordintoronto on 2012-06-24
No problem. Your md5sum is fine. The official values are here:
[https://help.ubuntu.com/community/UbuntuHashes/](https://help.ubuntu.com/community/UbuntuHashes/)

If you look closely, you can find the value for 12.04 386 desktop, which is the same as in your message.

Have you tried to install unetbootin?

---

### Post by Declanthedork on 2012-06-24
I got this error also. It turned out to be the slideshow at the end that was crashing. So what I did was opened a terminal and typed
```

sudo apt-get remove ubiquity-slideshow-ubuntu

```

If you're using a different distro (I used mint), then just change your distro name at the end, i.e.
```

sudo apt-get remove ubiquity-slideshow-mint

```

I installed from a pen drive when I did this. I'm not sure if it will work on a live CD.

---

