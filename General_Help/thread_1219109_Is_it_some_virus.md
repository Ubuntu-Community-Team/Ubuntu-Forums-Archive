---
title: "Is it some virus?"
date: 2009-07-21
forum: General Help
---

### Post by kewl_123 on 2009-07-21
Hi,
    I had the setting to suspend my laptop when the lid is closed, but yesterday I noticed that it was ON even after closing the lid. So I made the necessary change. Again today it the same problem has occured. How come the settings are getting changed automatically? Is it some virus?

---

### Post by XCan on 2009-07-21
I don't think that is a virus, but rather something else you are using that's interfering with the settings. Perhaps when Ubuntu switches between the different power-saving modes?

PS. If it indeed is a virus, you should almost feel lucky for managing to get one. ;)

---

### Post by mudcat on 2009-07-21
Probably not a virus, but use ClamAV just to be safe ;).

---

### Post by hyperdude111 on 2009-07-21
You are not going to get a virus on Linux. They do not exist, there are security exploits but they get patched instantly. You do not need clamav, clamav is an app designed for those using windows and ubuntu to scan their files to prevent windows from getting a virus, ubuntu will not get a virus. 

The only way for a virus to do damage on linux is if it was a linux designed virus and you actively entered your password for this third party piece of software knowing what it was going to do. In ubuntu/linux you can NOT ge a virus from going to an infected wesite of stuff like that.

---

### Post by WIGGMPk on 2009-07-21
> **hyperdude111 said:**
> You are not going to get a virus on Linux. They do not exist, there are security exploits but they get patched instantly. You do not need clamav, clamav is an app designed for those using windows and ubuntu to scan their files to prevent windows from getting a virus, ubuntu will not get a virus. 

The only way for a virus to do damage on linux is if it was a linux designed virus and you actively entered your password for this third party piece of software knowing what it was going to do. In ubuntu/linux you can NOT ge a virus from going to an infected wesite of stuff like that.

This is not true.. Linux can definitely get a virus, and to say otherwise would be completely ignorant. Linux is better to be considered as 1000000% more virus RESISTANT than Windows, due to its design. Another aspect that plays a role is the fact that Windows is targeted more often than any other Operating System. I just recently (even though its outdated now) read an article about the Bliss virus that was posted on some security forum. It was a Linux designed virus and it worked.

It is, however, impossible for a native Windows virus to infect a Linux system, which is most likely what you were trying to refer to.

The key relys on education of the user and awareness. Not running things as root! Familiarize yourself with the system and how it works. Understand where you are getting stuff from BEFORE running it. Dont use packages that arent digitally signed.

---

### Post by devildoc5 on 2009-07-21
kinda what WIGGMPk was getting at but don't EVER run things as root that have no need to be run as such and don't run things from places you do not trust. 

In other words use your head and don't use anything that has even a LITTLE bit of suspicion in your mind AT ALL.....EVER

also this quote from: [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

```

The number of malicious programs&#8212;including viruses, Trojans, 
and other threats&#8212;specifically written for Linux has been on 
the increase in recent years and more than doubled during 2005 from 422 to 863

```

---

### Post by Tipped OuT on 2009-07-21
> **kewl_123 said:**
> Hi,
    I had the setting to suspend my laptop when the lid is closed, but yesterday I noticed that it was ON even after closing the lid. So I made the necessary change. Again today it the same problem has occured. How come the settings are getting changed automatically? Is it some virus?

It's definitely not a virus. Could just be a driver problem, or you have something configured incorrectly.

---

### Post by WIGGMPk on 2009-07-21
kewl_123

If your interested in Linux/Ubuntu security and some of the difference between the operating systems (which I assume you have migrated or are in the process of migrating from Windows) there is a really good article about the differences between the two mindsets (Linux Vs Windows).


[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by kewl_123 on 2009-07-21
> **devildoc5 said:**
>  and don't run things from places you do not trust. 

From this quote and all the replies, I understand one thing that any software I install on Ubuntu must be from trusted/genuine source. As a newbie, could you please tell me whats the criteria that decides if a source is trustworthy, besides digital certificate?
I have read about repositiries, but it seems you need to edit some files to add repositiries, which I dont want to do at this stage.
Thank you.

---

### Post by WIGGMPk on 2009-07-22
> **kewl_123 said:**
> From this quote and all the replies, I understand one thing that any software I install on Ubuntu must be from trusted/genuine source. As a newbie, could you please tell me whats the criteria that decides if a source is trustworthy, besides digital certificate?
I have read about repositiries, but it seems you need to edit some files to add repositiries, which I dont want to do at this stage.
Thank you.

Adding repositories is very easy and straight forward.. 

Let me reference some 3rd party software that made things easier for me when I first came to Ubuntu.

Ubuntu Tweak has you add a repository to your source list the original way. That would be by doing this from a terminal:

```
gksudo gedit /etc/apt/sources.list
```

And then adding this line to the bottom of the file and saving:

```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main
```

This line (specific to Jaunty Jackalope only) is the repository. The source.list file you add it to is where aptitude checks to 'retrieve' software you ask for.

Then, you download and add the 'key' that identifies the source of the packages for security and 'trust'.

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220
```

After that, you finished...

Running the following command will update your systems available resources (repository)

```
sudo apt-get update
```

And if you wish to install the package (which is why you would add the repository in the first place) you would run

```
sudo apt-get install ubuntu-tweak
```

The alternative way of adding the repository and downloading the application is via the GUI. If your not comfortable with using the commandline (terminal), then you can do it this way:

System > Administration > Software Sources

It should prompt you for your password. After that, there is a tab to add the same line from above (except its user interface driven). After that, another tab is in the same application to add keys. When you exit, it will recognize a change and ask you to 'reload' your sources.. This is the same as running the "sudo apt-get update" command above.

In this particular situation it would be easier to add the key from the command shown above. (Primarily cause im at work and I dont remember the GUI very well)

To install the application, you would open up System > Administration > Synaptic Package Manager

Once inside there, enter in the search box the application you want to install. In this case, Ubuntu Tweak. Click on the application and hit apply.

Repositories have a big advantage for installing software. However you could always search online to fine .deb packages and install them by double clicking (much like a .exe file acts in windows). However installing from a downloaded .deb package is risky unless you know the source.

I hope this info proves helpful. You shouldnt be afraid of editing the /etc/apt/sources.list file for repositories. Its fun and its one of the first steps to getting to play around with your system.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

That will make a backup of the sources just incase.

```
sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list
```

Will move your backup copy to the original incase you need to recover.


BTW: Ubuntu Tweak has a feature to add repositories/keys for you via a cool user interface. It also has the ability to select and install popular software. You would find it useful, I have been using Linux for about 2 years and still consider myself a newbie, just ask a lot of questions and dont be afraid to break things.

---

