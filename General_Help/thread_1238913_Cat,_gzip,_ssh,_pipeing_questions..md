---
title: "Cat, gzip, ssh, pipeing questions."
date: 2009-08-12
forum: General Help
---

### Post by SoftwareExplorer on 2009-08-12
Overall idea: (ssh running cat /path/to/gzipfile.gz)->gzip decompression->dd of=/dev/sda1

Will it corrupt a gzip file to cat it and then pipe the output to gzip? (I want to do this so that I'm sending gzip compressed data over ssh and then decompressing it once its past having to go over the network) Second, how do I make gzip decompress stdin?

---

### Post by SoftwareExplorer on 2009-08-13
> **gzip --help said:**
> With no FILE, or when FILE is -, read standard input.
So does that mean don't specify a file and gzip will read whatever is piped to it?

---

### Post by DaithiF on 2009-08-13
Hi,
> So does that mean don't specify a file and gzip will read whatever is piped to it? 	Yes
> Second, how do I make gzip decompress stdin? 	
gunzip 

so, something like
cat testfile.gz | ssh you@somehost gunzip -c ">" newfile

(not sure what you're trying to do with the dd part, writing direct to /dev/sda is likely to be dangerous unless you know what you're doing)

---

### Post by slakkie on 2009-08-13
cat file | ssh you@server gzip -dc - 

This will unzip the file in the root.

---

### Post by SoftwareExplorer on 2009-08-13
> **DaithiF said:**
> Hi,
Yes

gunzip 

so, something like
cat testfile.gz | ssh you@somehost gunzip -c ">" newfile

(not sure what you're trying to do with the dd part, writing direct to /dev/sda is likely to be dangerous unless you know what you're doing)

Thanks. I have a dd image of sda1 that is gzip compressed on computer b. Right now, to restore on computer a, I run ssh me@b "gzip -dc /media/Backups/a/09-08-13/sda.img.gz" |
sudo dd of=/dev/sda1, from computer a. That sends the decompressed data over the network which takes alot of time. It also makes computer b, a single core do all the work when I have a Qaud core that I'm restoring on.

---

### Post by asmoore82 on 2009-08-13
```
ssh me@b cat /path/to/image.gz | gunzip | sudo dd of/dev/sda1
```

Be aware that this will break if your Environment scripts on b produce any output.

You may want to look into Clonezilla: [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by SoftwareExplorer on 2009-08-13
> **asmoore82 said:**
> ```
ssh me@b cat /path/to/image.gz | gunzip | sudo dd of/dev/sda1
```Be aware that this will break if your Environment scripts on b produce any output.
What are environment scripts and how would I check if they produce output?
> **asmoore82 said:**
> You may want to look into Clonezilla: [http://clonezilla.org/](http://clonezilla.org/)
I just read about it on it's home page. It says that it supports ext4 and ntfs. Is clonezilla in the repositories and if so, is it up-to-date enough to support those filesystems?

Thanks

---

