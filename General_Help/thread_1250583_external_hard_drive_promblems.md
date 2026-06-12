---
title: "external hard drive promblems"
date: 2009-08-26
forum: General Help
---

### Post by new4m3 on 2009-08-26
I hope i'am doing this right, Iam a new linux user and trying to learn. My simple tech external hard drive is not working at all it gives me can not display and unmount error and so fourth if anywould could tell me how to get it working i would be greatful to you. also i can not get my ipod to work at all with this in need of some major help. I just want to transfer my music and pic to my hard drive and it wount let me help please. thank you

---

### Post by scouser73 on 2009-08-26
Please follow the instructions set out in this tutorial: [[COLOR="Red"]**Mount External Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by Yvan300 on 2009-08-26
What kind of ipod are you using and try rhythm box for transfering your music to your ipod.

---

### Post by new4m3 on 2009-08-26
I have a 80g ipod classic, and i dont think i did the mount right is there a much easier way to use a simple tech external hard drive. so i can transfer my music and movies to  my external hard drive form my labtop

---

### Post by Yvan300 on 2009-08-30
Well for me i just plug it in and it's there ready for use. The weird thing was that it did not work in intrepid ibex but when i upgraded to jaunty jackalope, it worked like a charm. So maybe you could wait for karmic koala and then try your luck :)

---

### Post by SBenvie on 2009-09-30
ok, my problem seems very simple to me, but since i am still very new to the linux world i am aggravated as hell and do not know how to fix this problem. i have a 1 TB WD e-book external hard drive. ever since i installed ubuntu 9.04 it has always mounted itself as /media/WD TB Back-up , but tonight i plugged in an mp3 player, and a blackberry phone to load some pics and mp3s etc, and now everytime i mount the external hd it mounts itself as /media/WD TB Back-up_ 
now the problem itself is not that serious, BUT i am running wine on my computer so i can use u-torrent, and i have specifically setup u-torrent to save and download all torrents to my external hd, now whenever i open u-torrent it wont read any of the torrents, and i went into u-torrent and changed the directory, and it still wont read any of the torrents, or how much of what has already been downloaded. i have soime torrents that are 70gigs and at 50% completion, if i have to redownload them im going to be some pissed. lol. please, someone help me!!!!!

---

### Post by blueridgedog on 2009-09-30
One way out of the issue is to mount the external drive in a location that suits you.  I can show you how if you tell me more about the drive.  With the drive plugged in, can you post the output of the command:

```
mount
```

and 

```
sudo fdisk -l
```

This will help identify the drive and we can pick a mount location for it and make it permanent.

---

### Post by tnt533 on 2009-09-30
I am by no means an expert but here are some directions to look in.

First, I would make sure the drive is unmounted and the two hand-held devices are unplugged.I would remove the mount-point under /media/ for your ipod, your blackberry and your external drive.

Second, I would check the contents of your fstab file in /etc/fstab/. Look for an entry for all three devices. There more than likely isn't any but if there is, you should be able to create a new mount point in /media/ and then edit the fstab accordingly. Read the links below. There is enough information there to get you going.

Read [this]("http://www.tuxfiles.org/linuxhelp/fstab.html").

And [this]("https://help.ubuntu.com/community/Mount").



I would also suggest that you check out one of the native Linux bit-torrent clients like deluge. Deluge can be installed through synaptic or by typing the following command in a console. Running basic stuff like that in wine is really not needed unless uTorrent fills some abstract need most don't have.

sudo apt-get install deluge



One other problem that comes to mind is a dirty "unmount" from a windows partition causing issues. If that is the case, you can use a command to force the mount but I would instead suggest that you boot into windows and use the "safely remove hardware" system tray icon to "unmount" the drive in windows and then try it again in Ubuntu. If you don't properly remove some drives, windows will write a dirty bit to the drive so it knows it wasn't removed properly the last time. This can cause issues when trying to mount the drive in Linux. 

For the ipod, read [this]("https://help.ubuntu.com/community/PortableDevices/iPod") and [this]("http://www.linuxjournal.com/article/9266").

I have never used a Blackberry device so I would be of no help there.

---

### Post by SBenvie on 2009-09-30
ty for ur help. i have tried 3 diff torrent programs and just dislike them immensly, i also use winamp through wine, like i said i am still new to linux, but so far like it way better then any windows i have ever used, i am using ubuntu 9.04 and no windows at all, so i doubt the problem is a dirty unount. i am reading the 2 links posted above, will post more info if those dont work. again, ty for your help.

---

### Post by SBenvie on 2009-09-30
ok, so i read those articles, it doesnt help me a whole lot. but i was thinking and i know what happened, i have a laptop, and i also have a cooling tray to keep it from overheating, well it got unpluggd, my comp. overheated and shut itself down, and now the directory which my external hard drive used to be mounted is still there, but its an empty directory. hmmmm... anyway to fix it?

---

### Post by SBenvie on 2009-09-30
this is what i got when i typed in the command  "mount"

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shawn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shawn)
/dev/sdb1 on /media/WD TB Back-up_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

