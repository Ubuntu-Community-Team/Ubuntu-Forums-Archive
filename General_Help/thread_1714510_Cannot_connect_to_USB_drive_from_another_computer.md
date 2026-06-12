---
title: "Cannot connect to USB drive from another computer"
date: 2011-03-25
forum: General Help
---

### Post by petersfreeman on 2011-03-25
My wife's desktop computer "TOWER" is running Ubuntu 10.10 (Maverick) and has a USB drive connected to it that is formatted NTFS.  This drive is mounted in the fstab file:

```
UUID=GF66D23856B93762 /media/Media2 ntfs-3g defaults 0 0
```

I use a laptop "LAPTOP" also running Ubuntu 10.10 (Maverick) and I want to connect to the USB drive on my wife's computer.

Both Tower and Laptop computers are on the same workgroup "WORKGROUP"

On my wife's computer "TOWER", I used Nautilus, right clicked in the root area of the drive and set up a share called "Media2" and checked the box "Allow others to create and delete files in this folder".  Next I checked the permissions and noticed that it is owned by root and the group was root.  Regardless, my wife has no problems creating and deleting files on this drive.

On my laptop "LAPTOP", I first created a folder in /media called Media2 and set up ownership and permissions to make it most permissive for me with the strategy to first get it working then later reduce unncessary permissivness.

```
cd /media
sudo mkdir /Media2
sudo chown peter:peter Media2
sudo chmod 777 Media2
```

I click Places/Network and double click on the icon that represents my wife's computer "TOWER".  It opens up and displays the shares that I have set up on her computer.  I find the share "Media2", double click it and Nautilus displays the files and folders.  I create a test document in "Media2" and then I delete it.  I right click any folder or document and check the permissions and it shows "The permissions of 'xxxxxxxx' could not be determined".  So far so good.  To prepare for the next test, I unmount the drive by right clicking the "Media2 on Tower" icon that is sitting on my laptop's desktop and clicking "Unmount".

Again using my laptop "LAPTOP", I open a terminal session (Applications/Accessories/Terminal).  First I connect successfully as my wife.

```
sudo mount -t cifs //192.168.241.100/Media2 /media/Media2 -o username=wife,password=herpassword
```

Interestingly, when I try  to unmount by right clicking the "Media2 on Tower" icon that is sitting on my laptop's desktop, I get the message "umount: /media/Media2 is not in the fstab (and you are not root)".  I then unmount using the terminal by typing:

```
sudo umount -t cifs  /media/Media2
```

Now I try to connect as myself using the same code as before except with my user name and password but I am unsuccessful.

```
sudo mount -t cifs //192.168.241.100/Media2 /media/Media2 -o username=peter,password=peterspassword
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I have tinkered a bit trying to understand what is happening here and to solve this problem.

Where am I going with this?  Ultimately, I want to set up my /etc/fstab on "LAPTOP" so that when I reboot, I am automatically mounting this share.

Please help.

Peter Freeman

---

### Post by nothingspecial on 2011-03-25
If both computers are running linux, why not use a linux file system that suppots linux file permissions? Or is windows involved?

Then with ssh installed you could just click Places > Connect To Server and apply what ever permissions you like and auto mount using sshfs.

---

### Post by Morbius1 on 2011-03-25
**[1]** If I followed your description correctly the reason you can't connect using your username instead of your wife's is because your wife did not create a local account for you and did not add that account to the samba database.

So on TOWER she needs to create a local account for you. One way to do that if the account is just to be used for file sharing is to create an account that will not generate a home directory:
```
sudo useradd -s /bin/true peter
```Then add peter to the samba database:
```
sudo smbpasswd -a peter
```It will first ask for sudo's password then the samba password you want to use to access the share

Now you may be asking at this point: Why didn't she have to add her own name to the samba database? Starting in 10.10 Ubuntu has added a poorly conceived utility** libpam-smbpass** that will automatically generate a samba password that matches her login password. It's a very bad idea in my opinion as it introduces security and privacy problems but I wasn't asked ;)

**[2]** You are mixing and matching two different methods of mounting remote shares.

When you go to Places > Network ... what Nautilus is doing is this:
```
gvfs-mount smb://tower/media2
```It automatically generates a mount point at:
> /home/peter/.gvfs/media2 on towerThe "sudo mount -t cifs ..." is a different mechanism and it sound like you're mounting it twice. 

**[3]** This is more a FYI:
If you want to automount, the fstab method is the traditional way of doing it but you can use the gvfs method as well.

Using the terminal see if you can replicate what nautilus does:
```
gvfs-mount smb://tower/media2
```If it works like I described it above then you can add that line to your it to your startup programs so it launches on boot.

Of course the problem with both methods is that if you wifes machine is not running when you boot they fail to mount the remote share and there's no way to restart the process.

One way out of this is to use Gigolo ( a GUI for the gvfs method ): [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

It can be set up to scan the network at user defined intervals and mount the remote share only when the remote machine is available.

There is one problem with the gvfs / Gigolo method and that's the hidden ".gvfs" mountpoint. It may not be an issue for you but if it is you can get around this problem with a symbolic link to /media/Media.

---

### Post by nothingspecial on 2011-03-25
But if both machines are exclusively linux, then all this is unnecessary.

Samba is for windows.

That's why I asked :)

---

### Post by Morbius1 on 2011-03-25
(1) I am answering the question posted.

(2) I'll admit that I tend to get somewhat verbose in my posts but to answer his exact question "all of this" is this:
sudo useradd -s /bin/true peter
sudo smbpasswd -a peter

(3) He already has it working - just not with a different user.

(4) Samba will run on anything from an IBM Zenterprise mainframe to VMS with Linux, OSX, as well as Windows clients

---

### Post by petersfreeman on 2011-03-25
Thanks Morbius1.  As soon as I added the password to the Samba database, everything worked.  What I want to do now is to build it into fstab so it automatically loads on boot.

I appreciate that you took the time to provide a lot of valuable information.  I'll mark this thread as SOLVED.

Cheers,

Peter

---

### Post by petersfreeman on 2011-03-25
Hi nothingspecial, unfortunately, my son uses Windows and he needs to access the drive, hence the NTFS format.  I put my password in the Samba database and it all works fine now.  - Cheers, Peter

---

