---
title: "Can't click items in flash and youtube"
date: 2009-11-13
forum: General Help
---

### Post by getyourwings5 on 2009-11-13
I can't seem to use YouTube and Adobe Flash 10 applications to their full extent. If there is a button within the Flash, it won't do anything when I click it. This is most noticeable in YouTube, where I can't move the track position, click "replay", or play/pause. I am new to Ubuntu, so I am not good at diagnosing what the issue is. I run 9.10 64bit, so that may be an issue (if there is no support yet). However, I had this issue with 9.04 as well. Can anybody recommend what to do to fix this?

---

### Post by Giblet5 on 2009-11-13
Save this script as "getflashx64"

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# and one more update by Antonio Cassano bigbroantonio[at]yahoo[dot]it
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```

And run it via ```
sudo bash getflashx64
```

Tada!

---

### Post by wojox on 2009-11-13
Maybe add Firefox 64 as well [ftp://ftp.mozilla.org/pub/firefox/nightly/latest-firefox-3.5.x/firefox-3.5.6pre.en-US.linux-x86_64.tar.bz2](ftp://ftp.mozilla.org/pub/firefox/nightly/latest-firefox-3.5.x/firefox-3.5.6pre.en-US.linux-x86_64.tar.bz2)

---

### Post by Giblet5 on 2009-11-13
> **wojox said:**
> Maybe add Firefox 64 as well [ftp://ftp.mozilla.org/pub/firefox/nightly/latest-firefox-3.5.x/firefox-3.5.6pre.en-US.linux-x86_64.tar.bz2](ftp://ftp.mozilla.org/pub/firefox/nightly/latest-firefox-3.5.x/firefox-3.5.6pre.en-US.linux-x86_64.tar.bz2)

That isn't necessary (at all) and it causes Firefox to no longer be maintained via Update Manager.

---

### Post by getyourwings5 on 2009-11-13
Thank you Giblet5. This solved the problem. I hope that some day I will understand the magic behind it all\\:D/

---

### Post by nurvzy on 2009-11-14
Awesome! thank you very much for that fix.  I too was affected by this and was forced to use Opera for my youtube guilty pleasures.  

Hurray!

---

### Post by stoian on 2009-11-15
"getlibs" is an unknown command, you can use this instead:

apt-get install libcurl3 libnss3-1d libnspr4-0d

Other than that, everything worked fine, now I can click inside youtube flash player to start and stop the playback...

maybe Giblet5 can update the script...

thanks a lot!

---

### Post by compubike on 2009-11-15
Hi, yes getlibs package is 404.

Firefox bombed instantly after first time running.

2nd time bombed after a couple minutes.

3rd time has been stable.

youtube works, other flash apps seem faster and smoother.

thanks!

---

### Post by compubike on 2009-11-16
Update a day later. Gmail bombs firefox after login. Also bombing problems with vanguard.com

---

### Post by Matuku on 2009-11-17
I'm also having problems with GMail crashing Firefox; is there a simple way to undo the changes the script made?

---

### Post by closetpokey on 2009-11-17
Here is a relatively simple method that solved this problem for me. (i.e. mouse clicks not registering in flash like youtube, justin.tv, environments like that etc.)

It may be worth it to note that I'm using Ubuntu 9.10 Karmic Koala x64bit. I'm not sure if this works with 32-bit, or previous versions but it might be worth a try. Either way its easy enough to undo this change:

open up your terminal and type:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

```Then add:

```
export GDK_NATIVE_WINDOWS=1
``` before the last line of text.


Save and close the file, and restart anything that might use flash like Firefox, etc.


I took this from the Ubuntu bug report page. It's a known issue with the flashplugin-nonfree package. Hope this helps.

---

### Post by weremichael on 2009-11-17
> **closetpokey said:**
> Here is a relatively simple method that solved this problem for me. (i.e. mouse clicks not registering in flash like youtube, justin.tv, environments like that etc.)

It may be worth it to note that I'm using Ubuntu 9.10 Karmic Koala x64bit. I'm not sure if this works with 32-bit, or previous versions but it might be worth a try. Either way its easy enough to undo this change:

open up your terminal and type:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

