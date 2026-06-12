---
title: "Installing thunderbird"
date: 2011-03-19
forum: General Help
---

### Post by rogerpb on 2011-03-19
As a newbie who succeeded in installing Ubuntu 10.4 on a Samsung netbook, and accessing Firefox, I today tried to install Thunderbird.

Using an Addison-Wesley Guide (for version 9.4), I called up SYSTEM/ SYSTEM ADMINISTRATION/SYNAPTIC, and then marked the packets Thunderbird (the basic program) and thunderbird-locale-en-gb. I then used the green tick to apply.

I soon got a message “an error occurred”--- 
W. failed to fetch [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) /pool/main/t/ Could not resolve security.ubuntu.com. thunderbird_3.1.7+build3+nobinonly-0ubuntu.10.04.1_i386.deb
Could not resolve ‘security.ubuntu.com’

There was a similar message for the second file. 

After this failure, I referred to another book, simply called “Ubuntu”. from Markt+Technik Verlag, in German,published in 2010. It had different instructions for installing Thunderbird: Open Applications/Software Center, click in the category Internet, select Thunderbird and click on Install.

Several hours later I found two green arrows still rotating on the screen, with the message “In progress”. So I broke this attempt off.

I then tried running an update. This appeared to work.

Referring to Chapter 17 of the Addison Wesley book, Basics of Packet Administration, I learned that using Synaptic and the command apt-get would ensure that each packet is installed with all its dependencies. 

So I then tried the command line 
sudo apt-get install thunderbird.

This produced
E: could not get lock/var/lib/dpgk/lock - open (11:resource temporary unavailable
E: Unable to lock the administration directory (/var/lib/dpkg). is another process using it?

Where do I go from here? Perhaps I am trying to run before I can walk, but I thought that installing a standard mail program was a fairly basic process!:confused:

---

### Post by ChuckyDuckster on 2011-03-19
> **rogerpb said:**
> 
This produced
E: could not get lock/var/lib/dpgk/lock - open (11:resource temporary unavailable
E: Unable to lock the administration directory (/var/lib/dpkg). is another process using it?


All this means is that you already had an application open with admin proveleges (did you still have synaptic up?). Try to run the terminal commands without Synaptic open.

Cheers

---

### Post by rogerpb on 2011-03-28
> **ChuckyDuckster said:**
> All this means is that you already had an application open with admin proveleges (did you still have synaptic up?). Try to run the terminal commands without Synaptic open.

Cheers
OK. I restarted Ubuntu, ran sudo rm/var/lib/dpkg/lock, autoremoved packages it said were no longer required, using apt-get autoremove.

I read:

"The following new packages will be installed:
thunderbird"

 Then came....
----could not resolve 'at.archive.ubuntu.com'
----could not resolve 'security.ubuntu.com'
E: unable to fetch some archives, maybe run apt-get update or try with .... fix-missing.

I had previously run apt-get update, but have no idea of the syntax of --- fix missing.
sudo apt-get install thunderbird fix missing did not work: I got a message:
E:No command 'fix 'found, but there are sixteen similar ones.

So what do I do now, please?

---

### Post by scouser73 on 2011-03-28
Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by fela on 2011-03-28
Try this:

```
sudo apt-get update && sudo apt-get install thunderbird
```

---

### Post by SeijiSensei on 2011-03-28
I strongly suggest following fela's advice before trying to install TBird directly from Mozilla's site.  If you don't install from the repositories, Ubuntu will be unable to keep your version up-to-date.

Oh, and the command you wanted to use before is actually

```
sudo apt-get install thunderbird **--fix-missing**
```

Type "man apt-get" to see a complete list of options.

---

