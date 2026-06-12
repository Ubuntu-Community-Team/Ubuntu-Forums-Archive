---
title: "No Disk Space Left"
date: 2011-02-11
forum: General Help
---

### Post by aphung2 on 2011-02-11
Hello All,

I've googled and found many results, but let me warn you. I'm completely brand new to Linux and Ubuntu. 

So pretty much I have a message saying I have no space left on my disk. I rebooted my laptop to load XP and I uninstalled and deleted nearly everything. Problem is Ubuntu still says I have no space left. I'm sure you guys get this all the time, so sorry from a newbie.

---

### Post by aphung2 on 2011-02-11
I wonder if this helps


Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0             9821012   9034072    288048  97% /
none                   1016916       276   1016640   1% /dev
none                   1023768       824   1022944   1% /dev/shm
none                   1023768       220   1023548   1% /var/run
none                   1023768         0   1023768   0% /var/lock
/dev/sda2             75441236  49461468  25979768  66% /host

---

### Post by Grenage on 2011-02-11
Hi there.

Ubuntu is probably installed in a different partition, so cleaning XP data might not help - unless this is a Wubi install, but I've never touched one of those.

From a linux terminal, please type the following, and let us know what it says:

```
df -h
```

It basically means "Disc Free" and the -h means "Human-readable".

---

### Post by aphung2 on 2011-02-11
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0             9821012   9034072    288048  97% /
none                   1016916       276   1016640   1% /dev
none                   1023768       824   1022944   1% /dev/shm
none                   1023768       220   1023548   1% /var/run
none                   1023768         0   1023768   0% /var/lock
/dev/sda2             75441236  49461468  25979768  66% /host

---

### Post by aphung2 on 2011-02-11
Oh thanks for the speedy response!


Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            9.4G  8.7G  281M  97% /
none                  994M  276K  993M   1% /dev
none                 1000M  824K  999M   1% /dev/shm
none                 1000M  220K 1000M   1% /var/run
none                 1000M     0 1000M   0% /var/lock
/dev/sda2              72G   48G   25G  66% /host

Is there a way for me to use that freed up space? I was reading a tiny bit about people talking about mounting. Just trying to see if I could clarify that any more.

---

### Post by WorMzy on 2011-02-11
You have installed Ubuntu inside Windows. When you installed it, consequently you have a fixed virtual disk size, and this virtual disk is nearly full (You're using 97% of it according to df)

This Wiki page may help you: [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by Grenage on 2011-02-11
That explains what /dev/loop is all about!

---

### Post by aphung2 on 2011-02-11
I tried 
sudo sh wubi-add-virtual-disk /home 15000

and it ran a bunch of lines for a while... told me to reboot afterwards.

Still have the same message that I have no space left.

---

### Post by aphung2 on 2011-02-11
Can anyone help clarify this please? I typed this in the terminal.

sudo sh wubi-add-virtual-disk /home 15000 
[FONT=monospace]
And what I believed that did was had 1.5GB on my home virtual drive. For some reason after rebooting my computer, I still get a "Not enough space" message. 

I will shower you with compliments if you can help! Or try =)

Thanks in advance from a noobie. 

Andrew
[/FONT]

---

### Post by Dnajun_Tnuieh on 2011-02-11
I'd say just do a fresh install of Ubuntu on it's own or at least dual-boot with a sufficent enough partition size for your needs.

---

### Post by bcbc on 2011-02-11
That script creates a new virtual disk for /home.

But it leaves a backup copy of /home on the root.disk Just in case the new virtual disk (home.disk) didn't work.
So if it's working with the new home.disk you need to delete the backed up home from the root.disk to free up that space.

EDIT: i just looked at the script. At the end it says:
"Operation completed successfully, if all is good feel free to remove /home.backup
Rebooting is recommended."

So if you remove it then you should have the free space (15GB) (15000 means 15GB or did you specify 1500 instead)

---

### Post by bcbc on 2011-02-11
Before you start deleting things, please give the output of:
```
cat /etc/fstab
mount
ls /home*
ls -l /host/ubuntu/disks

```

---

### Post by aphung2 on 2011-02-11
This is what I get

andrew@ubuntu:~$ ls /home*
/home:
andrew  lost+found

/home.backup:
andrew
andrew@ubuntu:~$ ls -l /host/ubuntu/disks
total 14549604
drwxrwxrwx 1 root root           0 2011-02-03 15:23 boot
-rwxrwxrwx 1 root root 15001000000 2011-02-11 19:55 home.disk
-rwxrwxrwx 2 root root 10217324544 2011-02-11 19:55 root.disk
-rwxrwxrwx 2 root root   268435456 2011-02-03 10:39 swap.disk

---

### Post by bcbc on 2011-02-11
OK so you have a 15GB home.disk file. (That leaves about 10GB free on the Windows /host).
You have a 10GB root.disk that has /home.backup, a copy of /home that is still on the root.disk, which is why it's not showing any space freed up. If you delete /home.backup you'll see that free space (however big your /home is) on the root.disk. 

if you run:
```
df -h
``` 
it will show a separate line for /home (/dev/loop1) and it will show how much space is used. That is how much space you'll free up on / (/dev/loop0) when you remove /home.backup

---

### Post by aphung2 on 2011-02-11
As promised.

*Ahem*

Thank you bcbc. In this self righteous world you reached out and helped me. I may not be the best writer, but it doesn't take a writer to say you are good news my friend. You also look cute.

Andrew

---

### Post by aphung2 on 2011-02-11
Err... how can I delete back up home? 

I found the folder and all, but it won't go into the Trash.

---

### Post by bcbc on 2011-02-11
Please use with caution - the following command is very dangerous if mistyped.
```
sudo rm -rf /home.backup
```

That's the easy/dangerous way.

A safer way might be ALT-F2, enter "gksu nautilus /" (without quotes).
Enter password when prompted, then select the home.backup folder, hold down the Shift key, and hit the Delete key, then Enter to confirm delete.
Make sure you hold down the shift key or it will go to trash which you don't want.

---

### Post by bcbc on 2011-02-11
By the way, you should keep backups of important data. Wubi generally works well but because the virtual disks are files, there is greater chance of catastrophic loss if the file is corrupted.

Technically one should backup all important data anyway - but in practice many people don't so I thought I'd mention it. There's also this: [https://wiki.ubuntu.com/WubiGuide#Warning](https://wiki.ubuntu.com/WubiGuide#Warning)

---

