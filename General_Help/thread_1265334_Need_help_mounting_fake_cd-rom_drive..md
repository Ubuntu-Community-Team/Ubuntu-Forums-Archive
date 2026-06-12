---
title: "Need help mounting fake cd-rom drive."
date: 2009-09-13
forum: General Help
---

### Post by dragos240 on 2009-09-13
I want to mount a fake cd-rom drive that ubuntu can recognize and wine too. I want to burn a cdi to this using boot dreams. Rather than wasting disks, I want to create a simple, fake cd drive, how can I do this?

---

### Post by jflaker on 2009-09-13
If you use Virtualbox, you can do that...but the system can't be faked out.

Sorry

---

### Post by Shea7993 on 2009-09-13
Hey there

not too sure what your intentions are for this, but likewise i was looking for something similar, to mount my game ISO's to launch installation of games through PlayonLinux, my solution was getting G-mount ISO from the repository, and KISO to create and edit ISO's, maybe this will help, maybe im just not understanding your goal very clearly, either way, hope i was any help to you

---

### Post by falconindy on 2009-09-13
You mean you want to mount CD images?

Fusemounter will do that. [Here's](http://webupd8.blogspot.com/2009/03/mount-iso-files-linux-on-right-click.html) an easy way to set it up so you can just right-click on an .iso and mount it.

As for burning to a "fake" cd drive, I think you mean you just want to make an image.

---

### Post by StuartN on 2009-09-13
You can mount a CD iso image at a path that exists (e.g. ~/my_cd) like this:

```
mkdir ~/my_cd
sudo mount -t iso9600 -o loop my_cd.iso ~/my_cd

# and to un-mount when you have finished
sudo umount ~/my_cd
```

---

### Post by dragos240 on 2009-09-13
CDI files aren't cd image files, rather they are Pardus DiskJuggler files. to my knowledge, wine is the only way to burn these. What I need is a BLANK fake cd drive, I can't have anything premounted, like an iso file. I need to fake out wine into thinking there is a drive there.

---

### Post by sisco311 on 2009-09-13
> **dragos240 said:**
> CDI files aren't cd image files, rather they are Pardus DiskJuggler files. to my knowledge, wine is the only way to burn these. What I need is a BLANK fake cd drive, I can't have anything premounted, like an iso file. I need to fake out wine into thinking there is a drive there.

winecfg -> *Drivers* tab -> Add... -> select a path -> Show Advanced -> Type: CD-ROM

---

### Post by dragos240 on 2009-09-13
> **sisco311 said:**
> winecfg -> *Drivers* tab -> Add... -> select a path -> Show Advanced -> Type: CD-ROM

Hmm. I tried that, Bootdreams recognized the CD Drive, but it only detected my REAL cd drive when it asked for the drive to bun it to.

---

### Post by t.h.w. on 2009-11-29
> **dragos240 said:**
> Hmm. I tried that, Bootdreams recognized the CD Drive, but it only detected my REAL cd drive when it asked for the drive to bun it to.

Similar question here... 
DVD Decrypter (under Wine) gives an error-message on the fake-drive...:

I/O Error!
Device: [0:0:0] (L:)
CDB: 12 00 00 00 FC 00
Interpretation: Inquiry
Reason: Request not supported

Anyone a suggestion?

---

### Post by Dinodoc on 2009-11-29
Not sure if it still applies but I found this on google:

[http://www.poptix.net/CDI-HOWTO.txt](http://www.poptix.net/CDI-HOWTO.txt)

---

