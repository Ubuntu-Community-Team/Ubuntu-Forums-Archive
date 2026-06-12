---
title: "Ubuntu - 9.04 - Java installing help"
date: 2009-09-10
forum: General Help
---

### Post by Rile on 2009-09-10
I've _always_ wanted Ubuntu ever since I've found out about it. Today I got the Ubuntu 9.04 disk in the mail and converted my Vista laptop into Ubuntu. I did this about 5 minutes ago. Well, I've been trying to set things up so they work and allow me to do things as my Vista did and I started with installing Java first. I went to the Java site and downloaded (Linux RPM self-extracting file) (not knowing if that is the right download or not) Well I downloaded it and it saved as a text file. I tried looking at things online to help me download it. 

I went to a Java help site and it told me to open the terminal and type;

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```Which I did. When I hit enter the terminal replied with;

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

I just want to install Java :(

I know I have lots yet to learn about Ubuntu, I would appreciate if someone would help me with this. Thanks.

---

### Post by mbrush on 2009-09-10
The command you tried worked for me.

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

Try updating your package list and then try the above command again:

sudo apt-get update

Also, what are the contents of the file '/etc/apt/sources.list'?

---

### Post by Zifnab06 on 2009-09-10
Another thing you can do is open a terminal and type "java" in the terminal. It will show you a list of packages, as well as how to install them, that contain java. I think that either sun-java6-jre or sun-java6-jdk will work.

---

### Post by Rile on 2009-09-10
I turned the repo on, etc. I did it again and it worked;

Setting up sun-java6-plugin (6-16-0ubuntu1.9.04) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

When I try watching youtube videos though it still says;

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/").

---

### Post by mbrush on 2009-09-10
Download the Linux version of Adobe flash player from [http://get.adobe.com/flashplayer]("http://get.adobe.com/flashplayer") (it should auto-detect that for you), choose the .deb for Ubuntu 8.04+ file.

Once it's downloaded use GDebiInstaller to install it or from the command line:
```

sudo dpkg -i install_flash_player_10_linux.deb

```

---

### Post by 4Orbs on 2009-09-10
In the "Multimedia and Video" section of these forums is a sticky thread titled "Comprehensive Multimedia and Video How-to". It is the easiest way I have found to get all the good stuff working correctly.

---

