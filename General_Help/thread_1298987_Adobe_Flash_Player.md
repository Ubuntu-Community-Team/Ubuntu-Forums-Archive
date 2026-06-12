---
title: "Adobe Flash Player"
date: 2009-10-23
forum: General Help
---

### Post by Hosmion on 2009-10-23
Is there a Terminal command that allows me to download the latest version of Adobe Flash Player (I have trouble with downloading it from the website.)

---

### Post by Giblet5 on 2009-10-23
Adobe made it easy for you.

Aren't you glad?

They took the second-most-easy thing to do with a web browser and they broke it. That's hard to do. And where's the thanks?

OK, sarcasm over...

If you have plenty of disk space (not a micro-mini netbook), you'll probably want to have the usual stuff that PC owners need to function.

Open a terminal window and type ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras
```

If you don't get any errors, mark the thread SOLVED, please.

---

### Post by martrn on 2009-10-23
```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb
```
The first command fetches the latest version of flashplayer directly from an adobe site.

```
sudo dpkg --install install_flash_player_10_linux.deb
```

The second command installs your freshly downloaded flash player and gives you an error message if you have already used the previous message shown above or else installs the package. 

Check the man page yourself for dpkg :
```
man dpkg
```

Sorry missed out the sudo.

---

### Post by Hosmion on 2009-10-23
Can someone please verify those "trusted" commands?

---

### Post by Giblet5 on 2009-10-23
> **Hosmion said:**
> Can someone please verify those "trusted" commands?

Mine?

The first command updates your list of available Ubuntu software and patches.

The second installs any needed patches.

The last command will install support for flash, quicktime, and divx within Firefox, plus it will add MP3 (and others) music support, plus the ability to watch DVD movies.

Check the man page yourself: ```
man apt-get
```

---

### Post by Hosmion on 2009-10-23
I need to get adobe flash player, not update it..

---

### Post by fluffman86 on 2009-10-23
Actually, to get support for mp3, quicktime, java, and flash all in one swoop, the command is:

sudo apt-get install ubuntu-restricted-extras

Giblet5 left out the ubuntu- at the beginning. :\

You can also install *JUST* flash (no mp3, java, etc) with 

sudo apt-get install flashplugin-nonfree

Martrn's command will also work.  Basically, the two apt-get commands will download flash from Ubuntu's software repository, while Martrn's wget command will GET the package from the website listed (adobe), and then dpkg will DePacKaGe and install the file that's listed (install_flash_player_10_linux.deb)

Or, if the command line isn't really your thing, you can use Applications > Add/Remove... to search for "flash" and install it there.

---

### Post by Giblet5 on 2009-10-23
> **Hosmion said:**
> I need to get adobe flash player, not update it..

Before you install anything, it's a good idea to update what you have. That is up to you. You can certainly take whatever risks you wish with your own system.

The third command will install Adobe Flash and a lot of other things that I already wasted time describing.

Search in synaptic for that package and read the description. It basically turns a server-class workstation into a multi-purpose workstation with rich media support.

The term "restricted" is applied to any "vendor strings attached" packages (nvidia display drivers, adobe anything, etc).

---

### Post by Giblet5 on 2009-10-23
> **fluffman86 said:**
> Giblet5 left out the ubuntu- at the beginning. :\

Fixed. Now... Thanks.

---

### Post by m4tic on 2009-10-23
there's also an offline ubuntu-restricted-extras from hacktolive, google "ubuntu extras hacktolive" and the first wiki result click on it, alternatively if you wnt to download from your computer, open Add/Remove programs, on the "show" button, select all available software. then search for "flash". They all worked for me after a clean install.
You don't have to be locked inside Adobe's software.

---

### Post by Hosmion on 2009-10-23
> **fluffman86 said:**
> Actually, to get support for mp3, quicktime, java, and flash all in one swoop, the command is:

sudo apt-get install ubuntu-restricted-extras

Giblet5 left out the ubuntu- at the beginning. :\

You can also install *JUST* flash (no mp3, java, etc) with 

sudo apt-get install flashplugin-nonfree

Martrn's command will also work.  Basically, the two apt-get commands will download flash from Ubuntu's software repository, while Martrn's wget command will GET the package from the website listed (adobe), and then dpkg will DePacKaGe and install the file that's listed (install_flash_player_10_linux.deb)

Or, if the command line isn't really your thing, you can use Applications > Add/Remove... to search for "flash" and install it there.

What does the nonfree part mean?  Does it cost to install it?

---

### Post by oldos2er on 2009-10-23
No cost, it just means flash is not open source software.

 Btw if you're using 64-bit Ubuntu, you should (in my opinion) install 640bit flash with this script: [http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938](http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938)

---

### Post by emigrant on 2009-10-23
> **Giblet5 said:**
> Mine?



The last command will install support for flash, quicktime, and divx [COLOR="DarkRed"]within Firefox[/COLOR], plus it will add MP3 (and others) music support, plus the ability to watch DVD movies.


is it only within firefox or in chrome also?

---

### Post by Hosmion on 2009-10-23
> **fluffman86 said:**
> 

sudo apt-get install flashplugin-nonfree

Or, if the command line isn't really your thing, you can use Applications > Add/Remove... to search for "flash" and install it there.

I tried them both, and when I tried it in Add/Remove Programs, this is what it says :

Adobe Flash Plugin 10 cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.
Adobe Flash Plugin 10 is available in the third party software channel 'jaunty-partner'. To install it, please click on the checkbox to activate the software channel.
Canonical does not provide updates for Adobe Flash Plugin 10. Some updates may be provided by the third party vendor.

---

### Post by Hosmion on 2009-10-23
Bump

---

### Post by oldos2er on 2009-10-25
To enable the partner repository, go to System, Administration, Software Sources, Third-Party Software, and tick the boxes next to [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner and [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner (Source Code). Close, and once the sources have reloaded, retry **sudo apt-get install flashplugin-nonfree**

---

