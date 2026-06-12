---
title: "i have created a small command of thing i need"
date: 2010-02-22
forum: General Help
---

### Post by aviramof on 2010-02-22
what do you think about it and is there something i need to add or fix

sudo aptitude install ubuntu-restricted-extras p7zip-full p7zip-rar gparted startupmanager miredo gnome-device-manager smplayer python python-gtk2 intltool gettext nfoview pidgin assogiate fusion-icon simple-ccsm emerald rar gimp w32codecs && cd ~/.fonts && sudo aptitude install xfonts-terminus && sudo fc-cache -fv  

the final part is related to this guide:
[http://www.64bitjungle.com/ubuntu/view-and-render-nfo-files-correctly-in-ubuntu-with-nfo-viewer/](http://www.64bitjungle.com/ubuntu/view-and-render-nfo-files-correctly-in-ubuntu-with-nfo-viewer/)

i'm hopping i did it right.

and what about this how can i add what i need from here to this command?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

i'm using lucid.

thanks in advance.

here is a longer command:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update && sudo apt-get remove gnash gnash-common libflashsupport  mozilla-plugin-gnash swfdec-mozilla && sudo aptitude install ubuntu-restricted-extras p7zip-full p7zip-rar gparted startupmanager miredo gnome-device-manager smplayer python python-gtk2 intltool gettext nfoview pidgin assogiate fusion-icon simple-ccsm emerald rar gimp w32codecs skype alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs icedtea6-plugin unrar && cd ~/.fonts &&  sudo aptitude install xfonts-terminus && sudo fc-cache -fv

---

### Post by blazemore on 2010-02-22
It's a matter of personal preference.
Technically the command will work, but what you install is totally up to you.

---

### Post by aviramof on 2010-02-22
i know this the question is did i wrote the larger command properly or do you think something there might cause damage?

and also do you have some recommended software that maybe i don't know about them.

---

### Post by kellemes on 2010-02-22
> **aviramof said:**
> i know this the question is did i wrote the larger command properly or do you think something there might cause damage?

The simple fact you're asking this question proves you better use small steps to setup your system..
A long chain of commands like this should be used only when you know what you're doing.
Well, my opinion anyway.. ;-)

---

### Post by aviramof on 2010-02-22
i'm trying to create a command that i could use if i need to install ubuntu again this command include all the softwares i need and some extra codecs and etc from guides in this forum so any help would be appriciated.

---

### Post by ron999 on 2010-02-22
Hi
Instead of installing p7zip-full, p7zip-rar, rar and unrar you can just install **file-roller**.
This puts an Archive Manager in your Accessories manager and installs all the required compression tools.
It's up to you though.

> File-roller supports the following formats:
 * Tar (.tar) archives, including those compressed with
   gzip (.tar.gz, .tgz), bzip (.tar.bz, .tbz), bzip2 (.tar.bz2, .tbz2),
   compress (.tar.Z, .taz), lzop (.tar.lzo, .tzo) and lzma (.tar.lzma)
 * Zip archives (.zip)
 * Jar archives (.jar, .ear, .war)
 * 7z archives (.7z)
 * iso9660 CD images (.iso)
 * Lha archives (.lzh)
 * Single files compressed with gzip (.gz), bzip (.bz), bzip2 (.bz2),
   compress (.Z), lzip (.lz), lzop (.lzo), lzma (.lzma) and xz (.xz)

File-roller doesn't perform archive operations by itself, but relies on
standard tools for this.


---

### Post by aviramof on 2010-02-22
i don't see that he support rar files most of the files on my computer are rar's i don't mind not to compress new files with rar but i still 
need to be able to extract rar's.

---

### Post by ron999 on 2010-02-22
My bad.
If you need to create rar archives then you need to install rar also.

---

### Post by oldos2er on 2010-02-22
Why the "cd ~/.fonts"? The rest of it seems fine.

---

### Post by aviramof on 2010-02-22
i took it from here:
[http://www.64bitjungle.com/ubuntu/view-and-render-nfo-files-correctly-in-ubuntu-with-nfo-viewer/](http://www.64bitjungle.com/ubuntu/view-and-render-nfo-files-correctly-in-ubuntu-with-nfo-viewer/)

altoughe now that i think of it maybe it does redandent now that i'm using sudo aptitude install xfonts-terminus and not 
wget [http://fractal.csie.org/~eric/Terminus.ttf](http://fractal.csie.org/~eric/Terminus.ttf) am i right?

and again if you have good software to recommend i would love to hear about them.

---

### Post by colobix on 2010-02-22
Sir. Why don't you just make a dvd backup disc instead of working forever with this command. It takes you like 2 minutes.
Use remastersys or whatever you want.

---

### Post by oldos2er on 2010-02-22
> **aviramof said:**
> i took it from here:
[http://www.64bitjungle.com/ubuntu/view-and-render-nfo-files-correctly-in-ubuntu-with-nfo-viewer/](http://www.64bitjungle.com/ubuntu/view-and-render-nfo-files-correctly-in-ubuntu-with-nfo-viewer/)

altoughe now that i think of it maybe it does redandent now that i'm using sudo aptitude install xfonts-terminus and not 
wget [http://fractal.csie.org/~eric/Terminus.ttf](http://fractal.csie.org/~eric/Terminus.ttf) am i right?

and again if you have good software to recommend i would love to hear about them.

 Yes, the "cd ~/.fonts" in your original command is pointless. It won't hurt anything, but there's really no need for it.

Look into Synaptic's 'Save markings' option, under the File menu. It's a somewhat simpler method of keeping track of packages you've installed.

---

### Post by aviramof on 2010-02-23
thank you very much.

---

