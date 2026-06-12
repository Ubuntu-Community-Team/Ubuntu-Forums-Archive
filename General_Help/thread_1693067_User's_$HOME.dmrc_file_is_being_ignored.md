---
title: "User's $HOME/.dmrc file is being ignored"
date: 2011-02-22
forum: General Help
---

### Post by frank cox on 2011-02-22
Hi:

 I am trying to copy all my personal  files on my Ubuntu 9.04 installation so I can wipe the drive and install 10.10. I added the Xubuntu desktop a while back if that matters. On boot up I get this error message:
When I boot up 

  	 	      		 		 			 			 			 			 			                          			 [User's $HOME/.dmrc file is being ignored]("http://ubuntuforums.org/showthread.php?t=755043&highlight=users+home+folder+permissions")

It goes on to say it needs to have 644 permissions and be owned by user. I thought I ran the correct commands to fix this but apparently not. It also seem that with the Xubuntu desktop anyway I no longer own my own $Home directory.

I want to learn why this happened but if it is going to be an ordeal is there a way to bypass all this and just copy the files so I can wipe the drive?

Thanks

---

### Post by oldfred on 2011-02-22
It seems to happen sometimes when moving or copying /home. If you copy to a non-linux formated partition and lose ownership & permissions?

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

---

### Post by frank cox on 2011-02-22
> **oldfred said:**
> It seems to happen sometimes when moving or copying /home. If you copy to a non-linux formated partition and lose ownership & permissions?

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username


That seems to have worked, there were no error messages at startup.

Thanks!

I will wait until I do my copying and then if no problems I will mark it solved.

While I have someone who obviously understands this os perhaps you would be so kind as to tell me how to set it all back up?

I have 2 drives-One 250 gb that is running Linux Mint 9 and Xubuntu 10 but it is corrupted and I never use it, Mint is what I use the most as well as several frugal puppy Linux installs.  I won't go in to detail about the partitioning but lets say its "unique' "different" and not recommended :} .
The other has XP and this install, Ubu 9.04, which was my first attempt at Linux .

What I want to do is wipe everything and start over . I would like to install Linux Mint 10.10 and perhaps PC Linix or SuSE on the 250 gb drive and XP and Xubuntu 10.10 and possible something else on the 500 . The way I want to set it up is with a home directory on each that are synchronized so they mirror each other and all the operating systems can share the same home directory. . And when I get to it to a file server as well. It would be nice if XP could read the home directories but it is not critical as XP is rarely used, only when there is no other way.  Any advice or links to tutorials for that kind of thing would be greatly appreciated.

---

### Post by frank cox on 2011-02-22
Well there is still a problem. There was no error at boot but when I try to copy a directory it gets almost to the end and then hangs up. All I really want to do is back it up and nuke the drive but I can't

---

### Post by oldfred on 2011-02-23
It still sounds like a permission problem. What does this show both the from & to locations.

sudo ls -l
```
-rwxrwxrw- 1 fred fred     179 2010-12-13 17:35 examples.desktop
lrwxrwxrwx 1 fred fred      18 2010-12-13 19:46 fredCopy -> /mnt/data/fredCopy
drwxrwxrw- 3 fred fred    4096 2011-01-01 18:38 GNUstep

```Sharing /home can lead to the issues you are having. And even my next suggestion has issues with non-Debian distributions as the userid may not be the same.

Do not share /home but share all the data from /home in a separate data partition.
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relavent
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
How to Multi-boot (Maintain more then 2 OS) ignore old grub,  as you now have grub2
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
You can minimize permission problems while maintaining security by making a new group, say "data", and giving ownership of the data partition to root.data with permissions of 770.

I aggressively move hidden folders with lots of data like Firefox and Thunderbird out of home into either a NTFS /shared or /data, so my home now is only 1GB. My root is about 6GB and all my data is in /data or /shared.
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)


Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

I cahnged the mount location from my link above to this:
sudo mkdir /mnt/data
sudo chown -R fred:fred /mnt/data
sudo chmod -R 766 /mnt/data
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by frank cox on 2011-02-23
Thanks- I will try this when I get to the office. Once I get my new install completed it is possible to copy the the whole thing and install it on my home come computer? I only have dial up at home and it would be impossible to update the installation from there.

---

### Post by oldfred on 2011-02-23
I have never done it:

Copy/backup system
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

aptoncd or copy updates
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Location of downloaded debs
/var/cache/apt/archives/

---

