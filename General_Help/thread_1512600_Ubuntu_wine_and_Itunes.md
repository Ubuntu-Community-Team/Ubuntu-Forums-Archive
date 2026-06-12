---
title: "Ubuntu wine and Itunes"
date: 2010-06-18
forum: General Help
---

### Post by medphys on 2010-06-18
Greetings all;

I installed latest version of Wine on my Toshiba Textra laptop (9.10 Ubuntu) last night and tried to install the latest version of Itunes 9.2 on it. I keep getting errors that Itunes was not configured and to reinstall.  I did that about 4 times last night but to no avail.  

I removed Wine from the computer and to my suprise when I opened up Applications, I still saw the wine app still there along with the Itunes folders and everything it downloaded.

I would like to start over just with Wine, until I do some research as to how to install Itunes properly if at all.  

My question is, how do I get rid of the Wine application in Applications and insure everything is removed (wine and Itunes and associated programs so that I can do a fresh install of Wine?

---

### Post by ajgreeny on 2010-06-18
Uninstall wine with ```
sudo apt-get remove wine
``` though it sounds as if you already did that, then delete the hidden folder in your home **/home/user/.wine**

Now reinstall wine and try again.  I don't know if iTunes comes as an .exe setup file, but if so, in terminal, navigate to the folder where you have the itunes.exe and then run ```
wine itunes.exe
``` or whatever the file is named, or simply right click on the .exe and chose "Open with wine"

I have no idea about iTunes in wine, as I have never ever used, it even in windows all those years ago when I used that.

---

### Post by realzippy on 2010-06-18
AFAIK-someone will correct me?- itunes does not run correctly under wine.
No way so far...


Get rid of wine:
[http://ubuntuforums.org/showthread.php?t=1340955](http://ubuntuforums.org/showthread.php?t=1340955)

---

### Post by instinct46 on 2010-06-18
I've tried for a while with an epic fail with wine and Itunes, and I tried quite a few software packages before I found one which works perfectly, Floola.

I know you asked about removing wine just thought this may help in the future.

---

