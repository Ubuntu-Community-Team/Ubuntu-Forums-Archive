---
title: "Flash 64 bit"
date: 2011-02-27
forum: General Help
---

### Post by shashanksingh on 2011-02-27
I have ubuntu 10.10 64 bit and I downloaded the flash package required for the same.

It has a libflas*.so file.

How do I proceed??

---

### Post by howefield on 2011-02-27
Open a terminal and copy it to /usr/lib/mozilla/plugins

If there is only the one account on your machine, you could copy it to the .mozilla/plugins directory in /home.

---

### Post by shashanksingh on 2011-02-27
So do I need to copy this in the plugin directory for chrome as well??

thnx.:)

---

### Post by howefield on 2011-02-27
No I don't think so, chrome will pick it up from the mozilla directory.

---

### Post by shashanksingh on 2011-03-14
> **howefield said:**
> Open a terminal and copy it to /usr/lib/mozilla/plugins

If there is only the one account on your machine, you could copy it to the .mozilla/plugins directory in /home.

It used to work few days back, I guess after a firefox automatic update, it has stopped working.

The libflash*.so file is in both the directories.

---

### Post by plucky on 2011-03-15
The method in this  [link](http://www.ubuntugeek.com/adobe-flash-player-10-for-64-bit-linux-released-and-ubuntu-installation-instructions.html) works for me.

Good Luck

---

### Post by shashanksingh on 2011-04-16
> **howefield said:**
> Open a terminal and copy it to /usr/lib/mozilla/plugins

If there is only the one account on your machine, you could copy it to the .mozilla/plugins directory in /home.

I tried both the options, it worked for a few days but I dnt know how suddenly it has stoped working again, although the file libflashplayer.so is present on both
/usr/lib/mozilla/plugins and /home/usr/.mozilla/plugins

---

### Post by shashanksingh on 2011-04-16
I have a 64 bit machine.
I downloaded a 64 bit version of flash from <a href="http://labs.adobe.com/technologies/flashplayer10/square/">
here</a>

I extracted the libflashplayer.so file to both
/usr/lib/mozilla/plugins
/home/user/.mozilla/plugins

I can now watch videos on youtube, but I cant upload pics on facebook using the same flashplayer plugin. I have to use the simple uploader for it.

Any ideas???

---

### Post by garvinrick4 on 2011-04-16
After downloading and extracting and from that directory I will: (Make sure to close all Firefox running)
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
#Link libraries below:
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
seems to work fine with native-64bit-flash-installer downloaded from adobe.
#If problem start over and remove all just to make sure nothing old hanging around.
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

---

### Post by Elfy on 2011-04-16
merged

---

### Post by shashanksingh on 2011-04-16
here is my locate libflashplayer.so

/home/user/.mozilla/plugins/libflashplayer.so
/home/user/Downloads/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla-firefox/plugins/libflashplayer.so
/usr/share/mozilla/libflashplayer.so

Facebook still asks me to get flash player for photo uploads, but I can watch videos on you tube.

---

### Post by shashanksingh on 2011-04-16
Its a fresh copy. I tried the link as well previously but the situation is still the same

---

### Post by 5149.5 on 2011-04-16
The flash-aid addon will make this job very easy.

---

### Post by garvinrick4 on 2011-04-16
> **shashanksingh said:**
> here is my locate libflashplayer.so

/home/user/.mozilla/plugins/libflashplayer.so
/home/user/Downloads/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla-firefox/plugins/libflashplayer.so
/usr/share/mozilla/libflashplayer.so

Facebook still asks me to get flash player for photo uploads, but I can watch videos on you tube. Here is mine for Native 64 bit square: You have a lot of old stuff going
on there: If you are not going to start with rm command on all the left over from stable 32 bit flash I would take previous advice and use flash aid. Or remove and reinstall from commands previously gave. You got just way to much stuff going on there. Are you using 
10.3.162.29  ? Right click on any flash video and go to about adobe flash.

/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by shashanksingh on 2011-04-18
> **5149.5 said:**
> The flash-aid addon will make this job very easy.

Here's what I did.
1. rm -rf <all libflashplayer>
2. sudo apt-get remove firefox
3. Install the latest firefox 4 tar, unrar it in /opt/firefox
4. ln -sf /opt/firefox/firefox /usr/bin/firefox
5. run firefox
6. install flash aid add-on
7. Execute the script it gives

Im back to where I was, I can watch videos but facebook prompts me to get the latest flashplayer NOT FOR VIDEOS, but just while uploading pics.

The add on creates a report which I have attatched

---

