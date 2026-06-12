---
title: "ssh to myworldbook for mp3 files"
date: 2010-04-18
forum: General Help
---

### Post by xigen on 2010-04-18
Hi,

I would like to back up my music collection to a Western Digital MyWorldbook 1TB using grsync and I am running into trouble.

The music collection is at:
/media/disk/wilson/Music/

The IP of my worldbook is:
192.168.1.67

I have SSH enabled.  However, when I try to start the back up ... the files (strangely) go to /home/wilson  ... a 10gb partition on my local disk.

The music collection lives on a 480 gb partition of my local disk.

..

The Western Digital back up I have has DRM .. it is awful.. don't buy one.  [www.wired.com/gadgetlab/2007/12/western-digital/](www.wired.com/gadgetlab/2007/12/western-digital/)

I worked through the how-to's and installed SSH and a nice web interface: [http://martin.hinner.info/mybook/](http://martin.hinner.info/mybook/)
...

1) How do I create a copy of ./Music on the western digital drive?

source: /media/disk/wilson/Music/
destination: ssh JOEJOE@192.168.1.67  
and in the directory:  /shares/internal/PUBLIC/SAMSAM

* I checked -- there is plenty of room in the destination directory
** from the terminal I have up .. it looks like SSH is working
*** As long as I am asking for everything -- how do I do a checksum ... or some method to automatically make sure that a file has transfered without errors. 

The picture shows Grsync and my latest attempt.

As always -- Thank you!

---

### Post by ju2wheels on 2010-04-18
```

scp -r /media/disk/wilson/Music/ JOEJOE@192.168.1.67:/shares/internal/PUBLIC/SAMSAM/

```

or

```

rsync -r /media/disk/wilson/Music/ JOEJOE@192.168.1.67:/shares/internal/PUBLIC/SAMSAM/

```

---

### Post by xigen on 2010-04-18
hmmm...

wilson@wilson-desktop:~$ scp -r /media/disk/wilson/Music/ JOEJOE@192.168.1.67:/shares/internal/PUBLIC/SAMSAM
JOEJOE@192.168.1.67's password: 
Could not chdir to home directory /home/JOEJOE: No such file or directory
scp: /shares/internal/PUBLIC/SAMSAM/Music: Permission denied

wilson@wilson-desktop:~$ rsync -r /media/disk/wilson/Music/ JOEJOE@192.168.1.67:/shares/internal/PUBLIC/SAMSAM/
JOEJOE@192.168.1.67's password: 
Could not chdir to home directory /home/JOEJOE: No such file or directory


suggestions?

---

### Post by ju2wheels on 2010-04-18
1. Does the user JOEJOE exist on the machine you are trying to ssh into?

2. Looks like you may also need to check your folder permissions on the destination machine and most likely make them world writable...

```

chmod a+w -R /destination/folder/

```

---

### Post by xigen on 2010-04-19
first -- Thank you.

