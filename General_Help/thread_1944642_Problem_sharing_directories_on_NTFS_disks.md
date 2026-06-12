---
title: "Problem sharing directories on NTFS disks"
date: 2012-03-21
forum: General Help
---

### Post by impalerau on 2012-03-21
I have a file server with a system disk and 3 NTFS data disks.  I need to share folders on the NTFS disks.

I have the disks mounting at boot.  My fstab looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devicesRasp0p0va

# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=6079bef5-b656-4727-8980-4b795ac12fe6  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=602d3b9b-3ac3-4702-a804-86003ed81129  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
UUID=28604CB603827D12                      /media/MMD01    ntfs  nls=iso8859-1,umask=000   0  0  
UUID=534486CA50CD4D6F                      /media/MMD02    ntfs  nls=iso8859-1,umask=000   0  0  
UUID=2140FEA15ED69203                      /media/MMD03    ntfs  nls=iso8859-1,umask=000   0  0  

```

When I ran the Share dialogue in Nautilus I got this:

```
'net usershare' returned error 255: net usershare add: cannot share path /media/MMD02/Documentaries as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.

```


Very friendly and useful message I thought.  So I searched the system disk for smb.conf.  There were several but I figured that the one in /etc/samba/ was the one I wanted.  I added the line thus:

```
.
.
.
# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

   usershare owner only = false

#======================= Share Definitions =======================
.
.
.

```


Now I get a slightly less informative error:

```
'net usershare' returned error 255: net usershare add: failed to add share album art. Error was Operation not permitted
```

Can anyone help please?

---

### Post by dcstar on 2012-03-22
> **impalerau said:**
> I have a file server with a system disk and 3 NTFS data disks.  I need to share folders on the NTFS disks.

I have the disks mounting at boot.  My fstab looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devicesRasp0p0va

# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=6079bef5-b656-4727-8980-4b795ac12fe6  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=602d3b9b-3ac3-4702-a804-86003ed81129  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
UUID=28604CB603827D12                      **/media/MMD01**    ntfs  nls=iso8859-1,umask=000   0  0  
UUID=534486CA50CD4D6F                      **/media/MMD02**    ntfs  nls=iso8859-1,umask=000   0  0  
UUID=2140FEA15ED69203                      **/media/MMD03**    ntfs  nls=iso8859-1,umask=000   0  0  

```
.........

Don't **ever** put internal disks in **/media**, /media is a System folder for auto-mounted devices. Create mount points in /mnt, that is what it exists for.

NTFS partitions are usually mounted with the **ntfs-3g** type.

---

### Post by impalerau on 2012-03-22
> **dcstar said:**
> Don't **ever** put internal disks in **/media**, /media is a System folder for auto-mounted devices. Create mount points in /mnt, that is what it exists for.

NTFS partitions are usually mounted with the **ntfs-3g** type.

Thanks for the tips David.  I must admit that I didn't actually make the decision about the mount directory.  I have to delve into these things very infrequently so I try to fing a GUI dialogue for the job (PySDM in this case) and just let it do its default thing.  I've been using Ubuntu since version 7.04 and remember that extra disks used to get mounted on /mnt.  I think the default behaviour changed to /media with Hardy Heron.  I just figured it was one of those things that changes from version to version.

The '-3g' definitely rings a bell as well.

Are either of the things you pointed out likely to be causing my sharing problem?  I'm still at work so I'll see if this solves it when I get home tonight.

Regards,
Vlad.

---

### Post by impalerau on 2012-03-22
I've edited fstab as recommended by David.  At first I thought the disks didn't mount at all because they didn't show up on the devices list in Nautilus.  Then I went into /mnt and they are there.  I preferred the "warm fuzzies" of seeing them in the Nautilus Devices list.  Does that simply display what's mounted in /media or is there another way of showing them there?

Still can't create a share though.  I'm getting the 255 "Operation not permitted" error.

