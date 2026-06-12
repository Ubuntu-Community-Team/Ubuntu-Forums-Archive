---
title: "Permissions issue with LibreOffice .lck files in LO-Base"
date: 2011-02-17
forum: General Help
---

### Post by EarlsFurniture on 2011-02-17
I've recently converted two Ubuntu 10.04 (one 64, one 32bit) machines to LibreOffice.  We've used OpenOffice.org since early 2.x
 The issue is a database file created in OOo and now needing to be  accessed in LO.  As far as I know, there shouldn't be any issue with  file compatibility.
 On the 64 bit machine, (a Ubuntu server installation - not headless)  the file opens with no trouble and is fully accessible.  (forms,  reports, tables, etc.)
 However, on the 32 bit machine, trying to access the file over the  network on the server via samba (because we also have Windows machines  on the network, so I serve it all up via samba) I am able to open the  database, but get the following error when trying to access any table,  form or report:
 The connection to the data source "Mattress Prices" could not be 
established.

SQL Status: 08001

Error code: -1

The database is already in use by another process: lockFile: 
org.hsqldb.persist.LockFile@ce62df2f[file 
=/mnt/samba/documents/Databases/Mattress Prices.odb.lck, exists=true, 
locked=false, valid=false, ] method: openRAF reason: 
java.io.FileNotFoundException: /mnt/samba/documents/Databases/Mattress 
Prices.odb.lck (Permission denied)
I tried accessing this file with Nautilus open showing permissions  so I could see what was going on.  Apparently, LO-Base is creating the  lock file with -rw-r--r-- permissions when any file created in that  directory *should* be full permissions.  (the directory and all files in it are owned by  "nobody:nogroup" with ugoa+rxw permissions so there are no issues with  all users creating, deleting and executing files on their machines from  the server directories.  Without this permission and ownership setup, I  have nightmares.)  So LO is apparently creating the lock file with owner  "nobody" and *limited* permissions, and the logged in user appears as not  being the owner or have access to the lockfile and LO seems to think this lock file belongs to someone *else* (nobody) and so I can't access the file at all other than opening it.
 This wasn't a problem before I changed the server to LO and accessed  the database with it. (this did happen post installing LO on the server,  with OOo on the client machine trying to access that file and then with  LO, the same result)


I've posted this to the LO forum, but it may not be an issue with that software and I suspect it is a permissions issue on my end.


*note, OOo 3.2 on a winXP machine can access the file just fine. So this really looks like a permissions issue with the offending Ubuntu 10.04 machine.


 Any help is greatly appreciated.

---

### Post by bryanl on 2011-02-17
You make me think of 2 bugs that have caused me grief with OOo and LAN shares.

If your 64 bit machine is doing OK and the 32 not and it's mounted via samba, see if you can access via gvfs - open the share via nautilus places->network, and that will get you a ~/.gvfs/share mountpoint

you can also try the 'nobrl' mount option for mount.cifs - that one is an OOo bug that handles the leftover .lck file - I have had to manually delete those files until I added this option.

I use autofs to mount the shares and the mountopts in auto.smb I use is 
 -- mountopts="-fstype=cifs,nounix,nobrl" -- autofs is problematic as well as I have had to use an auto.smb from several versions back to make it work.

these things get very frustrating.

---

### Post by EarlsFurniture on 2011-02-17
Thanks!

I'll give those suggestions a shot and see what happens.

I don't understand though why it worked so well just a week ago with the only thing being different was that I changed to LO from OOo.  Perhaps there was a bad regression in LO?

---

### Post by EarlsFurniture on 2011-02-17
So the .gvfs mount works fine.

Any way to automount that way on startup?

I'd like the user not to have to navigate to network -> main ->  server -> documents -> databases and then select the file every  time he needs it in a new session.  Putting a link on his desktop would  be fine, but of course, the mount would still have to have been done for  it to work.

I'll try the other methods listed and see what happens.

Note, I'm also having an automount problem on this same machine.  The  smb shares (where this database resides) will not mount on login, and I  have to use [FONT=Lucida Console]sudo mount -a.[/FONT]  (and enter the password for each share,  rather than just once, very odd)

Perhaps if I solve the original automount problem that might fix the other one with the database file?

Here's a sample share mount from fstab. (I have six of these)

[FONT=Lucida Console]# share-name on /mnt/samba/share-name
//serverIP/share-name /mnt/samba/share-name smbfs defaults    0    0 [/FONT]

note, I also can't use the server 'name' but rather am forced to use the IP address for this to work.  (no biggie, just a quirk)

---

### Post by EarlsFurniture on 2011-02-25
It seems the problem was with smbfs.

A switch to cifs solved the problem.  (though I thought cifs was deprecated, looks like that was done a little too soon)

Here is the thread that solved the issue:

[http://ubuntuforums.org/showthread.php?t=1690515](http://ubuntuforums.org/showthread.php?t=1690515)

---

