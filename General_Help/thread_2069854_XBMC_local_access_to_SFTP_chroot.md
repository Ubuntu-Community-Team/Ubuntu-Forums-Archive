---
title: "XBMC local access to SFTP chroot?"
date: 2012-10-11
forum: General Help
---

### Post by Zaggy on 2012-10-11
Hi, I've set up SFTP for transferring files and installed XBMC.
Attached TV/monitor to the machine, XBMC runs fine.
Can send files over by SFTP as well, cool!

How should I give the XBMC logged in user access to the local SFTP chroot folder?

---

### Post by TheFu on 2012-10-11
I'm confused.  Why not just remote mount the place where the files are stored with either CIFS, Samba or NFS?  No need to transfer the files at all if they are on the same LAN.

If you need to transfer the files ... want a local copy for the library, why not transfer them into the final directory and let XBMC know about it as a **Source**?  XBMC just needs read-access to those files, so that's an easy **chmod -R** command. I'm sure the GUI has a way to do it too.  Just change the permissions.

Is there a reason to use a chroot folder?  Normally that is only done when files are made available on the interent from dangerous services like DAV, FTP, or for other non-file services known to be constantly cracked over the years like BIND or sendmail.

---

### Post by Zaggy on 2012-10-11
> **TheFu said:**
> I'm confused.  Why not just remote mount the place where the files are stored with either CIFS, Samba or NFS?  No need to transfer the files at all if they are on the same LAN.

If you need to transfer the files ... want a local copy for the library, why not transfer them into the final directory and let XBMC know about it as a **Source**?  XBMC just needs read-access to those files, so that's an easy **chmod -R** command. I'm sure the GUI has a way to do it too.  Just change the permissions.

Is there a reason to use a chroot folder?  Normally that is only done when files are made available on the interent from dangerous services like DAV, FTP, or for other non-file services known to be constantly cracked over the years like BIND or sendmail.

Thanks for the response!
SFTP is for remote use.
Hadn't thought about mounting it separately yet, thanks!

---

### Post by TheFu on 2012-10-11
> **Zaggy said:**
> Thanks for the response!
SFTP is for remote use.
Hadn't thought about mounting it separately yet, thanks!

So you were able to setup a** chroot** environment AND get **sftp** working inside it, but not able to run **chmod**?  That doesn't sound right. 

Are you certain you setup **chroot**?  

I'm not saying this isn't possible, but that it seems really odd to be able to do the complex **chroot** work and not know about **chmod**.

If the files are coming over the internet, then you shouldn't try mounting them. The streaming performance won't work for any video formats.

Another option is to use a softlink to connect those files to someplace under the XMBC known "TV" and "Movie" locations.

---

### Post by Zaggy on 2012-10-11
> **TheFu said:**
> So you were able to setup a** chroot** environment AND get **sftp** working inside it, but not able to run **chmod**?  That doesn't sound right. 

Are you certain you setup **chroot**?  

I'm not saying this isn't possible, but that it seems really odd to be able to do the complex **chroot** work and not know about **chmod**.

If the files are coming over the internet, then you shouldn't try mounting them. The streaming performance won't work for any video formats.

Another option is to use a softlink to connect those files to someplace under the XMBC known "TV" and "Movie" locations.


Not a complex chroot but using the sftp chroot functionality in sshd:
Match group sftponly
        ChrootDirectory /storage/netdrive
        X11Forwarding no
        AllowTcpForwarding no
        ForceCommand internal-sftp

This in combination with [eldos netdrive]("www.eldos.com/sftp-net-drive/") works rather well.
I guess I could have it XBMC connect over ssh via a local mount.

---

### Post by TheFu on 2012-10-11
I didn&#8217;t know that ssh had a built-in chroot - very cool. Thanks!

So the netdrive is a NAS and XBMC is the sftp server that drops files on the NAS. Very cool. Just setup another mount using CIFS, samba or NFS to the NAS storage.  Don't bother with sshfs, it is too slow.  Any FUSE file system will probably be too slow.

---