Does JOEJOE exist?
[JOEJOE@MyBookWorld /]$ ls 
bin  etc   lib	    lost+found	mnt   opt   root  shares  tftpboot  usr
dev  home  linuxrc  man		none  proc  sbin  sys	  tmp	    var
[JOEJOE@MyBookWorld /]$ cd /shares/internal/PUBLIC
[JOEJOE@MyBookWorld PUBLIC]$ ls
Backup		Documents1009  Music   Sarah&Mario (D)	TAL	pictures102008
Davde - ManTra	Documents2     SAMSAM  Seeqpod stuff	Videos
[JOEJOE@MyBookWorld PUBLIC]$ chmod a+w -R SAMSAM
changing permissions of `SAMSAM': Operation not permitted
[JOEJOE@MyBookWorld PUBLIC]$ su
[root@MyBookWorld PUBLIC]# chmod a+w -R SAMSAM
[root@MyBookWorld PUBLIC]# exit
exit
[JOEJOE@MyBookWorld PUBLIC]$ 


2) It looks like changing permissions worked..

3) I am getting the error:
wilson@wilson-desktop:~$ rsync -r /media/disk/wilson/Music/ JOEJOE@192.168.1.67:/shares/internal/PUBLIC/SAMSAM/
JOEJOE@192.168.1.67's password: 
Could not chdir to home directory /home/JOEJOE: No such file or directory
^Crsync error: unexplained error (code 130) at rsync.c(544) [sender=3.0.5]
wilson@wilson-desktop:~$ 


suggestions?

Cheers...

---

### Post by xigen on 2010-04-19
I could not resist trying some ...stuff

[JOEJOE@MyBookWorld PUBLIC]$ rsync -r /media/disk/wilson/Music/ JOEJOE@192.168.1.67:/shares/internal/PUBLIC/SAMSAM/
Could not create directory '/home/JOEJOE/.ssh'.
The authenticity of host '192.168.1.67 (192.168.1.67)' can't be established.
RSA key fingerprint is 13:b9:74:d0:d9:72:7a:08:7f:bd:f1:91:eb:a9:a6:1d.
Are you sure you want to continue connecting (yes/no)? no
Host key verification failed.
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(463) [sender=2.6.8]

[JOEJOE@MyBookWorld PUBLIC]$ rsync -r /media/disk/wilson/Music/ /shares/internal/PUBLIC/SAMSAM/
rsync: link_stat "/media/disk/wilson/Music/." failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(892) [sender=2.6.8]

[JOEJOE@MyBookWorld PUBLIC]$ rsync -r wilson@192.168.1.64:/media/disk/wilson/Music/ /shares/internal/PUBLIC/SAMSAM/
ssh: connect to host 192.168.1.64 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: error in rsync protocol data stream (code 12) at io.c(463) [receiver=2.6.8]

---

### Post by xigen on 2010-04-20
It looks like I have SSH and rsync working .. however, I have a permissions issue...

rsync: stat "/shares/internal/PUBLIC/SAMSAM/Drum-and-Bass_Delirium-2008-VA/dnbmarch/Young_Ax-Higher_Ground-SAN004CD-2008-sour" failed: No such file or directory (2)
rsync: recv_generator: mkdir "/shares/internal/PUBLIC/SAMSAM/Eagles - Long Road Out Of Eden/Eagles - Long Road Out Of Eden (Disc 1)" failed: Permission denied (13)

[JOEJOE@MyBookWorld PUBLIC]$ ls -l
total 96
drwsrwsr-x  13 www-data www-data  4096 Aug 24  2008 Backup
drwsr-sr-x   6 www-data www-data  4096 Oct 25 13:21 Documents1009
drwsrwsr-x   7 www-data www-data  4096 Feb  2  2009 Documents2
drwsrwsrwx 549 www-data www-data 24576 Apr 19 04:49 SAMSAM
drwsr-sr-x   2 www-data www-data  4096 Oct 17  2009 TAL
drwsrwsr-x   4 www-data www-data  4096 Aug 23  2009 Videos
drwsr-sr-x  26 www-data www-data  4096 Jan 20 08:32 pictures102008
[JOEJOE@MyBookWorld PUBLIC]$ 

What permissions would you suggest that I change?

---

### Post by ju2wheels on 2010-04-22
See if you can login to your mybook as JoeJoe and create a random empty file in SAMSAM without getting a permission error. If you do get a permission error the next thing to change user owner/group of the SAMSAM folder to something that JoeJoe has access to.

---

### Post by xigen on 2010-04-26
well ....

I created a test file called test and saved it.   It looks like it worked.

drwsr-sr-x 2 www-data www-data      4096 Apr 19 04:46 modern jazz-VA
-rw-r--r-- 1 www-data www-data        19 Apr 26 16:33 test
drwsr-sr-x 2 www-data www-data      4096 Apr 19 04:46 the_knife_-_silent_shout
drwsr-sr-x 2 www-data www-data      4096 Apr 19 04:46 wired-VA
[JOEJOE@MyBookWorld SAMSAM]$ cat test 
tet test ties test
[JOEJOE@MyBookWorld SAMSAM]$ 

so... how could I use this information to move forward on my rsync issue?

---

### Post by xigen on 2010-04-28
Well -- I changed the source directory to a samba share ... and ... used just a simple copy to move the files.

right-click on folder, select 'Share' and make it a samba share. 

It worked.

cheers,

---

