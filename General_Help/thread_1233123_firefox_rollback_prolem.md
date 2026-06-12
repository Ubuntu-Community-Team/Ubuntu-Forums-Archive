---
title: "firefox rollback prolem"
date: 2009-08-06
forum: General Help
---

### Post by delubu on 2009-08-06
okay so this happened to me twice. I updated FF to latest version using 2 different tuts and after a day or 2 FF rolls back to old version 3.0 in an update. how can i fix this?

I recently used tut from psychocats to install the latest version and i see another update telling me to redownload old version :/ I am using Ubuntu 8.10 Intrepid Ibex

here is a pic of updates that i see

[http://i28.tinypic.com/11i0o6b.png](http://i28.tinypic.com/11i0o6b.png)

[IMG]http://i28.tinypic.com/11i0o6b.png[/IMG]

---

### Post by lovinglinux on 2009-08-06
That update has nothing to do with the version installed by psychocats method, which installs Firefox 3.5 side-by-side with 3.0. That update is for the official version, installed with Ubuntu. 

BTW...

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by dsimpson on 2009-08-07
I have the same problem with the updates, but I did an update on the 3.0 before I realized that it wasn't 3.5 and when I logged on it came up as FF3.0, and I had to go to Applications>Internet>Firefox web browser to log on using FF3.5. I used the manual method of installation, then used ubuntuzilla, so now when I try to remove FF3.0 it says that I will remove files that will disable the Firefox browser and I cannot remove FF3.0. I also still have Shiretoko Web browser listed under my Applications>Internet list and if I click that I will load Shiretoko instead of FF3.5, if I click the link on my panel it will load FF3.0, and if I click on the icon on my desktop it loads FF3.5 but loads with pages that was bookmarked in my 3.0 version. 
    I would like to remove the 3.0 and Shiretoko versions and just use the 3.5 version installed via ubuntuzilla. Sorry about having to jump in on this thread but it was the closest to what my problem is also, but I would appreciate any help with my problem also. I couldn't find an answer in the link provided, I would like the upgrades to reflect the FF 3.5 version and no longer the 3.01 version.

---

### Post by lovinglinux on 2009-08-07
> **dsimpson said:**
> I have the same problem with the updates, but I did an update on the 3.0 before I realized that it wasn't 3.5 and when I logged on it came up as FF3.0, and I had to go to Applications>Internet>Firefox web browser to log on using FF3.5. I used the manual method of installation, then used ubuntuzilla, so now when I try to remove FF3.0 it says that I will remove files that will disable the Firefox browser and I cannot remove FF3.0. I also still have Shiretoko Web browser listed under my Applications>Internet list and if I click that I will load Shiretoko instead of FF3.5, if I click the link on my panel it will load FF3.0, and if I click on the icon on my desktop it loads FF3.5 but loads with pages that was bookmarked in my 3.0 version. 
    I would like to remove the 3.0 and Shiretoko versions and just use the 3.5 version installed via ubuntuzilla. Sorry about having to jump in on this thread but it was the closest to what my problem is also, but I would appreciate any help with my problem also. I couldn't find an answer in the link provided, I would like the upgrades to reflect the FF 3.5 version and no longer the 3.01 version.

 - You shouldn't remove FF 3.0
 - You can't upgrade 3.0.x to 3.5.x
 
To remove Shiretoko, simply run this command

```
sudo apt-get remove firefox-3.5
```

The problem with the bookmarks is that Shiretoko makes a copy of your profiles from ~/.mozilla/firefox/ to ~/.mozilla/firefox-3.5 on the first time you start it. The version installed by Ubutuzilla uses the same directory as FF 3.0, which is ~/.mozila/firefox/. So any bookmark added or any personal settings made while using Shiretoko won't show when you start FF 3.0 or FF 3.5 installed by Ubuntuzilla.

If you want to use the bookmarks and settings you get when launching Shiretoko, but with the version installed by Ubuntuzilla, then simply replace the contents of ~/.mozilla/firefox/ with the contents of ~/.mozila/firefox-3.5.

If you want to make all your panels and launchers to launch Firefox 3.5 then just reinstall Firefox 3.5 with Ubuntuzilla commands and it should update the links to the new version. If it does not, make sure  the launcher has **firefox %u** as command.

---

### Post by dsimpson on 2009-08-07
Thank you lovinglinux, that clears up some of the questions about FF 3.0 to 3.5 upgrade, so I will leave 3.0 alone, but how can I stop the update notices for 3.0 and instead begin receiving updates for 3.5 or does ubuntuzilla automatically notify me when there is an update for the 3.5 version? 
All of the links are now pointing to FF 3.5 but the tabbed pages that load when I open the browser still comes up. In my file system I have Firefox, and 3 instances of firefox backups in separate folders. I didn't know what I was doing so I didn't want to delete or remove anything there so upon boot nothing has changed. 
One other question, I see Shiretoko is just the unbranded version of 3.5, are there benefits to using one over the other or are both equal in function? 
Again, thanks for the reply and help. Duane

---

### Post by delubu on 2009-08-07
thanks  lovinglinux that was a nice read. I am now using FF 3.5.2 I used psychocats method tho.

---

### Post by lovinglinux on 2009-08-07
> **dsimpson said:**
> Thank you lovinglinux, that clears up some of the questions about FF 3.0 to 3.5 upgrade, so I will leave 3.0 alone, but how can I stop the update notices for 3.0 and instead begin receiving updates for 3.5 or does ubuntuzilla automatically notify me when there is an update for the 3.5 version?

There is a way to stop updates for a particular application, but I don't remember how. Anyway, I see no reason to disable this. Those updates won't affect FF 3.5 and won't hurt your system.

Ubuntuzilla provides an option during installation to enable checking for new versions. If you have enabled this it will update itself. Keep in mind that this has nothing to do with the update alerts provided by Ubuntu package management system. Ubuntuzilla update alerts are simply a script that check for new versions on Mozilla site, download the file and extract it to the FF 3.5 folder. So alerts won't be like the one from the first post. They will be just a panel alert baloon.

> **dsimpson said:**
> All of the links are now pointing to FF 3.5 but the tabbed pages that load when I open the browser still comes up. 

I don't understand the problem.

> **dsimpson said:**
> In my file system I have Firefox, and 3 instances of firefox backups in separate folders. I didn't know what I was doing so I didn't want to delete or remove anything there so upon boot nothing has changed.

I don't understand. Do you mean when you start everything goes back to the way it was?

If you simply copied the contents of  firefox installation folder to another folder, then it's safe to delete the backups. Besides, there is no reason to backup the installation files. You can re-install FF 3 using Synaptic any time you want. Additionally, all personal data (bookmarks, passwords, extensions, themes...) are saved on FF profile folders, which are under ~/.mozilla/firefox/ and have nothing to do with FF installation folders. Even when you re-install FF these files are not changed.

> **dsimpson said:**
> One other question, I see Shiretoko is just the unbranded version of 3.5, are there benefits to using one over the other or are both equal in function? 
Again, thanks for the reply and help. Duane

They are the same program. Nevertheless, Shiretoko is tested and tweaked to work with Ubuntu. When you download and install FF directly from Mozilla, using Ubuntuzilla or  psychocats methods, you are installing the original Mozilla version for Linux. In terms of functionality, they are the same tho.

> **delubu said:**
> thanks  lovinglinux that was a nice read. I am now using FF 3.5.2 I used psychocats method tho.

You are welcome.

---