---

### Post by sleepitoff on 2009-09-30
I can't help with your mount problems, but I'd like to give you a suggestion of trying out GTK-Pod for music/photo/video transferring to your ipod. Works excellent and is really easy to use.. You can find it by opening Synaptic Package Manager and searching for GTKpod. Just make sure you install the the gtk-pod-aac version. 

Another thing, instead of using Winamp through Wine, why not use Audacious or XMMS? These are small, lightweight audio players that will do exactly what Winamp can do, plus they support Winamp skins. 

As for the BitTorrent client, use Transmission. It's native on Ubuntu and it's excellent.

---

### Post by blueridgedog on 2009-10-01
So, based on your mount command the drive is sdb1 and it has an NTFS file system on it.  The following will mount the drive in the same place each time (it is a manual mount method, not an automatic method).  It requires some command line work, but it allows you to take control over where drives are mounted.  It is a good first step in learning to manage your own system.  If you decide to try it and get stuck, just post and I and others will help.

In the following substitute you user name for USER.

Make a directory for the drive to be mounted to (rename it as you see fit):

```
mkdir /home/USER/files

```

Unmount the drives from its existing mount point:

```
sudo umount /dev/sdb1

```

Your user ID on the system is probably 1000, but it is easy to check:

```
cat /etc/passwd | grep USER
```

If your user ID is anything other than 1000, change it in the mount option below.

Edit /ect/fstab to mount the drives in the new locations
```

gksudo gedit /etc/fstab
```

Add The following line:

```
/dev/sdb1 /home/USER/files ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.UTF-8 0 1

```

Save the file then mount it with
```

sudo mount /home/USER/files

```

Remember to change USER everywhere you see it and also you can adjust the mount point as you want, but make certain you own the mount point.  If you make a mount point in another part of the system, give yourself ownership with:

```
sudo chown USER:USER /path/to/new/mountpoint
```

---

### Post by SBenvie on 2009-10-01
ok, i hate ALL of the torrent clients i have seen so far for linux, i tried all of the native ones and dont like any of them, i have been playing with rhythmbox and i think i like that alot, dont ever even use winamp anylonger. and u-torrent runs great through wine, and it runs very stable. i read your replies, and they have been a great help, but if i follow your steps, and do as you suggested, then i am going to have to start all of my torrents all over again. i changed the torrent directory in u-torrent, and rechecked the torrents, and updated the trackers, etc, etc. but it wont read that the torrents are partially completed already, one of the torrents is 70gig and half way downloaded, i dont want to have to restart the torrent from the beggining.

if you could help me find a solution so it will mount itself to its original directory that would be very much appreciated.

and yes i know, i contradicted myself as far as u-torrent running great and stable through wine, etc etc. but this is the first problem i have had with u-torrent, and my external hd.

---

### Post by scouser73 on 2009-10-01
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by SBenvie on 2009-10-01
ok, so thanks to you all i have fixed the problem, i logged in as root, del the dir from the media folder, un-mounted my external hd, remounted it, and it came up as WD TB Back-up like it is supposed to. now everything is back to normal and things are working correctly.

thank you all so much. :P  :guitar:

---

