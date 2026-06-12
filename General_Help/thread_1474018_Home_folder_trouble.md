---
title: "Home folder trouble"
date: 2010-05-05
forum: General Help
---

### Post by dfrag on 2010-05-05
After installing and living with Ubuntu 10.04 for a few days I decided I needed more room for things in my /home folder and it made sense to me to keep it on a separate partition to the OS so I don't have to loose everything if I reinstall.

After following a tutorial on the Ubuntu [site]("https://help.ubuntu.com/community/MoveMountpointHowto") I didn't follow every step as not all were relevant but I did change the fstab file and the OS now references the new partition as the /home folder. Over all this is a success but it has given me a new problem, I can't seem to locate the old /home folder for me to retrieve my files and documents. in retrospect I should of backed up the folder before hand but I was hoping the process would be something like moving the my documents folder in windows where the OS at some point asks to copy the existing folder to the new location.

so basically is it possible to locate the old /home folder to retrieve my files and copy them to the new one. I didn't delete the files nor did I see any activity suggesting they have been deleted but it's not really the end of the world if they have been it would be easier for me and my network if I can just move them from one partition to another.

Thanks in advance for any help.

---

### Post by Vaphell on 2010-05-05
if you haven't destroyed old home partition everything should be fine, just find it, mount it and copy the files.

```
sudo fdisk -l
```

---

### Post by WorMzy on 2010-05-05
Sounds like you're mounting the home partition over the top of the original /home folder (which I didn't think was possible unless the folder was empty, but oh well)

- If you run 'sudo umount /home && sudo mkdir /media/newhome'
- Then edit fstab so that your home partition will mount there (/media/newhome) for now
- Then run 'sudo mount -a' so it remounts your home partition

You should be able to access your original /home folder.

---

### Post by quadproc on 2010-05-05
> **dfrag said:**
> ...
so basically is it possible to locate the old /home folder to retrieve my files and copy them to the new one. I didn't delete the files nor did I see any activity suggesting they have been deleted but it's not really the end of the world if they have been it would be easier for me and my network if I can just move them from one partition to another.

Thanks in advance for any help.
Wormzy already mentioned the probable cause of your "missing" files and I wanted to add that you will need to copy (as opposed to move) your files from their old home to their new home once you manage to get both partitions mounted at the same time.  The copying process can be tricky because of things such as hard links, timestamps, and other details.  It is wise to compare your two /home directories after the copy to see if anything important is missing or damaged.  The diff program is pretty good at this.

Note that you'll need enough partition space to hold two sets of your /home data at the same time.  Once copied over and checked out, the old data can be deleted and this will return its disk space.

quadproc

---

### Post by dfrag on 2010-05-08
Thank you all for your responses, I solved the problem but I used a live disk as I couldn't unmount the /home folder as it was in use by the OS.

I first booted into my normal desktop changed permissions on all the drives and folders I was going to need to use, then popped in the Live disk and used it to copy everything over, job's agoodun!

thank you all for your help!

---

