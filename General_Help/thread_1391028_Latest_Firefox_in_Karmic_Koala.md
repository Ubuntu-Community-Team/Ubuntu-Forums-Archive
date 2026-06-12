---
title: "Latest Firefox in Karmic Koala"
date: 2010-01-26
forum: General Help
---

### Post by howcanireachthesekids on 2010-01-26
I am not sure if this is the right board ...

So i have some questions. Mozilla Firefox's latest version is out 3.6 like we know. I downloaded the package 4 days ago from firefox.com for Ubuntu. When i run it in the about menu it will show " Firefox 3.6.1pre " oh and the name is Namoroka, not Mozilla Firefox.

Is this supposed to be the latest stable version ? Or am i using some alpha release ?

What is the latest stable version of firefox for Ubuntu ?

---

### Post by warfacegod on 2010-01-26
> **howcanireachthesekids said:**
> I am not sure if this is the right board ...

So i have some questions. Mozilla Firefox's latest version is out 3.6 like we know. I downloaded the package 4 days ago from firefox.com for Ubuntu. When i run it in the about menu it will show " Firefox 3.6.1pre " oh and the name is Namoroka, not Mozilla Firefox.

Is this supposed to be the latest stable version ? Or am i using some alpha release ?

What is the latest stable version of firefox for Ubuntu ?

I believe that the latest stable version for *Ubuntu* is still 3.5, if a package isn't in the repositories yet, that generally means Ubuntu hasn't finished testing it yet.

---

### Post by crichard on 2010-01-26
> **howcanireachthesekids said:**
> I am not sure if this is the right board ...

So i have some questions. Mozilla Firefox's latest version is out 3.6 like we know. I downloaded the package 4 days ago from firefox.com for Ubuntu. When i run it in the about menu it will show " Firefox 3.6.1pre " oh and the name is Namoroka, not Mozilla Firefox.

Is this supposed to be the latest stable version ? Or am i using some alpha release ?

What is the latest stable version of firefox for Ubuntu ?

It seems you've installed firefox from ubuntu-mozilla-daily PPA repositories.If you are using 32 bit,it is better to install firefox from[ ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page").Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1193567") to optimize and troubleshoot firefox.

---

### Post by howcanireachthesekids on 2010-01-26
> **crichard said:**
> It seems you've installed firefox from ubuntu-mozilla-daily PPA repositories.If you are using 32 bit,it is better to install firefox from[ ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page").Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1193567") to optimize and troubleshoot firefox.
Well even when i download the package from firefox.com, it must be 3.6. I open it it will say 3.6.1pre

i am confused :? shouldn't it be 3.6 and named Mozilla Firefox and Namoroka ?

---

### Post by ratcheer on 2010-01-26
If you download and extract directly from the Firefox website, and start Firefox from the directory you extracted it to, it will be branded as "Firefox" and it will be the stable released version.

Tim

---

### Post by aysiu on 2010-01-26
There is no package for Ubuntu from firefox.com

What you should get, if you go there, is a .tar.bz2 file (which is just a compressed file). Extract it and double-click *firefox* and that will launch the stable 3.6.

That, however, does **not** install Firefox. That just has a bunch of files in your home directory. Clicking on the Firefox launcher or going to /usr/bin/firefox will still launch your old Firefox (which sounds as if it's from some PPA daily build).

If you want to install Firefox 3.6 and have it actually work, use UbuntuZilla.

---

### Post by Tourdog on 2010-01-26
I downloaded the file:   firefox-3.6.1pre.en-US.linux-x86_64.tar.bz2 from ppa.  It is a 10.9 mb archived file.   It is 3.6.1pre.   It is "namoroka".  It is one of the "nightly builds.   And, it is the 64 bit version of 3.6..........  it has the various "skins" to dress up the spare gnome front end of 9.10.  Unarchived, I think 44 files and if you use "places" up top your screen and chase your new namoroka down the executable script file is one of the 44.  Double click it (firefox) and voila!

It seems stable and I think a little faster.

On boot up I have it in my "Start Applications" as a script.   Works fine.

hth  ;)

---

### Post by ratcheer on 2010-01-27
> **aysiu said:**
> 

If you want to install Firefox 3.6 and have it actually work, use UbuntuZilla.

It ***actually works***, just fine, whether it is installed or not.

Tim

---

### Post by scouser73 on 2010-01-27
[[COLOR="Red"]**Download Firefox 3.6**[/COLOR]]("http://www.mozilla.com/en-US/firefox/all.html")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

Enter these commands in Terminal

> sudo -i
Enter your password if asked
> cd /opt
> chown -R username firefox
[COLOR="Red"]**The username is what you use to log in to Ubuntu**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

---

### Post by Uncle Spellbinder on 2010-01-27
> **aysiu said:**
> f you want to install Firefox 3.6 and have it actually work, use UbuntuZilla.
Without a doubt Ubuntuzilla the BEST way to go.

Simply add to following to your sources.list:
```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

Add the key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

Then do:
```
sudo apt-get update
```

Then do:
```
sudo apt-get install firefox-mozilla-build
```

More info here: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) and here: [http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by aysiu on 2010-01-27
> **ratcheer said:**
> It ***actually works***, just fine, whether it is installed or not.

Tim
I'm talking to howcanireachthesekids, not you.

---

