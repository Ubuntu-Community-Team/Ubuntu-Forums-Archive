---
title: "Mount NAS share in fstab"
date: 2010-09-03
forum: General Help
---

### Post by gldearman on 2010-09-03
Hi, everyone,

I have a router that supports NAS; that is, you can plug a USB drive directly into the router, and it becomes a Windows share.

I can manually mount the NAS share and use it properly.  But, I would like to have it automatically mount on startup.  The main reason for this is to assign it a proper mount point so that I can access it from the command line, since I'm having trouble doing that after I mount it manually.

To mount it manually, I go to Places > Connect to Server, select the "Windows Share" service type, and enter "//192.168.1.1/USB_Storage" as the server name.  The server name is supposed to be "//readyshare/USB_Storage," but that does not work, so I used the IP address.

I would like to mount this drive at /mnt/readyshare.  So, I followed (I thought) the instruction in [this document]("https://help.ubuntu.com/community/MountWindowsSharesPermanently").

[LIST]
[*]I created the directory /mnt/readyshare
[*]I assigned myself a samba password with smbpsswd
[*]I created a group "readyshare" with the GID 1010
[*]I created a .smbcredentials file in my home directory
[*]I modified my /etc/fstab file.
[/LIST]

The .smbcredentials file reads:```

username=<my username>
password=<the password I created with smbpsswd
```

The line I added to my /etc/fstab is:
```

//192.168.1.1/USB_Storage /mnt/readyshare smbfs iocharset=utf8,credentials=/home/<my username>/.smbcredentials,dir_mode=0775,gid=1010 0 0

```

But, no dice.  The share does not mount.

What am I doing wrong?

Thanks!

---

### Post by gandaran on 2010-09-03
> To mount it manually, I go to Places > Connect to Server, select the "Windows Share" service type, and enter "//192.168.1.1/USB_Storage" as the server name. The server name is supposed to be "//readyshare/USB_Storage," but that does not work, so I used the IP address.
after mounting the drive have you tried bookmarking it in nautilus?
next time you just click the bookmark in nautilus to open the drive.
about the fstab option sorry I cant help, I have never tried it as I don't need to.

---

### Post by gldearman on 2010-09-03
> **gandaran said:**
> after mounting the drive have you tried bookmarking it in nautilus?
next time you just click the bookmark in nautilus to open the drive.

Yes, I have a Nautilus bookmark for the share, so that I can access it in one click.  But that does not appear to create a real mount point for the share.  I can't figure out how to access it from the command line.

---

### Post by StuartN on 2010-09-03
> **gldearman said:**
> Yes, I have a Nautilus bookmark for the share, so that I can access it in one click.  But that does not appear to create a real mount point for the share.  I can't figure out how to access it from the command line.

Your mount command should look something like:

```
sudo mount -t smbfs -o iocharset=utf8,credentials=/home/<my username>/.smbcredentials,dir_mode=0775,gid=1010 192.168.1.1:USB_Storage /mnt/readyshare
```

If you run that command in a terminal, then the error messages should guide you to the correct magical incantation. (My NAS prefers cifs). The same error messages may also appear somewhere in **dmesg** or your logs if you want to plough through them, but running mount directly is a quicker debug.

---

### Post by gldearman on 2010-09-03
> **StuartN said:**
> 
If you run that command in a terminal, then the error messages should guide you to the correct magical incantation. (My NAS prefers cifs). The same error messages may also appear somewhere in **dmesg** or your logs if you want to plough through them, but running mount directly is a quicker debug.

OK, I'll give that a try.

Before I read that, I had already tried something new.  I had decided that cifs might work better, so I ran:
```

sudo mount.cifs //192.168.1.1/USB_Storage /mnt/readyshare -o user=<my username>,password=<password  I set using smbpsswd>

```

I got back:
```

mount error(11): Resource temporarily unavailable

```

I enabled cifs debugging in /proc/fs/cifs/cifsFYI, and then tried it again.  Here is the error code from /var/log/debug:

