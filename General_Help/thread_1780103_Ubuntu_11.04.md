---
title: "Ubuntu 11.04"
date: 2011-06-11
forum: General Help
---

### Post by fiblend on 2011-06-11
I have three issues that I would like help on.  First, I would like to say that I am somewhat of a novice with Ubuntu.  Now for the issues:

1. Ubuntu does not detect my USB HDD.  That also includes the Disk Utility Program.  However, Ubuntu does detect my USB Flash Drive.

2. Cron does not seem to work.  I have setup jobs (using the Scheduled Task Program) to run at specific times.  Nothing happens.

3. DVD's will not play.  What is the procedure for installing the needed codec and where can I locate said codec?

Environment Specifics:

Computer: HP Pavilion zv6000 Laptop.
Processor: AMD 64 bit Athlon
Memory: 1.5g
OS: Ubuntu 11.04 (only OS on the computer)

I like using Ubuntu to get away from Windows and the related overhead (including malware and viruses) that comes with the Window's OS.  I hope that someone can resolve these issues.  Thank you.

---

### Post by ivanovnegro on 2011-06-11
To your third question, install the Ubuntu Restricted Extras and also add [Medibuntu]("http://medibuntu.org/repository.php") to sources list.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **fiblend said:**
> I have three issues that I would like help on.  First, I would like to say that I am somewhat of a novice with Ubuntu.  Now for the issues:

1. Ubuntu does not detect my USB HDD.  That also includes the Disk Utility Program.  However, Ubuntu does detect my USB Flash Drive.

2. Cron does not seem to work.  I have setup jobs (using the Scheduled Task Program) to run at specific times.  Nothing happens.

3. DVD's will not play.  What is the procedure for installing the needed codec and where can I locate said codec?

Environment Specifics:

Computer: HP Pavilion zv6000 Laptop.
Processor: AMD 64 bit Athlon
Memory: 1.5g
OS: Ubuntu 11.04 (only OS on the computer)

I like using Ubuntu to get away from Windows and the related overhead (including malware and viruses) that comes with the Window's OS.  I hope that someone can resolve these issues.  Thank you.

Here is a guide to get everything you need installed:

