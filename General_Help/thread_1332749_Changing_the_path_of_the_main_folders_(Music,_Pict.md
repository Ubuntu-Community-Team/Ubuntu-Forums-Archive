---
title: "Changing the path of the main folders (Music, Pictures, Documents...)"
date: 2009-11-20
forum: General Help
---

### Post by dvalenca on 2009-11-20
I have the UNR Karmic Koala in my Acer Aspire One with SSD drive.

I know that we can't mount folders into other folders.
I know that we can't edit ISO images.

They say, that has a lot of problems if you mount your /home in the SDHC card (you can lost all your data if put to hibernate or something - doesn't matter, because I didn't intend to hibernate, but I tryed to install that way and I couldn't, just didn't work).

Well, as I have few space in drive and a SDHC card, I want to put some of the data in the SDHC. So I want to load the main folders (like Music, Pictures, Documents...) in my SDHC and left the config data at the SSD drive. But, if I just left it as a link, things like the "Save as" of the softwares wouldn't give me the path right in the way. So I want to try to mount the folders of the SDHC in the /home, mantaining the config files... any ideas?

I saw some tips to change the icons of the main folders changing some config file in gnome. But I don't if I can change the path...

I though of criating ISOs and mounting it (like a Documents.iso and mount in /home/Documents). But I can't write in ISO files. So I tryed .IMG, no success as well.

I don't want to do a lot of partions, because I don't know if someday I'll need more space for Music than Pictures, for exemple.

Any ideas?

(changing a config file, as I did to change the icon would be the ideal way...)

---

### Post by dcstar on 2009-11-20
> **dvalenca said:**
> 
.........
Well, as I have few space in drive and a SDHC card, I want to put some of the data in the SDHC. So I want to load the main folders (like Music, Pictures, Documents...) in my SDHC and left the config data at the SSD drive. But, if I just left it as a link, things like the "Save as" of the softwares wouldn't give me the path right in the way. So I want to try to mount the folders of the SDHC in the /home, mantaining the config files... any ideas?

I saw some tips to change the icons of the main folders changing some config file in gnome. But I don't if I can change the path...
........

Install Ubuntu Tweak.

---

### Post by dvalenca on 2009-11-23
I saw this, but I don't know how it will help me...

Can I mount something in a folder with other files, without blank the other folder?

Lets say that a folder has the files "file1" and "file2"...

Can I mount a drive with the "file3" and "file4" and when I go to this folder I would see all the 4 files?

See, the Linpus that was before installed in my Aspire One did that... It puts my SSD together with my SDHC... Like it was just one...
How can I do this?

---

### Post by dvalenca on 2009-11-23
**not "mantaining the config files", "keeping the config files... sorry my English!

---

### Post by alphaniner on 2009-11-23
If I'm understanding correctly, you could use symbolic links:

```
~$ ls -l ~
total 16
drwxr-xr-x 3 testing testing 4096 2009-11-11 12:35 bin
drwxr-xr-x 2 testing testing 4096 2009-11-12 13:58 Desktop
lrwxrwxrwx 1 testing testing   22 2009-11-23 15:12 Documents -> /mnt/bucket/Documents/
lrwxrwxrwx 1 testing testing   21 2009-10-22 17:59 Downloads -> /mnt/bucket/Downloads
-rw-r--r-- 1 testing testing  512 2009-10-21 09:58 MBR
lrwxrwxrwx 1 testing testing   21 2009-11-23 15:12 Pictures -> /mnt/bucket/Pictures/
lrwxrwxrwx 1 testing testing   19 2009-11-18 10:38 Public -> /mnt/bucket/Public/
drwxr-xr-x 2 testing testing 4096 2009-05-15 07:33 Templates

```

The Documents, Downloads, Pictures, and Public 'folders' are actually links to folders on another partition.  Let me know if you think this might work for you and I will explain it.

---

