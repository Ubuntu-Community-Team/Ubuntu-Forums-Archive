---
title: "ubuntu 11.10 64bit says I'm missing plugin but I don't think so ?"
date: 2011-12-24
forum: General Help
---

### Post by AgentZ86 on 2011-12-24
Hi all

[www.isohunt.com](www.isohunt.com) has a small embedded window in the left of the home page

Says I'm missing plugin

If I click it wants me to install some dos mono plugin thing called iLividSetup.exe?
Do I need this ? Is this really something I'm missing or what is this ?
Can anyone tell me what this is and if this is needed?

I currently have installed the latest Java with IceTea uninstalled and not experiencing any problems that I know of except I noticed this player recently ?

Please advise
Thanks

---

### Post by 73ckn797 on 2011-12-24
Did you install Java from the repos or from Sun?

The repo Sun-java, if it still shows up, does not work correctly anymore. I found that the icedtea-plugin will not work on some sites/link/applets.
I had to follow this: [https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by AgentZ86 on 2012-01-09
> **73ckn797 said:**
> Did you install Java from the repos or from Sun?

The repo Sun-java, if it still shows up, does not work correctly anymore. I found that the icedtea-plugin will not work on some sites/link/applets.
I had to follow this: [https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

Sorry i'm all late with this response, but I have the Sun java plugin installed directly from SUN and installed and it appears to work perfectly

However, this site does not ?

---

### Post by QIII on 2012-01-09
If it's asking you to run an .exe to install something, you're probably out of luck in Linux.  That's a Windows executable.

---

### Post by AgentZ86 on 2012-01-09
I actually do not see the embedded vid thing on that sites main page anymore so I'm assuming the spot that says (download) and Play are what was missing before but there is nothing missing now so I'm guessing it's working

But I don't really see the same embedded thing on that site now so I don't really know

Thanks again

---

### Post by imachavel on 2012-01-09
this is a bit confusing:

[http://www.java.com/en/download/help/enable_console_linux.xml](http://www.java.com/en/download/help/enable_console_linux.xml)

but honestly, isn't it always better to have java installed? I know java isn't always flash but flash is always java, right? Best to have flash working, how is your youtube working?

[http://helpsite.org/install-flash-player-and-java-plugins-for-linux/](http://helpsite.org/install-flash-player-and-java-plugins-for-linux/)

Well, you seem to be an experienced forum member, so if I told you this:

sudo apt-get install sun-java6-plugin flashplugin-installer

or this:

sudo apt-get remove icedtea6-plugin flashplugin-nonfree

from this:

[http://helpsite.org/install-flash-player-and-java-plugins-for-linux/](http://helpsite.org/install-flash-player-and-java-plugins-for-linux/)

---

### Post by QIII on 2012-01-09
No.  Flash Player != Java

Flash Player is to Adobe as pup is to dog.

Java is to Oracle as kitten is to cat (well, to small cat named "Sun" which has been eaten by large cat named "Oracle")

---

### Post by mcduck on 2012-01-10
> **imachavel said:**
> this is a bit confusing:

[http://www.java.com/en/download/help/enable_console_linux.xml](http://www.java.com/en/download/help/enable_console_linux.xml)

but honestly, isn't it always better to have java installed? I know java isn't always flash but flash is always java, right? Best to have flash working, how is your youtube working?

[http://helpsite.org/install-flash-player-and-java-plugins-for-linux/](http://helpsite.org/install-flash-player-and-java-plugins-for-linux/)

Well, you seem to be an experienced forum member, so if I told you this:

sudo apt-get install sun-java6-plugin flashplugin-installer

or this:

sudo apt-get remove icedtea6-plugin flashplugin-nonfree

from this:

[http://helpsite.org/install-flash-player-and-java-plugins-for-linux/](http://helpsite.org/install-flash-player-and-java-plugins-for-linux/)

Flash and Java have *absolutely nothing* to do with each other, apart from the single fact that both technologies can be used in the Web. :)

edit: by the way, "iLividSetup.exe" doesn't sound like any valid web plugin for windows either. I would dismiss anything like that popping up on a web page as a trojan.

edit2: it seems to be Rapidshare's download manager. Nothing to do with your videos or anything like that, you shouldn't need such thing for anything unless you are a heavy rapidshare user.

---

