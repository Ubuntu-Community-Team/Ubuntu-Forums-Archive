---
title: "Samba share frustrations w/Server 11.10"
date: 2011-12-28
forum: General Help
---

### Post by paulgj on 2011-12-28
Hello,

am trying to share a directory from Ubuntu Server 11.10 using the directions at [http://linhost.info/2010/05/simple-samba-server-configuration/]("http://linhost.info/2010/05/simple-samba-server-configuration/") but I cannot write anything to the shares from my Windows 7 boxes.  I get the "You need permission to perform this action" message whenever I try and put anything in the mapped drive.
In the smb.comf file I have the following settings (everything else is default)

```

security = share

[share]
 path = /home/paul/data
 browseable = yes
 guest ok = yes
 read only = no
 create mask = 0755

```

I'm tearing my hair out trying to find a solution as this seems like a really basic share.

Any help would be much appreciated.

Thank you!

---

### Post by Morbius1 on 2011-12-28
Without any other information I suspect the /home/paul/data directory doesn't have the correct permissions for an anonymous client to write. 

Did you follow the part in the HowTo that made you change ownership of the shared directory:
> sudo chown nobody.nogroup /media/mydrive/myshare/If this is truly a server then that should work but in you're particular case you have the shared folder within paul's home directory so changing ownership means paul will have only read access to the folder on the server itself.

Another way to achieve the same result is to change permissions not ownership of the shared folder:
```
chmod 777 /home/paul/data
```Or if there is going to be access to this folder from both a remote guest on the LAN and paul from within the server you might want to change the share definition to this:
> [share]
 path = /home/paul/data
 browseable = yes
 guest ok = yes
 read only = no
[COLOR=Blue]force user = paul[/COLOR]And change the ownership back to paul:
```
chown paul /home/paul/data
```The remote guest ( nobody ) will be converted to "paul" for that share so when he saves a file it will save with owner = paul and both local and remote users will have access.

---

### Post by paulgj on 2011-12-28
Thanks for the reply.  Is there something special about shares within the home directory?  I also set up a share outside of the home directory with the same permissions and I also couldn't write to it from an external client.  I'm not at home right now so I can't try your suggestions but it sounds like the step to change ownership basically made the share read only.

I'm a relative novice with Linux so am still learning the ins and outs of permissions, authority etc.


Thanks!

---

### Post by Morbius1 on 2011-12-28
By default in Linux a newly created directory will have permissions of 755 or drwxr-xr-x. The "7" allows the owner to read and write. The "5"'s allow group and everyone else to read only. Your share is set up to allow guests to write but to Linux a "guest" is "everyone else". Samba cannot override Linux file permissions so Linux will prevent a write to everyone other that the owner so you need to change permissions on the shared directory.

The only reason I brought up the home directory is becase the HowTo you are using is from the perspective of a true server - a machine whose only function is to provide shares to everyone else on the lan. But in a typical home network samba is being used in a more peer-to-peer manner - Bob wants to share a directory with Edna. 

In a true server the machine needs to be booted but does not necessarily have to be logged into to work. In a home network where the folder being shared is also on Bob's workstation, Bob needs access to the folder as well so something like a "force user" needs to be used.

---

### Post by paulgj on 2011-12-28
Interesting,  i'm currently reading up on *chgmod *and permissions in more detail.  I guess this share will be more like a NAS in this situation, a common storage area that I can read and write to from any computer on the LAN.  At some point I would also like to make the share available from outside the LAN.

thanks again for your comments, I appreciate your knowledge and willingness to share.

---

### Post by Baconator507 on 2011-12-28
> **paulgj said:**
> Thanks for the reply.  Is there something special about shares within the home directory?

I think you might have a problem if the home directory is encrypted...

---

### Post by paulgj on 2011-12-28
> **Baconator507 said:**
> I think you might have a problem if the home directory is encrypted...

I'm pretty sure I didn't select that option during install.

---

### Post by CharlesA on 2011-12-28
What are the permissions of the directory you are trying to share?

```
ls -ld /path/to/directory/being/shared/
```

I'm guessing it's a permissions issue as well.

Also: What error are you getting on the Windows box/ Path not found, or access denied?

---

### Post by paulgj on 2011-12-28
> **CharlesA said:**
> What are the permissions of the directory you are trying to share?

```
ls -ld /path/to/directory/being/shared/
```

I'm guessing it's a permissions issue as well.

Also: What error are you getting on the Windows box/ Path not found, or access denied?

thanks, yes it was a permissions issue.  The step in the instructions changed the permissions on the directory which removed write access for anyone except the owner "nobody". I recreated the directory as myself and the default permissions work well with my user ID.

This is the error I was getting in Windows when trying to write something to the share:

[IMG]http://img856.imageshack.us/img856/1739/win7sharewriteerr.png[/IMG]

thanks everyone for your help troubleshooting this.  I also learned everything I could want to know about file permissions :o

---

### Post by CharlesA on 2011-12-29
Thought that was the error you were getting. Glad you got it sorted. :)

Don't forget to mark the thread as Solved from thread tools.

---

