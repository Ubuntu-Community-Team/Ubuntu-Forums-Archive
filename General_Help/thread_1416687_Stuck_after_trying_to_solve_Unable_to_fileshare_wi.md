---
title: "Stuck after trying to solve: Unable to fileshare with Nx Nomachine."
date: 2010-02-26
forum: General Help
---

### Post by fisheater on 2010-02-26
Problem: Unable to fileshare with Nx Nomachine.

Setup: Laptop client 9.04 to desktop server 9.04

[[IMG]http://img710.imageshack.us/img710/4567/screenshotedo.png[/IMG]](http://img710.imageshack.us/i/screenshotedo.png/)

Followed this tutorial: [http://www.nomachine.com/howto/file-sharing.php](http://www.nomachine.com/howto/file-sharing.php)
No success.

Then tweaked it via: [https://lists.ubuntu.com/archives/ubuntu-users/2008-November/166974.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-November/166974.html)
Summary of this link: followed the above link, didnt work. Installed smbfs on server, it worked.
I tried the same, didnt work.

Went deeper under the hood with gedit...

/usr/NX/ect/server.cfg - nothing on file sharing 
/etc/samba/smb.conf -  not even sure what I am looking for.

Summary:
Well beyond my understanding of this, I suspect it is a simple fix &#8211; permissions or some how changing my Nx Client login.

Suggestions welcome.

Thanks!

FE

Update: Thanks to Steve for this link: [http://www.nomachine.com/ar/view.php?ar_id=AR08D00413](http://www.nomachine.com/ar/view.php?ar_id=AR08D00413)

Digging down into: configuration file /usr/NX/etc/node.cfg

Making the following changes:
both, either SMB and CIFS protocol are supported, this is the default value.
smbfs, only SMB protocol is supported.
cifs, only CIFS protocol is supported.
none, no network file-sharing protocol is supported.

Other NX node configuration keys are:

    * To specify the path of base directory where the NX node should mount
       shares exported by the user

      ShareBasePath = "$(HOME)/MyShares"

    * To allow the node to use privileged scripts to manage the shares

      EnableFileSharing = "1"

---

### Post by fisheater on 2010-02-28
update: no luck with file sharing.

modifications to /usr/NX/etc/node.cfg:

Making the following changes:

#both, either SMB and CIFS protocol are supported, this is the default #value.
#smbfs, only SMB protocol is supported.
#cifs, only CIFS protocol is supported.
#none, no network file-sharing protocol is supported.

MountShareProtocol = "both"

#To specify the path of base directory where the NX node should mount
shares exported by the user

ShareBasePath = "$(HOME)/MyShares"

#To allow the node to use privileged scripts to manage the shares

EnableFileSharing = "1" 

Suggestions? (for this problem, or another, more appropriate forum?)

TY 

FE

---

### Post by fisheater on 2010-02-28
The misadventure continues.

1. Checking to see if my samba server was working on client.

```
samba restart 
```(this showed server not running)
- needed to install samba4.
- oops this removed ubuntu-desktop, smbclient, samba-common, winbind.
- seems that this was taking me down the wrong path.
- when i restarted my computer, my Nx client couldn't see any drives to share... 
- reinstalled samba, winbind, smbclient.
- back to square 1.

2. Trying SWAT to see if it give me any more insight.
version 3.3.2
smbd: running
nmbd: running
winbinddd: running

No active connections, shares, open files.

Stuck.

Problem #3. 
My USB portable version of Nx client doesn't seem to have the ability to share mount file shares. (dynamic link error).

And do it goes.

Ty 

FE

---

### Post by fisheater on 2010-02-28
update:

Tried to log in from WinXp + Nx Client and IT WORKED!

Then tried ubuntu to ubuntu with no luck. Still looking.

FE

---

### Post by Baneblade on 2010-03-05
I'm getting the exact same error. Looking for a work-around too. I'll post here if I discover anything you haven't so far..

---

### Post by Baneblade on 2010-03-05
I think i may have found the problem.
From "man mount cifs"

> The non-superuser mounts.
              Normally,  only  the superuser can mount file systems.  However,
              when fstab contains the user option on a line, anybody can mount
              the corresponding system.
 Thus, given a line

             /dev/cdrom  /cd  iso9660  ro,user,noauto,unhide

              any  user  can  mount the iso9660 file system found on his CDROM
              using the command

                     mount /dev/cdrom

              or

                     mount /cd

Im going to try and edit fstab now and see if that fixes it.

---

### Post by Baneblade on 2010-03-05
Not really too sure what I'm supposed to add there exactly, but nothing I have tried so far has worked.

The error that comes up points to that as the cause however, so im fairly certain that given the correct permission via fstab the shares will work just fine.

Just need someone familiar with fstab to point us in the right direction.

---

### Post by fisheater on 2010-03-06
Dang.

That was a good approach, too bad it hasn't yet worked.

What puzzles me is that my winXP client to ubuntu server works. That suggests that my ubuntu server is set up correctly. when i try ubuntu to ubuntu it wont work... so that leads me to think that my laptop with ubuntu client is the issue (or a permission issue). 

Still stuck though.

My current workaround: gmail open on server and client and send files via that. bigger files sent via [http://www.transferbigfiles.com/](http://www.transferbigfiles.com/). Cumbersome but it works.

Thanks for the interest, I'll let you know if I find anything.

FE

---

### Post by Baneblade on 2010-03-06
I'm guessing that is because XP is always in "superuser" mode. Windows systems only began to emulate the 'nix setup of temporary root permissions for admins from Vista onwards.
Having said that, I have tried running NXClient as root and it didn't even mount the shares. Though it didn't throw up errors either.. so I'm confused about that one.

I'm thinking about posting another thread to see if someone can help us with the correct input and syntax for fstab. Will probably do it tomorrow if i can come up with it on my own tonight.

---

### Post by louieb on 2010-03-06
CIFS is great for sharing with a server running windows [Mount samba shares with utf8 encoding using cifs - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=288534&highlight=samba")

But if you going *nix to *nix you really should look at NFS.  Setup is a little bit of a pain, but once done - using the share is just like the data was in your home folder. [HOWTO: NFS Server/Client - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs")

---

### Post by Baneblade on 2010-03-08
Hmm, I've read through those links carefully and cant see how to implement anything in there to solve our current predicament. My understanding is that NXclient is supposed to mount any local shares on the remote server automatically after it authenticates the session. This doesn't seem to be happening due to some permissions error that i cant figure out.

For clarification the error is:
> Mount error(13). Permission denied. Refer to mount.cifs( 8 ) manual page.

---

### Post by pricetech on 2010-03-08
Is SCP an option for you ??  Since SSH is already running, connecting should be as simple as "Connect to Server" under Places.  (That's where it is in Hardy)

It seems I was able to make file sharing work in NX under winders, but didn't try it under Linux.  I wasn't doing anything but trying it anyway so I didn't pursue it.

---

### Post by Baneblade on 2010-03-10
SCP doesnt seem to work, although im not 100% sure on what im supposed to put into the fields. I have tried a few different configurations and nothing has worked so far.

This shouldn't be necessary however, as NXClient is supposed to be able to do this automatically, and from Windows-> Ubuntu, it can. This seems to be Ubuntu -> Ubuntu permissions problem.

---

