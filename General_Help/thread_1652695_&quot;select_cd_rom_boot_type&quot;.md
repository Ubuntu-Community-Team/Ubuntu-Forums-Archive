---
title: "&quot;select cd rom boot type&quot;"
date: 2010-12-25
forum: General Help
---

### Post by princeofnam on 2010-12-25
I have an [http://www.tigerdirect.com/applications/SearchTools/item-Details.asp?EdpNo=3172644&sku=I69-2152&SRCCODE=LINKSHARE&cm_mmc_o=-ddCjC1bELltzywCjC-d2CjCdwwp&AffiliateID=X3Th4gZi_iQ-fa9gNl3FLtnKyMEagzTcBQ](http://www.tigerdirect.com/applications/SearchTools/item-Details.asp?EdpNo=3172644&sku=I69-2152&SRCCODE=LINKSHARE&cm_mmc_o=-ddCjC1bELltzywCjC-d2CjCdwwp&AffiliateID=X3Th4gZi_iQ-fa9gNl3FLtnKyMEagzTcBQ)

When I tried to install 64-bit 10.10 I get this error upon loading the live Cd

1.
2.
select cd rom boot type

Any ideas?

---

### Post by karthick87 on 2010-12-25
You have to set your cdrom as first boot device in your bios.

---

### Post by princeofnam on 2010-12-25
I believe it's already set that way.  it's indicated so in my BIOS and I actually just installed Windows XP via CD ROM

---

### Post by Serpher on 2010-12-25
What .iso file did you download?

---

### Post by princeofnam on 2010-12-25
the 64 bit 10.10 AMD64 one from the ubuntu site

ubuntu-10.10-desktop-amd64.iso

I tried to install 10.10 and 10.04 (both 64-bit) via usb and I got "boot error"

I'm not sure what's going wrong here.

---

### Post by princeofnam on 2010-12-25
if it clarifies matters I already have a copy of Windows XP installed on a separate HD from the one I want to install ubuntu on.

---

### Post by mcduck on 2010-12-25
How did you burn the installer disk? Did you burn it as a disk image, or did you use some "bootable CD" or similar option from the burning application? And did you,a t any point, extract the .iso file?

Also did you check the MD5 sum of the downloaded image file? (this is of course not necessary if you downloaded it using Bittorrent, as torrent protocol handles this automatically).

---

### Post by princeofnam on 2010-12-25
I followed the instructions as per Ubuntu's guide.  I downloaded the ISO from the site.  I put a blank disk into my cd rom drive and opened up CD/DVD creator.  I right clicked the ISO and selected write to disk.  Was I suppose to extract the ISO?

How do I check the MD5 of the downloaded image file?

---

### Post by karthick87 on 2010-12-25
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by princeofnam on 2010-12-25
Thanks. I checked the md5sum and it matched that of the hash list.

sushi@Tyrork:~/Downloads$ md5sum ubuntu-10.10-desktop-amd64.iso
1b9df87e588451d2ca4643a036020410  ubuntu-10.10-desktop-amd64.iso


Still confused about the error though.


Update: I just loaded the live cd into my laptop and it booted the installation perfectly fine.

---

### Post by mcduck on 2010-12-25
> **princeofnam said:**
> I followed the instructions as per Ubuntu's guide.  I downloaded the ISO from the site.  I put a blank disk into my cd rom drive and opened up CD/DVD creator.  I right clicked the ISO and selected write to disk.  Was I suppose to extract the ISO?

How do I check the MD5 of the downloaded image file?

Are you burning the disc in Ubuntu or in Windows?

If you use Vista or older, you could try [InfraRecorder]("http://infrarecorder.org/"). In Windows 7 you should be able to just right-click the .iso file and select "Burn disc image".

In Ubuntu you should just right-click the .iso file on your desktop/in the file browser and select "Write to Disc"

(and no, you are not supposed to extract the .iso file. It's just a common mistake people make, mostly because some file compression tools (like WinRAR) tend to give .iso files a zip icon.)

---

### Post by princeofnam on 2010-12-25
Weird.  Now when the error prompts I can type.  Anyway I typed "1" and it loaded.  I guess it was confused about which cd rom drive to boot to?

---

### Post by Alcareru on 2011-01-19
I have experienced the same issue. However, I experienced it with the 64-bit alternate installation cd. Choosing 2 seems to boot of from first bootable HDD partition. Choosing 1 prompts me with the normal menu where I first pick a language and then choose what I want to do (install, check cd, boot from first bootable HDD partition, etc.). I figured that was normal for alternative installation cd and it was just great HCI to not include any explanations for the choices, however, if this happens randomly to ppl and with regulardless of which type of 64bit installation cds they use, I'm not sure what's going on.
O.o

P.S.
I ran the cd-rom integrity test and it's all good.

---

### Post by Alcareru on 2011-01-19
(double posting)

---

### Post by Alcareru on 2011-01-19
I have experienced the same issue. However, I experienced it with the 64-bit alternate installation cd. Choosing 2 seems to boot of from first bootable HDD partition. Choosing 1 prompts me with the normal menu where I first pick a language and then choose what I want to do (install, check cd, boot from first bootable HDD partition, etc.). I figured that was normal for alternative installation cd and it was just great HCI to not include any explanations for the choices, however, if this happens randomly to ppl and with regulardless of which type of 64bit installation cds they use, I'm not sure what's going on.
O.o

P.S.
I ran the cd-rom integrity test and it's all good.

---

### Post by rawler on 2011-04-10
I managed to get past this. With some clues from windows-forums, it seems the Mac BIOS doesn't support all ISO-formats.

I extracted everything from the CD into a folder, and then repacked it into a new ISO with instructions from here: [http://www.linux.com/archive/feature/137524](http://www.linux.com/archive/feature/137524).

Good luck!

---