### Post by Zaggy on 2012-10-11
> **TheFu said:**
> I didn’t know that ssh had a built-in chroot - very cool. Thanks!

So the netdrive is a NAS and XBMC is the sftp server that drops files on the NAS. Very cool. Just setup another mount using CIFS, samba or NFS to the NAS storage.  Don't bother with sshfs, it is too slow.  Any FUSE file system will probably be too slow.

Actually it's all on the same box.
I'm new to this so please let me know if it's setup in a silly way.
os on ssd, raid 5 mounted to /storage
/storage/netdrive is the chroot

Getting permission denieds when attempting to remote mount

---

### Post by TheFu on 2012-10-11
Output from **df -k** please. Only need the /dev/ stuff, not the virtual file systems.

---

### Post by Zaggy on 2012-10-11
> **TheFu said:**
> Output from **df -k** please. Only need the /dev/ stuff, not the virtual file systems.

```
df -kh
df: `/var/lib/lightdm/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/md1        103G   89G  8.7G  92% /
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           1.6G  1.3M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.8G  684K  3.8G   1% /run/shm
/dev/md2        5.5T  120G  5.3T   3% /storage
```

---

### Post by TheFu on 2012-10-11
So under /storage/netdrive you have TV/, Movie/, Music/ directories?
If you trust the people with sftp access, then I'd just use those directly from XBMC. You don't need to mount them, since /storage is already mounted to the computer.  Just point XMBC sources to the specific TV, Movie, Music subdirs.

[http://blog.jdpfu.com/2011/02/21/xbmc-tips](http://blog.jdpfu.com/2011/02/21/xbmc-tips) explains more about the needed directory setup. I'm sure there are lots of other articles about that elsewhere.  Don't fight the directory structure that XBMC likes.

---

### Post by Zaggy on 2012-10-11
> **TheFu said:**
> So under /storage/netdrive you have TV/, Movie/, Music/ directories?
If you trust the people with sftp access, then I'd just use those directly from XBMC. You don't need to mount them, since /storage is already mounted to the computer.  Just point XMBC sources to the specific TV, Movie, Music subdirs.

[http://blog.jdpfu.com/2011/02/21/xbmc-tips](http://blog.jdpfu.com/2011/02/21/xbmc-tips) explains more about the needed directory setup. I'm sure there are lots of other articles about that elsewhere.  Don't fight the directory structure that XBMC likes.


The thing is, for the sshd chroot to work, the top directories /storage/netdrive have to be set up with the following rights:

```

[drwxr-xr-x root     root    ]  storage/storage
&#9492;&#9472;&#9472; [drwxr-s--- root     sftponly]  netdrive
    &#9492;&#9472;&#9472; [drwxrwsr-x root     sftponly]  netdrive
```

So for the chrooted SFTP only user it works, but other users can't cd into it.

I tried mounting with sshfs and the SFTP user but running into access denieds.

---

### Post by TheFu on 2012-10-11
sshfs is too slow for streaming video, even if it worked.

At this point, I'd move those files out of the netdrive area into somewhere the XBMC user controls.  Sorry, but I don't fully understand what your directory structure stuff is showing.   Is there really a /storage/netdrive/netdrive/ directory?

The output from this command would be helpful so I can see the exact directory owner/group and mask permissions, if I'm missing the /s/n/netdrive/ above :
**$ find /storage/ -type d -ls -maxdepth 2  |more**


Regardless, I'd create another directory /storage/xbmc/ and put Music/, TV/, Movies/ under that and **mv** the files over as needed.  Be certain to **chown** the files and **chmod **the permissions as needed in the new location.  If you make  /storage/xbmc/ owned by xbmc-user and set the sticky bit on it, that should force any files copied in to get that same owner, unless root does the **mv**. If that's the case, a recursive **chown -R** will be best.  You can script all this and drop it into the root crontab to happen automatically.

---

### Post by Zaggy on 2012-10-11
> **TheFu said:**
> sshfs is too slow for streaming video, even if it worked.

At this point, I'd move those files out of the netdrive area into somewhere the XBMC user controls.  Sorry, but I don't fully understand what your directory structure stuff is showing.   Is there really a /storage/netdrive/netdrive/ directory?

The output from this command would be helpful so I can see the exact directory owner/group and mask permissions, if I'm missing the /s/n/netdrive/ above :
**$ find /storage/ -type d -ls -maxdepth 2  |more**


Regardless, I'd create another directory /storage/xbmc/ and put Music/, TV/, Movies/ under that and **mv** the files over as needed.  Be certain to **chown** the files and **chmod **the permissions as needed in the new location.  If you make  /storage/xbmc/ owned by xbmc-user and set the sticky bit on it, that should force any files copied in to get that same owner, unless root does the **mv**. If that's the case, a recursive **chown -R** will be best.  You can script all this and drop it into the root crontab to happen automatically.

```
22    4 drwx--s--x  10 root     root         4096 Oct  6 11:14 /storage/
59899905    4 drwxr-s---   5 root     sftponly     4096 Oct 11 16:04 /storage/netdrive

