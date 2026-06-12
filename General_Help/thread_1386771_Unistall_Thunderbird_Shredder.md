---
title: "Unistall Thunderbird Shredder"
date: 2010-01-21
forum: General Help
---

### Post by jimmyUT on 2010-01-21
I tried installing TB 3 but it looks like I got the beta 3.02.. How can I get rid of that so I can install 3.01

I used:[I]
sudo [/I][I]add-apt-repository ppa:ubuntu-mozilla-daily/ppa
[/I]
then
*sudo aptitude update && sudo aptitude install *[I]thunderbird-3.0 thunderbird-3.0-gnome-support
[/I]
How do I get the stable version?

---

### Post by scouser73 on 2010-01-21
Go into **Synaptic Package Manager** & search for either Thunderbird or Shredder and delete it.

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

You will now have Mozilla Thunderbird 3.01 installed and you can find it under the **Internet** sub-menu

---

### Post by jamesisin on 2010-01-21
scouser73 offers one method.  It's not my preferred method.

This is:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

You will want to remove the repository (you can do that through Synaptic) which you added and you will be able to remove the version of Thunderbird as per scouser73.  I just offer a (what I consider) better method for getting the latest stable Thunderbird and keeping it up to date.  (This is also the Mozilla recommended method, I believe.)

---

### Post by nanotube on 2010-01-21
> **jamesisin said:**
> scouser73 offers one method.  It's not my preferred method.

This is:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

You will want to remove the repository (you can do that through Synaptic) which you added and you will be able to remove the version of Thunderbird as per scouser73.  I just offer a (what I consider) better method for getting the latest stable Thunderbird and keeping it up to date.  (This is also the Mozilla recommended method, I believe.)

jamesisin: i haven't seen anything where mozilla has officially recommended ubuntuzilla - though if you have, i'd like to see it :) that said, the repository is a lot simpler and more 'standardized' way to install, than doing it all manually.

scouser73: any particular reason you prefer to set it all up manually, rather than using the ubuntuzilla repository?

---

### Post by jimmyUT on 2010-01-21
The Second method posted here worked for me, thanks... I do notice that it only worked for TB, and my firefox still says Shiretoko... should it have reverted both programs or just TB?

Jim

---

### Post by nanotube on 2010-01-21
> **jimmyUT said:**
> The Second method posted here worked for me, thanks... I do notice that it only worked for TB, and my firefox still says Shiretoko... should it have reverted both programs or just TB?

Jim

Hi

ubuntuzilla repository contains three packages, firefox-mozilla-build, thunderbird-mozilla-build, and seamonkey-mozilla-build.

if you install package 'thunderbird-mozilla-build', it will to thunderbird, if you install 'firefox-mozilla-build' it will do firefox. basically, whatever you install, will be installed. ;)

you may still have shortcuts pointing directly to shiretoko, even after you install firefox-mozilla-build. you can just delete the shortcut - or uninstall the shiretoko package.

---

### Post by scouser73 on 2010-01-21
> scouser73: any particular reason you prefer to set it all up manually, rather than using the ubuntuzilla repository?

I just prefer to set it up that way to be honest, I've never looked at installing Ubuntuzilla, perhaps when Lucid comes out I'll install it when I do a clean install.

---

### Post by nanotube on 2010-01-21
> **scouser73 said:**
> I just prefer to set it up that way to be honest, I've never looked at installing Ubuntuzilla, perhaps when Lucid comes out I'll install it when I do a clean install.

well just to clarify - ubuntuzilla /used/ to be a script that automatically installs the mozilla build, but now it is a repository hosting actual mozilla packages. so there's no longer a need to 'install ubuntuzilla'. just add the repository and install your mozilla packages in the usual manner.

but anyway, when/if you do get around to it, let me know if you run into any problems. :)

---

