---
title: "Debian package Google Earth - how do I run it"
date: 2010-06-13
forum: General Help
---

### Post by charonred on 2010-06-13
I've installed the '*utility to automatically build a Debian package of Google Earth*' via Software Center, but have no idea how to build the actual Debian package

---

### Post by medic2000 on 2010-06-13
Why are you using Debian package for Ubuntu. They are different even Ubunut based on Debian.

---

### Post by charonred on 2010-06-13
because when I looked for Google Earth in Lucid 10.04 Software Center, that was the option, so I installed it, but have no idea how to run it to build the actual .deb installer.

---

### Post by tom.swartz07 on 2010-06-13
> **charonred said:**
> I've installed the '*utility to automatically build a Debian package of Google Earth*' via Software Center, but have no idea how to build the actual Debian package

Rather than use that, perhaps the best method would be to install the actual program.

Make sure that you have the 'partner' repos added. Go to System>Administration>software sources

on the other sources tab, check the box for the partner repos. it should be the 2nd or 3rd in the list. the last word on the line is 'partner' check em all.

reload the data when you close it, and then search for Google Earth again in the software center. The full program should be there for you

---

### Post by wojox on 2010-06-13
The Google Earth package

```
sudo make-googleearth-package
```

```
sudo dpkg -i googleearth_**?**i386.deb
```

The question mark should be with whatever build number you have created. :p

---

### Post by charonred on 2010-06-13
tom.swartz07
tried that, but still only lists the package builder in Software Center and Synaptic

wojox
didn't work
```
~$ sudo make-googleearth-package
cat: /etc/mailname: No such file or directory
Refusing to run as root; use --force to override
```

---

### Post by wojox on 2010-06-14
Oops, no root, try 

```
make-googleearth-package --force
```

```
sudo dpkg -i *.deb
```

---

### Post by loyal one on 2010-06-14
I know this sounds too simple, but I just installed ver 3.0 google earth, so this will work. Google and navigte to to the google earth download site; select the version you want, note 32 bit or 64 bit. Download the selected file to a place you can find: maybe desktop or wherever. Locate the downloaded file on your hard drive or desktop; doubleclick the file; file roller will automatically install the program. 

Loyal

---

### Post by loyal one on 2010-06-14
You can also use this command: sudo apt-get install googleearth. This is from the sticky post in Forums, Multimedia and Video, near the end of the post. I have used this method as well. Sometimes, it is difficult to get the google earth site to respond and download, but this has always worked.
Loyal

---

### Post by charonred on 2010-06-14
thanks loyal one, but google earth site doesn't give me 32 or 64 bit options, only the same file I tried earlier.

thanks wojox, this worked
```
make-googleearth-package --force
```

and in this case
```
sudo dpkg -i *.deb
```

was
```
sudo dpkg -i googleearth_5.2.1.1329+0.5.7-1_amd64.deb
```

---

### Post by wojox on 2010-06-14
Your welcome charonred. :p

---

### Post by charonred on 2010-06-14
the more I 'fix' little hiccups/problems in Ubuntu, the more I love it - unlike Windows where your final way of fixing things is to re-install the whole OS.

I've also got a new Asus K52F Notebook with Win7 Home Premium 64bit, but it's also running a WUBI of Lucid 10.04 64bit - despite a few bugs to work out, guess which starts, runs and shuts-down faster ...

---

