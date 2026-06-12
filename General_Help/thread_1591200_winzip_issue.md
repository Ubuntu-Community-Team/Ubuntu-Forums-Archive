---
title: "winzip issue"
date: 2010-10-08
forum: General Help
---

### Post by manikishorepulikonda on 2010-10-08
Archive:  /home/kishore/Desktop/wrar391.exe
[/home/kishore/Desktop/wrar391.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/kishore/Desktop/wrar391.exe or
          /home/kishore/Desktop/wrar391.exe.zip, and cannot find /home/kishore/Desktop/wrar391.exe.ZIP, period.


i am not able to extract the files in ubuntu can you tell me when i click archieve manager i am getting this error and which software i have to download for the zip files to be extract in ubuntu

---

### Post by Rmantingh on 2010-10-09
Try installing p7zip-full and p7zip-rar.

  sudo apt-get install p7zip-full p7zip-rar

I think they will allow you to open most archives including .exe files.

---

### Post by gandaran on 2010-10-09
> wrar391.exe
you need to install wine to run windows .exe files.

---

### Post by manikishorepulikonda on 2010-10-09
> **Rmantingh said:**
> Try installing p7zip-full and p7zip-rar.

  sudo apt-get install p7zip-full p7zip-rar

I think they will allow you to open most archives including .exe files.

can you please provide me the extract of zip files software download so that it would be better to me for the extraction of the zip files in ubuntu. and more over i am unable to play my dvd in the ubuntu can  u suggest me what to do in this case mep4 plugins are missied and aob file format is there.

---

### Post by Rmantingh on 2010-10-09
I'm not sure what you mean with your first sentence.

For playing DVD's install package ubuntu-restricted-extras.
Run following command in a command terminal (menu Applications -> Accessories -> Terminal):-

  sudo apt-get install ubuntu-restricted-extras

An extract of the description of this package:-
===========================================================================
Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio
files), and DVD playback.

Please note that this does not install libdvdcss2, and will not let you play
encrypted DVDs. For more information, see
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
===========================================================================

MPEG-4 files should be playable after installing ubuntu-restricted-extras.

I've never heard of aob files. Can't help you there.

---

### Post by oldos2er on 2010-10-09
Is wrar391.exe the actual winzip program, or is it an archive of it? Ubuntu already comes with zip and unzip (and many other compression apps) installed as CLI apps. If you want graphical, look for File Roller in menus Applications, Accessories.

---

### Post by Mark Phelps on 2010-10-09
That file is almost certainly the installer for WinRAR v3.91 -- and as previously said, can only be run AFTER you install Wine because it is an MS Windows executable, not Linux.

You would do far better NOT messing around with Wine and simply installing the archive-handling packages in Ubuntu, especially unrar.

---