```
Edited out number of irrelevant folders
Would rather not have to log on separately to provide access to the XBMC user.
But yeah, media and documents would end up there.

I'll give [http://wiki.xbmc.org/index.php?title=SFTP](http://wiki.xbmc.org/index.php?title=SFTP) a try.

---

### Post by TheFu on 2012-10-11
> **Zaggy said:**
> I'll give [http://wiki.xbmc.org/index.php?title=SFTP](http://wiki.xbmc.org/index.php?title=SFTP) a try.

Using sftp to the local machine seems *wrong*.
Mainly because all credentials are stored in plain text inside the XBMC setting files, but also because it adds an extra layer that isn't necessary.

Lastly, if the sftponly user can't read the directories .. and the file permissions say that is the case, XBMC won't be able to see them either.

I really think you need to move the files somewhere else for XBMC to access them.

I have a LUG meeting tonight, so I'll ask the wider group for a solution.  I'm probably missing a simple and elegant answer.

BTW, using sftp **is** the best way to allow incoming file transfers. Very nice.

---

### Post by Zaggy on 2012-10-12
> **TheFu said:**
> Using sftp to the local machine seems *wrong*.
Mainly because all credentials are stored in plain text inside the XBMC setting files, but also because it adds an extra layer that isn't necessary.

Lastly, if the sftponly user can't read the directories .. and the file permissions say that is the case, XBMC won't be able to see them either.

I really think you need to move the files somewhere else for XBMC to access them.

I have a LUG meeting tonight, so I'll ask the wider group for a solution.  I'm probably missing a simple and elegant answer.

BTW, using sftp **is** the best way to allow incoming file transfers. Very nice.

Thank you!

---

### Post by TheFu on 2012-10-12
Ok, so I asked about 25 people about the best solution for this last night.  Some suggested that you setup a new group that has both the sftpuser and xbmc-user in it and make the group permissions for this area use that other group.  The security-minded people pointed out how **that would lessen overall system security significantly.** 

We considered using ACLs - Access Control Lists - these are extended attributes that have been part of UNIX/Linux for decades, but are mostly ignored because you have to expect them to know to look for them.  They can override the normal file permissions that **ls -al** displays, which can be extremely frustrating.  Everyone in the room who ever used them had forgotten and been burned later.

Lastly, I described the automatic **mv** and** chown** idea presented here previously. While we didn't like it, we all agreed it could be easily scripted and put into the root crontab to run as often as you like - every 5 minutes, every hour, every day, every week - whatever.  As long as the mv stayed within the same file system, it would be instantaneous.  Files being written to would still be written, since the inode wouldn't change, just the directory link.

There you have it.  3 ideas for solutions.  Good luck!

---

### Post by Zaggy on 2012-10-12
> **TheFu said:**
> Ok, so I asked about 25 people about the best solution for this last night.  Some suggested that you setup a new group that has both the sftpuser and xbmc-user in it and make the group permissions for this area use that other group.  The security-minded people pointed out how **that would lessen overall system security significantly.** 

We considered using ACLs - Access Control Lists - these are extended attributes that have been part of UNIX/Linux for decades, but are mostly ignored because you have to expect them to know to look for them.  They can override the normal file permissions that **ls -al** displays, which can be extremely frustrating.  Everyone in the room who ever used them had forgotten and been burned later.

Lastly, I described the automatic **mv** and** chown** idea presented here previously. While we didn't like it, we all agreed it could be easily scripted and put into the root crontab to run as often as you like - every 5 minutes, every hour, every day, every week - whatever.  As long as the mv stayed within the same file system, it would be instantaneous.  Files being written to would still be written, since the inode wouldn't change, just the directory link.

There you have it.  3 ideas for solutions.  Good luck!

Thanks for the suggestions!

Have tried 1 and 2 but no luck, access denieds all around, chroot means no in and out it seems :<
I might actually go for the auto mv chmod cron script.
I'm going to ask the OpenSSH folks what they think about it, will report back.

---

### Post by TheFu on 2012-10-12
> **Zaggy said:**
> Thanks for the suggestions!
Have tried 1 and 2 but no luck, access denieds all around, chroot means no in and out it seems :<
I might actually go for the auto mv chmod cron script.
I'm going to ask the OpenSSH folks what they think about it, will report back.

The chroot stuff only impacts the user stuck inside it. For all local users, it is only the directory and file permissions that matter.

I'm pretty certain the ACLs will work.

The ssh folks will provide a different perspective. Good to ask.  OTOH, we're talking about a 2 line script - hardly something difficult or resource intensive.

---

### Post by Zaggy on 2012-10-24
> **TheFu said:**
> The chroot stuff only impacts the user stuck inside it. For all local users, it is only the directory and file permissions that matter.

I'm pretty certain the ACLs will work.

The ssh folks will provide a different perspective. Good to ask.  OTOH, we're talking about a 2 line script - hardly something difficult or resource intensive.

When I put any groups on the root folder of the chroot, in this case /storage the sftp jail stops working.
root only access to /storage is required for the jail to work, as shown by below message that is returned in /var/auth.log:
> fatal: bad ownership or modes for chroot directory component "/storage/"

Haven't had any response from the ssh folks, I'll try there again.

The script is an easy solution, BUT you will either have to copy the files, making duplicates, eats space.
Or move them, making them no longer accessible on the SFTP netdrive.

I could just throw out the ssh chroot and go with normal ssh access and using ACL/rights for the appropriate folders.
I don't believe that much in my ability to lock down rights on every single file though.

---

### Post by Zaggy on 2012-10-24
[s]Found a possible workaround with:
sudo mount -r --bind /storage/netdrive/netdrive /netdrive

Now to find out how to put this into /etc/fstab without having it break on reboots, system is headless..[/s]

Disregard, rights still apply.

---

### Post by TheFu on 2012-10-24
> **Zaggy said:**
> I could just throw out the ssh chroot and go with normal ssh access and using ACL/rights for the appropriate folders.
I don't believe that much in my ability to lock down rights on every single file though.

I think you've made this much harder than it should be.
* if you add another group, then you need to add that group and users inside the chroot jail too. This may be too complex to grasp.
* the script is bonehead. Is there some reason you haven't just done it already?

---

### Post by Zaggy on 2012-10-25
> **TheFu said:**
> I think you've made this much harder than it should be.
* if you add another group, then you need to add that group and users inside the chroot jail too. This may be too complex to grasp.

The problem is as such:
Raid 5 mounted to /storage
Chroot jail requires the root of the path to the jail to be root accessible only, preventing me or other program from saving anything to it unless I use sudo or root.
Now, I can add myself to the group but then I'm left with SFTP ONLY access.
Apologies for not explaining my meaning earlier.

> 
* the script is bonehead. Is there some reason you haven't just done it already?

As stated earlier:
> The script is an easy solution, BUT you will either have to copy the files, making duplicates, eats space.
Or move them, making them no longer accessible on the SFTP netdrive.

I'm dropping the chroot jail, normal SSH/SCP access go!
Thanks for your time, marking topic as closed.

---

