---
title: "Recover a lost file from pen drive"
date: 2011-11-17
forum: General Help
---

### Post by Maro848 on 2011-11-17
Hey guys I have accidentally deleted a file from my usb drive that I need for a project I am using Ubuntu 10.10 but have access to older releases and other distro's if needed. Please let me know what packages need to be installed and how to go about recovering my lost file. All help is appreciated in advance

---

### Post by coffeecat on 2011-11-17
First thing to say is that if you simply highlighted the file and used the keyboard delete key, and didn't empty the trash, the file will still be physically on the pendrive in a hidden folder. If this is so, plug the drive in and let it be mounted and then press ctrl-H in the Nautilus window to reveal hidden files/folders. Look for a folder called .Trash-1000. In that is a folder called files, and in that should be your "deleted" file.

If you did a GUI hard delete (shift+delete) or rm from the terminal, it will be deleted from the filesystem, and you will have to use recovery software. Don't use the pendrive to ensure that you don't overwrite the deleted file and have a look here:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Look at the photorec section, not testdisk. Photorec is effective but not especially friendly and will recover tens, hundreds or even thousands of deleted files. There may be a more user-friendly app that you can use in Windows, but I have no experience of one.

---

### Post by Maro848 on 2011-11-17
The file was deleted from the pendrive from a windows machine will Photorec still be able to get me the file?

---

### Post by coffeecat on 2011-11-17
I can't remember whether Windows deletes files in its Recycle bin when you unmount a pendrive but it might be worth looking for the file. Windows' method of hiding folders is different and its hidden folders are fully visible in Ubuntu. If I remember correctly, the folder that Windows creates is called RECYCLE BIN or $RECYCLE BIN. Have a look in there. Or simply plug the pendrive into Windows and see if there is anything in the recycle bin.

But to answer your question, yes, photorec should be able to find files deleted in Windows. That is, if they are really deleted and not lurking in the trash/recycle bin.

**EDIT**: by the way, photorec doesn't preserve the original filenames and it can recover a large but incomplete set of filetypes. From the package description: 

> PhotoRec is file data recovery software designed to recover
 lost pictures from digital camera memory or even Hard Disks.
 It has been extended to search also for non audio/video headers.
 It searchs for following files and is able to undelete them :
 * Sun/NeXT audio data (.au)
 * RIFF audio/video (.avi/.wav)
 * BMP bitmap (.bmp)
 * bzip2 compressed data (.bz2)
 * Source code written in C (.c)
 * Canon Raw picture (.crw)
 * Canon catalog (.ctg)
 * FAT subdirectory
 * Microsoft Office Document (.doc)
 * Nikon dsc (.dsc)
 * HTML page (.html)
 * JPEG picture (.jpg)
 * MOV video (.mov)
 * MP3 audio (MPEG ADTS, layer III, v1) (.mp3)
 * Moving Picture Experts Group video (.mpg)
 * Minolta Raw picture (.mrw)
 * Olympus Raw Format picture (.orf)
 * Portable Document Format (.pdf)
 * Perl script (.pl)
 * Portable Network Graphics (.png)
 * Raw Fujifilm picture (.raf)
 * Contax picture (.raw)
 * Rollei picture (.rdc)
 * Rich Text Format (.rtf)
 * Shell script (.sh)
 * Tar archive (.tar )
 * Tag Image File Format (.tiff)
 * Microsoft ASF (.wma)
 * Sigma/Foveon X3 raw picture (.x3f)
 * zip archive (.zip)

---

### Post by Maro848 on 2011-11-21
ok I just got this done and found the file I am VERY sorry for the delay in response as I have been busy all weekend with a friends wedding but thank you very much for your assistance!

---

### Post by coffeecat on 2011-11-21
I'm glad you recovered your file.

Good luck!

---

