---
title: "How Do I Install A tar.gz File On Ubuntu?"
date: 2012-06-13
forum: General Help
---

### Post by Cyanarchy on 2012-06-13
I've downloaded a file named anomos-linux.tar.gz from this website: [http://anomos.info/wp/downloads/](http://anomos.info/wp/downloads/). 

After months of trying to find a way to install it, all I've really learned to do is to extract the files. I've looked through many tutorials, they usually involve the terminal, but I always end up with errors. Can anyone here help me?

---

### Post by Sylos on 2012-06-13
Hello there.

a tar file is just a compressed archive (like a zip file in windows). In order to install whatever is inside you should uncompress the archive and then look for a read me file for how to install it. Or it may just have a .sh file that you can execute directly.

I should point out that you should always be shure about what you are downloading and installing when you are installing stuff that isnt from the repos - make shure you can trust the source.

Cheers

---

### Post by dniMretsaM on 2012-06-13
> **Cyanarchy said:**
> I've downloaded a file named anomos-linux.tar.gz from this website: [http://anomos.info/wp/downloads/](http://anomos.info/wp/downloads/). 

After months of trying to find a way to install it, all I've really learned to do is to extract the files. I've looked through many tutorials, they usually involve the terminal, but I always end up with errors. Can anyone here help me?

First, re-download the file and check the SHA256 checksum (scroll down on the download page, you will see them listed). If you don't get any errors, extract the file and go into it (in the terminal). Look at the files for something like README or INSTALL and read the contents. Follow the instructions therein. I usually requires something similar to this:
```
./configure
make
sudo make install
```If you have any questions or get any errors, feel free to post back here.

> **Sylos said:**
> I should point out that you should always be shure  about what you are downloading and installing when you are installing  stuff that isnt from the repos - make shure you can trust the source.

Cheers

I searched for it in the repos and it doesn't appear to be there. But yes, always look there.

---

### Post by kanikilu on 2012-06-13
What have you done so far? I've never heard of this software before now, but was easily able to get it downloaded and started using the instructions on the website. There is no compilation (make) or "install" necessary. Just download and run it with python...

Open a new terminal and do the following:

```
sudo apt-get install openssl python-m2crypto
cd ~/Downloads
wget http://anomos.info/releases/anomos-linux.tar.gz
tar zxvf anomos-linux.tar.gz
cd anomos/
python anondownloadgui.py
```

Each line above is a separate command, translation is:

1) Install requirements/prerequisites
2) Move to your downloads folder (optional)
3) Download the tar.gz package from the website using wget
4) Extract the downloaded package
5) Change into the newly-created "anomos" directory
6) Run the anomos graphical user interface

For what it's worth, torrents are blocked on the network I'm on now, so I couldn't actually test it, but the GUI does come up...

---

### Post by Cyanarchy on 2012-06-13
I seem to have very little understanding of all of this. There is a README file, but I don't understand it. I typed in the lines that I assume are supposed to be typed into the terminal but I received error messages about the lack of such a file or directory existing.

---

### Post by kanikilu on 2012-06-13
> **Sylos said:**
> I should point out that you should always be shure about what you are downloading and installing when you are installing stuff that isnt from the repos - make shure you can trust the source. Good point. I don't think it's in any main repos, but someone did package it on GetDeb.net:

[http://www.getdeb.net/software/Anomos](http://www.getdeb.net/software/Anomos)

Still, given that it's a relatively simple python application, I'm not sure I'd personally go to the trouble of adding the getdeb repos and installing it, but to each his own :)

---

### Post by dniMretsaM on 2012-06-13
> **Cyanarchy said:**
> I seem to have very little understanding of all of this. There is a README file, but I don't understand it. I typed in the lines that I assume are supposed to be typed into the terminal but I received error messages about the lack of such a file or directory existing.

What commands are you typing in and what are the errors?

---

### Post by Cyanarchy on 2012-06-13
> **kanikilu said:**
> What have you done so far? I've never heard of this software before now, but was easily able to get it downloaded and started using the instructions on the website. There is no compilation (make) or "install" necessary. Just download and run it with python...

Open a new terminal and do the following:

```
sudo apt-get install openssl python-m2crypto
cd ~/Downloads
wget http://anomos.info/releases/anomos-linux.tar.gz
tar zxvf anomos-linux.tar.gz
cd anomos/
python anondownloadgui.py
```Each line above is a separate command, translation is:

A million thanks sir, that seemed to work, will I have to use that last command to run it every time or is there a way to put it in the Applications menu?

---

### Post by kanikilu on 2012-06-13
> **Cyanarchy said:**
> A million thanks sir, that seemed to work, will I have to use that last command to run it every time or is there a way to put it in the Applications menu?
I don't see why you wouldn't be able to create a launcher. Just keep in mind that you'd need to put the full path to that .py file in the launcher, so if it's still in your Downloads folder, then it would be:

```
python ~/Downloads/anomos/anondownloadgui.py
```

---

