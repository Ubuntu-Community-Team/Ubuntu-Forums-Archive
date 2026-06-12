---
title: "Problems with Ubuntu 10.04"
date: 2010-05-04
forum: General Help
---

### Post by gramsyn on 2010-05-04
I have installed the new version of Ubuntu 10.04. Everything seems to work fine except:

1) The sound does not work when I play video from YouTube! OTHER SOUND APPLICATIONS WORK PROPERLY

2) When some minutes pass, the screen gets dark (as supposed) but then requires password to log in again.

How can I fix these problems?

Thanks in advance

---

### Post by iblazev on 2010-05-04
Hello!

> 
1) The sound does not work when I play video from YouTube! OTHER SOUND APPLICATIONS WORK PROPERLY


What version of Ubuntu do u use, i386 (i686) or amd64? Have u installed flashplugin-nonfree maybe?

> 
2) When some minutes pass, the screen gets dark (as supposed) but then requires password to log in again.


Go to *System -> Preferences -> Screensaver* and there uncheck *Activate screensaver ...* and *Lock screen ...*

---

### Post by joosto on 2010-05-04
I don't know the answer to your first question but maybe I can help you a bit with your second question.

This is actually supposed to happen, but you can probably turn this off. Maybe look for the screensaver or energy saving settings?

---

### Post by gramsyn on 2010-05-04
I use i386. I have installed flashplugin-nonfree but problem was not solved

---

### Post by swalker23 on 2010-05-04
For you sound issue you can try opening up your volume mixer and increase the PCM to the max.  I had to do that on Kubuntu when I first installed it.

---

### Post by gramsyn on 2010-05-04
Every scroll of the sound mixer is at max

---

### Post by gramsyn on 2010-05-07
Has anyone any more ideas about my sound problem?

Thanks

---

### Post by dracayr on 2010-05-07
There seem to be very many people with this problem. Do you have more than 1 soundcard? Flash 10 will only work with the default alsa soundcard. Maybe you can switch to it in System&#8594;Preferences&#8594;Sound?

dracayr

---

### Post by gramsyn on 2010-05-07
I have only 1 internal soundcard. With the previous version of Linux I had no problem, even when I plugged an external soundcard

---

### Post by sandyd on 2010-05-07
type
```

about:plugins

```

in your browser address bar.
look for the entry with "shockwave flash"

copy the stuff right under it, and paste.

---

### Post by gramsyn on 2010-05-07
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by gramsyn on 2010-05-07
Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 9.0 r31

---

### Post by pqwoerituytrueiwoq on 2010-05-07
flash 9!? you serious? that would do it.
flash 10 has sound but does not work for everything. :(
the current flash 10.1 rc 4 (and rc2 do not know about 3) has a issue also.
10.1 rc1 works :)
sadly it is no longer available for download. :( edit: looks like i was wrong on that one see next post
any one know if it is legal to attach the file here?

---

### Post by sandyd on 2010-05-07
This is the reason why git commits exist :)
[http://github.com/dolphinaura/Flash-Plugin-Tools/commit/44ad893b50bc6733b1102bcbf108ccedadf4ccaf](http://github.com/dolphinaura/Flash-Plugin-Tools/commit/44ad893b50bc6733b1102bcbf108ccedadf4ccaf)

that was the commit that I used to upgrade my installer's link from 10.1 RC1 to RC2....

so...

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc_linux_040510.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc_linux_040510.tar.gz)

---

### Post by sandyd on 2010-05-07
> **pqwoerituytrueiwoq said:**
> flash 9!? you serious? that would do it.
flash 10 has sound but does not work for everything. :(
the current flash 10.1 rc 4 (and rc2 do not know about 3) has a issue also.
10.1 rc1 works :)
sadly it is no longer available for download. :(
any one know if it is legal to attach the file here?
and flash 10 works on everything for me.

run this
```

sudo apt-get remove --purge flashplugin-nonfree flashplugin-installer
sudo rm /usr/lib/mozilla/plugins/libflash*
sudo rm /usr/lib/mozilla/plugins/flashplugin*
sudo apt-get install flashplugin-installer
```if that doesn't work, then
```

sudo apt-get remove --purge flashplugin-nonfree flashplugin-installer
sudo rm /usr/lib/mozilla/plugins/libflash*
sudo rm /usr/lib/mozilla/plugins/flashplugin*
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc_linux_040510.tar.gz
tar xvfz flashplayer10_1_rc_linux_040510.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
rm  flashplayer10_1_rc_linux_040510.tar.gz
```

and yes, really im the self-proclaimed queen of playing w/ flashplayer ;)

---

### Post by gramsyn on 2010-05-07
I am really sorry, but can you explain it a little easier to a novice user? I have downloaded the file you said and extracted. It has a .so extension. i tried to move it to /usr/lib/mozilla/plugins but the system doesn' t let me. I tried to run on console the code you mentioned at the second message. i think it removes the previous package but doesn't install the new one?

Can you give me some simpler instructions, please?

---

### Post by gramsyn on 2010-05-07
The second code worked. Thanks a lot

---

### Post by pqwoerituytrueiwoq on 2010-05-07
> **gramsyn said:**
> I am really sorry, but can you explain it a  little easier to a novice user? I have downloaded the file you said and  extracted. It has a .so extension. i tried to move it to  /usr/lib/mozilla/plugins but the system doesn' t let me. I tried to run  on console the code you mentioned at the second message. i think it  removes the previous package but doesn't install the new one?

Can you give me some simpler instructions, please?
you have to do it as root
```
sudo cp source destination
```or use the gui
```
gksu nautilus
```

---

