---
title: "Questions about the linux ext4 file system"
date: 2010-08-06
forum: General Help
---

### Post by espressobeanie on 2010-08-06
I'm trying to figure out why files in linux are oriented in the folders the way they are. In Windows it's much simpler to picture. You have program files (C:\Program Files(x86), system files (C:\Windows), user settings for programs or personal stuff(C:\User), and some weird folder names. I was noticing that the Ubuntu ext4 filesystem is a little more complicated. Some folder names are self explanatory, but others are not. Is there a guide, or some reading material on the history of the linux filesystem and how it morphed into what is presently used in Ubuntu?

---

### Post by worksofcraft on 2010-08-06
You might find the answers you want in this wiki:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

IMO one of great strengths in UNIX/Linux File System Hierarchy is that it separates read-only from read-write branches. This improves security and virus protection as well as allowing you to run from read only media like DvD.

---

### Post by mcduck on 2010-08-06
This has noting to do with Ext4, or any other file system. The directory hierarchy would be the same no matter what file system you used.

Anyway, the Windows hierarchy feels easier to you, but that's only because you already know it. When you learn the Linux hierarchy you'll notice that it makes a lot sense...

Every file is put in a place based on the file's *purpose*, not based on what the program it belongs to or what company that made the program is called.

So, you'll have all the documentation files for all your programs in one place (/usr/share/doc), executable files for all your programs in one place (/usr/bin), all system-wide configuration files in one place (/etc) and so on.

For example if you need to read the documentation for a program, instead having to figure out what was the name of the company that made a program to be able to find the program's directory inside C:\Program Files and then browsing through that program's own non-standard directories you'll always know that what you are looking for is in /usr/share/doc. Same goes for the executable, any additional icons and images the program uses, and pretty much everything else.

---

### Post by What Rights on 2010-08-06
That is the edge I have in windows knowledge vs ubuntu knowledge. The file system.

I will not go back to windows until Windows 8, for learning purposes. And I will occasionally look up and practice certain hardware and software fixes in windows for learning purposes as well.

---

### Post by jv2112 on 2010-08-06
Once you learn you won't go back.....I was Windoze User since 3.1 to Vista then I installed Hardy (Ubuntu) and I have been Linux only for 2 Years...........

Suggested Reading->

Ubuntu Linux Toolbox -Negus /Caen (Good for linux in general and any Debian based distros - Ubuntu, Mint etc)

The Command Line - William E. Schotts 
[http://linuxcommand.org/index.php]("http://linuxcommand.org/index.php")   --> Get a Free Download.

Keep Earning Beans, Making mistakes and learning from them

:guitar:   Have fun.

---

### Post by TBABill on 2010-08-06
+1 for keep on experimenting. In 20 minutes you can have a fresh install if you bork it so badly there's no turning back. But nothing wrong with using both Windows and Linux. They both have their place and purpose and whatever gets your work or mission accomplished best is the right choice at the time. I pretty much stay in Linux at home, but when I need it I use Windows.

---

### Post by espressobeanie on 2010-08-06
Sweet. I'll bookmark this for future reference.

---

