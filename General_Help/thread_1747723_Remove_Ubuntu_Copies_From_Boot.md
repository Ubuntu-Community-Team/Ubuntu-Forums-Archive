---
title: "Remove Ubuntu Copies From Boot?"
date: 2011-05-02
forum: General Help
---

### Post by BlueNinja16 on 2011-05-02
I'm using Windows 7 as my primary operating system. I've been searching but have yet to solve my problem. I suspect my lack of knowledge regarding operating systems is partly to blame.

After a long and difficult process of installing Ubuntu (not Ubuntu's fault), I finally got it to work as an application within Windows via burning the .iso onto a CD. I had some difficulties that I suspect are related to a previous upgrade from XP to Win 7 and the fact that I have two hard-drives.

Anyway, I go into my computer and if I wait it automatically selects windows 7. However, my options look like this:

Earlier version of windows
Windows 7
Ubuntu
Ubuntu
Ubuntu

The first two installations do not work. One does not even load, if I recall correctly. The third appears to be properly installed as a partition within the same drive as Windows 7 (I previously intended to install it on the other drive, which has a windows file I can't remove containing System32 and flash, but nothing else). 

Anyway, there are other problems going on, but my primary concern is just cleaning things up to remove the two additional Ubuntu options. I've looked around for previous installation files (though I had been uninstalling them before) and I've been unsuccessful in terms of removing them.

My third instance of Ubuntu is working well and it seems like a nice operating system so far. The CD is no longer needed and is not present in the drive. Sorry if I was unclear. As I mentioned, I'm fairly unfamiliar with operating systems. This is my first time dealing with them (I'm learning programming languages and Linux seems like a better OS for some of them - Ruby, in particular, which seems to have differing code for different OS')

Thanks

---

### Post by oldfred on 2011-05-02
Welcome to the forums. 

You say you installed inside Windows. Is this a Wubi install. Since you menu shows windows first I expect it is wubi.

Wubi adds menu entries to windows boot loader and uses windows to boot. It really is just a file inside the NTFS partition. Depending on what version of windows you boot, you have to edit windows boot. With win7 I believe it is bcdEdit that you have to use. You may want to backup as I do not know how to tell which is the working version and which is not.

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?")

---

### Post by BlueNinja16 on 2011-05-03
Thanks. I believe it is Wubi. I had intended to install it independently but I ran into too many problems, and I don't have a big preference either way. Your information allowed me to solve the problem. It named the Ubuntu installations in an identical manner "except" for a single letter difference, a, b, c. It also showed me the order in which these installations appear in my menu (and allowed me to change it). So given that I knew the third installation was the one that worked and that installation was "c," I just deleted the others. I figured I'd respond in case someone is searching for the same thing.

So far so good. Thanks again.

---

