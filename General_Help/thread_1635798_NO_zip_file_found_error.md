---
title: "NO zip file found error"
date: 2010-12-02
forum: General Help
---

### Post by robertlucas on 2010-12-02
Hi i've just got Ubuntu 10.10 and I also downloaded the most recent version of Wine at the same time, but i've got 4 torrents i've downloaded and I can't run any of them this same message keeps coming up:

"Archive:  /home/thedemonkiller/Downloads/AnyDVD 6.7.1.0 + Key-[HB]/setup/SetupAnyDVD6710.exe
[/home/thedemonkiller/Downloads/AnyDVD 6.7.1.0 + Key-[HB]/setup/SetupAnyDVD6710.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/thedemonkiller/Downloads/AnyDVD 6.7.1.0 + Key-[HB]/setup/SetupAnyDVD6710.exe or
          /home/thedemonkiller/Downloads/AnyDVD 6.7.1.0 + Key-[HB]/setup/SetupAnyDVD6710.exe.zip, and cannot find /home/thedemonkiller/Downloads/AnyDVD 6.7.1.0 + Key-[HB]/setup/SetupAnyDVD6710.exe.ZIP, period.

No zipfiles found. "

does anyone know how to fix this or what the problem is? thanks

---

### Post by mcduck on 2010-12-02
You are trying to open the .exe files with the Archive Manager instead of Wine. ;)

(some .exe files are self-extracting zip files, so .exe files open with Archive Manager by default).

Try right-clicking on the .exe and specifically selecting to open it with Wine.

---

### Post by robertlucas on 2010-12-02
hi thanks for that...
just tried it and ti's came up with..

"The file '/home/thedemonkiller/Downloads/SlySoft.CloneDVD.v2.9.2.8.Multilingual.Incl.Keymaker(Murlok)/SetupCloneDVD2928Slysoft.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

suggestions how to get round this?

---

### Post by robertlucas on 2010-12-02
don't worry i've worked it out :D thanks anyway guys..

hay does anyone know if Any DVD and clone DVD and Nero work in Wine?

---

### Post by robertlucas on 2010-12-02
[SIZE=1]ok totally new question..
I've got rid of any DVD, clone DVD and nero and opeted just to used K9copy instead...
but every time i open it up it crashes
i read it's because i don't have "
[/SIZE][B][SIZE=1]libdvdcss-dev" installed but i can't find anywhere i can get it? can anyone help?
[/SIZE][/B]

---

### Post by coffeecat on 2010-12-02
> **robertlucas said:**
> [SIZE=1]
i read it's because i don't have "
[/SIZE][B][SIZE=1]libdvdcss-dev" installed but i can't find anywhere i can get it? can anyone help?
[/SIZE][/B]

You need libdvdcss2, not libdvdcss-dev. You can do one of two things.

1 - Add the [Medibuntu]("http://medibuntu.org/") repository and then install it from Software Centre or Synaptic. Look at the repository howto link on that page for adding Medibuntu.

or

2 - Run this code in a terminal:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```Also - make sure you've installed the ubuntu-restricted-extras package for libdvdread which you also need plus a load of restricted multimedia stuff. More here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Spyderkid on 2010-12-02
[check here about libdvdcss]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

