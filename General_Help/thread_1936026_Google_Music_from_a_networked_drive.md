---
title: "Google Music from a networked drive"
date: 2012-03-05
forum: General Help
---

### Post by piratemurray on 2012-03-05
I'm trying to upload my music to Google Music from a networked USB drive. 

The problem is since the drive is networked, Google Music won't recognise the folders with my music. 

How can I trick it into thinking that they are local folders? The drive is Samba'd if it helps.

---

### Post by kostkon on 2012-03-05
Are you able to access hidden files in google music's file chooser dialog? Like for example, in the gtk file chooser, you can right click and select Show Hidden Files.

Then, try to see if you can access your networked data by going into the hidden *.gvfs* folder (that resides in your home folder, i.e.
/home/yourusername/.gvfs) and selecting the folder named after the samba share you want to access.

Hope that helps.

---

### Post by piratemurray on 2012-03-05
kostkon: I can access the folder that way, but Google Music says the folder is empty :(

Perhaps this is a Google Music fault?

---

### Post by kostkon on 2012-03-05
Can you see your data if you open this folder in nautilus?

---

### Post by HiImTye on 2012-03-05
sounds like a permissions problem, try to chown them
```
sudo chown -R /path/to/folder
```
if not you can try using chmod to give it permissions in the same way

---

### Post by piratemurray on 2012-03-06
> **kostkon said:**
> Can you see your data if you open this folder in nautilus?

I can see the data in nautilus, but Google Music doesn't see them.

> sounds like a permissions problem, try to chown them

```
sudo chown -R /path/to/folder
```

if not you can try using chmod to give it permissions in the same way 


I'll try this when I get home. Cheers!

---

### Post by piratemurray on 2012-03-06
Didn't work. :(

Unable to change either the owner or the permissions on the folder. Even mounted it directly into my computer rather than through the router and the same thing. 

The hard drive is probably formatted with NTFS since it was left over from my Windows days. Either way it wouldn't upload to Google Music.

No cloud music for me :(

---

### Post by piratemurray on 2012-03-09
> **piratemurray said:**
> Didn't work. :(

Unable to change either the owner or the permissions on the folder. Even mounted it directly into my computer rather than through the router and the same thing. 

The hard drive is probably formatted with NTFS since it was left over from my Windows days. Either way it wouldn't upload to Google Music.

No cloud music for me :(



For anyone with a similar problem this is how I fixed it.

The drive was an old drive mounted as a FAT volume. Bummer. Had to copy everything off it to another drive, reformat into something sensible like ext4 and then copy it back. It was a permissions thing in the end. Now the new ext4 filesystem had permissions that Google Music could use. Uploading to the cloud right now!

---

