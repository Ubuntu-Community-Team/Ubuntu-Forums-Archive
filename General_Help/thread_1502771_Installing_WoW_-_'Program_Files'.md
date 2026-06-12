---
title: "Installing WoW - 'Program Files'?"
date: 2010-06-06
forum: General Help
---

### Post by keish on 2010-06-06
Hi guys.

I've just installed Ubuntu on my laptop. This is the first time I've ever dealt with linux, and was very much a spur of the moment thing (probably not ideal, I know). My laptop is only small and does not have a disc drive.

I would like to install World of Warcraft onto my laptop. Usually my plan of action would be to pop the files under Program Files onto an external hard drive, then copy them over and voila.

I'm not 100% sure what the Ubuntu equivalent is to Program Files. Google search suggests usr/bin, but it requires permission to move files there and I'm really not sure how to go about doing this.

Any help would be really appreciated (remembering that I'm trying to copy over already installed files, not disc contents).

Cheers

Keish

---

### Post by Ozymandias_117 on 2010-06-06
You will need to install Wine to be able to run WoW

```
sudo aptitude install wine
```

I would suggest moving it to ~/.wine/ Er... I don't have Wine installed here. There is a Drive_C with Program files somewhere in there. the ~ is a shortcut for /home/user/ That's where Wine would put installs.

---

### Post by keish on 2010-06-06
> **Ozymandias_117 said:**
> You will need to install Wine to be able to run WoW

```
sudo aptitude install wine
```I would suggest moving it to ~/.wine/ Er... I don't have Wine installed here. There is a Drive_C with Program files somewhere in there. the ~ is a shortcut for /home/user/ That's where Wine would put installs.

Thanks for your help. I've installed wine and popped the files in there, however upon clicking the launcher I get this error message:

"Archive:  /home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe
[/home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe or
          /home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe.zip, and cannot find /home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe.ZIP, period."

---

### Post by Ozymandias_117 on 2010-06-07
> **keish said:**
> Thanks for your help. I've installed wine and popped the files in there, however upon clicking the launcher I get this error message:

"Archive:  /home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe
[/home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe or
          /home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe.zip, and cannot find /home/keish/.wine/dosdevices/c:/Program Files/World of Warcraft/Launcher.exe.ZIP, period."

Right click on it, Properties and check that in "Permissions" tab make sure "Allow executing file as program" is checked. Then go to  "Opens With" and make sure Wine Windows Program loader is selected.

---

