---
title: "help! system user gone"
date: 2009-12-14
forum: General Help
---

### Post by slim@jim on 2009-12-14
Hi,

My ubuntu is in bad shape right now and i have no idea how to fix it. 

The terminal says:   

I have no name!@water-box:
  
For some reason i cant start any applications to help fix this problem because they just crash.

I just ran remastersys to back up my install and now the user is gone along with these other issues, before i did the remastersys my system worked perfectly fine.

I have a lot of valuable data on this drive. I can't mount my other drives to save my files too them, it just says "no permissions".

I'm scared to shut my system down because i don't know if it will boot back up with the user gone ? 

please help me out with this one, i'm in a bad situation. Thanks

---

### Post by lmarmisa on 2009-12-14
Type these commands:

```

sudo fdisk -l
mount

```You will see the partitions detected and mounted.

May be you will be able with this information to mount manually other drivers in order to save important files.

---

### Post by slim@jim on 2009-12-14
> **lmarmisa said:**
> Type these commands:

```

sudo fdisk -l
mount

```You will see the partitions detected and mounted.

May be you will be able with this information to mount manually other drivers in order to save important files.


Thanks for helping me out so quickly :)

i put that command in the terminal and i got back:


I have no name!@water-box:~$ sudo fdisk -l mount
sudo: uid 999 does not exist in the passwd file!

---

### Post by lmarmisa on 2009-12-14
Hmmm.

I don't like. 

Is water-box the name of your computer?.

It seems that some importants files of your system are not accesible.

Probably you will need a Ubuntu Live CD for fixing the problem.

Any output to command mount?

Repeat the first command but without sudo

```

fdisk -l

```

---

### Post by slim@jim on 2009-12-14
Yes, water-box is my computers name.

I entered the command without sudo this time and got no response. It just opened a new line in the terminal with no effect.

I have no name!@water-box:~$ fdisk -l
I have no name!@water-box:~$

---

### Post by lmarmisa on 2009-12-14
I have found this reference to your problem:

[http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlbash.html](http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlbash.html)

*Login invokes the shell program at the user's privilege level. One of the things bash will do is to look in the /etc/passwd file to get the name of the user. It will use the UID number to find the username and set the environment variable, USERNAME, to that value. If bash cannot read the /etc/password file it will put the string "I have no name" in the environment variable. If this happens, it is because the permissions on the /etc/passwd file are not set properly. The permissions should be "-rw-r--r--". This file must be set so all users can read it.*

---

### Post by lmarmisa on 2009-12-14
Apparently you have user privileges and you are not able to get superuser privileges with the command modifier **sudo** because the file /etc/passwd cannot be read.

Type these commands:

```

cd /etc
ls -l passwd

```

---

### Post by lmarmisa on 2009-12-14
What about the command **mount** ?

---

### Post by slim@jim on 2009-12-14
ahhh that would make sense then. I don't really understand to much about ubuntu when we get into the system files and what not but i can learn. I've been using ubuntu for about a year now.

I get back from those commands:

I have no name!@water-box:/etc$ ls -l passwd
-rw-r--r-- 1 root root 2248 2009-12-13 21:36 passwd
I have no name!@water-box:/etc$ 

If i'm right the permissions are right because that paragraph from above said: 

The permissions should be "-rw-r--r--"

---

### Post by slim@jim on 2009-12-14
mount says:

I have no name!@water-box:~$ mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-17-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
I have no name!@water-box:~$

---

### Post by lmarmisa on 2009-12-14
Commands look good.

How do you copy the outputs of these commands to your posts? Can you use Gnome, Firefox and internet?

Please, type this command:

```

whoami

```

---

### Post by lmarmisa on 2009-12-14
The /home partition is mounted.

You can access to your files there

```

find /home

```
Don't panic. I think that the problem is not important.

---

### Post by slim@jim on 2009-12-14
I have no name!@water-box:~$ whoami
whoami: cannot find name for user ID 999
I have no name!@water-box:~$


I copy/paste the output from the terminal. 

Gnome seams to run fine, firefox is working well too, but other applications just crash including system apps and 

gksudo nautilus

crashes too which is how i usually change permissions since i'm not that good with the command line yet.

---

### Post by slim@jim on 2009-12-14
find /home

printed out a whole lot of stuff. Directory paths for i guess everything in my /home partition. 

/home/dave/.local/share/sounds/__custom/message-new-email.ogg
/home/dave/.local/share/sounds/__custom/index.theme
/home/dave/.local/share/sounds/__custom/bell-terminal.ogg
/home/dave/.local/share/sounds/__custom/trash-empty.ogg
/home/dave/.local/share/sounds/__custom/window-unmaximized.ogg
/home/dave/.local/share/sounds/__custom/window-maximized.ogg
/home/dave/.local/share/sounds/__custom/button-pressed.disabled
/home/dave/.local/share/audacious
/home/dave/.local/share/audacious/Skins
/home/dave/.local/share/audacious/Plugins
/home/dave/.local/share/mime
/home/dave/.local/share/mime/packages
/home/dave/.local/share/mime/packages/user-extension-bin.xml
/home/dave/.local/share/mime/aliases
/home/dave/.local/share/mime/magic
/home/dave/.local/share/mime/mime.cache
/home/dave/.local/share/mime/XMLnamespaces
/home/dave/.local/share/mime/globs
/home/dave/.local/share/mime/globs2
/home/dave/.local/share/mime/application
/home/dave/.local/share/mime/application/x-extension-bin.xml
/home/dave/.local/share/mime/subclasses
/home/dave/.local/share/mime/types
/home/dave/.local/share/mime/treemagic


and on and on.

---

### Post by lmarmisa on 2009-12-14
I thought that you had only a shell terminal, but I see that this is not the case.

