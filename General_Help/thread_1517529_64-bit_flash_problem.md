---
title: "64-bit flash problem"
date: 2010-06-25
forum: General Help
---

### Post by GoldDragon on 2010-06-25
Solved!
Before upgrading to Ubuntu Lucid I had had problems with flash sound cutting out and installed 64-bit flash on my system using some instructions I'd found here on the forums. After upgrading I have the same sound problems.. it cuts off after a few minutes of using flash.
I decided to replace flash again but.. I'm not sure how to remove the previous install? I looked in the lib flash plugin folders and the libflashplayer.so files aren't in either the lib, 32 bit or 64 bit folders.. but flash still plays.
Can someone please tell me how I can remove it and so I can do a new install?

Thanks

---

### Post by xoomer.ap on 2010-06-25
Hi. What's name of browser that you using?

In Opera look in "About" page - here you'll find pathes where plugin might be.
In Firefox, I think - you should look at /usr/lib64 folder. Or somewhere near to this.

Btw, before installing 64-bit version you removed 32-bit?

---

### Post by howefield on 2010-06-25
Try this Firefox addon : FLASH-AID

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by GoldDragon on 2010-06-25
I am using firefox, the files are not there. Yes, I had flash working perfectly before upgrading to Lucid.

>  	
Re: 64-bit flash problem
Try this Firefox addon : FLASH-AID

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

I tried this and got a message saying something couldn't be completed ( closed out the error message by accident can't remember the whole thing).
Now websites that worked before ( like joost and hulu ) don't work at all.
I still can't find any .so files either :confused:.

---

### Post by howefield on 2010-06-25
> **GoldDragon said:**
> ( closed out the error message by accident can't remember the whole thing).

Hard to help without knowing what's happened.

Try running FLASH-AID again.

---

### Post by prshah on 2010-06-25
> **GoldDragon said:**
> I looked in the lib flash plugin folders and the libflashplayer.so files aren't in either the lib, 32 bit or 64 bit folders.. but flash still plays.

type ```
about:plugins
``` in the firefox address bar to find the flash files in use. Depending on whether you are using the 64bit version of flash (10.0?) or 32bit with nsplugin (10.01rXX?), the instructions to remove them will change. 

Please post back with your version details (as well as version of firefox [Help-About])

---

### Post by lovinglinux on 2010-06-25
> **GoldDragon said:**
> I tried this and got a message saying something couldn't be completed ( closed out the error message by accident can't remember the whole thing).
Now websites that worked before ( like joost and hulu ) don't work at all.
I still can't find any .so files either :confused:.

Run FLASH-AID again and don't interrupt the terminal.

---

### Post by GoldDragon on 2010-06-25
> type
Code:

about:plugins


I did this and got:
>     File: libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

I did a system search and found the libflashplayer.so file under /usr/lib64/mozilla/plugins.. I'm guessing that's the problem?

---

### Post by lovinglinux on 2010-06-25
> **GoldDragon said:**
> I did this and got:


I did a system search and found the libflashplayer.so file under /usr/lib64/mozilla/plugins.. I'm guessing that's the problem?

You are using the old version, which has a critical vulnerability.

Run FLASH-AID again to install the most recent version or run these commands:

```
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

---

### Post by GoldDragon on 2010-06-26
I decided to do a full reinstall of both firefox and flash and it fixed the problems.

Thanks!

---

### Post by robgue on 2010-08-10
Thank you lovinglinux. I was having the same problem and that worked:p

---

### Post by lovinglinux on 2010-08-10
> **robgue said:**
> Thank you lovinglinux. I was having the same problem and that worked:p

You are welcome.

---

