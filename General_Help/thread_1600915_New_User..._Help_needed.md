---
title: "New User... Help needed"
date: 2010-10-19
forum: General Help
---

### Post by pvew on 2010-10-19
Finally tired of MS making my life a misery! Completely new to LInux, Ubuntu 10.10 installed no problems. Like what i see so far But how do I install drivers etc for Webcam (Logitech Quickcam STX) Printer (Cannon MP600). I'm reasonable at sorting out problems in windows but this OS seems like you really have to be a computer wizard. Am I out of my depth using this? or am I just missing the obvious.
Any help appreciated.

---

### Post by M!K3_$ on 2010-10-19
> **pvew said:**
> Webcam (Logitech Quickcam STX) Printer (Cannon MP600). 

Have you tried just plugging in the printer?

or using the webcam?

---

### Post by M!K3_$ on 2010-10-19
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters")

there is the link on how to install cannon printers if yours isn't plug and play

---

### Post by Rubi1200 on 2010-10-19
> **M!K3_$ said:**
> Have you tried just plugging in the printer?

or using the webcam?
+1

Many things _just work_ in Ubuntu with nothing more required than plugging the device in.

If you run into problems, post back with as much information as possible to help us troubleshoot the issue.

Ubuntu, like any other operating system, involves a learning curve, but you will be surprised how quickly you will learn to do things.

Good luck and welcome to the forums.

---

### Post by M!K3_$ on 2010-10-19
[https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")

and that is the docs page for webcams.

---

### Post by ivarn on 2010-10-19
Welcome to the forum and linux.
Ok, what version of ubuntu are you running? 10.04 or 10.10?
Most drivers are already installed as you probably already can see, but if they aren't you should visit their website and find the driver there.
Logitech and cannon are both popular, so it's weird if the driver is not already installed.
Plug in your printer and go to system>admin>printers and see if you can find your printer there if it doesn't work right away.

---

### Post by M!K3_$ on 2010-10-19
> **ivarn said:**
> welcome to the forum and linux.
Ok, what version of ubuntu are you running? 10.04 or 10.10?


> **pvew said:**
> completely new to linux, ubuntu 10.10 installed no problems.

8)

---

### Post by pvew on 2010-10-19
Printer is now working. Moving on to the webcam..... I think I have a lot to learn, I'm so used to MS. Also what do you recommend regards antivirus etc, I read in one area that it is not so necessary in Linux based OS is that true?

---

### Post by rado1 on 2010-10-19
until you try running linux as server there is no need for antivirus.
Install from ubuntu software center cheese ( for webcam ) and ufw (firewall) but that is really a simple firewall ( for that you should check ubuntu forum ).

---

### Post by pvew on 2010-10-19
Hi, thanks for the AV info, my modem is firewalled also I think.
I just tried to install cheese from software center but it wouldn't do it for some reason. Will keep trying and come back if no luck

---

### Post by rado1 on 2010-10-19
Funny think is that cheese install itself in applications -> sound and video.
if not just install skype and go for video test, if that's the reason why you need web cam.

---

### Post by ubudog on 2010-10-19
If you need cheese, you can make sure it's installed by using the terminal.  (Applications>Accessories>Terminal)

At the prompt, to start cheese, type:
```
cheese
```

That simple.  Also, the terminal is the best tool to learn how to use in Linux.  Welcome and hope you enjoy!

---

### Post by rado1 on 2010-10-19
to install cheese from terminal :
sudo apt-get install cheese ( hit enter )
you will be asked for your password, when you write your password it will look like nothing hapends on the screen, but it's normal in terminal

---

### Post by ubudog on 2010-10-19
And if you're wondering, "apt-get" is the default package manager for Ubuntu, but there is also "aptitude".  For example:
```
sudo aptitude install cheese
```

---

### Post by pvew on 2010-10-19
ubudog, excellent advice webcam working
Any good with cannon printer scanner MP600... I installed and the printer works but scanner does not, any ideas.

---

### Post by ubudog on 2010-10-19
What program did you use to scan with?

