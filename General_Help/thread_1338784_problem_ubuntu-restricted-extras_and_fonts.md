---
title: "problem ubuntu-restricted-extras and fonts"
date: 2009-11-26
forum: General Help
---

### Post by bt101 on 2009-11-26
I tried installing ubuntu-restricted-extras on a 9.04 desktop machine and now every time I try and use apt it keeps trying to download font files.  If I try and install any other (unrelated) package, apt  goes back to trying to download fonts.  If I try and uninstall ubuntu-restricted-extras, apt goes back to that darn font download.  How do I fix this?

The machine is not connected to the internet.  Unlike MS Windows where I can just download software and go and install it, with linux I have to drive out the the linux machine, print a list of URIs to download, drive back to the location with internet and download the files, then drive back to the linux machine and install.  Aside from tripling my carbon footprint, this method was working OK.  For some reason, this package meeds a bunch of extra files.  So I need to figure out how to either:
a) unjamb apt
b) come up with another convoluted method (on top of my current convoluted method) of getting and installing these extra font files.

Thanks

---

### Post by Woody1987 on 2009-11-26
You will have to let apt finish its installation of the fonts, to do this you need internet.

---

### Post by bt101 on 2009-11-27
> **Woody1987 said:**
> You will have to let apt finish its installation of the fonts, to do this you need internet.

Thanks for the reply.  The internet won't be possible.  Is there no way to fix it other than reinstalling linux, or ... installing Windows?

---

### Post by Dennis N on 2009-11-27
If you had internet access for the machine in question, there is a script available that will download the ttf-mscorefonts correctly. Since you don't have an internet connection, you probably can simply uninstall the ttf-mscorefonts-installer, since that is a preliminary step to running the script. This probably will stop the attempted font installions you are seeing.

```
sudo apt-get remove ttf-mscorefonts-installer
```

If you want the script later to install the fonts, it can be found here:

[install ttf-mscorefonts]("http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/")

(If you have an Windows machine, you can also get the fonts from there as well by copying.)

---

### Post by bt101 on 2009-11-27
> **Dennis N said:**
> If you had internet access for the machine in question, there is a script available that will download the ttf-mscorefonts correctly. Since you don't have an internet connection, you probably can simply uninstall the ttf-mscorefonts-installer, since that is a preliminary step to running the script. This probably will stop the attempted font installions you are seeing.

```
sudo apt-get remove ttf-mscorefonts-installer
```

If you want the script later to install the fonts, it can be found here:

[install ttf-mscorefonts]("http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/")

(If you have an Windows machine, you can also get the fonts from there as well by copying.)

Thanks that worked great.  It has saved me a lot of time.

---

