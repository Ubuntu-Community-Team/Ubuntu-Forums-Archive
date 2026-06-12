---
title: "Creating my own shell script, need some help."
date: 2009-09-21
forum: General Help
---

### Post by rapt0rjezuz on 2009-09-21
First off, Hello!

I'm not entirely new to Linux but new enough and I just found out about shell scripts which I think are pretty functional. 

What I am trying to do is create a script that can download irssi (cli IRC client), some irssi scripts, create the directories for irssi and the scripts since irssi only creates its own "/.irssi" directory the first time you run it(not when you install it), then transfer the scripts to the "/.irssi/scripts" folder, and lastly remove the scripts.

The script installs irssi fine but doesn't seem to create the folders in the "/.irssi" directory thus not copying the scripts over to it. 

Heres the script so far..

```

#!/bin/bash

echo "Installing irssi..."
sudo aptitude install -y irssi

echo "Downloading some useful scripts..."
sudo wget http://scripts.irssi.org/scripts/nicklist.pl

echo "Creating irssi folders"
sudo mkdir /.irssi
sudo mkdir /.irssi/scripts
sudo mkdir /.irssi/scripts/autorun

echo "Copying scripts to /scripts..." 
sudo cp nicklist.pl /.irssi/scripts

echo "Cleaning up..."
sudo rm nicklist.pl

echo "Finished."

```

---

### Post by Bachstelze on 2009-09-21
You certainly don't want /.irssi, but ~/.irssi. And you don't need sudo.

---

### Post by rapt0rjezuz on 2009-09-21
> **Bachstelze said:**
> You certainly don't want /.irssi, but ~/.irssi. And you don't need sudo.
Ahh, thank you!

---

### Post by andrew.46 on 2009-09-23
Hi rapt0rjezuz,

A couple of small points only: rather than download the script and then move it you can use the -O option of wget to deposit the file wherever you wish. But probably a greater issue is that the Ubuntu repository carries a package that contains a great many scripts that *includes* the nicklist script that you have mentioned:

Filelist of package irssi-scripts in jaunty of architecture all
[http://packages.ubuntu.com/jaunty/all/irssi-scripts/filelist](http://packages.ubuntu.com/jaunty/all/irssi-scripts/filelist)

so you might be better to download this as well and use the script to make a link to the required script in $HOME/.irssi/scripts/autorun.

Andrew

---

