---
title: "installing skype"
date: 2006-02-19
forum: General Help
---

### Post by Maassive on 2006-02-19
I'm a complete newbie.. can you give me step-by-step instructions on installing skype.  I tried installing the debian package available on skype's website and was told it needed libraries which I can't find.  Thank You.

---

### Post by macdo on 2006-02-19
Have you uncommented the universe lines in /etc/apt/sources.list?

If not, then type in a console
 ```
sudo gedit /etc/apt/sources.list
```

Halfway down the page, there are two lines called 
# deb [http://archives.ubuntu.com](http://archives.ubuntu.com) breezy universe
# deb-src [http://archives.ubuntu.com](http://archives.ubuntu.com) breezy universe

(or something like that - I'm doing this from memory. Make sure that there is the  "universe" in them)

Delete the # at the beginning of the lines, save, close the file, and in the command line type
```
sudo apt-get update
```
Then try to install skype again.

HTH

-- 
macdo

---

### Post by aysiu on 2006-02-19
[Skype is not in the Universe repositories... or any Ubuntu repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=skype&searchon=name&subword=1&version=all&release=all).

Go to [the Skype homepage](http://www.skype.com/products/skype/linux/) and download the Fedore Core 3 package to your desktop.

Then open a terminal (Applications > Accessories > Terminal) and type ```
cd Desktop
sudo apt-get update
sudo apt-get install alien
sudo alien -i skype*.rpm
```

---

### Post by mappleJoe on 2006-02-20
Maassive: take a look at [Ubuntu PLF]("http://wiki.ubuntu-fr.org/doc/plf").

Basically, you need to add these lines to your /etc/apt/sources.list

# Ubuntu PLF
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

Then
```

apt-get update
apt-get install skype

```

I think this should do the trick and install Skype without problems.

This French site provides many interesting Ubuntu packages, check it out.

---

### Post by ronmarley1 on 2006-02-20
I'd get Automatix and let it install Skype for me. It worked for me.  See this thread to download [http://www.ubuntuforums.org/showthre...ight=automatix](http://www.ubuntuforums.org/showthre...ight=automatix)

Some folks don't like Automatix, but I do.  This is just my opinion (and I have to say this is my opinion, because somone will have a strong desire to reply to this post saying that the install of Automatix is crappy advice).
Good luck!

---

