---
title: "Samba problems"
date: 2006-03-22
forum: General Help
---

### Post by thumper on 2006-03-22
I have an external maxtor NAS that share I connect to using smbfs.

It has my music on it, and I play it using Amarok.  However after some time it just stops and anything trying to access the mount freezes.

In syslog I then get errors like:
```
Mar 21 12:20:17 localhost kernel: [4712925.261000] smb_lookup: find <filename stripped> failed, error=-512
Mar 21 12:20:41 localhost kernel: [4712949.407000] smb_add_request: request [c9abf980, mid=13922] timed out!
Mar 21 12:22:14 localhost kernel: [4713042.602000] smb_lookup: find <filename stripped> failed, error=-5
Mar 21 12:22:41 localhost kernel: [4713069.408000] smb_add_request: request [c9abf980, mid=13939] timed out!

Mar 21 12:24:11 localhost kernel: [4713159.408000] smb_file_read: <filename stripped> validation failed, error= 4294967291
Mar 21 12:25:11 localhost kernel: [4713219.411000] smb_add_request: request [c9abf980, mid=13949] timed out!

Mar 21 12:28:41 localhost kernel: [4713429.454000] smbiod_handle_request: smbiod got a request ... and we don't implement oplocks!

```
I had a quick google for samba error codes, but it didn't return much.

Does anyone have any ideas?

BTW while my linux box is having problems accessing the files, the windows boxes are fine and have no problems.

---

### Post by thumper on 2006-03-22
Just happened again.

It appears that the error messages above only happen after the non-responsiveness of samba.

None of the log files seemed to have anything.  The only way I can get it to work again is to remount the samba share.

This really screws up my listening pleasure :-|

---

### Post by thumper on 2006-05-29
Bump.

Not limited to amaroK, viewing stuff in Gwenview or Konq also trigger the freeze.

---

### Post by uteck on 2006-05-30
From the line; Mar 21 12:24:11 localhost kernel: [4713159.408000] smb_file_read: <filename stripped> validation failed, error= 4294967291

I would hazard to guess that you are being logged out of the samba connection.  Do you have to supply a username and password to connect each time?

---

### Post by thumper on 2006-05-31
Nope.  It is shared to all.  None of the windows machines have any problems with it.  From windows it quite happily plays the mp3s using winamp over the network connection, but amarok will just block after 5 - 10 songs.

The external drive is a Maxtor NAS, and I am assuming that it is running some form of embedded linux.

It is mounted using smbfs.  Can it be mounted with cifs?  Which is "better"?

---

### Post by thumper on 2006-05-31
Just in case people are actually reading this, I have found out that smbfs is in the early phases of being deprecated in favour of cifs.

cifs is the suggested way to mount "windows" type shares.  It is actively maintained whereas smbfs isn't.

Apparently there were some problems with cifs/smbfs under heavy load (like what might happen when Konq opens a directory with 100 photos and tries to get thumbnails of them) which was due to incomplete socket operations.  This was fixed in cifs for the 2.6.6 kernel.

I'll whack it in tonight and see if it fixes it.

---

### Post by airtonix on 2007-07-14
you will find that cifs is include with samba.....the one you already have...

i think it is a matter of keywords used in conf fils that make it cifs rather than smb

---

### Post by TSJason on 2007-07-31
Hi,

 I just recently ran into the same type of issues with the connections dropping, however it was on an old machine running dapper that is connecting to my feisty machines. Like magic, changing smbfs to cifs in /etc/fstab made it work flawlessly.

This updated my fstab and remounted the drives for me:
```

sudo sed -i 's/smbfs/cifs/g' /etc/fstab
sudo for each in `grep smbfs /proc/mounts|awk '{print $2}'` ; do umount -l $each ; mount $each ; done

```

---

