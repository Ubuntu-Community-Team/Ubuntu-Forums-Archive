---
title: "Cannot delete song from Rhythmbox over samba share"
date: 2010-07-29
forum: General Help
---

### Post by cbstryker on 2010-07-29
Not sure if this is the right category.

My problem is as such: I just moved all my songs over to my samba share server. I've been meaning to do it for a while and I finally did. Before that I had all my songs locally and if I needed to delete something I didn't want I could do it straight from Rhythmbox as I was listening to it (instead of tediously going through a file browser and manually deleting it).

However, now that I've put everything on to the samba share (which I've mapped to /home/chris/Music in my fstab as CIFS) I cannot delete anything from Rhythmbox. I get an "Operation not supported by backend" error. However, I can delete, copy, paste, create and do anything else fine in nuatilus, windows explorer or a terminal from any computer.

Why would I be getting this error? I'm 99.9% sure it's _not_ a samba issue. Is it possible that Rhythmbox cannot handle remote shares except reading from them? The only workaround I can think of is to keep files both locally and on the samba share and to also create a two way sync between the two root "Music" folders. Anything updated or deleted on either end would be populated across the other. But my point here is that I shouldn't have to. I would like to just keep it simple, plus the point of having the samba share is to free up space on my local end as well as making all the songs available over the network.

---

### Post by cbstryker on 2010-07-29
Is this maybe in the wrong category?

---

### Post by cbstryker on 2010-07-29
bump?

---

### Post by cbstryker on 2010-07-30
bump again? seriously? no one has a suggestion?

---

### Post by cbstryker on 2010-08-04
Ok, someone needs to have some idea!

---

### Post by psypher on 2010-10-12
Hi,

I have the same problem. First I tried changing the permissions on the samba server. Full permissions didn't work. So I tried using banshee, got a bit more informative error this time.

Cannot delete a non-local resource: smb.     smb://ip/share/folder etc etc. Did the same thing for ftp.

My shares are mounted via bookmarks. So I tried manually mounting the samba share and it worked!

So I'm guessing the problem lies with gvfs mounting the share with fuse.

I don't know how the process works. 

What I did notice is difference in the permissions for the gvfs mounted and manually mounted shares.  gvfs perms on the client are 700 user:user. manual is 777 user user.

Not sure how to get gvfs to mount the folder 777. But I think there will still be an application limitation which will stop it deleting the files.

Manually mounting is the only current solution I have.

BTW I am running on Meerkat. Fully updated.

Help on manually mounting:
[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

Thanks

---

