---
title: "Installation of thunderbird 3"
date: 2010-01-29
forum: General Help
---

### Post by musdem on 2010-01-29
I have just downloaded Thunderbird and I'm trying to install it but whenever I try to run the "thunderbird" file it just runs and it doesn't install. How do i install it properly?

---

### Post by linuxwizard on 2010-01-29
Use Ubuntuzilla to install Thunderbird. Works Great

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by musdem on 2010-01-29
I downloaded the deb file and it said: Error: Wrong architecture 'i386'
I have a 64 bit version of Ubuntu.

---

### Post by Uncle Spellbinder on 2010-01-29
64bit users note: there are no 64bit packages in this repository, since Mozilla only releases 32bit builds. For alternative installation options, see [here](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#64bit_users).




.

---

### Post by musdem on 2010-01-29
Please stop giving me links I can't find anything on any of these links.

---

### Post by Uncle Spellbinder on 2010-01-29
> **musdem said:**
> Please stop giving me links I can't find anything on any of these links.
??????????????????????????????


Links are working fine for me. All full of useful info. :-k

And besides, you asked for help. If you don't want to be redirected to a place (link) that can offer assistance then why even bother asking????

---

### Post by akshay.sulakhe on 2010-01-29
I just  did this,sudo apt-get install thunderbird...m i wrong???

---

### Post by musdem on 2010-01-29
I do want help I just want a straight forward answer not just a link.

---

### Post by SecretCode on 2010-01-29
> **musdem said:**
> I do want help I just want a straight forward answer not just a link.

Straightforward answer: Install Thunderbird 2 from the repositories. 

You shouldn't be trying Tb 3 if you are not comfortable doing research on the web. Many Tb 2 extensions are not yet available for Tb 3 and require some hacking ... which you will not find out about.

---

### Post by musdem on 2010-01-29
I'm perfectly comfortable looking things up on the web its just on the links provided I didn't find anything.

---

### Post by Uncle Spellbinder on 2010-01-29
> **musdem said:**
> I'm perfectly comfortable looking things up on the web its just on the links provided I didn't find anything.

Couldn't find anything???? I posted a link for you in [post #4](http://ubuntuforums.org/showthread.php?p=8743506#post8743506) which is loaded with information on EXACTLY your situation. I just followed from that link as if I were in your situation using 64 bit. I had no issue. Simple to follow. All you need to do is *read*.

Simply follow the link I provided, or use Thunderbird 2. Quite simple, really.

---

### Post by wojox on 2010-01-29
[Installation of thunderbird 3]("http://wojox.homelinux.net/?p=20")

---

### Post by musdem on 2010-01-29
OK on the link you gave me there was this link [Ubuntu Mozilla Daily PPA]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa") I clicked on it and it gave me a bunch of packages including thunderbird 3.0 but none of them were download links am i missing something or do they show up as links for you?

---

### Post by wojox on 2010-01-29
[http://wojox.homelinux.net/?p=20](http://wojox.homelinux.net/?p=20)

---

### Post by scouser73 on 2010-01-29
Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3.01**[/COLOR]]("http://www.mozillamessaging.com/en-US/thunderbird/all.html")


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

### Post by wilee-nilee on 2010-01-29
> **wojox said:**
> [http://wojox.homelinux.net/?p=20](http://wojox.homelinux.net/?p=20)

Use this method it will install the repository and the signing key, and T3.

---

