---
title: "How to use apt for installing software?"
date: 2010-01-14
forum: General Help
---

### Post by pstein on 2010-01-14
Sorry for this newbie question: But how do I install new software with apt in detail?
Ok, the command is e.g.:
 
sudo apt-get install sun-java5-jdk 
 
But from where do I know that the package name is "sun-java5-sdk" and not e.g.
"sunjava-5" or "j2ee-5-sdk" ?
 
As far as I know I have to add the URL of remote software repositories to an Ubuntu list file. To which file? And from where do I get the remote URL?
Is there a meta file which collects all (or at least the top 3000) software package URLs?
 
As far as I know there is a graphical frontend "Synaptics" for apt.
Is it recommended to use this?
 
How do I install this?
 
Thank yuo
Peter

---

### Post by Cheesemill on 2010-01-14
> **pstein said:**
> But from where do I know that the package name is "sun-java5-sdk" and not e.g.
"sunjava-5" or "j2ee-5-sdk" ?

You can use the apt-cache command. For example:
apt-cache search java
will list all the packages that contain the word java (and their descriptions).
 

> 
As far as I know I have to add the URL of remote software repositories to an Ubuntu list file. To which file? And from where do I get the remote URL?
Is there a meta file which collects all (or at least the top 3000) software package URLs?
 
You don't have to do this at all, nearly all of the software your likely to need comes in the default repositories.

> 
As far as I know there is a graphical frontend "Synaptics" for apt.
Is it recommended to use this?
 
How do I install this?
 

You can use it if you want (It's already installed) but for beginners it's better to use the Software Center (Add/Remove Programs in versions earlier than 9.10), all of these have exactly the same end effect.

---

### Post by michy99 on 2010-01-14
The Synaptic Package Manager is already installed under System->Administration->Synaptic Package Manager. If you don't know the name of the package you are looking for, then Synaptic has a pretty good search function. The file that has your repositories is at /etc/apt/sources.list. There is a GUI for managing it at System->Administration->Software Sources. Most things you need are in the standard Ubuntu repositories, so you probably don't need to worry about adding third party repositories unless you want something out of the ordinary.

---

### Post by Leppie on 2010-01-14
you can do a search in the package cache:
```
apt-cache search sun java
```
it will come up with a list of java-related packages.

---

### Post by pstein on 2010-01-14
> **Leppie said:**
> you can do a search in the package cache:
```
apt-cache search sun java
```
it will come up with a list of java-related packages.
 
Ok, fine. Thank you.
 
But in general: Do Synaptics and apt-cache use the same source list (e.g. /etc/apt/sources.list)?
 
 
Or is the software base list of one of them longer and more comprehensive?
 
How can I tell Ubuntu to update this local list from remote master copy?
 
Peter

---

### Post by snowpine on 2010-01-14
> **pstein said:**
> Ok, fine. Thank you.
 
But in general: Do Synaptics and apt-cache use the same source list (e.g. /etc/apt/sources.list)?
 
 
Or is the software base list of one of them longer and more comprehensive?
 
How can I tell Ubuntu to update this local list from remote master copy?
 
Peter

apt-get, synaptic, add/remove programs, software center, etc. all use the same software sources and repository. They are different user interfaces for the same process.

'sudo apt-get update' will update your local list from the remote repositories.

---

### Post by audiomick on 2010-01-14
have a look at
```
man apt
```(type it in a terminal, it calls up the manual page)
and
```
man apt-get
```

---

### Post by Leppie on 2010-01-14
or check online on pages like:
[http://linuxmanpages.com/](http://linuxmanpages.com/)
[http://linux.die.net/man/](http://linux.die.net/man/)
[http://man.he.net/](http://man.he.net/)
[http://www.kernel.org/doc/man-pages/online_pages.html](http://www.kernel.org/doc/man-pages/online_pages.html)

---

### Post by pstein on 2010-01-14
> **snowpine said:**
> apt-get, synaptic, add/remove programs, software center, etc. all use the same software sources and repository. They are different user interfaces for the same process.
 
'sudo apt-get update' will update your local list from the remote repositories.
 
Thank you.
Ok I try to install Sun Java EE 6 SDK available from this web site:
 
[http://java.sun.com/javaee/downloads/index.jsp](http://java.sun.com/javaee/downloads/index.jsp)
 
When I enter now 
 
apt-cache search java ee 6
 
or 
 
apt-cache search java ee sdk
 
or use Synaptics for the same search then I found lots of matches but none of them
does show
 
Java EE 6 SDK
 
Only "normal" Java JDK and libs are listed.
 
Whats the problem?
 
How can it be that this important piece of software is not listed
 
Peter

---

### Post by roharme on 2010-01-14
Type 
sudo apt-get install and press "TAB"

you will get a list of known packages. You can restrict the number of results by typing first few letters of the package and press TAB

---

### Post by Cheesemill on 2010-01-14
It's sun-java6-sdk you're after.

---

### Post by oldos2er on 2010-01-14
Apt only knows about packages in the repositories, that is the list of servers defined by /etc/apt/sources.list (and any listed in files in /etc/apt/sources.list.d/).

If you download a *.deb file from a website, you can install it graphically with the program gdebi, or in the terminal with **sudo dpkg -i filename.deb**

---

