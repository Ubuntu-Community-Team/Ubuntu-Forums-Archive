---
title: "Copy Home to USB"
date: 2010-10-15
forum: General Help
---

### Post by jesuisbenjamin on 2010-10-15
Hi there,

I'm trying to copy the content of my /home to a USB stick.
My /home properties declare it is 12.3GB large.
My USB properties declare it has 14.9GB free space.

When copying /home on USB, an error occurs with the claim that 30.9GB are required.

How come this difference? I surely don't have that much GB in my home, not a movie, 7GB of music and for the rest few documents....

Any idea as to what's going on here?

Thanks
B.

---

### Post by Vaphell on 2010-10-15
maybe your usb is divided to big blocks and you got plenty of small files (config files for example) which occupy 1 block but use only tiny part of it?
try selecting only things you want to copy, not the whole dir with all hidden config files and stuff.

---

### Post by matt_symes on 2010-10-15
Hi,

Is it following and trying to copy through hard or symbolic links stored in you home folder?

Kind regards.

---

### Post by coffeecat on 2010-10-15
@jesuisbenjamin, I think matt_symes has the answer to your problem, but there's another issue you need to be aware of. Are you copying your home just to backup personal data or are you wanting to copy the whole of home including your personal configuration files? If the latter, don't use a MS filesystem such as NTFS or FAT32 on your USB drive. Although all your files are owned by you, some of the hidden config files, such as ~/.dmrc need certain permissions  which will be lost if you copy to a MS filesystem. This may cause login problems if you restore from your backed up home contents.

---

### Post by btindie on 2010-10-15
Is your home directory stored on it's own partition?
What's the output of
```
sudo mount
sudo df -h
sudo du -sh /home
```
 
You may have X GB free on your USB stick but depending on the size of the files it may require more space than the sum of the file sizes.

---

### Post by jesuisbenjamin on 2010-10-15
I couldn't be bothered: i selectively copied the folders i needed on the USB, it went fine that way.
Thanks for the help anyway.

---

