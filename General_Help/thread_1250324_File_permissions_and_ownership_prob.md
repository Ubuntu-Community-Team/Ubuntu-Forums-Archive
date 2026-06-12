---
title: "File permissions and ownership prob"
date: 2009-08-26
forum: General Help
---

### Post by gandalf458 on 2009-08-26
My intranet is in /var/www

I mostly edit the files on another computer and copy them across via a USB stick. I invariably have to change the mode with
```
sudo chmod -R a+r /var/www
```
but still some files are not displayed, so I tried changing the owner
```
sudo chown root:me /var/www
```
Can anyone tell me what I'm missing, please?

---

### Post by M!K3_$ on 2009-08-26
so are the files not showing up in your file browser or your web browser?

---

### Post by gandalf458 on 2009-08-26
Sorry - they show up in File browser but not in my web browser.

---

### Post by M!K3_$ on 2009-08-26
check the permissions on the individual files.

```
cd /var/www
ls -l
```

maybe it is the specific file that needs the permission change

---

### Post by gandalf458 on 2009-08-26
Ha, thanks - some seem to be owned by me and some by root and seem to have different permissions. So it looks as though my chmod and chown haven't worked? I'm puzzled.

---

### Post by M!K3_$ on 2009-08-26
> **gandalf458 said:**
> ...so I tried changing the owner
```
sudo chown root:me /var/www
```


maybe it was because you made the owner of the /var/www directory, "root".

either way, if it works now then you're good to go.

---

### Post by unutbu on 2009-08-26
gandalf458, what type of filesystem contains /var/www ?

(You can find it out by running
```
df -T /var/www
```
)

If the filesystem type is FAT or NTFS, then the file and directory ownership and permissions are set once for the entire filesystem at mount-time. FAT and NTFS are impervious to chown and chmod.

Edit: After re-reading the thread (LOL!) perhaps the problem is that you need the -R (recursive flag):
```
sudo chown -R root:me /var/www
```
If /var/www is on an ext3, ext4, jfs or xfs filesystem, this will make all files and subdirectories owned by root, with group-owner set to "me".

---

### Post by M!K3_$ on 2009-08-26
> **unutbu said:**
> 
Edit: After re-reading the thread (LOL!) perhaps the problem is that you need the -R (recursive flag):
```
sudo chown -R root:me /var/www
```


BINGO!!!!


i think that should do it.

---

### Post by gandalf458 on 2009-08-26
Yeah! Thanks for your help chaps!

---

