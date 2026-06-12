---
title: "Permission Problem with Synchronization"
date: 2012-07-30
forum: General Help
---

### Post by omiazad on 2012-07-30
Hi,
I have a Western Digital NFS where I keep backup of my files. After switching to Ubuntu, I found 2 excellent file/folder Synchronization applications. But none of them are able to sync with NFS directly. So here is what I did, I mount the network location locally with the following command (to clarify that I have given write permission to the folder) -
```
sudo mount //192.168.192.13/Files/ /media/Net-Files/ -o username=user,password=pass,file_mode=0777,dir_mode=0777
``` and then I tried to sync with that folder.

Now after modifying a file, when I want to sync back, it gives the following errors

FreeFileSync-
[IMG]http://i45.tinypic.com/2a0ezbn.png[/IMG]

Unison-
[IMG]http://i47.tinypic.com/b4bz41.png[/IMG]

I can understand that this is a permission related problem. I tried to sync->modify->sync with a flash drive and there was no error, but this happens only with the NFS.

Do you know any solution for this?

---

### Post by LewisTM on 2012-07-30
It looks like you mounted your NAS with SMB (Windows share) instead of NFS. I don't know if that was intentional but chances are Unison won't be able to propagate Unix permissions to the NAS mounted as SMB.

What you can do is add [FONT="Courier New"]dontchmod = true[/FONT] to your Unison profile. Or work on properly mounting with the mount.nfs command.

Cheers!

---

### Post by omiazad on 2012-07-30
> **LewisTM said:**
> It looks like you mounted your NAS with SMB (Windows share) instead of NFS. I don't know if that was intentional but chances are Unison won't be able to propagate Unix permissions to the NAS mounted as SMB.

What you can do is add [FONT="Courier New"]dontchmod = true[/FONT] to your Unison profile. Or work on properly mounting with the mount.nfs command.

Cheers!

Well I was searching for a solution how to mount the share and that was the first working solution I found. As I'm not a geek, I just wanted to learn a solution that works. 

Can you please help me to learn how I can mount the partition as NFS? 

Also, if Linux chmod my files, will there be any problem to access them from Windows?

---

### Post by LewisTM on 2012-07-30
Sure thing buddy :)

Many NAS offer NFS or SMB as a way to access the files from client computers. For Linux NFS is usually a bit faster and will support permissions. SMB can work fine, only don't try to change the attributes. Changing perms on the NAS shouldn't affect Windows users accessing through SMB, the NAS will take control of the files and serve them transparently (at least it SHOULD).

For NFS add a line in your /etc/fstab like
```
192.168.192.13:/Files /media/Net-Files nfs defaults 0 2
```
and go from there, perhaps adding options [FONT="Courier New"]noauto,user[/FONT] to be able to mount the NAS on demand as a normal user. By default the NAS would be mounted a startup.
The command line should be 
```
mount.nfs 192.168.192.13:/Files /media/Net-Files
```

---

### Post by omiazad on 2012-07-30
> **LewisTM said:**
> Sure thing buddy :)

Many NAS offer NFS or SMB as a way to access the files from client computers. For Linux NFS is usually a bit faster and will support permissions. SMB can work fine, only don't try to change the attributes. Changing perms on the NAS shouldn't affect Windows users accessing through SMB, the NAS will take control of the files and serve them transparently (at least it SHOULD).

For NFS add a line in your /etc/fstab like
```
192.168.192.13:/Files /media/Net-Files nfs defaults 0 2
```
and go from there, perhaps adding options [FONT="Courier New"]noauto,user[/FONT] to be able to mount the NAS on demand as a normal user. By default the NAS would be mounted a startup.
The command line should be 
```
mount.nfs 192.168.192.13:/Files /media/Net-Files
```

Thanks once again. But my NAS needs username/password to access. Can you please suggest how to put that? 

I also didn't get the noauto,user option. :(

---

### Post by LewisTM on 2012-07-30
If it needs a username/password that means it only supports Windows-style access, so forget about NFS.

Just go as you did at the beginning and add the [FONT="Courier New"]dontchmod = true[/FONT] line to your /home/<user>/.unison/<profile>.prf

---

### Post by omiazad on 2012-07-30
> **LewisTM said:**
> If it needs a username/password that means it only supports Windows-style access, so forget about NFS.

Just go as you did at the beginning and add the [FONT=Courier New]dontchmod = true[/FONT] line to your /home/<user>/.unison/<profile>.prf

Looks like I didn't have any luck with this solution. The error remains same.

About the NFS, when I try to browse the network share it shows me the share without entering into the Windows share portion -
[IMG]http://i49.tinypic.com/x52p06.png[/IMG]

I must thank you for giving your valuable attention to this issue. Please suggest what I can do now.

---

### Post by omiazad on 2012-07-30
Just tried a new Java based application called [DirSync Pro,]("http://www.dirsyncpro.org/download.html") and looks like it do not have all those problems. Closing this thread as my job is done. :)

---

