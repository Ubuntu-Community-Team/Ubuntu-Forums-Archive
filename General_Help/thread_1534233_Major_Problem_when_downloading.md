---
title: "Major Problem when downloading"
date: 2010-07-19
forum: General Help
---

### Post by Uppercut on 2010-07-19
So, I just found out I have a major problem, whenever I try any sudo apt-get command I get a segmentation  failure error. Also I can't download any applications from the synaptic manager either. Whenever I start it the application immediatly shuts down without any warning.

What should I do about this? I can't download/upgrade/install any application, this is causing me many problems.

For example, I highly need to install an app to unrar some files. Whenever I try:
sudo apt-get install unrar 
all I get is:
Segmentation failure... 0%

Thanks!

---

### Post by MooPi on 2010-07-19
Have you tried? ```
sudo apt-get update 
```

---

### Post by Uppercut on 2010-07-19
Yeah, heres what I get:

```
Hit http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/main Translation-pt_PT
Ign http://archive.ubuntu.com jaunty/restricted Translation-pt_PT
Ign http://archive.ubuntu.com jaunty/universe Translation-pt_PT
Ign http://archive.ubuntu.com jaunty/multiverse Translation-pt_PT
Hit http://archive.ubuntu.com jaunty-updates Release.gpg
Ign http://archive.ubuntu.com jaunty-updates/main Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-pt_PT
Hit http://archive.ubuntu.com jaunty-security Release.gpg
Ign http://archive.ubuntu.com jaunty-security/main Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-security/universe Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-pt_PT
Hit http://archive.ubuntu.com jaunty-backports Release.gpg
Ign http://archive.ubuntu.com jaunty-backports/main Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-backports/restricted Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-backports/universe Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-backports/multiverse Translation-pt_PT
Hit http://archive.ubuntu.com jaunty-proposed Release.gpg
Ign http://archive.ubuntu.com jaunty-proposed/restricted Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-proposed/main Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-proposed/multiverse Translation-pt_PT
Ign http://archive.ubuntu.com jaunty-proposed/universe Translation-pt_PT
Hit http://archive.ubuntu.com jaunty Release
Hit http://archive.ubuntu.com jaunty-updates Release
Hit http://archive.ubuntu.com jaunty-security Release
Hit http://archive.ubuntu.com jaunty-backports Release
Hit http://archive.ubuntu.com jaunty-proposed Release
Hit http://archive.ubuntu.com jaunty/main Packages   
Hit http://archive.ubuntu.com jaunty/restricted Packages
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://archive.ubuntu.com jaunty/main Sources    
Hit http://archive.ubuntu.com jaunty/multiverse Sources
Hit http://archive.ubuntu.com jaunty/universe Sources
Hit http://archive.ubuntu.com jaunty/universe Packages
Hit http://archive.ubuntu.com jaunty/multiverse Packages
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://archive.ubuntu.com jaunty-updates/main Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.ubuntu.com jaunty-security/main Packages
Hit http://archive.ubuntu.com jaunty-security/restricted Packages
Hit http://archive.ubuntu.com jaunty-security/restricted Sources
Hit http://archive.ubuntu.com jaunty-security/main Sources
Hit http://archive.ubuntu.com jaunty-security/multiverse Sources
Hit http://archive.ubuntu.com jaunty-security/universe Sources
Hit http://archive.ubuntu.com jaunty-security/universe Packages
Hit http://archive.ubuntu.com jaunty-security/multiverse Packages
Hit http://archive.ubuntu.com jaunty-backports/main Packages
Hit http://archive.ubuntu.com jaunty-backports/restricted Packages
Hit http://archive.ubuntu.com jaunty-backports/universe Packages
Hit http://archive.ubuntu.com jaunty-backports/multiverse Packages
Hit http://archive.ubuntu.com jaunty-backports/main Sources
Hit http://archive.ubuntu.com jaunty-backports/restricted Sources
Hit http://archive.ubuntu.com jaunty-backports/universe Sources
Hit http://archive.ubuntu.com jaunty-backports/multiverse Sources
Hit http://archive.ubuntu.com jaunty-proposed/restricted Packages
Hit http://archive.ubuntu.com jaunty-proposed/main Packages
Hit http://archive.ubuntu.com jaunty-proposed/multiverse Packages
Hit http://archive.ubuntu.com jaunty-proposed/universe Packages
Hit http://archive.ubuntu.com jaunty-proposed/restricted Sources
Hit http://archive.ubuntu.com jaunty-proposed/main Sources
Hit http://archive.ubuntu.com jaunty-proposed/multiverse Sources
Hit http://archive.ubuntu.com jaunty-proposed/universe Sources
Falha de segmentaçãoacotes... 0%

```

Hence why I call it a major problem. I get this segmentation error everytime I try any apt-get command.

---

### Post by mr clark25 on 2010-07-19
does synaptic package manager work? (sometimes it can be better than using the terminal)


does aptitude work?

you can use it almost exactly like "apt-get"

```

sudo aptitude install unrar

```

---

### Post by Uppercut on 2010-07-19
> **mr clark25 said:**
> does synaptic package manager work? (sometimes it can be better than using the terminal)


does aptitude work?

you can use it almost exactly like "apt-get"

```

sudo aptitude install unrar

```

Nope, I get the exact same error with aptitude that I get with apt-get.

And as I said in the first post, the synaptic package manager doesn't work either. Whenever I try to start it, it just automatically shuts down without any warning or error.

This is really bugging me out, any other ideas?

---

### Post by techunit on 2010-07-19
I could you try the following command please

```
sudo dpkg --reconfigure -a
```

---

### Post by Uppercut on 2010-07-19
> **techunit said:**
> I could you try the following command please

```
sudo dpkg --reconfigure -a
```

Im gessing there is something wrong with that command, heres what I get.

```
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
```

---

### Post by Uppercut on 2010-07-20
Any ideas?

Im quite desperate right now :(

---

### Post by Uppercut on 2010-07-20
Ok, I can live with a broken synaptic manager, but is there a way I can open this rar file without using synaptic package manager or any console command?

---

### Post by oldos2er on 2010-07-20
> **Uppercut said:**
> Im gessing there is something wrong with that command

It should be **sudo dpkg --configure -a**

---

