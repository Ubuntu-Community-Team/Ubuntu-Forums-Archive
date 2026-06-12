---
title: "Help with Grub2"
date: 2012-02-08
forum: General Help
---

### Post by ChemMeister on 2012-02-08
Hi,

I had two hard drives on my desktop, one had Ubuntu 11.10 and the other one Windows 7. I purchased a larger capacity hard drive , so i removed the old one that had Ubuntu on it replaced it with the new one, and installed Ubuntu from Live CD. However when i start the computer I get the error "no such device found" and the grub rescue command prompt. Any ideas how to fix this? Thanks

---

### Post by Quackers on 2012-02-08
Is your bios set to boot the Windows drive or the new drive?

---

### Post by oldfred on 2012-02-08
And did you auto install so grub2 installed to sda, or manually selected where to install grub2's boot loader so it is on the same drive as Ubuntu. 

It is best to keep Windows boot loader on the Windows drive and the grub2 boot loader on the Ubuntu drive, so each drive can boot separately. Your old install may have had grub in the Windows drive and that is what is not working now.

---

### Post by ChemMeister on 2012-02-08
I am not sure where grub2 was installed. I had Windows 7 installed before Ubuntu. I added the new hard drive to my system and then installed Ubuntu on it. And then i got the Grub menu that gave me the option to select which OS i want to boot with.

---

### Post by oldfred on 2012-02-08
If you want to know what is installed where, you can run the bootinfo script.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

The test version has some fixes and you can directly download it.
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by ChemMeister on 2012-02-08
> **oldfred said:**
> If you want to know what is installed where, you can run the bootinfo script.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

The test version has some fixes and you can directly download it.
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Thanks for the detailed response. Please dont laugh at me, i realized that for some unknown reason the system was not reading the hard drive. So I disconnected the cables connecting and re-connected. it is working now :)

---

### Post by oldfred on 2012-02-08
Glad you have it fixed. Been there, done that.

I have yet to open case on my desktop and not bump something loose. PATA cables were the worst for me as I would just loosen them enough that they looked connected but a push fully connected them. Sometimes the drive would even start to work but have just enough wires not connect to fail.

---

