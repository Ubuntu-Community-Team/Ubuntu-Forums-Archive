---
title: "need help installing flash"
date: 2009-07-31
forum: General Help
---

### Post by Keithbonham on 2009-07-31
i recently installed ubuntu 8  and upgraded it to 904. ive looked around everywheres trying to find something to help me get it installed. no matter what i try i get nothing. it says flashplugin-nonfree can not be found and i cant seem to find it anywheres from the software sources and its not in synaptic . i duno im all confused, i have been sittin here for hrs trying to get it to work, any ideas?

---

### Post by Tclarkie on 2009-07-31
[I]here is the .deb 
[http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb](http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb)

its a double click installer
[/I]

---

### Post by Keithbonham on 2009-07-31
wrong architechure i386 is the error i get with that

---

### Post by saidinesh5 on 2009-07-31
simply download the flash plugin's .deb installer from the adobe's website.
it would do the task for you

good luck :)

---

### Post by mike555 on 2009-07-31
download the .deb from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)  , then be sure to close Firefox , then install ...

---

### Post by Keithbonham on 2009-07-31
still getting the error wrong arhectecure

---

### Post by saidinesh5 on 2009-07-31
are you trying to install 64 bit flash on 32 bit ubuntu 
or vice versa??

make sure that you ubuntu's architecture matches with the flash players's

---

### Post by Keithbonham on 2009-07-31
to be honest with u i have no idea if its 32 or 64

---

### Post by Keithbonham on 2009-07-31
how do i find out

---

### Post by Hamchan on 2009-07-31
If your getting that error, you are probably working on 64 bit ubuntu and trying to install the 32 bit flash.

There is a 64 bit flash plugin you can download from adobe labs ([http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")).

Extract the file to your desktop then go into your home folder. Hit ctrl+h to display hidden folders and find the .mozilla folder. Go into that folder and create a new folder called plugins. Then you just drag the .so file off your desktop into this new folder. Restart firefox and you should be fine

---

### Post by vinutux on 2009-07-31
You may run 64 bit os install 64 bit flash from above link

---

### Post by Keithbonham on 2009-07-31
still not working, ive done all that 
its 64bit by the way, if i reinstall to 8.10 would it work better?
and if i were to reinstall, could i reinstall it to 32 bit?

---

### Post by Keithbonham on 2009-07-31
or is there an open source version of flash

---

### Post by Keithbonham on 2009-07-31
can i download the 32 bit desktop version and install that ? will it work on the ps3

---

### Post by oldos2er on 2009-08-01
You may need to copy libflashplayer.so to /usr/lib/mozilla/plugins

---

### Post by vinutux on 2009-08-01
you need to install 64 bit flash player from [COLOR="Red"]adobe labs[/COLOR].....

Download [**http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz**]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz")

---

### Post by anne_maree on 2009-08-02
> **Hamchan said:**
> 
Extract the file to your desktop then go into your home folder. Hit ctrl+h to display hidden folders and find the .mozilla folder. Go into that folder and create a new folder called plugins. Then you just drag the .so file off your desktop into this new folder. Restart firefox and you should be fine

Thanks for that - I've been having ongoing flash wars since I moved to 64-bit on a couple of computers.

---

### Post by Keithbonham on 2009-08-02
yeah everything u guys have said has not worked so far

---

### Post by Keithbonham on 2009-08-02
i reinstalled back to 8.10 but still cant get none of it to work

---

