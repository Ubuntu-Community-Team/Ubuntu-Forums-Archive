---
title: "My system is blocked -- help"
date: 2010-06-08
forum: General Help
---

### Post by nav16een on 2010-06-08
Dear fellow mates,
       My system is blocked. I'm unable to login into my account. When I enter my username and password, It says it **"failed to update ICEauthority in the location /home/MY ID/.ICEauthority." **Consequently it says "**/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256**".. Then the system hangs.. I'm **able to login** in using my **root account**. I went into /home/MY ID/. There is a file named "Access your Private Data and a README file." In the readme file it says 
"[B]THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
"

But nothin happens when i tried both of them. 

[/B]I have a lot of datas in that account. I need them badly. Please help me guys. PLZ PLZ...

---

### Post by _khAttAm_ on 2010-06-08
Seems like disk is full.. Drop to the terminal (Ctrl+Alt+F1) and try deleting some files... one way is to remove package cache files.. those deb files that get downloaded when you upgrade or install a package.. they can be deleted using
```
sudo apt-get clean
```
Then restart using Ctrl+Alt+Del and you should be able to login.

If that does not help, please share the output of ```
cat /etc/fstab
```

---

### Post by nav16een on 2010-06-09
No no.. the hard disc is not full.. and i also tried the cleaning command. It didn't work. the output of the 2nd command is 
root@assault-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=414664d4-dce5-40c7-8ccc-9de7b8f16c3a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d70eda2e-f947-489a-b6ea-a93abf19e3d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



thanks for the response.. I need to somehow get the data outside.. Please help me..

---

### Post by newboyo on 2010-06-09
Hi,
 
The same thing happened to me when I installed Avira. 
 
I had asked Dazuko to protect /home and had the same error messages.
 
I fixed it by amending fstab where I asked Dazuko to protect /home/user, after which I was able to log in.
 
hope this helps.

---

### Post by applehead on 2010-06-09
I had a similar problem.
 I booted into recovery mode (hold shift on boot up) and then chose the option to log in (cant remember exactly what it says, I think its the first option) this lets you log in at the command line, then just type startx.

I think my problem was because I changed the settings to to log in without a password.

---

### Post by _khAttAm_ on 2010-06-10
what exactly does: ecryptfs-mount-private say?

Also post the o/p of:
```
 ls -la /home/your_id | grep Private
```

---

### Post by nav16een on 2010-06-10
> **applehead said:**
> I had a similar problem.
 I booted into recovery mode (hold shift on boot up) and then chose the option to log in (cant remember exactly what it says, I think its the first option) this lets you log in at the command line, then just type startx.

I think my problem was because I changed the settings to to log in without a password.


Thanks a lot.. a part of my problem is solved. i'm able to access my files now.. but then i rebooted my system. the same prob persists. i had to repeat the whole process again. 
what could be the problem??

---

### Post by nav16een on 2010-06-10
> **newboyo said:**
> Hi,
 
The same thing happened to me when I installed Avira. 
 
I had asked Dazuko to protect /home and had the same error messages.
 
I fixed it by amending fstab where I asked Dazuko to protect /home/user, after which I was able to log in.
 
hope this helps.


I'm sorry.. i'm new to Ubuntu and i don't know wat is Dazuko.. Could u please elaborate it for me??):P

---

### Post by nav16een on 2010-06-10
> **_khAttAm_ said:**
> what exactly does: ecryptfs-mount-private say?

Also post the o/p of:
```
 ls -la /home/your_id | grep Private
```


hi.. thanks a lot.. ecryptfs-mount-private was asking for the login passphrase. i didn't what to give. today i just gave my login password and it worked.. but the problem persists ..

---

