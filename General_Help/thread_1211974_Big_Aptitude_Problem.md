---
title: "Big Aptitude Problem"
date: 2009-07-13
forum: General Help
---

### Post by dellwood on 2009-07-13
Hi, 

When I got to work this morning, I found that none of my perl scripts were working, because the perl interrupter was not being found in '/usr/bin/perl.'  I looked around and couldn't find it anywhere.  So, I decided to reinstall perl (sudo apt-get remove perl && sudo apt-get install perl) when all hell broke loose.  The remove started removing packages that seemed (at least to me) not to do anything with perl, so I stopped the remove about 15 seconds in. Now, I get this error when I try to do anything with aptitude, I get something like the following: 

for **sudo apt-get -f install**

I get this: [http://picasaweb.google.com/luskjh/Pictures#slideshow/5357923104869725042](http://picasaweb.google.com/luskjh/Pictures#slideshow/5357923104869725042)

I would have just copied the output, but gnome-terminal won't open and xterm won't copy and paste.  Like I said, all hell has broken loose... :(.

Anyway, all help is greatly appreciated :).

-Josh

---

### Post by geirha on 2009-07-13
> **dellwood said:**
> Hi, 

When I got to work this morning, I found that none of my perl scripts were working, because the perl interrupter was not being found in '/usr/bin/perl.'  I looked around and couldn't find it anywhere.  So, I decided to reinstall perl (sudo apt-get remove perl && sudo apt-get install perl) when all hell broke loose.  The remove started removing packages that seemed (at least to me) not to do anything with perl, so I stopped the remove about 15 seconds in. Now, I get this error when I try to do anything with aptitude, I get something like the following: 

for **sudo apt-get -f install**

```
sudo aptitude reinstall perl
``` doesn't help much either I take it?

It sounds like you have a chicken and the egg problem as it appears perl is vital for the package manager to do its magic. One way that **might** get things back to normal is to boot the ubuntu cd. In the live session, mount the root filesystem to /mnt (or wherever), then copy all files from the live session's perl. This may possibly break things even more, so make sure you **backup** all vital data before you attempt this.
```

dpkg -L perl | while read file; do 
    if [ -d "$file" ]; then 
        [ -d "/mnt/$file" ] || sudo mkdir "/mnt/$file"
    else
        sudo cp -dp "$file" "/mnt/$file"
    fi
done

```

Then boot back to your system and try ```
sudo apt-get -f install
```   again, and then ```
sudo aptitude reinstall perl
```

It's possible you need to do the same with other packages. Check /var/log/dpkg.log to see what packages were uninstalled when you attempted to remove perl.

For later though. Doing a remove followed by an install is rarely necessary, and is prone to breakage, especially with such an important package as perl. Just do aptiture reinstall instead.

> **dellwood said:**
> 
I would have just copied the output, but gnome-terminal won't open and xterm won't copy and paste.  Like I said, all hell has broken loose... :(.


Sure you can copy and paste from xterm. Just mark the text with the left mouse button, and paste it by clicking the middle button ... or was that what was not working?

---

### Post by dellwood on 2009-07-13
Thanks for the reply.  I'm going to get one of the IT guys here first, just so they can only blame me for the perl part in case the other part goes awry :D.  I'll try what you said after, though. And yea, no middle-button pasting :(.

-Josh

---

### Post by HotForLinux on 2009-07-13
shouldn't it be:

> if [ -d "$file" ]; then 
        [ -d "/mnt/$file" ] || sudo mkdir [COLOR=Red]-p[/COLOR] "/mnt/$file"
?


---

### Post by geirha on 2009-07-14
> **HotForLinux said:**
> shouldn't it be:

Well, the -p won't hurt, but I do not think it is necessary. I've checked the dpkg -L output of several packages, and in all cases, whenever a directory was listed, all the parent directories had already been listed.

---

### Post by HotForLinux on 2009-07-14
Geirha: You are probably right. I just didn't check the order they appeared in the output list or didn't  want to assume that that order was always present.

---

