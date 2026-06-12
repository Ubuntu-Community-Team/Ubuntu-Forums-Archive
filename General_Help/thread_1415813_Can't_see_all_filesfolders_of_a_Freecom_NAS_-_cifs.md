---
title: "Can't see all files/folders of a Freecom NAS - cifs problem?"
date: 2010-02-25
forum: General Help
---

### Post by -Robert- on 2010-02-25
I own a [Freecom NAS]("http://www.freecom.com/ecproduct_detail.asp?ID=3402&CatID=8020&sCatID=1146195&ssCatID=1146196") which is attached to a [SMC router]("http://www.frontierpc.com/ProductDetails.aspx?eId=1010536898") (SMCWBR-14N).
 I can approach the drive just fine by opening *Places > Network* but I can't view all content, some files/folders just seem to hide themselves.
 When I approach the drive under XP there's no problem and I can see all content.
 The filesystem type of the drive is _cifs_ and when I choose "properties" by right-clicking on a opened share I see this: [URL="http://i50.tinypic.com/28sas9c.png"]
[/URL]
[URL="http://i50.tinypic.com/28sas9c.png"]
[/URL]
[[IMG]http://i50.tinypic.com/28sas9c.png[/IMG]]("http://i50.tinypic.com/28sas9c.png")
 

 I found this topic and followed the instructions: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
 

 
[LIST]
[*]I installed *smbfs*
[*]I made a mount point
[*]I tried to manually mount the shared folder (the samba share does not require a password)
[/LIST]
 

 The results:
 

```
robert@PCRWUBUNTU:~$ sudo mount -t cifs //192.168.2.151/robert /home/robert/mount -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 
 mount error(5): Input/output error 
 Refer to the mount.cifs(8) manual page (e.g.man mount.cifs) 

``````
robert@PCRWUBUNTU:~$ sudo mount -t cifs //fnd/robert /home/robert/mount -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 
 mount error: could not resolve address for fnd: No address associated with hostname 
 No ip address specified and hostname not found 

``````
robert@PCRWUBUNTU:~$ sudo mount //192.168.2.151/robert /home/robert/mount 
 Password:  
 mount error(5): Input/output error 
 Refer to the mount.cifs(8) manual page (e.g.man mount.cifs) 
 
```I Googled for possible solutions and searched in the man pages but I really don't know what's going wrong and how I should fix this.
Could someone offer me some assistance? Thanks in advance.
 

 Robert

---

### Post by -Robert- on 2010-02-26
I finally found the solution:

I added my NAS to /etc/hosts, that way I can also mount the drive by it's name instead of only by IP adress.

In 9.04 I had to add the option *nounix*.

```
sudo mount -t cifs //fnd/robert /media/fndrobert/ -o guest,nounix,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```This didn't work out for 9.10, I also had to add the option *noserverino* to successfully mount my folder on the NAS.

```
sudo mount -t cifs //fnd/robert /media/fndrobert/ -o guest,nounix,rw,noserverino,iocharset=utf8,file_mode=0777,dir_mode=0777 
```Right now I can view all my folders/files so my problem is solved. :)

---

### Post by Her Ghost on 2010-02-27
Thanks for this - I've just spent all day trying to get this to work and your solution was the only one that worked and it is so much simpler than the rest!

---

### Post by -Robert- on 2010-02-27
Glad to hear that it also worked out for you. :)

---

### Post by JonEK90 on 2010-11-26
I just wanted to add my thanks as I have been trying to get this to work on and off for a while.

My problem was that my mount command was failing:
```
sudo mount -t cifs //fnd/Public /mnt/fndPublic -o user=jon,password=,noexec,rw,_netdev,noperm
mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```But your options work:
```
sudo mount -t cifs //fnd/Public /mnt/fndPublic/ -o guest,nounix,rw,noserverino,iocharset=utf8,file_mode=0777,dir_mode=0777

```Other threads suggest it is something to do with permissions which cannot be changed on this NAS.

Now, will I be able to back up to that dir?... ;)

I hope others hitting my error will also find this solution.

---