```
Sep  3 21:40:08 brunhilda kernel: [  791.860910]  /build/buildd/linux-2.6.32/fs/cifs/cifsfs.c: Devname: //192.168.1.1/USB_Storage flags: 64 
Sep  3 21:40:08 brunhilda kernel: [  791.860924]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: CIFS VFS: in cifs_mount as Xid: 4 with uid: 0
Sep  3 21:40:08 brunhilda kernel: [  791.860940]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Username: <my username>
Sep  3 21:40:08 brunhilda kernel: [  791.860947]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: UNC: \\192.168.1.1\USB_Storage ip: 192.168.1.1
Sep  3 21:40:08 brunhilda kernel: [  791.860968]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Socket created
Sep  3 21:40:08 brunhilda kernel: [  791.864739]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: sndbuf 16384 rcvbuf 87380 rcvtimeo 0x6d6
Sep  3 21:40:08 brunhilda kernel: [  791.864852]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Existing smb sess not found
Sep  3 21:40:08 brunhilda kernel: [  791.864872]  /build/buildd/linux-2.6.32/fs/cifs/cifssmb.c: secFlags 0x7
Sep  3 21:40:08 brunhilda kernel: [  791.864881]  /build/buildd/linux-2.6.32/fs/cifs/transport.c: For smb_command 114
Sep  3 21:40:08 brunhilda kernel: [  791.864885]  /build/buildd/linux-2.6.32/fs/cifs/transport.c: Sending smb:  total_len 82
Sep  3 21:40:08 brunhilda kernel: [  791.864984]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Demultiplex PID: 2944
Sep  3 21:40:08 brunhilda kernel: [  791.874468]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: rfc1002 length 0x65
Sep  3 21:40:08 brunhilda kernel: [  791.874516]  /build/buildd/linux-2.6.32/fs/cifs/cifssmb.c: Dialect: 2
Sep  3 21:40:08 brunhilda kernel: [  791.874530]  /build/buildd/linux-2.6.32/fs/cifs/cifssmb.c: negprot rc 0
Sep  3 21:40:08 brunhilda kernel: [  791.874535]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Security Mode: 0x3 Capabilities: 0x8003f5 TimeAdjust: 28800
Sep  3 21:40:08 brunhilda kernel: [  791.874540]  /build/buildd/linux-2.6.32/fs/cifs/sess.c: sess setup type 2
Sep  3 21:40:08 brunhilda kernel: [  791.874656]  /build/buildd/linux-2.6.32/fs/cifs/transport.c: For smb_command 115
Sep  3 21:40:08 brunhilda kernel: [  791.874660]  /build/buildd/linux-2.6.32/fs/cifs/transport.c: Sending smb:  total_len 242
Sep  3 21:40:08 brunhilda kernel: [  791.882526]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Reconnect after unexpected peek error 0
Sep  3 21:40:08 brunhilda kernel: [  791.882536]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Reconnecting tcp session
Sep  3 21:40:08 brunhilda kernel: [  791.882540]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: State: 0x3 Flags: 0x0
Sep  3 21:40:08 brunhilda kernel: [  791.882587]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Post shutdown state: 0x3 Flags: 0x0
Sep  3 21:40:08 brunhilda kernel: [  791.882640]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Socket created
Sep  3 21:40:08 brunhilda kernel: [  791.883039]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: sndbuf 16384 rcvbuf 87380 rcvtimeo 0x6d6
Sep  3 21:40:08 brunhilda kernel: [  791.883067]  /build/buildd/linux-2.6.32/fs/cifs/transport.c: marking request for retry
Sep  3 21:40:08 brunhilda kernel: [  791.883071]  /build/buildd/linux-2.6.32/fs/cifs/misc.c: Null buffer passed to cifs_small_buf_release
Sep  3 21:40:08 brunhilda kernel: [  791.883077]  /build/buildd/linux-2.6.32/fs/cifs/sess.c: ssetup rc from sendrecv2 is -11
Sep  3 21:40:08 brunhilda kernel: [  791.883103]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: CIFS VFS: leaving cifs_mount (xid = 4) rc = -11
```

So, that gives me some things to google, but I'm still not sure what's going on here or why this isn't working.  I'll try the command you wrote, but my guess is it will give me roughly the same information.

Any help from anyone would be appreciated.  Thanks!

---

### Post by gldearman on 2010-09-03
> **StuartN said:**
> Your mount command should look something like:

```
sudo mount -t smbfs -o iocharset=utf8,credentials=/home/<my username>/.smbcredentials,dir_mode=0775,gid=1010 192.168.1.1:USB_Storage /mnt/readyshare
```

OK, I tried that, too.  Same error messages I got when I tried the mount.cifs command above.

---

### Post by StuartN on 2010-09-04
> **gldearman said:**
> OK, I tried that, too.  Same error messages I got when I tried the mount.cifs command above.

I think the relevant error is the SMB session error, which is probably the unavailable resource:

```
Sep  3 21:40:08 brunhilda kernel: [  791.864852]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Existing smb sess not found

```