I got a copy of the required entries in smb.conf from one of our OpenVMS system managers at work who looks after SAMBA on our VMS boxes.  I'll give that a go and post the results.

---

### Post by impalerau on 2012-03-22
Editing smb.conf worked fine as expected.  I now have shares that I can access from other boxes.

Entries are as follows:

```
[Movies]
   read only = no
   path = /mnt/MMD01/Movies
   guest ok = yes

[Pictures]
   read only = no
   path = /mnt/MMD01/Pictures
   guest ok = yes
.
.
.
etc.
```

Only problems left are seeing the the disks in the Nautilus Devices list and no visible indication on the folder icons in nautilus that the folders are shared.  Minor issues, I know but is there a solution?

---

### Post by Morbius1 on 2012-03-22
For the benefit of anyone who searches and finds this topic the original error was this:
> 'net usershare' returned error 255: net usershare add: cannot share path /media/MMD02/Documentaries as we are restricted to only sharing directories we own.     Ask the administrator to add the line "usershare owner only = false"      to the [global] section of the smb.conf to allow this.That was caused by this:
>  UUID=534486CA50CD4D6F                      /media/MMD02    ntfs  nls=iso8859-1,umask=000   0  0Although the partition is accessible by everyone it's owner is still root. There's 3 ways to fix this:

** Change ownership of the mounted partition by adding uid=1000 to the options list in fstab:
```
UUID=28604CB603827D12 /media/MMD02 ntfs nls=iso8859-1,uid=1000,umask=000   0  0
```[COLOR=Blue]*Note: specifying "ntfs" in fstab points to the ntfs-3g "driver" automatically unless there's a problem with your install and the earth will still revolve around it's sun if you have a mount point in /media.*[/COLOR]

** Or do what the error message says and add "usershare owner only" to the [global] section of smb.conf although you might not want to do that in a multiuser setup for obvious reasons.

** Bring up nautilus as sudo ( gksu nautilus ) and share the directory as the owner - root.

I suspect that the next error:
>  'net usershare' returned error 255: net usershare add: failed to add share album art. Error was Operation not permittedWas caused by one of 3 possible conditions:
The "album art" share already exists but is owned by root. 
The permissions on the location for the share definitions is not correct.
The user is not a member of the sambashare group

Listing the ownership and permissions of the share definitions and it's parent directory would have cleared that up - maybe ;) :
```
ls -al /var/lib/samba/usershares
```The op has decided to use the traditional or "Classic" method to creating samba shares and there is nothing wrong with that but it has nothing to do with the original error message.

BTW:
> Only problems left are seeing the the disks in the Nautilus Devices list ...Open Nautilus and drill to /mnt/MMD02 then bookmark it: [B]Bookmarks > Add bookmark.
[/B]> ... and no visible indication on the folder icons in nautilus that the folders are shared.The Classic method of Samba sharing never altered the emblem of folders that it shares. Only shares created through Nautilus did that - and sometime even there is was not persistant.

---

### Post by jerome1232 on 2012-03-22
> **dcstar said:**
> Don't **ever** put internal disks in **/media**, /media is a System folder for auto-mounted devices. Create mount points in /mnt, that is what it exists for.

NTFS partitions are usually mounted with the **ntfs-3g** type.

I have to adamantly disagree, you can mount a partition wherever you darn well please. Whether it be in your home, in /mnt in /media, in /, etc... Doesn't matter. That's up for the user of the system to decide.

/rant

---

### Post by bab1 on 2012-03-22
> **jerome1232 said:**
> I have to adamantly disagree, you can mount a partition wherever you darn well please. Whether it be in your home, in /mnt in /media, in /, etc... Doesn't matter. That's up for the user of the system to decide.

/rant
To add to your rant:  The reason to mount *anything* at /media/some_mount_point is to get it to show up on the desktop (if you have that enabled via gconf).  I have several Samba shares mounted that way.  The user can visually see the folder when it is mounted, just as the OP wanted.  The type of media (fixed or removable) is not relevant in this context.

---

