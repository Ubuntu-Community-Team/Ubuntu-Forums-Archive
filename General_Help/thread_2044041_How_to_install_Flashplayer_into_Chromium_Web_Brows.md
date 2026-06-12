---
title: "How to install Flashplayer into Chromium Web Browser in Lubuntu"
date: 2012-08-17
forum: General Help
---

### Post by benmayim on 2012-08-17
1. Download latest "libflashplayer.so" file from adobe in a tar.gz file.
2. [http://www.adobe.com/go/getflashplayer?promoid=ISMRZ](http://www.adobe.com/go/getflashplayer?promoid=ISMRZ)
3. Use file manager in lubuntu to find the tar.gz file. In Lubuntu it's usually in "/home/this/Downloads"
4. unzip .tar.gz file (usually this will start by double-clicking on the tar.gz file. You'll get a window and just
     hit "extract" and this will extract the file  "libflashplayer.so" to the same folder ("/home/this/Downloads")
5. Use file manager to make sure you have a "/usr/lib/chromium-browser/plugins" folder
6. You have to copy this file from the downloads location to the plugins location
7. You have to use a terminal and "sudo" in order to copy that file from one location to the other
     because you do not have administrative rights in the file manager, and the file manager won't allow you
     to just drag and drop it there.
8. So go to start-accessories-LXTerminal and open a terminal window
8. Here's the command to copy the above file using a terminal:
    sudo cp /home/this/Downloads/libflashplayer.so /usr/lib/chromium-browser/plugins

    Just type that into the black terminal window

Of course your download may come to a different folder and maybe your destination folder will be different,
but once you get the .so file to the proper location the plugin will work.

---

### Post by spacemonkey87 on 2013-03-04
well, i followed the instructions step by step...and i pretty much got nowhere...
i kept on stumbling upon this thing: 

*You might want to run 'apt-get -f install' to correct these:**The following packages have unmet dependencies:*

and it went on with a list each time it showed up

any ideas?

---

### Post by claracc on 2013-03-04
what lubuntu are you using? 12.04, 12.10?. It would be desirable to see what errors of unmet dependencies are found

In this case why not to install flashplugin installer from synaptic which will install the last adobe flashplayer available for lubuntu. Then, open chromium browser, write in the address bar abou: plugins, click on details and you will see the adobe flash plugin installed ( no need to do nothing more) and ready to use by chromium.

---

