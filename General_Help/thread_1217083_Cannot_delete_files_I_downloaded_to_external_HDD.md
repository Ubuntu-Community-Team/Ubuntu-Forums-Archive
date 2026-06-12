---
title: "Cannot delete files I downloaded to external HDD"
date: 2009-07-19
forum: General Help
---

### Post by terrorhawk on 2009-07-19
Hey guys I need some help here, for sure.

Basically what happened is this:

I have two computers. One is a Toshiba Satellite L35 laptop that I run Ubuntu 9.04 on and the other is a desktop, a Dell Dimension 2400 with WIndows XP. I used to use the laptop as my torrent / all-around internet media machine. I liked it's download speed what not, and the Windows machine was my basic editing computer.

Problem: I downloaded two movies on the laptop, and moved them to my external HDD (it's formatted in NTFS, from this Dell and it's been this way since I got it). Now, on the Windows computer, when I plug the drive in they show up as blank "files" but have no extension and Windows media, even with these 3rd party codecs I've got, can't recognize and play the "files" (which are really movies). I can't delete them either.

My question: Does anyone know how I can fix this WITHOUT Ubuntu? I ask only because the hard drive on the laptop died, and I can't use it anymore... so I've gotta know if it can be done on Windows. I know this is a Linux forum, but it started with Linux so I'm hoping it can also be the solution. Could Ubuntu may have accidentally put on an extension to the file that maybe Windows XP can't recognize? I'm searching frantically for options, because I like my HDD's space and I don't want old stuff taking it up.

If someone can help me out, it'd be appreciated. Thanks guys...

- Kyle

---

### Post by coffeecat on 2009-07-19
I don't know why Windows can't read the files or delete them, but there is a way of using Ubuntu to try to delete them. Yes, I know the laptop is dead and that the Dell only has Windows.

Simply boot up with the live CD on the Dell. It won't affect your Windows installation - so long as you don't mount your Windows partition or start the installer! :wink: Now plug in and switch on the external drive and see if you can delete the files.

Going back to what happened to the files when you used the laptop to write them to the external hdd: You say that the laptop hdd died. Perhaps it was beginning to error when you did the copy to the hdd and either corrupted the files themselves or corrupted the parts of the filesystem that point to the files.

So - it might be an idea to do a chkdsk of the external hdd from Windows. Either before or after you try a delete in Ubuntu. I would certainly do a chkdsk after deleting them in Ubuntu (if that works) if only to reassure myself the NTFS filesystem is sound.

---

