---
title: "Read only"
date: 2012-01-20
forum: General Help
---

### Post by Asad3ainJalout on 2012-01-20
So my Windows crashed on my dual booted laptop (windows 7 and ubuntu) I formatted and reinstalled the windows partition without thinking and now i cannot boot up to ubuntu. I also cannot copy my home folder using a live CD since I am not the owner.  How can 1) boot up to Ubuntu, or 2) copy the home folder.

Thank you in advance.

---

### Post by WorMzy on 2012-01-20
Assuming you've mounted your ubuntu partition, you can use

```
sudo cp -rp /media/ubuntu/home/username /media/usbstick
```

Or similar.

-rp means that everything in the home folder will be copied, and the permissions will be preserved. However, if you're copying the files to a FAT or NTFS partition the permissions will be lost anyway as Windows file systems don't support UNIX file permissions.

If that command is too intimidating for you, you could always use

```
gksudo nautilus
```

to open the file manager as root; you won't get any permissions problems that way either.

---

### Post by Asad3ainJalout on 2012-01-20
well i have a windows partition is it possible to send it directly to the desktop of the windows partition? I do not really care about permissions right now, but the information on that home drive is very important considering i use linux for everything but gaming.

(sorry Ive been described as intermediate to almost advanced linux user but i feel more like a newb)

---

### Post by drmrgd on 2012-01-20
Isn't the problem that Windows 7 just overwrote the bootloader?  If you just repair Grub2, I think you should be able to boot back to Ubuntu.  Here's a quick link to [repair Grub2 after installing Windows]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2")

---

### Post by Asad3ainJalout on 2012-01-20
Well I am getting rid of Ubuntu and replacing it with Zorin-OS for my wife who is only used to windows. I just need the home folder so i can format the ubuntu partition merge it and install the new OS

---

### Post by WorMzy on 2012-01-20
> **Asad3ainJalout said:**
> well i have a windows partition is it possible to send it directly to the desktop of the windows partition?

Sure. Just mount the partition using the file manager, or however you usually mount it.

e.g.

```
udisks --mount /dev/sda1
or
sudo mount /dev/sda1 /mnt
```

Then fix amend the copy command.

Your Windows desktop should be under [COLOR="Red"]*mountpoint*[/COLOR]/Users/username/Desktop

EDIT: My copy command is erroneous; I forgot to factor in that you're on a LiveCD. Your installation's home folder will be under /media/ubuntu (or similar) after you mount the partition. I've changed my first post to reflect this.

---

### Post by Asad3ainJalout on 2012-01-20
Thank you both Very much for the help. I am currently on my Zorin-OS partition copying back the home folder from my windows 7 desktop.

soon as i figure out how to give you guys beans or coffee beans or pluses or watever ill give it to you.

---

