---
title: "Flash problem"
date: 2010-09-16
forum: General Help
---

### Post by mistikkia on 2010-09-16
Hello,

I am trying to fix my flash 10 plugin on ubuntu lucid lynx. I installed the adobe one that you can choose when you first open a webpage that has some flash content on it. I think firefox offers 3 choices, the adobe one, and 2 gnus or something like that, so I chose the adobe one.
The problem I have is that I cannot play anything fullscreen because it simply "explodes" - the video stops and it is replaced by a grey box and I also cannot use the BBC Iplayer. The Iplayer works well for the first 9 seconds then I get a message saying that "a script is causing adobe flash 10 to run slowly. Kill the script now?"   with Yes or No buttons to click on.

Did a bit of investigation and found this page : **[http://www.omgubuntu.co.uk/2010/06/fixing-fullscreen-flash-in-ubuntu-10-04/](http://www.omgubuntu.co.uk/2010/06/fixing-fullscreen-flash-in-ubuntu-10-04/)  **but although i un-tick the hardware acceleration in settings, after i click on close it still stays on (if i go back to settings to check it  i see that the box near hardware acceleration is still ticked)
I also set GDK_NATIVE_WINDOWS=1 in .bashrc . 

Any suggestions on how to fix it are appreciated.

M.

---

### Post by philinux on 2010-09-16
> **mistikkia said:**
> Hello,

I am trying to fix my flash 10 plugin on ubuntu lucid lynx. I installed the adobe one that you can choose when you first open a webpage that has some flash content on it. I think firefox offers 3 choices, the adobe one, and 2 gnus or something like that, so I chose the adobe one.
The problem I have is that I cannot play anything fullscreen because it simply "explodes" - the video stops and it is replaced by a grey box and I also cannot use the BBC Iplayer. The Iplayer works well for the first 9 seconds then I get a message saying that "a script is causing adobe flash 10 to run slowly. Kill the script now?"   with Yes or No buttons to click on.

Did a bit of investigation and found this page : **[http://www.omgubuntu.co.uk/2010/06/fixing-fullscreen-flash-in-ubuntu-10-04/](http://www.omgubuntu.co.uk/2010/06/fixing-fullscreen-flash-in-ubuntu-10-04/)  **but although i un-tick the hardware acceleration in settings, after i click on close it still stays on (if i go back to settings to check it  i see that the box near hardware acceleration is still ticked)
I also set GDK_NATIVE_WINDOWS=1 in .bashrc . 

Any suggestions on how to fix it are appreciated.

M.

Adobe just released a preview new 64 bit plugin. It works miles better for me.
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

Just copy the new libflashplayer.so to ~/.mozilla/plugins restart FF and it will pick up the 64 bit version

---

### Post by mistikkia on 2010-09-16
I just noticed that  ~/.mozilla/plugins is not a folder, but a file. How can I copy another file to it ? But funny enough when I did cp libflashplayer.so ~/.mozilla/plugins it did not complain at all ... however still no change. I can't use fullscreen or Iplayer

best,
M.

---

### Post by howefield on 2010-09-16
> **mistikkia said:**
> I just noticed that  ~/.mozilla/plugins is not a folder, but a file. How can I copy another file to it ?

Create the folder, then copy it over.

---

### Post by mistikkia on 2010-09-16
tried to but got this:

.....~/.mozilla$ mkdir plugins
mkdir: cannot create directory `plugins': File exists

---

### Post by howefield on 2010-09-16
> **mistikkia said:**
> tried to but got this:

.....~/.mozilla$ mkdir plugins
mkdir: cannot create directory `plugins': File exists

You need to delete the file you previously created, the file named plugins.

---

### Post by mistikkia on 2010-09-16
i think that was there from the very beginning , don't think it was created by me.
i did create a folder called plugins and now youtube fullscreen works but iplayer has the same issue, you cannot use the control buttons after the first 9 seconds ... but i can on youtube ... how bizarre

---

### Post by 3Miro on 2010-09-16
> **philinux said:**
> Adobe just released a preview new 64 bit plugin. It works miles better for me.
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

Just copy the new libflashplayer.so to ~/.mozilla/plugins restart FF and it will pick up the 64 bit version

=D> :guitar: \\:D/

Now all they have to do is to release it as FOSS.

---

### Post by philinux on 2010-09-16
> **mistikkia said:**
> i think that was there from the very beginning , don't think it was created by me.
i did create a folder called plugins and now youtube fullscreen works but iplayer has the same issue, you cannot use the control buttons after the first 9 seconds ... but i can on youtube ... how bizarre

Some things to check.

In firefox address bar about:config and use the filter full_path. Double click it to change it to true. Now use ```
about:plugins
``` and post what it says is the full location of libflashplayer.so.

Now in a terminal

```
sudo updatedb

No output from that it just updates the locate database. Then

locate libflashplayer.so
```

Post back what the locate displays.

---

### Post by Mark76 on 2010-09-16
> **mistikkia said:**
> I also cannot use the BBC Iplayer. The Iplayer works well for the first 9 seconds then I get a message saying that "a script is causing adobe flash 10 to run slowly. Kill the script now?"   with Yes or No buttons to click on.

Have you considered the possibility that the BBC is to blame for this? The same thing happens to me.

---

### Post by philinux on 2010-09-16
> **Mark76 said:**
> Have you considered the possibility that the BBC is to blame for this? The same thing happens to me.

Iplayer working fine here with new 64 bit plugin. Worked fine with 32 bit one too. So it's not the beeb.

---

### Post by Mark76 on 2010-09-16
Then it must be something wrong with Ubuntu 10.04. Since I doubt we're both using the same browser yet we both have the same problem

---

### Post by mistikkia on 2010-09-16
about: plugins has the following 2 things :

Shockwave Flash  -->appears first

    File: /home/pc_name/.mozilla/plugins/libflashplayer.so
    Version: 
    Shockwave Flash 10.2 d161

Shockwave Flash

    File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r82

when  i try to locate the libflashplayer.so I find the following locations :
/home/pc_name/.mozilla/plugins/libflashplayer.so  
/home/pc_name/Downloads/libflashplayer.so
/home/pc_name/Downloads/libflashplayer.so (2)
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

I am using Firefox 369, Mozilla Firefox for Ubuntu Canonical 1.
The interesting thing is that now I notice that it takes longer for the message to appear (the one that says that a script is causing flash to be slow)  and it takes longer for the image to recover after i click yes.

I have another friend who did exactly what I have done (as described in my first post) and his is working perfectly ... I really don't understand why mine isn't

---

### Post by lovinglinux on 2010-09-16
try version 1.0.12 of FLASH-AID, an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

It supports the new 64bit version of flash.

[http://flash-aid-extension.blogspot.com](http://flash-aid-extension.blogspot.com)
[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)
[http://github.com/lovinglinux/flash-aid/downloads](http://github.com/lovinglinux/flash-aid/downloads)

---

### Post by mistikkia on 2010-09-16
Thank you for the suggestion, but it does not work. Still same behaviour, but more than that, now I found pages that have flash and I can't play it at all (only a white box is displayed) .. like this for example : [http://videolectures.net/bootcamp2010_anthoine_pmn/](http://videolectures.net/bootcamp2010_anthoine_pmn/)

---

### Post by mistikkia on 2010-09-23
yeap .. still no joy .. any suggestions anyone ?

---

### Post by lovinglinux on 2010-09-23
> **mistikkia said:**
> Thank you for the suggestion, but it does not work. Still same behaviour, but more than that, now I found pages that have flash and I can't play it at all (only a white box is displayed) .. like this for example : [http://videolectures.net/bootcamp2010_anthoine_pmn/](http://videolectures.net/bootcamp2010_anthoine_pmn/)

See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html). There is a solution for that problem.

---

### Post by mistikkia on 2010-09-25
what is the solution that you are referring to?
I tried using Flash-AID and export GDK_NATIVE_WINDOWS=1 and still no joy. These are the only ones that apply to me.

---

### Post by drdos2006 on 2010-09-25
Here is what worked for me....
```

Installing Adobe FlashPlayer 10 in Ubuntu 9.10 64 bit
Close the browser
Downloaded  latest libflashplayer .tar.gz from here
http://labs.adobe.com/downloads/flashplayer10.html

Extracted into /home/temp by double-click on downloaded file.
Copied /home/temp/libflashplayer.so to /usr/lib/mozilla/plugins/  in terminal with
sudo cp /home/temp/libflashplayer.so /usr/lib/mozilla/plugins/

Went to /usr/lib/mozilla/plugins/ via Terminal with 
cd /usr/lib/mozilla/plugins/

Executed these commands from /usr/lib/mozilla/plugins/ via Terminal.
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

Run Firefox
Check plugins with Firefox, about:plugins

```
regards

---

### Post by mistikkia on 2010-09-25
nope it doesn't really work.
but they are there:
**Shockwave Flash**

 File:  libflashplayer.soVersion:   Shockwave Flash 10.2 d161 
MIME Type Description Suffixes Enabled    
application/x-shockwave-flash Shockwave Flash swf Yes   
application/futuresplash FutureSplash Player spl Yes



sudo rm /usr/lib/firefox-addons/plugins/ 
sudo rm /usr/lib/xulrunner-addons/plugins/
  --> these should remove the soft links I made, right?

 thanks for the suggestion

---

### Post by drdos2006 on 2010-09-25
I have the same version of flash that you have.
Maybe uninstall firefox and re-install firefox.

regards

---

### Post by mistikkia on 2010-10-12
i hear it is not a good idea to uninstall ff since this can lead to numerous problems
even though i see there have been some updates I still have the same problem with my flash player

---

### Post by lovinglinux on 2010-10-12
> **mistikkia said:**
> i hear it is not a good idea to uninstall ff since this can lead to numerous problems
even though i see there have been some updates I still have the same problem with my flash player

Not really. Sometimes it removes some dependencies, like gecko-mediaplayer, but you can reinstall without fear:

```
sudo apt-get install --reinstall firefox
```

---

