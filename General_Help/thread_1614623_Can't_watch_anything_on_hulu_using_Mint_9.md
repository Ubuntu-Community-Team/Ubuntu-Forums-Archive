---
title: "Can't watch anything on hulu using Mint 9???"
date: 2010-11-05
forum: General Help
---

### Post by steve509 on 2010-11-05
Hello to all. I can't seem to watch anything in Hulu. I'm using Mint 9. Any suggestions as to why?? I'm still a newbie at this so please help.
Thanks
steve509

---

### Post by nl4m on 2010-11-05
If you have the same problem as me go to google.com type in "adobe flash" and download the ".DEB" package. But first make sure that you have a directory: "/home/(your user name)/.mozilla". To do this you can go from folder to folder to see if it's there (don't forget to show the hidden files). or you can type in the command line:

test -d /home/(your user name)/.mozilla

The next command you type is:

echo $?

If the output is a "0" do this. If it is a "1", I'll tell you something else. So if it's a "0" go to this link:

[http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.1_for_Linux_(.deb](http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.1_for_Linux_(.deb))

Download it to your "Desktop" folder. And follow these commands:
1. cd /home/(your user name)/Desktop
2. ar -x linux_flash.deb
change "linux_flash.deb" with the name of the downloaded file.
3.tar -xzf data.tar.gz
4. cd usr/lib/adobe-flashplugin
5. mv /home/(user name)/.mozilla/plugins/libflashplayer.so /home/(user name)/.mozilla/plugins/libflashplayer.so.old
6. cp libflashplayer.so /home/(your user name)/.mozilla/plugins
7. Restart Firefox, if needed.

If it does not work type this in:
mv /home/(user name)/.mozilla/plugins/libflashplayer.so.old /home/(user name)/.mozilla/plugins/libflashplayer.so

---

### Post by steve509 on 2010-11-05
nl4m, thank you so much for your reply. I downloaded the .deb but I get a "Wrong architecture 'i386' message. I also tried the 64 bit (which is what i have) and it tells me that its for firefox, Moxilla and Seamonkey. I use Chromium. What do i do now? btw, the echo $? came up with 0
again, thanks

---

### Post by Moldjelly on 2010-11-05
just install google chrome it comes with flash

---

### Post by steve509 on 2010-11-05
Chrome is installed and still not working I get the message "Sorry, this video is currently unavailable. We apologize for any inconvenience.  Note: If this message appears repeatedly, you may need to clear your browser cache and restart your browser."

I did this and still keep getting the same message over and over again.
Any other thoughts as to what it could be?? appreciate all the help

---