11.04
[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

10.10 
[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by fiblend on 2011-06-11
I still get the message "An error occurred Could not read DVD.  This may be because the DVD is encrypted and a DVD decryption library is not installed."

Anything else that I need to do?  Again, thanks.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **fiblend said:**
> I still get the message "An error occurred Could not read DVD.  This may be because the DVD is encrypted and a DVD decryption library is not installed."

Anything else that I need to do?  Again, thanks.
```

sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/./install-css.sh

sudo apt-get install libdvdcss2 libdvdnav4 vlc

```Does it say it has installed successfully when you try that? Or did you catch an error that the package isn't available?

---

### Post by ivanovnegro on 2011-06-11
> **fiblend said:**
> I still get the message "An error occurred Could not read DVD.  This may be because the DVD is encrypted and a DVD decryption library is not installed."

Anything else that I need to do?  Again, thanks.

Install now libdvdcss2, libdvdread4 and maybe also w32codecs for DVD playback.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **ivanovnegro said:**
> Install now libdvdcss2, libdvdread4 and maybe also w32codecs for DVD playback.

I think the user needs to install all the codecs on that guide I posted..   They are skipping something probably.

---

### Post by ivanovnegro on 2011-06-11
> **linuxinstalledfromhdd said:**
> I think the user needs to install all the codecs on that guide I posted..   They are skipping something probably.

Yes, you provided the right steps to install them all.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **ivanovnegro said:**
> Yes, you provided the right steps to install them all.

Weird :)

---

### Post by fiblend on 2011-06-11
I also installed w32codecs and it worked.  Thank you for your help

---

### Post by fiblend on 2011-06-11
> **ivanovnegro said:**
> Install now libdvdcss2, libdvdread4 and maybe also w32codecs for DVD playback.
There be DVD here.  Thank you.

---

### Post by fiblend on 2011-06-11
That was a major help to the insight of workings of Ubuntu.  Again, thank you.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **fiblend said:**
> I also installed w32codecs and it worked.  Thank you for your help

First you tell me you went down the list I posted, and then you say you missed one of them...   Seriously, if users follow the instructions as posted, you wouldn't have any problems anymore. :)   If you are still having trouble go down the list I posted already, and this time really really really make sure, by using the commands I gave you.. I'm not going to tell the same user twice.

---

### Post by ivanovnegro on 2011-06-11
> **fiblend said:**
> That was a major help to the insight of workings of Ubuntu.  Again, thank you.

Glad that it worked, enjoy your Ubuntu install.

> **linuxinstalledfromhdd said:**
> First you tell me you went down the list I posted, and then you say you missed one of them...   Seriously, if users follow the instructions as posted, you wouldn't have any problems anymore. :)   If you are still having trouble go down the list I posted already, and this time really really really make sure, by using the commands I gave you.. I'm not going to tell the same user twice.

Ok, I understand what you mean, but it seems we posted the same time, maybe it was confusing, also many people dont like the command line route.
You can install everything from Synaptic or the Software Center once you added the correct repo, even the repo you can add the graphical way. Though, with more experience you could also use the command line, it is maybe also better to use the command line when you really know what the commands are doing for you instead to just copy them. Even though you provided great links and how-to's but sometimes the people are scared about too many informations. This is not a critique, I try to understand the way the OP wanted to solve the problem.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **ivanovnegro said:**
> Glad that it worked, enjoy your Ubuntu install.



Ok, I understand what you mean, but it seems we posted the same time, maybe it was confusing, also many people dont like the command line route.
You can install everything from Synaptic or the Software Center once you added the correct repo, even the repo you can add the graphical way. Though, with more experience you could also use the command line, it is maybe also better to use the command line when you really know what the commands are doing for you instead to just copy them. Even though you provided great links and how-to's but sometimes the people are scared about too many informations.

If they went down the list, cut and paste each of those commands (reading the instructions before hand of course) this probem would have been solved for them hours ago.  I posted it, and they don't read it, or use it, and still have issues..  Bah. Users have to take the time to learn how to use their systems first.

---

### Post by nothingspecial on 2011-06-11
> **ivanovnegro said:**
> it is maybe also better to use the command line when you really know what the commands are doing for you instead to just copy them.

Absolutely :D

If you post commands, explain exactly what they do.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **nothingspecial said:**
> Absolutely :D

If you post commands, explain exactly what they do.

I posted a link to a web site.  It explains what they do. They aren't taking the time to read it though.

"*Everybody's Got to Learn Sometime..."*

---

### Post by 3rdalbum on 2011-06-11
> **fiblend said:**
> I have three issues that I would like help on.  First, I would like to say that I am somewhat of a novice with Ubuntu.  Now for the issues:

1. Ubuntu does not detect my USB HDD.  That also includes the Disk Utility Program.  However, Ubuntu does detect my USB Flash Drive.

2. Cron does not seem to work.  I have setup jobs (using the Scheduled Task Program) to run at specific times.  Nothing happens.

1. As far as Ubuntu is concerned, USB hard disks are the same thing as USB flash drives - same driver and everything. Does this hard disk definitely work, like, on other computers? What filesystem is on it? Does it show up if you run the 'lsusb' command? If it has a separate power cable, is this plugged in? (some can run through the bus OR through a power cable, try it with the power cable).

2. Cron will not run graphical programs; if you tried to test it out by putting "firefox" in your crontab, for instance, it will not work.

---

### Post by fiblend on 2011-06-12
As far as crontab is concerned, I was able to make it work in the GUI by stating the run type as an xapplication not default.  I'll look at the HDD issue in a little while.  Thank you.

---

