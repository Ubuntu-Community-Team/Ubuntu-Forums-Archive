---
title: "Samba share for all local users"
date: 2009-08-01
forum: General Help
---

### Post by jamesisin on 2009-08-01
I am setting up a desktop machine for my brother and his new wife (9.04).  I would like to creat a Samba share that is shared regardless of who happens to log into the machine (even prefereably if no one has signed into the machine).  If I try to do it through the GUI as I am familiar I run into ownership conflicts (can't share a folder of which you are not the owner).  I'm sure there is a solution, so here I am asking the experts.

---

### Post by shp on 2009-08-01
The shares are all ways shared it doesn't matter who is logged in to the computer. You'll just have to share it with the use that has ownership.

---

### Post by adamitj on 2009-08-01
First of all, what is the folder you're trying to share?

Be sure of this folder is under /home path, otherwise all other folders should be root property - and these you might not change ownership.

You can try to change the folder permission from console:
```
$ sudo chown <username> <path_and_folder>
```

Example (changing ownership of Music folder to user tiago):
```
$ sudo chown tiago /home/tiago/Music
```

---

### Post by adamitj on 2009-08-01
> **shp said:**
> The shares are all ways shared it doesn't matter who is logged in to the computer. You'll just have to share it with the use that has ownership.

A common problem is to deflate a zip, gzip or bz2 file with "sudo" command. If the packaged doesn't contain ownership information, all uncompressed folders and files will be automatically defined as "root" property and then you can't share them from GUI.

---

### Post by jamesisin on 2009-08-01
> **shp said:**
> The shares are all ways shared it doesn't matter who is logged in to the computer. You'll just have to share it with the use that has ownership.

Ah, that is not obvious.  The 'share' emblem disappears from the folder when another user is logged in.  I have tested and confirmed that the shares are accessible when a different user is logged in so I am going to call it good.  Thanks.

---

### Post by jamesisin on 2009-08-02
One follow-up question...

Now that the share is accessible I am having some trouble getting the permissions sorted out correctly.  I have created a group (called musicshare) of which the 3 users are members.  This is the group of ownership of the share (recursively).  Yet I am not able to write while connected to the share.  How do I tell the share to allow members of musicshare to write to the share?

---

### Post by jamesisin on 2009-08-02
Oh, what silliness...

Just check the box to allow others to write to the share and rely upon Ubuntu's permissions (ie the group) to control it.

---

