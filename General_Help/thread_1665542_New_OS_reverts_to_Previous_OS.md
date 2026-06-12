---
title: "New OS reverts to Previous OS"
date: 2011-01-12
forum: General Help
---

### Post by embra55 on 2011-01-12
Hi All,
I'm relatively new to Linux and have been trying out various distros, first on live cd's and then installing. Before installing a new distro I used to back up my home folder, and then let the partition manager sort the rest out dual boot xp), and then import my backed up home folder. i then read on the forums how to keep my home folder seperate. So when I install a distro what I now have is xp on 80G, swap 4G, ext4 20G (mounted at "/"), 395G ext4 (mounted at "/home").
The problem I seem to have is that when I install a new distro it seems to "default" to the first distro I installed. This occurs for both gnome & kde flavours.
The Gnome distros i have installed are Zorin 3. , Mint 10,Zorin 4, & Ubuntu 10.10 (my latest). The KDE distros I've tried are Kubuntu, PCLinuxOS, Mint KDE, and open Suse 11.3
My latest tryout, Ubuntu 10.10, is on my desktop and is nothing like the live cd. I have the Zorin task bar & menu at the bottom of the screen. The only thing i can see which resembles the live cd is the software manager.
Is there something I'm missing when I set up my partitions when installing? I can only assume that there is, and it's probably a simple fix. Any help appreciated.
Thanks in advance,
embra55

---

### Post by WorMzy on 2011-01-12
If you're using the same /home for each install, then your config will remain. If you want a fresh config, create a new user, or delete all the relevant "." folders in your home folder. e.g. deleting ~/.gconf will remove your settings for applications which use gconf, which includes gnome-panel, nautilus, gedit, etc.

---

### Post by embra55 on 2011-01-12
Hi WorMzy,
Thanks for your reply. I was looking thru my home folder and viewed hidden files etc. and theres a lot of stuff relating to previous installs. Before i go daft & delete stuff, is all this stuff needed or do i just delete the gconfig stuff?

---

### Post by embra55 on 2011-01-12
Hi WorMzy,
Thanks for your reply. I was looking thru my home folder and viewed hidden files etc. and there's a lot of stuff relating to previous installs & apps. Before I go daft & delete stuff, is all this stuff needed or do I just delete the gconfig stuff?

---

### Post by oldfred on 2011-01-12
Since you have so many installs and each may need different settings in /home, you really should keep each /home inside each install. Then if you know you want some specific settings you can copy them. 

You set up another /data partition for all your data and mount it inside each install. I created a little bash script that was just a history copy of the first time I linked my /data manually.

Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
kansasnoob's sharing
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)

I have changed my mount of /data to /mnt/data and may just change it to /data, but link all the folders into /home.
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

NOTE: The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not.

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

---

### Post by WorMzy on 2011-01-12
> **embra55 said:**
> Hi WorMzy,
Thanks for your reply. I was looking thru my home folder and viewed hidden files etc. and theres a lot of stuff relating to previous installs. Before i go daft & delete stuff, is all this stuff needed or do i just delete the gconfig stuff?

I wouldn't say that any of the settings folders are "needed" as such -- "." folders should be recreated when the application relaunches -- but you may want to keep some folders for various reasons (e.g. .mozilla/ for firefox settings/bookmarks/etc).

You could, instead of deleting the folders, move them to another place (e.g. ~/dot-backups), and then move specific folders back which contain settings you want to keep.

Personally, I do what oldfred suggested. I currently multiboot nine operating systems (two Windows, seven Linux), and instead of having a separate /home partition, I have a data partition instead. Every Linux operating system mounts that in the same way, and links my ~/Documents, ~/Downloads, etc, folders to the corresponding folders on the data partition. So each OS has it's own settings, but Documents, etc, are shared between them all.

---

### Post by embra55 on 2011-01-13
Hi WorMzy & oldfred, I've done what you suggested and it worked fine. Regarding olfred's solution that is one the next install. 
By the way, I didn't/don't have loads of distros installed at once (just xp & 1 other). I did have loads of settings for all the other distros I had tried in my home folder.
Anyways thanks for help, much appreciated.

---