Try the same mount command with options **-o username=<real NAS username>,password=<real NAS password>,uid=<Ubuntu username>** to see if you can mount without SMB.

---

### Post by Morbius1 on 2010-09-04
> **gldearman said:**
> Yes, I have a Nautilus bookmark for the share, so that I can access it in one click.  But that does not appear to create a real mount point for the share.  I can't figure out how to access it from the command line.
There is a real mount point , it's just in an unconventional place - developers sense of humor I guess.

It's at:
> /home/your_user_name/.gvfs/share_name on server_name
Note the "." before the gvfs - it's in a "hidden" directory.

---

### Post by gldearman on 2010-09-04
> **StuartN said:**
> I think the relevant error is the SMB session error, which is probably the unavailable resource:

```
Sep  3 21:40:08 brunhilda kernel: [  791.864852]  /build/buildd/linux-2.6.32/fs/cifs/connect.c: Existing smb sess not found

```

Really?  I had figured that was an all-clear; i.e., no existing session found, so the resource is not in use.  Which is why "Resource temporarily unavailable" is so confusing.

I'm basing that on [this page]("http://fixunix.com/samba/186367-samba-help-mount-error-11-cant-find-any-info.html"), where the user is also getting error 11.  But his log, instead of "Existing smb sess not found," reads:

```

Mar 21 19:14:32 wajlnx05 kernel: [2806892.931729] fs/cifs/connect.c:
Existing tcp session with server found
Mar 21 19:14:32 wajlnx05 kernel: [2806892.931736] fs/cifs/connect.c:
Existing smb sess found
....
Mar 21 19:14:32 wajlnx05 kernel: [2806892.931898] CIFS VFS: cifs_mount
failed w/return code = -11

```

> **StuartN said:**
> 
Try the same mount command with options **-o username=<real NAS username>,password=<real NAS password>,uid=<Ubuntu username>** to see if you can mount without SMB.

The problem is, the NAS is not password-protected, nor does it support usernames.

I checked the logs at /var/log/samba/, but the only messages in them are related to samba starting up when the machine is booted.

I tried disabling the machine's firewall, restarting, then connecting, just to eliminate that as a source of the problem.  Did not help.  I'm running low on ideas.

---

### Post by gldearman on 2010-09-04
> **Morbius1 said:**
> There is a real mount point , it's just in an unconventional place - developers sense of humor I guess.

It's at:

Note the "." before the gvfs - it's in a "hidden" directory.

I was excited for a minute there.  But, no, it isn't there.  My ~/.gvfs/ directory is entirely empty.

What I did to try and find it was to conntect to the NAS, and create on it a file with a silly name.  Then, I went to / and ran:

```

sudo find . -name "<silly file name I put on the NAS>"

```

No results.  So, if there's a hidden mount point somewhere in the system, I can't see it.

---

### Post by Morbius1 on 2010-09-04
DId you open nautilus and go to the share and the share opens up and you can view it's contents? If so the share is mounted in the .gvfs directory.

---

### Post by gldearman on 2010-09-04
> **Morbius1 said:**
> DId you open nautilus and go to the share and the share opens up and you can view it's contents? If so the share is mounted in the .gvfs directory.

Nope.  I tried it again just to be sure.  Opened the share in nautilus, messed around with it for a bit, then checked my .gvfs directory.  Empty.

---

### Post by Morbius1 on 2010-09-04
Okey Doke, sorry for the interruption.

**[COLOR=Blue]EDIT:[/COLOR]** Just out of curiosity, if you have nothing else to do , do you by any chance not have gvfs-fuse installed?

---

### Post by gldearman on 2010-09-04
> **Morbius1 said:**
> Okey Doke, sorry for the interruption.

**[COLOR=Blue]EDIT:[/COLOR]** Just out of curiosity, if you have nothing else to do , do you by any chance not have gvfs-fuse installed?

I do have gvfs-fuse installed.

---

### Post by khaidinh on 2011-01-24
Not sure if this will be helpful, but I have a Netgear WNDR3700 router with an external harddrive attached.  Here's how I was able to mount this drive via command line:

sudo mount -t cifs //<ip_of_rounter>/mediamusic ~/Music -o username=<username>,password=

---

### Post by jamie.nicholson on 2011-05-18
See my post on this thread for getting Samba share to work, perhaps viewing the Nas shares will help you get to your solution.

[http://ubuntuforums.org/showthread.php?p=10834714#post10834714](http://ubuntuforums.org/showthread.php?p=10834714#post10834714)

---

