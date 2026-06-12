---
title: "Ubuntu 11.10 and (U)EFI Issues"
date: 2012-01-12
forum: General Help
---

### Post by maxietom on 2012-01-12
I recently got a new motherboard for my computer. I've been trying to UEFI boot because I really wan't to get off of BIOS boot before I have too much stuff on my hard drive, and it's becoming slightly more mainstream.

So, I plugged in my LiveUSB, booted off UEFI, and followed a few guides to converting an MBR hard drive to GPT. I did do it successfully. I then install Grub-EFI, and it also worked... Sort of... It would boot into the EFI file, and display the menu, but I couln't get past the purplish screen. So, I checked my Grub.cfg and found that it still used the msdos instead of gpt. So I switched that, added a few EFI needed things, and it still wouldn't boot. I checked my fstab, and it had a few errors. So then it would boot.

While I was upgrading everything, I decided to update my BIOS. It went perfectly fine, and I restored my settings. However, the option to boot my ESP was gone. So, I tried reinstalling grub-efi, and it didn't work. I tried several other things related to grub, and it didn't work either. Then I found a guide for efibootmgr, and I got it to boot. However, I was back to Ubuntu not booting. I checked my fstab and Grub.cfg, but no errors were found. I tried to go into recovery or text boot, but they both couldn't get past grub. Even the MemCheck didn't work.

So, I tried reinstalling grub since I thought it was a grub issue. It didn't work. I tried to use efibootmgr, but it didn't work still. I then tried an Ubuntu upgrade to 11.10 from 11.10. After that, it booted into grub, but Ubuntu wouldn't boot. I tried to install grub again, but now I'm stuck at a grub rescue prompt saying "Error: File not Found."

So, is there anything I can do to fix this? Or should I revert back to MBR? I don't want to go back, because it worked before, and I'm sure it will still work.

---

### Post by oldfred on 2012-01-13
Post this,  the test version of boot script now parses efi partitions and has some other improvements.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Standard version with instructions:
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

### Post by maxietom on 2012-01-14
I found the problem. I had deleted a few files in my ESP partition that were needed by my GRUB2 install. Ubuntu boots fine now. :)

I also fixed a few BIOS settings reguarding the boot order. The efibootmgr messed with a few things, so when I'd plug in my Live USB, the hard disk order would mix up. This screwed up GRUB, so it wouldn't boot.

---