Apparently your bash shells and other programs have gone mad, but not Gnome. Do you understand it?. ;)

Your shell is not able to read the /etc/passwd file. This is 100% sure.

But, what about you open a new terminal?

---

### Post by slim@jim on 2009-12-14
i got something back with:

echo $USER

which i weird since whoami didn't work.  


I have no name!@water-box:~$ echo $USER
dave
I have no name!@water-box:~$

---

### Post by slim@jim on 2009-12-14
No i don't understand :( and i'm about to go mad too ;)

whoooops yeah i'm still in gnome and using my desktop.

I can open as many terminals as i want.


and i forgot to add to the above post that when i ran:

find /home

at first it printed out remastersys dummy system for a long time. Don't know what that could mean but it is strange i think.

Thats when my ubuntu went sideways, after i tryed to back my install up with rematersys.

---

### Post by lmarmisa on 2009-12-14
I repeat my question:

Does this problem occur in all terminals?. Open more terminals and check it, please.

---

### Post by slim@jim on 2009-12-14
Yes i get the same thing in all terminals. Every terminal i open and type:



whoami returns

I have no name!@water-box:~$ whoami
whoami: cannot find name for user ID 999
I have no name!@water-box:~$ 



find /home

returns a lot of directory paths in my /home partion. 

The read out starts in:

/home/remastersys/remastersys/dummysys

maybe thats what is messing things up, you think ?

I'm supposed to execute the command:

sudo remastersys clean

after using remastersys, but it wont run and returns:
   
I have no name!@water-box:~$ sudo remastersys clean
sudo: uid 999 does not exist in the passwd file!


[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

---

### Post by slim@jim on 2009-12-14
You know what when i run that command:

find /home

it prints out all the files in my:

/home/remastersys/remastersys/dummysys

first.


Then prints out all the directories from my real home folder:

/home/dave

You think maybe bash is tring to read from the dummy file system instead of my real home file system ?


#Remastersys Global Configuration File


# This is the temporary working directory and won't be included on the cd/dvd
WORKDIR="/home/remastersys"

---

### Post by lmarmisa on 2009-12-14
Well, it is very probable that remastersys is guilty on this little disaster.

I have a doubt. Did you make a backup or a restore with remastersys?.

It does not make sense that making a backup your system crash. In theory, a back up is not a dangerous oparation for the system. A backup does not modify your system at all. The restore operation is different, bacause you modify your system. Do you agree?.

---

### Post by lmarmisa on 2009-12-14
[I]You think maybe bash is tring to read from the dummy file system instead of my real home file system ?

[/I]I do not think so. I think that the problem is that some programs receive bad information about its owner or are not able to open the /etc/passwd file. Why?. This is a mistery.

Maybe this problem will disapear when you restart your system. But, I am not sure about that.

Apparently your files are safely in the home partition. But they are not backed-up.

---

### Post by slim@jim on 2009-12-14
Yes i do agree that a restore would tear my system up like it is right now.

But i didn't and don't have anything to restore my system with. This is the first time i've used remastersys and don't have a back-up yet to restore anything with.

The guide that i used doesnt have any restore commands either, take a look.
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") 

So i don't see how i could have accidentally restored ubuntu.


What i did do tho at first was a back-up of my whole system at first by mistake. The command:

2) to make a livecd/dvd backup and call the iso custom.iso
sudo remastersys backup custom.iso


When i realized i made a mistake i killed the terminal and ran the command to just back up my install:

Creating An ISO Image
To create an iso image of your installation, simply run

sudo remastersys dist

This will create an iso image called customdist.iso in the /home/remastersys directory. The dist option makes that your personal folder (e.g. /home/ruchi) will not be included in the iso image. You might have to insert your Ubuntu installation CD during the process.

Maybe since i killed bash that screwed something up ? But like you said its just a back-up so i don't see how it could ?

---

### Post by slim@jim on 2009-12-14
> **lmarmisa said:**
> [I]Apparently your files are safely in the home partition. But they are not backed-up.


Yes my files are safe but unfortunately not backed up:(

If i install ubuntu on another disk will i bee able to access my partion from the new install and copy the files to another disk ?  

Or will i be shut out of this disk if i shut down ?


Thank You for all your help it is very nice of you ;)

---

### Post by lmarmisa on 2009-12-14
I make my backups with 

[http://www.clonezilla.org/](http://www.clonezilla.org/)

This is a Live CD and I use an USB HD for storing the backups files.

I like a Live CD type solution because the Ubuntu system is stopped and so the backup of the full system is 100% guaranteed.

---

### Post by slim@jim on 2009-12-14
ok well i'll be tring that one out next time i do this !

thanks for all your help :D

i'm going to reboot and see what happens :D

maybe i'll get some sleep tho :P

---

### Post by lmarmisa on 2009-12-14
This is my recommendation:

Download clonezilla, burn a CD with it and make a backup of your /home partition (not the full system, only /dev/sdb6). I suppose that all your important files are there, right?. I don't know if you have an external USB drive for storing the backup. Maybe it is also possible to use other partition of your system (ntfs or fat32) for the backup files.

Clonezilla allows three types of operations: disk or partition backup, disk or partition restore and disk to disk or partition to partition cloning. Of course, I recommend the 1st option.

When you have your files backed-up, it will be time to see if the system is recovered or a new installation is needed.

---

### Post by lmarmisa on 2009-12-14
Only a question.

Where are you?

---

### Post by slim@jim on 2009-12-15
thanks i'll try clonezilla next time.

i ended up reinstalling without formating my /home folder, got back up and running with a fresh install of 9.10. needed to upgrade anyway;)

worked like a dream. thanks ubuntu !

the more u work with linux the more u like it !

thanks for your help lmarmisa !

i recovered my system now.

---