```Then add:

```
export GDK_NATIVE_WINDOWS=1
``` before the last line of text.


Save and close the file, and restart anything that might use flash like Firefox, etc.


I took this from the Ubuntu bug report page. It's a known issue with the flashplugin-nonfree package. Hope this helps.


That worked for me. Thanks.

---

### Post by ethos101 on 2009-11-18
> **closetpokey said:**
> Here is a relatively simple method that solved this problem for me. (i.e. mouse clicks not registering in flash like youtube, justin.tv, environments like that etc.)

It may be worth it to note that I'm using Ubuntu 9.10 Karmic Koala x64bit. I'm not sure if this works with 32-bit, or previous versions but it might be worth a try. Either way its easy enough to undo this change:

open up your terminal and type:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

```Then add:

```
export GDK_NATIVE_WINDOWS=1
``` before the last line of text.


Save and close the file, and restart anything that might use flash like Firefox, etc.


I took this from the Ubuntu bug report page. It's a known issue with the flashplugin-nonfree package. Hope this helps.

PERFECT!  Thank you sir!

---

### Post by stadja on 2009-11-23
To Matuku and compubike...
I had the same'Gmail bombs firefox' problem.

To solve it, I had to install libadns1 and then reboot. And....
well, that's it.
so:
```
sudo apt-get install libadns1
sudo reboot
```

At restart, it worked! :popcorn:

---

### Post by andy16666 on 2009-11-28
#11 is indeed a very nice solution.

---

### Post by ruario on 2009-12-19
Opera users should try the steps in this [blog post]("http://my.opera.com/ruario/blog/flash-problems-on-linux#first-click").

---

### Post by jksm on 2009-12-24
> **Giblet5 said:**
> Save this script as "getflashx64"

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# and one more update by Antonio Cassano bigbroantonio[at]yahoo[dot]it
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```And run it via ```
sudo bash getflashx64
```Tada!


thing is for those of us new ubuntu people., saying 'save this code as x' - save it where? how? what program? how does it work?

---

### Post by Byrd740 on 2009-12-26
Thanks!  I have had this problem on both 32bit and x64bit, Karmic.  This worked for me on my x64bit desktop, but I noticed that on my 32bit laptop, the file(npviewer) is not there.  Would there maybe be a different file?

> **closetpokey said:**
> Here is a relatively simple method that solved this problem for me. (i.e. mouse clicks not registering in flash like youtube, justin.tv, environments like that etc.)

It may be worth it to note that I'm using Ubuntu 9.10 Karmic Koala x64bit. I'm not sure if this works with 32-bit, or previous versions but it might be worth a try. Either way its easy enough to undo this change:

open up your terminal and type:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

```Then add:

```
export GDK_NATIVE_WINDOWS=1
``` before the last line of text.


Save and close the file, and restart anything that might use flash like Firefox, etc.


I took this from the Ubuntu bug report page. It's a known issue with the flashplugin-nonfree package. Hope this helps.

---

### Post by VMOS on 2010-01-02
I love you Giblet5


> thing is for those of us new ubuntu people., saying 'save this code as x' - save it where? how? what program? how does it work?

here's what I did

open up terminal or konsole

enter this 
       
      cd ~/
this will take you to your home directory
       
      vi getflash64
press i to get to insert mode, paste the script, hit esc, enter wq! to save the script and quit vi
      
     chown 777 getflash64
this makes the script executable (a little heavy handed maybe, but it works)

     ./getflash64
job done

---

### Post by floflooo on 2010-02-07
Damn Flash!
> **closetpokey said:**
> Open up your terminal and type:
```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

```Then add:
```
export GDK_NATIVE_WINDOWS=1
``` before the last line of text.

Brilliant solution. Thank you!

---

### Post by sarge1221 on 2010-02-11
How about for the sake of simplicity someone repost all this as one problem solving solution as I'm completely lost. I have no clue where or what format scripts are saved in on linux. Second VMOS's post involving the hitting escape then typing wq in terminal doesn't work because i can do exactly as he says and when i type the command chown 777 getflash64 to activate the script I get a error message stating no such file or directory exists. Though i can go back to do the previous steps over and it says a file type already exists and gives options to delete or edit the script. By the way i was assuming this was all done in the home directory as i entered cd ~/ just as he had specified in the beginning. 


Just a general helper tip too can you guys please try to include step by step directions as it is extremely irritating for new members to have to go hit and miss something about twenty times only because of something simple that would of maybe taken you a few extra seconds to type in the post. for example Giblet instead of rushing through and posting the script then assuming everyone knows how to make a script in linux and know's where it needs to be placed why not just include that in the post as well?

---

