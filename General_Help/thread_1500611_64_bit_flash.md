---
title: "64 bit flash"
date: 2010-06-03
forum: General Help
---

### Post by jamesjph on 2010-06-03
A version of flash for all ubuntu 64bit computers.

:)

Here is the coding within

```
#!/bin/bash

function strinput {
 unset refstr
 echo -n "$1"
 read refstr
}

echo " This script is used to setup the Flash 10 Alpha. "
echo " Type y and hit enter to start : "

if [ "$installtype" = "" ]
then
 echo -n "(Enter the lower case y and press enter key)"
 strinput
else
 refstr=$installtype
fi

if [ "$refstr" = "y" ]
then
 echo "Flash installing."

sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so

sudo mkdir /tmp/jphweb/
sudo mkdir /tmp/jphweb/flash
cd /tmp/jphweb/flash/
sudo wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz

sudo tar xvf libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/

elif [ "$refstr" = "n" ]
then
 echo "I am sorry but you have to agree. "

else
 echo  " I am sorry but you have to agree. "
 echo
fi

sudo rm -rfd /tmp/jphweb/
```

---

### Post by howefield on 2010-06-03
Always better downloading from an authoritative/trusted site.

Unlike the link in this thread.

---

### Post by jamesjph on 2010-06-03
Changed link to attachment.
Thanks

---

### Post by howefield on 2010-06-03
> **jamesjph said:**
> Changed link to attachment.
Thanks

So what ?

Why would someone take a file from an untrusted source ?

Not that you are untrustworthy necessarily, just saying. Your original link saved an html file, what is in your new file at only 627 Bytes ?

---

### Post by philinux on 2010-06-03
I always get it from here. It's been available for ages.

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

---

### Post by tommcd on 2010-06-03
> **jamesjph said:**
> A version of flash for all ubuntu 64bit computers.
:)
Flash for 64bit Ubuntu is in the Ubuntu repos:
[http://packages.ubuntu.com/lucid/flashplugin-installer](http://packages.ubuntu.com/lucid/flashplugin-installer)

---

### Post by howefield on 2010-06-03
> **tommcd said:**
> Flash for 64bit Ubuntu is in the Ubuntu repos:
[http://packages.ubuntu.com/lucid/flashplugin-installer](http://packages.ubuntu.com/lucid/flashplugin-installer)

This isn't 64 bit flash though, is it ?

---

### Post by philinux on 2010-06-03
> **tommcd said:**
> Flash for 64bit Ubuntu is in the Ubuntu repos:
[http://packages.ubuntu.com/lucid/flashplugin-installer](http://packages.ubuntu.com/lucid/flashplugin-installer)

Thats the 32 bit flash using the wrapper. Full screen button doesn't work with it either.

---

### Post by Bluesan on 2010-06-03
> **tommcd said:**
> Flash for 64bit Ubuntu is in the Ubuntu repos:
[http://packages.ubuntu.com/lucid/flashplugin-installer](http://packages.ubuntu.com/lucid/flashplugin-installer)

Adding...

If you're running a 64 bit install, and you then install the Ubuntu restricted extras packages, do you now get the 64 bit version of flash automatically?

[http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

Edit:

Apparently not. The post above mine ^ showed up while I was composing and posting.

---

### Post by philinux on 2010-06-03
It would have caused less suspicion if the OP had posted the contents of the archive i.e. the script instead.

```
#!/bin/bash

function strinput {
 unset refstr
 echo -n "$1"
 read refstr
}

echo " This script is used to setup the Flash 10 Alpha. "
echo " Type y and hit enter to start : "

if [ "$installtype" = "" ]
then
 echo -n "(Enter the lower case y and press enter key)"
 strinput
else
 refstr=$installtype
fi

if [ "$refstr" = "y" ]
then
 echo "Flash installing."

sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so

sudo mkdir /tmp/jphweb/
sudo mkdir /tmp/jphweb/flash
cd /tmp/jphweb/flash/
sudo wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz

sudo tar xvf libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/

elif [ "$refstr" = "n" ]
then
 echo "I am sorry but you have to agree. "

else
 echo  " I am sorry but you have to agree. "
 echo
fi

sudo rm -rfd /tmp/jphweb/
```

---

### Post by tommcd on 2010-06-03
> **philinux said:**
> Thats the 32 bit flash using the wrapper. Full screen button doesn't work with it either.
So why is that?
The 64bit flash has been available for some time from Adobe:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)
Adobe manages to keep 64bit flash for linux well hidden though.
I always just download the Adobe flash installer from Adobe.com and extract it and then copy the liblflashplayer.so to /usr/lib/mozilla/plugins, or for 64 bit: /usr/lib64/mozilla/plugins, and it works ok.
I have read that that the flash for linux 64 bit does not work as well as the 32 bit flash for linux.
This is one of the reasons why I continue to use 32 bit Ubuntu.

---

### Post by howefield on 2010-06-03
> **tommcd said:**
> I have read that that the flash for linux 64 bit does not work as well as the 32 bit flash for linux.

Using 64 bit flash seems to work better than using the wrapper plus 32 bit flash on 64 bit Ubuntu systems.

At least, it does for me, and by what I am reading in these forums, for most others also.

There is always an exception though ;-).

---

### Post by philinux on 2010-06-03
> **tommcd said:**
> So why is that?
The 64bit flash has been available for some time from Adobe:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)
Adobe manages to keep 64bit flash for linux well hidden though.
I always just download the Adobe flash installer from Adobe.com and extract it and then copy the liblflashplayer.so to /usr/lib/mozilla/plugins, or for 64 bit: /usr/lib64/mozilla/plugins, and it works ok.
I have read that that the flash for linux 64 bit does not work as well as the 32 bit flash for linux.
This is one of the reasons why I continue to use 32 bit Ubuntu.

It's still alpha thats why it's not in the ubuntu repo's. Works fine for me.

---

### Post by cascade9 on 2010-06-03
No issues with 64bit flash on any of the distros I've used either.

---

### Post by VastOne on 2010-06-03
> **cascade9 said:**
> No issues with 64bit flash on any of the distros I've used either.

Ditto...

Isn't there a sticky on this and if not, should there be?

---

### Post by oldos2er on 2010-06-03
There are the stickies in the now-defunct x86_64 subforum. They may or may not be updated anymore; I haven't checked. It would be nice if they could be moved to General Help or Multimedia & Video.

---

### Post by cascade9 on 2010-06-03
> **VastOne said:**
> Ditto...

Isn't there a sticky on this and if not, should there be?

oldos2er is right, there was one in th 64bit forum- 

[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

There is a new version of that thread, which the OP even asked to be stickied, but so far its not. Newer thread here- 

[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

I'm caught between amused and annoied at this....after 64bit specific forum get shut (I cant remember the exact wording I saw but it was alongthe lines of 'this forum is uneeded) then canonical puts up the '64bit - Not recommended for daily desktop usage' on the d/l page. Several wires have been crossed I think :S

---

### Post by jamesjph on 2010-06-04
This is to make installing flash easier for beginners.

---

