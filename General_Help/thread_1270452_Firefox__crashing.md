---
title: "Firefox  crashing"
date: 2009-09-19
forum: General Help
---

### Post by arnab_das on 2009-09-19
Firefox is crashing constantly on Ubuntu 9.04 since the past few days for some unknown reason. I've to admit this is Swiftfox which is crashing but since they're basically the same thing, i presume the problem would be the same with Firefox as well.

I cant find a solution, only thing is firefox crashes mostly while watching flash videos, say youtube ones, etc.

Help would be appreciated.

---

### Post by Vaphell on 2009-09-19
about: plugins
version of flash?

---

### Post by arnab_das on 2009-09-19
> **Vaphell said:**
> about: plugins
version of flash?


i'm using the latest version of adobe flash, 10. something

addons i have flashblock enabled, which obviously helps me to stay away from annoying ads.

---

### Post by Wobblybob on 2009-09-19
My Firefox constantly crashes when viewing flash based site such as BBC iplayer & Flickr. It was fine using Intrepid but the upgrade to Jaunty has done something and as it’s doing it on both my laptop and desktop both recently upgraded to Jaunty. First I closed Firefox then removed the installed plugins typing the following into a Terminal;

sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree


Then I downloaded Flash Player 10 .deb file for Ubuntu v8.04 from the adobe Web Site found [here]("http://get.adobe.com/flashplayer/"), then I closed Firefox and removed the adobe-flashplugin in a Terminal type;

sudo apt-get remove --purge adobe-flashplugin

now I navigated to my download and double clicked on the install_flash_player_10_linux.deb file which opens the [Package installer] and complained there was a newer version in the repositories. I [ok]‘d the install and retested Firefox, so far all is well even after upgrading to Firefox-3.5

---

### Post by jamillikan on 2009-09-19
Installing Firefox 3.5 resolved the crashing issue for me.  I'd suggest that as a solution.  I haven't had a crash since, FWIW.

---

### Post by arnab_das on 2009-09-19
thanks mate. but i'm already using 3.5.1!

the firefox version's something different though. its swiftfox whose version is 3.5.1

---

### Post by lovinglinux on 2009-09-19
See **Solution** [*[COLOR="Red"]**FOT008**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT008).

This problem has been fixed on Firefox 3.5.3, but unfortunately Swiftfox and Swiftweasel are still 3.5.2

---

### Post by arnab_das on 2009-09-19
> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT008**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT008").

This problem has been fixed on Firefox 3.5.3, but unfortunately Swiftfox and Swiftweasel are still 3.5.2

thanks. i uninstalled and reinstalled adobe flash. working fine as of now.
why is it that youtube videos get "stuck" in ubuntu irrespective of what browser i'm using?

---

### Post by lovinglinux on 2009-09-19
> **arnab_das said:**
> thanks. i uninstalled and reinstalled adobe flash. working fine as of now.
why is it that youtube videos get "stuck" in ubuntu irrespective of what browser i'm using?

Because Adobe doesn't really care about making a decent version for Linux :)

Now seriously, it seems that there is some bug that prevent flash from being rendered by the graphics card, thus putting an extra load on the CPU.

Nevertheless, Firefox 3.6.1 alpha and Chromium alpha plays flash much better than any other browser. If you cannot wait, you could use one of those versions, but keep in mind there are security concerns, since they are in alpha stage.

---

### Post by arnab_das on 2009-09-19
> **lovinglinux said:**
> Because Adobe doesn't really care about making a decent version for Linux :)

Now seriously, it seems that there is some bug that prevent flash from being rendered by the graphics card, thus putting an extra load on the CPU.

Nevertheless, Firefox 3.6.1 alpha and Chromium alpha plays flash much better than any other browser. If you cannot wait, you could use one of those versions, but keep in mind there are security concerns, since they are in alpha stage.


thank u again. but how can i install a new version of firefox? i guess ubuntu doesnt allow it, apart from official releases that come with ubuntu, right?

---

### Post by lovinglinux on 2009-09-19
> **arnab_das said:**
> thank u again. but how can i install a new version of firefox? i guess ubuntu doesnt allow it, apart from official releases that come with ubuntu, right?

It does allow to install side-by-side.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm.

---

### Post by arnab_das on 2009-09-20
> **lovinglinux said:**
> It does allow to install side-by-side.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567"). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm.

thank u very much, very informative post that one.

---