### Post by sarge1221 on 2010-02-11
For anyone still having problems with this I suggest this youtube video [http://www.youtube.com/watch?v=O2EPwlFLZMY](http://www.youtube.com/watch?v=O2EPwlFLZMY) as it completely fixed my problem minus using the script or any of the terminal commands posted here. Good luck everyone.

---

### Post by BirdonLinux on 2010-03-02
Awesome, I have been crawling around forums on and off for weeks. This script does it all!

Thanks a lot! Cheers.

---

### Post by mcba89 on 2010-03-12
@[closetpokey]("http://ubuntuforums.org/member.php?u=942358") muchisimas gracias, me funciono a la perfeccion!!
--------------------------------------------------------------------------
@[closetpokey]("http://ubuntuforums.org/member.php?u=942358") thank you so much, it worked perfectly...!!!

---

### Post by Mooki on 2010-03-15
> **closetpokey said:**
> Here is a relatively simple method that solved this problem for me. (i.e. mouse clicks not registering in flash like youtube, justin.tv, environments like that etc.)

It may be worth it to note that I'm using Ubuntu 9.10 Karmic Koala x64bit. I'm not sure if this works with 32-bit, or previous versions but it might be worth a try. Either way its easy enough to undo this change:

open up your terminal and type:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

```Then add:

```
export GDK_NATIVE_WINDOWS=1
``` before the last line of text.


Save and close the file, and restart anything that might use flash like Firefox, etc.


I took this from the Ubuntu bug report page. It's a known issue with the flashplugin-nonfree package. Hope this helps.

Works perfect. Thank you. =D>

---

### Post by ovu on 2010-03-15
@Giblet5]
 awsome Thank you so much, great fix

---

### Post by Otto Nascarella on 2010-05-06
Well guys.

Script worked fine for me. THANKS A LOT!

We're already on lucid lynx, problem hasn't still been fixed.
Quite annoying, cos I've risked installing 64bit this time and some stuff are still not 100%.

Luckily, there's always someone who knows better and shares knowledge, which is great.



Thanks once again.



Otto

---

### Post by Maximus_ARNP on 2010-07-13
I was unable to click inside flash objects in Firefox and Chrom. I was also not able to click Full-screen or change resolution. Following instruction fixed all problems on Ubuntu 10.04 AMD64 with Firefox 3.6.6 and Chrom as well.

> **closetpokey said:**
> 
open up your terminal and type:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

```Then add:

```
export GDK_NATIVE_WINDOWS=1
``` before the last line of text.


Save and close the file, and restart anything that might use flash like Firefox, etc.



Thank you.

---

### Post by iCyber on 2010-07-15
> **Giblet5 said:**
> Save this script as "getflashx64"

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# and one more update by Antonio Cassano bigbroantonio[at]yahoo[dot]it
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```And run it via ```
sudo bash getflashx64
```Tada!
-------

[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]
Hey, so i did that , and now instead of not being able to click youtube buttons, this just scr3w3d up my whole flash -.-, now everytime i get on youtube or anything, whole firefox crashes... i tried doing the other method about the npviewer after using ur method, now my npviewer file is empty also...
when i run youtube, it just crashes, sometimes giving me an error message about a script not working properly or others, the following error is only ONE of the random msgs i get... 
error msg is : 
Script [http://s.ytimg.com/yt/jsbin/www-core-vfl174821.js:100](http://s.ytimg.com/yt/jsbin/www-core-vfl174821.js:100)
// this script apparently stopped working? what is ytimg anyway? it tells me thats what its going to instead of youtube when i read at bottom when loading youtube page ?
so what to do now? PS: am REALLY basic at ubuntu.Thanks.[IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]
oh and my computer is the following if it matters: Linux pc-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
oh and my firefox is version 3.5.9 for linux mint mint -1.0, 
Duno about what flash i was running just before it got messed up tbh.. thanks for the help everyone , i need a reply quickly bcos i messed up my boss's computer  lol...

---

### Post by zobcat on 2010-07-25
Thanks go to closetpokey. Which also happens to be the name of my favorite childhood game. Great fix. Thanks alot.

---

### Post by razzbar on 2010-07-27
> **andy16666 said:**
> #11 is indeed a very nice solution.

?? Which one is "#11" ??

---

### Post by bvanaerde on 2010-07-28
> **razzbar said:**
> ?? Which one is "#11" ??

That number represents the number of the post in this thread, being closetpokey's post on page 2.
[http://ubuntuforums.org/showthread.php?t=1325824&page=2#11](http://ubuntuforums.org/showthread.php?t=1325824&page=2#11)

This solution worked for me too, btw. Thanks!

---

### Post by razzbar on 2010-07-30
So what can I do if I'm running a 32 bit system?

---

