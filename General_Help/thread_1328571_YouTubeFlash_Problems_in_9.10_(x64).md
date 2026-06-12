---
title: "YouTube/Flash Problems in 9.10 (x64)"
date: 2009-11-16
forum: General Help
---

### Post by Cam! on 2009-11-16
I tried a couple of methods to get Flash to work on my 64-bit Ubuntu. YouTube and other flash things work (for the most part), but many times, I'm unable to click anything on YouTube, so I'm just stuck watching a movie with no controls.

What do I do?

---

### Post by hwttdz on 2009-11-16
[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

The question has been asked loads of times, and most of the threads seem to die out without finding this rather simple solution, which makes it hard to find the solution by searching.  I empathize with you, I spend a lot of time searching for it myself.

---

### Post by Giblet5 on 2009-11-16
Or, you can save this script ```
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

as x64flash and run it via: ```
bash x64flash
```

---

### Post by hwttdz on 2009-11-16
As a warning, the mentioned script did not work for me on at least one of my machines, and I think 2.

---

### Post by Cam! on 2009-11-16
I guess it can't hurt to try. How do I save that as a script, and execute it?

---

### Post by hwttdz on 2009-11-16
I suggest editing /usr/lib/nspluginwrapper/i386/linux/npviewer first.  That said:

Either download the attached file or save everything in the code box.  Move the download (or copied text) to x64flash.  Change to the directory of x64flash, "chmod +x x64flash" (makes it executable), then ./x64flash to run the script.

Or as suggested, "bash x64flash".

---

### Post by Giblet5 on 2009-11-16
Select all of the text in that code block. Hit Ctrl+C to copy it.

Bring up a terminal window (Applications -> Accessories -> Terminal) and enter:

```
cat > x64flash
```

Hit Shift+Ins. Hit Enter. Hit Ctrl+D.

You're back to a prompt.

Now enter ```
bash x64flash
```

It will ask for your password and will not echo that password as you type it. Press enter after your password and it will install everything to make x64 Adobe Flash 10 work.

Now test it. I find that [www.megavideo.com](www.megavideo.com) is a very good test.

---

### Post by prasadchalasani on 2009-11-16
I faced the same problem, disable compiz.

---

### Post by hwttdz on 2009-11-16
> **prasadchalasani said:**
> I faced the same problem, disable compiz.

prasadchalasani, did you try editing /usr/lib/nspluginwrapper/i386/linux/npviewer ?  Did it work for you?  I like some of the compiz functions, and I'd be sad to give them up.

---

### Post by JBAlaska on 2009-11-16
This worked 100% on my laptop and 2 desktops:

Open a terminal and enter:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add: ```
export GDK_NATIVE_WINDOWS=1
``` before the last line of text.

Restart FF and it should be all good.
Note: this does NOT work for Chrome/Chromium.

---

### Post by blueridgedog on 2009-11-16
This thread is a duplicate of many others:

[http://ubuntuforums.org/showthread.php?t=1321243](http://ubuntuforums.org/showthread.php?t=1321243)

[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

---

### Post by happyisland on 2009-11-16
> **JBAlaska said:**
> This worked 100% on my laptop and 2 desktops:

Open a terminal and enter:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add: ```
export GDK_NATIVE_WINDOWS=1
``` before the last line of text.

Restart FF and it should be all good.
Note: this does NOT work for Chrome/Chromium.

Also worked for me on a Vaio laptop running 9.10 64. Thanks for posting the fix!

---

### Post by jhenager on 2009-11-16
> **Giblet5 said:**
> Select all of the text in that code block. Hit Ctrl+C to copy it.

Bring up a terminal window (Applications -> Accessories -> Terminal) and enter:

```
cat > x64flash
```

Hit Shift+Ins. Hit Enter. Hit Ctrl+D.

You're back to a prompt.

Now enter ```
bash x64flash
```

It will ask for your password and will not echo that password as you type it. Press enter after your password and it will install everything to make x64 Adobe Flash 10 work.

Now test it. I find that [www.megavideo.com](www.megavideo.com) is a very good test.

Worked great. Thank you.

---

### Post by synapse13 on 2009-11-16
I had this trouble myself just a bit ago.  I found that this post helped.  Had to do with my Nvidia card and desktop effects in Ubuntu.  Disable GPU detection on the web first:
[http://ubuntuforums.org/showthread.php?p=8215570#post8215570](http://ubuntuforums.org/showthread.php?p=8215570#post8215570)

Then disable advanced desktop effects in system administration>appearance.  

Did the trick for me.....

---

### Post by Cam! on 2009-11-16
I have a new problem. FireFox frequently crashes. A LOT.

---

### Post by TheCheeze on 2009-11-16
> **JBAlaska said:**
> This worked 100% on my laptop and 2 desktops:

Open a terminal and enter:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```Then add: ```
export GDK_NATIVE_WINDOWS=1
``` before the last line of text.

Restart FF and it should be all good.
Note: this does NOT work for Chrome/Chromium.

Worked beautiful, thanks!

---

