---
title: "gfire (Xfire plugin for Pidgin) &quot;Connection reset by peer&quot;"
date: 2009-08-17
forum: General Help
---

### Post by Famicommander on 2009-08-17
Pidgin refuses to let me log into xfire on either my desktop or netbook (both running 9.04). It keeps saying "Connection closed by peer" and logging me back out.

I know there's nothing wrong with my account, because I logged into Windows and everything worked fine.

Anyone got any ideas?

I tried to reinstall the gfire plugin, and it didn't change anything. And I tried reinstalling Pidgin altogether, and that didn't help either.

I don't understand why it would do this on both of my computers. Is anyone else having an issue with gfire?

---

### Post by Famicommander on 2009-08-17
Sorry, that's "Connection closed by peer", not "rest". I don't know how to edit my topic title.

---

### Post by Bowlerhatted on 2009-08-17
I was having the same issue, and it's not just us.

[http://gfireproject.org/forums/viewtopic.php?f=3&t=489](http://gfireproject.org/forums/viewtopic.php?f=3&t=489)

> Short manual:


[LIST]
[*]Execute the command found on our downloads page
[*]Switch into the trunk directory
[*] Make sure you have the Pidgin development files installed
[*]Run *./configure --prefix=/usr* or *./configure --prefix=/usr/local* if you have installed Pidgin from a [http://www.pidgin.im]("http://www.pidgin.im/") package
[*]Run make
[*]Run (sudo) make install
[*]Restart pidgin
[/LIST]


---

### Post by Famicommander on 2009-08-17
> **Bowlerhatted said:**
> I was having the same issue, and it's not just us.

[http://gfireproject.org/forums/viewtopic.php?f=3&t=489](http://gfireproject.org/forums/viewtopic.php?f=3&t=489)

Not sure how to do that. Can you just give me a series of commands to copy/paste?

---

### Post by Bowlerhatted on 2009-08-17
> **Famicommander said:**
> Not sure how to do that. Can you just give me a series of commands to copy/paste?

"I was having the same issue" is probably a bit misleading -- I'm kinda just bashing my head against google to work out how to do those things. ;_; (hooray for only having been using ubuntu for a year!)

---

### Post by Famicommander on 2009-08-18
> **Bowlerhatted said:**
> "I was having the same issue" is probably a bit misleading -- I'm kinda just bashing my head against google to work out how to do those things. ;_; (hooray for only having been using ubuntu for a year!)
Well, let me know if you figure things out.

---

### Post by HiImTye on 2009-08-18
from the instructions, they want you to use the SVN located at the bottom of the download page. not sure of what svn program works for ubuntu, haven't needed one myself but I'm sure you can google ubuntu svn and get some results.

then you want to make sure you have the development files installed (which should be located on the svn)

etc..

---

### Post by LookTJ on 2009-08-18
It started happening to me today, Google landed me on this thread.

I will be following this thread for the solution.

---

### Post by Famicommander on 2009-08-18
> **HiImTye said:**
> from the instructions, they want you to use the SVN located at the bottom of the download page. not sure of what svn program works for ubuntu, haven't needed one myself but I'm sure you can google ubuntu svn and get some results.

then you want to make sure you have the development files installed (which should be located on the svn)

etc..

Again, I wouldn't know where to begin.

---

### Post by HiImTye on 2009-08-18
I've neither used svn nor gfire on Ubuntu as of yet so I really can't help much else. if you want to install the svn client type in a terminal (accessories > terminal)

```
sudo apt-get install subversion
```

somewhere in the program will be a 'host' or 'server' option. you want to add

```
svn co http://my-svn.assembla.com/svn/gfire
```

you want to switch to the trunk folder and download the package

you also want to make sure you have the development files installed

---

### Post by LookTJ on 2009-08-18
> **HiImTye said:**
> I've neither used svn nor gfire on Ubuntu as of yet so I really can't help much else. if you want to install the svn client type in a terminal (accessories > terminal)

```
sudo apt-get install subversion
```somewhere in the program will be a 'host' or 'server' option. you want to add

```
svn co http://my-svn.assembla.com/svn/gfire
```you want to switch to the trunk folder and download the package

you also want to make sure you have the development files installed
Well...

make doesn't work for me.  This is in trunk.
```
make: *** No targets specified and no makefile found.  Stop.
```

UPDATE: connfigure first then make :)

---

### Post by NJN on 2009-08-18
In case anyone is still having trouble with this, here are the commands that worked for me:

```
sudo aptitude install subversion pidgin-dev

cd /tmp

svn co http://my-svn.assembla.com/svn/gfire

cd gfire/trunk

./configure --prefix=/usr

make

sudo make install
```

Then restart pidgin

---

### Post by KindredCharles on 2009-08-18
> **NJN said:**
> In case anyone is still having trouble with this, here are the commands that worked for me:

```
sudo aptitude install subversion pidgin-dev

cd /tmp

svn co http://my-svn.assembla.com/svn/gfire

cd gfire/trunk

./configure --prefix=/usr

make

sudo make install
```

Then restart pidgin

Not only did this work great for me but it gave me features of gfire I was missing like showing buddy list for clans and friends of friends and peoples profile pics, Thank you so much!

---

### Post by jpeddicord on 2009-08-18
If it helps at all, gfire is available in the archives for Karmic (9.10, out in a few months).

---

### Post by Famicommander on 2009-08-19
> **KindredCharles said:**
> Not only did this work great for me but it gave me features of gfire I was missing like showing buddy list for clans and friends of friends and peoples profile pics, Thank you so much!

This also worked great for me, but since I didn't have intltools installed it made me do that in the middle of the process.

But thanks.

---

### Post by jpeddicord on 2009-08-19
0.8.3 seems to have been released. Supposedly fixes the issue, haven't tested it myself. Working to get it updated for Karmic.

---

### Post by m3ld4r10n on 2009-08-20
This was an issue not only for linux users but windoze users as well. My windozer wasn't able to connect to xfire until I patched to 0.8.3.

Just thought you'd like to know.

---

### Post by M03BIUS on 2009-08-21
I get an error window after login on Pidgin saying 

```
 **Error Reading gfire_games.xml** An error was ecountered reading your Gfire Games List. They have not been loaded, and the old file has been renamed to /home/MYUSER/.purple/gfire_games.xml~.
```


I'm sorry but...what do I do?

---

