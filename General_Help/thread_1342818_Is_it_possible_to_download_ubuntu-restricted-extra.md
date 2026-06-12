---
title: "Is it possible to download ubuntu-restricted-extras without installing?"
date: 2009-12-01
forum: General Help
---

### Post by emigrant on 2009-12-01
hi all,
im using a low bandwith mobile broadband directly connecting from my phone.
im wondering if it is possible to download ubuntu-restricted-extras as a package or whatever and keep safe, so it can be used in several machines which doesnt have interent.

thank you very much for your time.

:popcorn:

---

### Post by dvlchd3 on 2009-12-01
I believe if you run this command:
```

sudo apt-get update && sudo apt-get --download-only install ubuntu-restricted-extras
```

then check the /tmp directory for the package.  Make sure you copy it out of this directory as it will most likely get deleted after a reboot or `apt-get clean` is run.

---

### Post by emigrant on 2009-12-01
> **dvlchd3 said:**
> I believe if you run this command:
```

sudo apt-get update && sudo apt-get --download-only install ubuntu-restricted-extras
```then check the /tmp directory for the package.  Make sure you copy it out of this directory as it will most likely get deleted after a reboot or `apt-get clean` is run.

thanks.
how many files will it download?
and how to install after i save them in another folder.

---

### Post by chrisbay90 on 2009-12-01
Im not sure how many.

to install them either navigate to the folder you moved them to and click on the file you wish to install. If you want to install all of them at once then enter this in gnome terminal.

```
cd /path/to/folder
sudo dpkg -i *.deb
```

---

### Post by emigrant on 2009-12-01
thank you very much all :)

---

### Post by emigrant on 2009-12-01
by the way can these be installed in different version of ubuntu?
i mean karmic,jaunty,hardy etc...

---

### Post by mikewhatever on 2009-12-01
> **emigrant said:**
> by the way can these be installed in different version of ubuntu?
i mean karmic,jaunty,hardy etc...

That may be a problem, because different Ubuntu releases may need different versions of certain packages.

---

### Post by 73ckn797 on 2009-12-01
You can choose to down load package files only from Synaptic. Once you have selected the package and click on the apply button the window will have an option at the bottom to down load package only. I believe that this will not install anything but it will give you what you want.

---

### Post by ed-koala on 2009-12-01
Do not install a Karmic package on a Jaunty install, etc, etc. Each package is geared for the specific release/kernel/etc and it will cause issues, so for different versions you need the package for that version.

---

### Post by bhadresh_dahanuwala on 2009-12-15
Hi,

Is this possible for Ubuntu updates too?

If yes, how to save the file and then install later on?

Regards,
Bhadresh.

---

### Post by emigrant on 2009-12-15
yes this is posible. go to keryxproject.org for more info

---

### Post by markgrohl75 on 2009-12-15
thanks guys, you're always very helpful

---

