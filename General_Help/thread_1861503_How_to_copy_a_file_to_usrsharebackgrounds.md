---
title: "How to copy a file to /usr/share/backgrounds?"
date: 2011-10-15
forum: General Help
---

### Post by mr.interested on 2011-10-15
Hi,

I'm trying to change login background in Ubuntu 11.10 using [this]("http://www.omgubuntu.co.uk/2011/10/simple-lightdm-manager-lets-easily-tweak-ubuntu-11-10-login-screen/") software. Because my home directory is encrypted, it is suggested to copy a wallpaper to /usr/share/backgrounds using the command

 ```
sudo cp /home/username/pic.jpg /usr/share/background/pic.jpg
```

The file is copied, its size is correct, but it looks as if it's corrupted, as when opening it I have the following error:

> Could not load image 'pic.jpg'.

Failed to open input stream for file

How can I correctly copy the file?

Best

---

### Post by dcstar on 2011-10-15
> **mr.interested said:**
> Hi,

I'm trying to change login background in Ubuntu 11.10 using [this]("http://www.omgubuntu.co.uk/2011/10/simple-lightdm-manager-lets-easily-tweak-ubuntu-11-10-login-screen/") software. Because my home directory is encrypted, it is suggested to copy a wallpaper to /usr/share/backgrounds using the command

 ```
sudo cp /home/username/pic.jpg /usr/share/background/pic.jpg
```

The file is copied, its size is correct, but it looks as if it's corrupted, as when opening it I have the following error:



How can I correctly copy the file?

Best

Try:
```
gksudo nautilus
```

---

### Post by mr.interested on 2011-10-16
> **dcstar said:**
> Try:
```
gksudo nautilus
```

Many thanks for that, it worked. Just a quick note to everyone interested. You also need to change the permissions of the file to read-only (as per image below) to be accessible once you close the window that you opened using the command "gksudo nautilus".

[[URL=http://imageshack.us/photo/my-images/824/screenshotat20111016090.png/][IMG]http://img824.imageshack.us/img824/3888/screenshotat20111016090.th.png[/IMG]]("http://imageshack.us/photo/my-images/824/screenshotat20111016090.png/")
[/URL]

---