---

### Post by rado1 on 2010-10-19
sude aptitude install xsane 
i don't see the diference between apt-get and aptitude, is there any?

---

### Post by ubudog on 2010-10-19
Not that big of a difference, but this site talks a little about it.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by rado1 on 2010-10-19
thanks ubudog .

---

### Post by ubudog on 2010-10-19
No problem.

---

### Post by pvew on 2010-10-19
I used the 'simple scan' application in the Ubuntu graphics menu

---

### Post by rado1 on 2010-10-19
this would help : [http://ubuntuforums.org/showthread.php?t=1278863&highlight=canon+scaner](http://ubuntuforums.org/showthread.php?t=1278863&highlight=canon+scaner)
you need canon drivers from their web page.

---

### Post by ivarn on 2010-10-19
HOpe you got your webcam fixed
Back to the virus and firewall thing.
There's no such thing as virus or spyware in ubuntu, but you can get hacked if you use a server since you have open ports. UFW will keep the ports closed if they are not in use.
But ofcourse, they need to know/guess your password to get through, so there's really no need to worry at all.

Here are 3 helpful tools you might wanna use:

1. Terminal on right-click: sudo apt-get install nautilus-open-terminal

2. Remastersys, make personal and distro cd/dvd backup of your system:
[http://scumbox.com/ubuntu/remastersys_2.0-5_all.deb](http://scumbox.com/ubuntu/remastersys_2.0-5_all.deb)

3. Useful java, video and flash codecs:[FONT=monospace]
[/FONT]sudo apt-get install ubuntu-restricted-extras

Have fun with Ubuntu :)

---

### Post by ubudog on 2010-10-20
> **ivarn said:**
> 3. Useful java, video and flash codecs:
sudo apt-get install ubuntu-restricted-extras


That is a great thing to have installed, it provides many codecs and should install flash too, if you don't already have it installed.  Enjoy Ubuntu, an if you need help, just ask!

---

### Post by ubudog on 2010-10-20
Also, since you came from Windows, you may like the program Wine.  It can run .exe files, and some games too. 

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by pvew on 2010-10-20
Hello again,
I installed Wine. I am now trying to install as per instruction of Canon link that Rado 1 gave. I am stuck at this point
[COLOR=#660000]On both distributions, run the .[FONT=courier new]/configure[/FONT] command like this:[/COLOR]

[FONT=courier new]$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var[/FONT]

This will choose [FONT=courier new]/usr/lib/sane[/FONT] as SANE lib directory, [FONT=courier new]/etc/sane.d[/FONT] as SANE config files dir, and [FONT=courier new]/var/lock/sane[/FONT] as state directory: The ones that are used by Mandriva and Ubuntu.

When I type this in terminal command line it tells me
bash: ./configure: No such file or directory
Any help is appreciated.

---

### Post by ubudog on 2010-10-20
Make sure you are in the correct directory/folder.  To get there, you may have to type something like this:

```
cd nameofdir
```

Nameofdir being the name of the directory.

Also, since there is a configure file, there is probably a makefile, so don't use Wine on this.  No need because it can run natively once you compile.

---

### Post by pvew on 2010-10-21
Thanks to all, for the advice and links.. I now have printer/scanner and  webcam. You guys (or girls) have become a Yoda to my Skywalker and I  appreciate it. I have to say, the help for the Linux uneducated on this  forum is way more effective than any MS forum I have ever questioned.
I'm beginning to understand a little but I'm sure to be seeking help again soon.
Keep up the good work.

---

### Post by ubudog on 2010-10-21
No problem!  Just ask if you need more help, one of us will definitely respond.

---

### Post by SeijiSensei on 2010-10-21
If you have to compile the driver, make sure you've installed the "build-essential" package first.  ("sudo apt-get install build-essential")  That contains the gcc compiler and many other tools required to compile software from scratch.

Once you're in the directory with the unpacked source code, you can type ./configure and "make" to compile the driver.  You'll need to use sudo for the final step, "sudo make install".

---

