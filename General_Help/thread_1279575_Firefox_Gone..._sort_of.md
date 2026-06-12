---
title: "Firefox Gone... sort of?"
date: 2009-10-01
forum: General Help
---

### Post by mk_kano on 2009-10-01
So I booted up today and Firefox was gone. It was missing from my AWN dock, and from my Applications Menu. I tried reinstalling it, installing another version, and it won't show up any where. I instead installed A Browser, which is working now and oddly enough has all my firefox plugins and what not. However I would like to get firefox back. Any idea what happened/is happening?

I am running 9.04/64bit

---

### Post by tkelito on 2009-10-01
Have you tried running Firefox directly from Command Line.  If not and you are just looking for it in the graphical sense, open up terminal.

Applications > Accessories > Terminal

Run command "firefox %u"

If that opens the program, then we know it is installed just missing from the menus and panel.

---

### Post by mk_kano on 2009-10-01
Running from the command line doesn't work. I also tried using Synaptic to remove it, and then reinstall it, that didn't work either :(

---

### Post by zkriesse on 2009-10-01
If you cant see it try running it from the terminal...like the previous poster said. If that doesn't work than I don't know.

---

### Post by bwang on 2009-10-01
Try 
```
locate firefox
```
See if you get any results.
If not, you could always get the official version from Mozilla's website (which is faster, too).

---

### Post by tkelito on 2009-10-01
In terminal

sudo apt-get remove firefox

Just to make sure it is fully removed.

Then I would use your A Browser to navigate to [http://www.mozilla.com/products/download.html?product=firefox-3.5.3&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-3.5.3&os=linux&lang=en-US)

Get the latest version of 3.5.3 and install it, see what happens.

I know you tried to reinstall via apt-get or the package manager, but try downloading it manually as the tar.gz file.

---

