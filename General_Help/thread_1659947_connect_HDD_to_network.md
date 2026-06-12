---
title: "connect HDD to network"
date: 2011-01-04
forum: General Help
---

### Post by aziz.joh on 2011-01-04
Hello everyone

[COLOR="Red"]***what I have***[/COLOR]
1- [COLOR="SeaGreen"]1TB HDD[/COLOR]. "has 2 partitions"
    1.1- [COLOR="Orange"]Data1[/COLOR] 250GB NTFS.
    1.2- Data2 750GB EXT4. "Content 4 folders"
        1.2.1- [COLOR="orange"]Documents[/COLOR]. 
        1.2.2- [COLOR="orange"]Music[/COLOR].
        1.2.3- [COLOR="orange"]Pictures[/COLOR].
        1.2.4- [COLOR="orange"]Videos[/COLOR].

2- laptops with Ubuntu 10.10 Desktop 32bit. "I have 3 laptops"
    2.1- TV-laptop."I connect to it TV, sound system and [COLOR="SeaGreen"]1TB HDD[/COLOR]"
    2.2- MY-laptop.
    2.3- MyWife-laptop.

[COLOR="Red"]***What I Done so far is that***[/COLOR]
1- I connect my [COLOR="SeaGreen"]1TB HDD[/COLOR] to TV-laptop.
2- I configure Samba on TV-laptop. "Add Samba share"

    2.1- basic (/media/Data1,[COLOR="Orange"]data1[/COLOR],,writable,visible)
         access(allow access to everyone).

    2.2- basic (/media/Data2/Documents,[COLOR="orange"]documents[/COLOR],,writable,visible)
         access (allow access to everyone).

    2.3- basic (/media/Data2/Music,[COLOR="orange"]music[/COLOR],,writable,visible)
         access(allow access to everyone).

    2.4- basic (/media/Data2/Pictures,[COLOR="orange"]pictures[/COLOR],,writable,visible)
         access(allow access to everyone).

    2.5- basic (/media/Data2/Videos,[COLOR="orange"]videos[/COLOR],,writable,visible)
         access(allow access to everyone).


[COLOR="Red"]***what I want is that***[/COLOR]
1- I want to mount [COLOR="SeaGreen"]1TB HDD[/COLOR] to all laptops via network "Wireless" automatically when I connect [COLOR="SeaGreen"]1TB HDD[/COLOR] to TV-laptop.
2- I want all laptops to save data to [COLOR="SeaGreen"]1TB HDD[/COLOR]. such as all laptops Docs will be in Data2/[COLOR="orange"]Documents[/COLOR] and so on.
3- I want the laptops synchronize the data.
4- I want some application add data from [COLOR="SeaGreen"]1TB HDD[/COLOR] such as Rhythmbox.

---

### Post by aziz.joh on 2011-01-07
guys any help or guides to set it up please

---

### Post by aziz.joh on 2011-01-09
for more info see
[URL="http://ubuntuforums.org/showthread.php?t=280473"]http://ubuntuforums.org/showthread.php?t=280473
[/URL]
[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]https://help.ubuntu.com/community/Partitioning/Home/Moving
[/URL]
[URL="http://en.wikipedia.org/wiki/Fstab"]http://en.wikipedia.org/wiki/Fstab
[/URL]

server side
1- connete your HDD to you your PC but do not mount it
2- make folders in the place that you want this folder. (it will be good if you mount in /mnt folder or media)
[PHP]	cd /media/
	sudo mkdir Data1 Data2
	sudo chmod -R 777 Data1 Data2[/PHP]
3- make a backup of fstab after that open fstab
[PHP]	sudo cp /etc/fstab /etcfstab.$(Date +%Y-%m-%d)
	sudo open gedit /etc/fstab[/PHP]
4- add your partitions to mount directly next time
	# (identifier)	(location)	(format)	(some settings) 
	UUID=partition	pleace		type		option     	0	1
	to find UUID use:
	[PHP]sudo blkid[/PHP]

[PHP]	UUID=7AEED6DC770...	/media/Data1	ntfs	auto,dev,exec,rw,sync,user	0	1
	UUID=b50d8d81-4a34...	/media/Data2	ext4	auto,dev,exec,rw,sync,user	0	1[/PHP]
5- save and close /etc/fstab
6- you can set samba to share (setup#2 in what i done so far)
7- restart the computer
	[PHP]sudo reboot[/PHP]
Hint you can use ([PHP]sudo mount -a[/PHP]) to mount all the partitions to know everything work very well before restart.

you can make link to this folder in your home folder make it more easy

clint side
1- make folders in the place you
	[PHP]sudo mkdir /media/data1 /media/documents /media/music /media/pictures /media/videos
	sudo chmod -R 777 /media/data1 /media/documents /media/music /media/pictures /media/videos[/PHP]
2- you have to know the server IP for example 192.168.1.15
3- you can try to mount one folder (it should to mount when you try it if not there is an error somewhere)
	[PHP]sudo mount -t cifs //192.168.1.15/Documents /media/documents -o username=myuser,password=mypassword,uid=1000,mask=000[/PHP]
4- unmount the folder
	[PHP]sudo smbumount /media/documents[/PHP]
5- edit the /etc/fstab
	sudo open gedit etc/fstab
6- add the mount point
	# //IP/folder		/place		type	options (add the same option in the server side + credentials)
	#//192.168.1.15/Data1 /mnt/data1/	smbfs	auto,dev,exec,rw,sync,user,credentials=/root/.credentials   0 1

	[PHP]//192.168.1.15/data1	/mnt/data1/	smbfs	auto,dev,exec,rw,sync,user,credentials=/root/.credentials   0 1
	//192.168.1.15/documents /mnt/documents/smbfs	auto,dev,exec,rw,sync,user,credentials=/root/.credentials   0 1
	//192.168.1.15/music 	/mnt/music/	smbfs	auto,dev,exec,rw,sync,user,credentials=/root/.credentials   0 1
	//192.168.1.15/pictures	/mnt/pictures/	smbfs	auto,dev,exec,rw,sync,user,credentials=/root/.credentials   0 1
	//192.168.1.15/videos	/mnt/videos/	smbfs	auto,dev,exec,rw,sync,user,credentials=/root/.credentials   0 1[/PHP]
7- save /etc/fstab and close it
8- you can try ([PHP]sudo mount -a[/PHP]) to mount it all 
9- restart[PHP]sudo reboot[/PHP]
you can add some sortcut to this mount in your home

---

