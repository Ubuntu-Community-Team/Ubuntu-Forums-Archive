---
title: "Problem in downloading: Need [CAUTION] &quot;unconventional&quot; [/CAUTION] help!"
date: 2010-07-02
forum: General Help
---

### Post by madmax.santana on 2010-07-02
Hello!
I was trying to download the Source Code for XScreenSaver. It is available at the following page.

[http://www.jwz.org/xscreensaver/download.html](http://www.jwz.org/xscreensaver/download.html)

But there is some problem with our server. It is not letting me download the files with extensions .gz

The best option in my mind is to ask if any of you guys take some time out for me, download that tarball, extract it, convert it to simple rar format and then upload it to some fileserver, (like mediafire perhaps), then pass me the link.

That would be great help. Thanks.

---

### Post by WorMzy on 2010-07-02
[http://www.megaupload.com/?d=N4XOZDU0]("http://www.megaupload.com/?d=N4XOZDU0")
It's in tar.bz2 format, as I don't have unrar installed.

---

### Post by bodhi.zazen on 2010-07-02
Why are you running X on a server ?

If you want a graphical config tool, use webmin.

Why do you need to compile X screensaver form source on a server ? Another decision you should reconsider. I strongly discourage installing gcc , make, etc on a server. What feature could you possibly need the you have to compile xscreensaver ?

If you must, what prevents you from downloading and re-packaging the source code yourself ?

---

### Post by madmax.santana on 2010-07-02
> **bodhi.zazen said:**
> Why are you running X on a server ?

If you want a graphical config tool, use webmin.

Why do you need to compile X screensaver form source on a server ? Another decision you should reconsider. I strongly discourage installing gcc , make, etc on a server. What feature could you possibly need the you have to compile xscreensaver ?

If you must, what prevents you from downloading and re-packaging the source code yourself ?
[COLOR=RoyalBlue]No actually I was trying to have a look on the source code of the screensavers so I can build one myself... :)
I am not sure if that is the same source I should be downloading but that was the only one I could think of!

EDIT: I am not running a server. I am running a desktop. True, it already came with xscreensaver installed. But as I told earlier, I am not using xscreensaver source to build the package, just to have a look at it.
[/COLOR]

---

### Post by bodhi.zazen on 2010-07-02
I guess I was confused when you said there was a problem with your server:

> But there is some problem with our server. It is not letting me download  the files with extensions .gz

To download and examine the source code for Ubuntu use apt-get:

Lots of information on this:

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

```
sudo apt-get install build-essential dpkg-dev
sudo apt-get depbuild xscreensaver
apt-get source xscreensaver
```[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/)

---

### Post by madmax.santana on 2010-07-02
Wow! Good... Thanks a lot...
I see your name here a lot. You must be one of those hardcore Ubuntu-ers who contribute 90% of our smooth Ubuntu experience... :)
Have a nice time.

[COLOR="SeaGreen"]EDIT: 
[/COLOR]
[COLOR="RoyalBlue"]When I said OUR SERVER, I actually meant that I am a part of a Local Area Network and we connect to internet through a server. And since it runs on Windows, it usually has many problems... :) 
[I tried to talk'em into converting to Linux. But they are stubborn Windows fans, or that I think... :P][/COLOR]

---

