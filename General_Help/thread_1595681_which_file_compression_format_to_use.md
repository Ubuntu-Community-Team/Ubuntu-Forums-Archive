---
title: "which file compression format to use?"
date: 2010-10-13
forum: General Help
---

### Post by Ascenti0n on 2010-10-13
I notice in Nautilus file manager, if I right click on a directory, I can **'compress'** that file or directory. clicking this provides options for different compression formats, but how do I know which one to use?

Most of my files are data files, ie text. Though I do have photo/image folders and a music folder.

any advice?

---

### Post by TeoBigusGeekus on 2010-10-13
If you wish to share the archive with windows users, go for rar or zip.
If you want the archive for yourself or for sharing with linux users, go for tar(.bz/.gz).

---

### Post by Ascenti0n on 2010-10-13
What about zip, is that for Windows only?

I think most of the stuff I will be compressing will be for backups/archiving on Ubuntu, so if there is no difference between tar.gz and tar.bz2, I might stick to .gz, as I think that's what most people use?

---

### Post by coffeecat on 2010-10-13
> **Ascenti0n said:**
> What about zip, is that for Windows only?

I think most of the stuff I will be compressing will be for backups/archiving on Ubuntu, so if there is no difference between tar.gz and tar.bz2, I might stick to .gz, as I think that's what most people use?

I believe zip started as a Windows compression standard but Ubuntu, Windows and MacOS can unzup zip files so it's a convenient "universal" format. But if it's just for yourself I would go for gz or bz2. You get smaller archives with bz2, but it's a little slower. I tend to use .tar.gz for my purposes.

One advantage of tar.gz (and tar.bz2 I believe) is that MacOS can deal with them - if that's ever a consideration for you.

---

### Post by waltercool on 2010-10-13
Great compression: tar.bz2
Good and fastest compression: tar.gz (im actually compressing with targz, is fast and not bad)
Compatible method: zip (is badly, poor than tar.gz)

Im always using tar.gz, but sometimes im using tar.bz2, because WinRaR can open tar.bz2. A windows without WinRar just can use zip.

---

### Post by Refalm on 2010-10-13
I like 7z a lot. It has a high compression rate, and a lot of Windows users have WinRAR (can open 7z) or even 7-Zip itself installed.

---

### Post by The Cog on 2010-10-13
A tar file will save the unix file properties and permissions, and symlinks. These get lost with zip files.

---

