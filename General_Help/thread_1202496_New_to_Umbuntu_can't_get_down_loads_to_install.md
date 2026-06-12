---
title: "New to Umbuntu can't get down loads to install"
date: 2009-07-02
forum: General Help
---

### Post by aljp497 on 2009-07-02
Hello people I just loaded Umbuntu 9 on a old computer some one gave me because I built them a new one. Anyway I have it up and runing but if I down load c cleaner or win zip I can't seem to get them to install and run I have yet to try AVG anti virus . I get a message about unable to unzip ????

HELP !! lost in up state NY


):P

---

### Post by WRDN on 2009-07-02
Welcome to Ubuntu and the Ubuntu Forums!

First off, Ubuntu is not Windows, so there will be multiple programs that are not available, and some you no longer need.

Starting with CCleaner, there is little need for such a tool in Ubuntu (no registry).
As for WinZip, it isn't supported, so you need to use the unzip tool instead.
You don't need antivirus program(s) in Linux, as you can't get a virus. You can get rootkits though, so, I would recommend always installing software through the official repositories (these can be viewed in System > Administration > Synaptic Package Manager, and the list of repositories can be viewed at /etc/apt/sources.list).

If you really want to run Windows Applications in Ubuntu, use WINE:

```
sudo apt-get install wine
```

Then:

```
wine application.exe
```

---

### Post by aljp497 on 2009-07-02
> **wrdn said:**
> welcome to ubuntu and the ubuntu forums!

First off, ubuntu is not windows, so there will be multiple programs that are not available, and some you no longer need.

Starting with ccleaner, there is little need for such a tool in ubuntu (no registry).
As for winzip, it isn't supported, so you need to use the unzip tool instead.
You don't need antivirus program(s) in linux, as you can't get a virus. You can get rootkits though, so, i would recommend always installing software through the official repositories (these can be viewed in system > administration > synaptic package manager, and the list of repositories can be viewed at /etc/apt/sources.list).

If you really want to run windows applications in ubuntu, use wine:

```
sudo apt-get install wine
```

then:

```
wine application.exe
```



where do i type this don't have ru cmd so how do i go about this

---

### Post by natravis on 2009-07-02
> **aljp497 said:**
> where do i type this don't have ru cmd so how do i go about this

An answer to your specific question:

In the top left of your screen, click on Applications -> Accessories -> Terminal to access the cmd line. It is very useful for certain things but you can do almost anything from the GUI (graphical user interface ... in other words, what you see by default). To see available applications, click Applications -> Add/Remove. There are lots of apps available for different purposes. Within Add/Remove, just check a program's box to install or uncheck to uninstall and then hit Apply Changes.

Read through this thread

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

for some advice on getting started. There are many resources already available to you. Try using the search function after going through some of the Beginner's Help forum and then ask away! The community is glad to help those who first try to help themselves (that isn't being mean or anything, just how it works. Look for the answer before asking because oftentimes it is already there).

Good Luck!

---

### Post by DeMus on 2009-07-02
I don't want to be annoying but it seems to me you really have to do a lot of reading before you can really use this OS.
Linux and Windows are both OS's and that is all they have in common.
They both use different filesystems ( the way they put data on disk ), they use different types of programs ( Windows .exe, Linux about everything).
Windows programs won't run on Linux, except when using a layer in between the two called Wine.
Viruses are not known to the Linux world, so no anti-virusprogram is needed.
You use the computer as a "simple" user, instead of an administrator like in Windows.
You see there a lot of differences. Read as much as you can find about Linux and Ubuntu in particular, start here for example:

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty")

[http://ubuntuforums.org/showthread.php?t=801404]("http://ubuntuforums.org/showthread.php?t=801404")

[https://help.ubuntu.com/9.04/index.html]("https://help.ubuntu.com/9.04/index.html")


Have fun and forget about everything you learned in the Windows world. You don't need it anymore. It's time for a change.

---

### Post by oldos2er on 2009-07-02
> **DeMus said:**
> Read as much as you can find about Linux and Ubuntu in particular, start here for example:

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)


Have fun and forget about everything you learned in the Windows world. You don't need it anymore. It's time for a change.

 And to add a link I think is important: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by aljp497 on 2009-07-04
Thank you all so much for your replys..


AL

---

### Post by natravis on 2009-07-05
> **DeMus said:**
> 
Viruses are not known to the Linux world, so no anti-virusprogram is needed.

This is kind of deceptive. Viruses are technically not around on Unix based systems but rootkits and other malware are definitely around and ways to prevent/fight those can be found in the security forums.

---

