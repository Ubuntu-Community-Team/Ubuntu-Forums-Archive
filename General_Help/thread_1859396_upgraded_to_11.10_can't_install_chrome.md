---
title: "upgraded to 11.10 can't install chrome"
date: 2011-10-13
forum: General Help
---

### Post by mortsemious on 2011-10-13
I just installed oneiric and tried to install chrome. I downloaded chrome, opened it with the software center, and then got an error message:
> The file "/home/username/downloads/google-chrome-stable_current_i386(1).deb

How do I get around this and install chrome?

---

### Post by xingular on 2011-10-13
Same problem with Opera here.

I solved doing this (installing manually) 

Open a new console window (control+alt+t).

sudo -i and enter your password

Type cd /home/username/downloads (to go to the directory)

Then write: sudo dpkg -i google-chrome-stable_current_i386(1).deb

Now I'm having problems with Banshee: mp3, mp4, avi files. I only have a white screen when I try to play one. But I think it was a problem with the internet conection during the installation (very slow).
Tomorrow I will try again re-installing Ubuntu.

---

### Post by mortsemious on 2011-10-13
Thank you:p

---

### Post by ruario on 2011-10-19
You can fix this long term and hence allow you to easily install chrome (or opera for that matter) via software center in the future.

Installer either xz-lzma or lzma. Alternatively just setup up a symlink as follows:

```

cd /usr/bin
sudo ln -s xz lzma

```

This will allow Gdebi and Software Centre to use xz to decompress the data.tar.lzma within some packages.

P.S. Here is the bug report if you want to track it [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188)

---

### Post by p2ranger on 2011-10-19
That worked thanks!

---

