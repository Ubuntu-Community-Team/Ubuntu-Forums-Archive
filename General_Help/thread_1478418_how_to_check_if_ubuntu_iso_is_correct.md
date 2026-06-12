---
title: "how to check if ubuntu iso is correct"
date: 2010-05-09
forum: General Help
---

### Post by elliotn on 2010-05-09
hi i just dloaded ubuntu 10.04 iso, i used firefox and on the way i had to pause n start for about 5 times, when i burned the iso with brasero and booted from it I got an error, but recently I have burned discs with my burner and they never work. So how do i check if the iso is correct or not

---

### Post by Catharsis on 2010-05-09
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by elliotn on 2010-05-09
ok i used md5sum here is what i got

100% d044a2a0c8103fc3e5b7e18b0f7de1c8

So I dont know what it means

---

### Post by Catharsis on 2010-05-09
Did you read the link?
> Compare the hash (the alphanumeric string on left) that your machine calculated with the corresponding hash on the UbuntuHashes page.

An easy way to do this is to open the UbuntuHashes page in your browser, then copy the hash your machine calculated from the terminal into the "Find" box in your browser (in Firefox you can open the "Find" box by pressing <Ctrl> <F>).

When both hashes match exactly then the downloaded file is almost certainly intact. If the hashes do not match, then there was a problem with either the download or a problem with the server. You should download the file again from either the same mirror, or from a different mirror if you suspect a server error. If you continuously receive an erroneous file from a server, please be kind and notify the webmaster of that mirror so they can investigate the issue.

---

### Post by roubman on 2010-05-09
When burning your ISO image use the verify tool. In order to know the correct one to download, one without bugs... Download off the linux website (a site you can trust).

---

### Post by elliotn on 2010-05-09
k it matches 100% so maybe my cd burner is dead. I will try using my friend cd burner

---

### Post by Catharsis on 2010-05-09
When you boot from the LiveCD, do you get the purple screen with a keyboard and stickfigure at the bottom? If so, hit Enter here and then select "Check disc for errors" from the menu.

---

### Post by elliotn on 2010-05-09
> **Catharsis said:**
> When you boot from the LiveCD, do you get the purple screen with a keyboard and stickfigure at the bottom? If so, hit Enter here and then select "Check disc for errors" from the menu.

i get I/O error

error reading boot cd
         reboot

---

### Post by Catharsis on 2010-05-09
Try burning another CD. And make sure the burn speed is on the lowest setting.

---

### Post by elliotn on 2010-05-09
> **Catharsis said:**
> Try burning another CD. And make sure the burn speed is on the lowest setting.

i burned 2 cds in the lowest speed, i think it was 6x and that the lowest option i have

---

### Post by James78 on 2010-05-09
Your computer may simply just hate your CD-ROM drive or your disk, or even something about the disk. But either way, I boot from USB, no wasted disks, you can delete the files when done, and you can put them back on. Of course it does require configuring the flash drives MBR though..

I have a certain DVD drive that whenever it burns something, it almost never burns it correctly. I don't know why, but that's just the way it is. Sometimes it's the brand of the media, quality, the computer, or the drive, you never really can tell, but if it continues on usually it won't work again. You could try cleaning the lense and see if that helps. Perhaps with a cutip, don't blame me if the lense gets scratched and wrecked though, it's a dangerous thing to try to clean leanses, as they're really fragile.

---

### Post by elliotn on 2010-05-09
oh and i just updated the burner firmware in windows, wonder it will take effect in linux

---

### Post by CharlesA on 2010-05-09
Firmware is global - not OS dependant.

Try a different burner, could be a combination of the drive, and the media.

If you were able to get into linux, you could run md5sum on the cd.

---

### Post by elliotn on 2010-05-13
i tried installing it via wubi

i use unetbootin to convert the iso into usb.

Use wubi.exe but it fails.
So i guess the iso is faulty

---

