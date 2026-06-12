---
title: "Problems with Flash Player"
date: 2011-03-23
forum: General Help
---

### Post by joelstitch on 2011-03-23
I am having problems using flash on my computer. Whenever I try to watch a youtube video or use any website that uses flash I get a message saying that I need to install flash (which I have installed). I'm trying to install it again using the directions on this website [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) but I'm having these problems:

I go to the flash website ([http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)) and select **APT for Ubuntu** **9.04+** then I click on Download Now and I get this:

[IMG]http://img864.imageshack.us/img864/9164/47156539.png[/IMG]

I choose **aptget  **and click **OK** and then I get this:

[IMG]http://img69.imageshack.us/img69/4840/18859704.png[/IMG]
I click **Yes** and then it starts installing stuff but I get this error afterwards:

[IMG]http://img690.imageshack.us/img690/9531/32605983.png[/IMG]
> Could not download all repository indexes

The repository may no longer be available or could not be contacted  because of network problems. If available an older version of the failed  index will be used. Otherwise the repository will be ignored. Check  your network connection and ensure the repository address in the  preferences is correct.

[QUOTE]Failed to fetch  [http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something  wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address  associated with hostname)
Failed to fetch [http://wicd.longren.org/dists/feisty/Release.gpg](http://wicd.longren.org/dists/feisty/Release.gpg)   Something wicked happened resolving 'wicd.longren.org:http' (-5 - No  address associated with hostname)
Failed to fetch  [http://wicd.longren.org/dists/feisty/all/i18n/Translation-en_CA.bz2](http://wicd.longren.org/dists/feisty/all/i18n/Translation-en_CA.bz2)   Something wicked happened resolving 'wicd.longren.org:http' (-5 - No  address associated with hostname)
Failed to fetch  [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Something  wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address  associated with hostname)
Failed to fetch  [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something  wicked happened resolving 'archive.canonical.com:http' (-5 - No address  associated with hostname)
Failed to fetch [http://wicd.longren.org/dists/feisty/all/binary-amd64/Packages.gz](http://wicd.longren.org/dists/feisty/all/binary-amd64/Packages.gz)  Something wicked happened resolving 'wicd.longren.org:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.[/QUOTE]So I click **Close** and then get this:

[IMG]http://img6.imageshack.us/img6/6948/44042795.png[/IMG]

> Package 'adobe-flashplugin' is virtual.So now I have no idea what to do...

---

### Post by gandaran on 2011-03-23
download the .deb package, click to install but remove the old flash plugin installed first

---

### Post by pqwoerituytrueiwoq on 2011-03-23
the deb file will work
edit was looking over the urls it used one is 64 bit
if you are using a 64bit system use the 64bit flash
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

---

### Post by joelstitch on 2011-03-23
I tried the deb file but I get this error:

> Error: Wrong architecture 'i386

[IMG]http://img52.imageshack.us/img52/702/87915135.png[/IMG]

---

### Post by gandaran on 2011-03-23
you have ubuntu 64-bits so it's better to install 64-bits flash.
use this [firefox addon flash-aid]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/") to remove the flash already installed and install the correct flash for ubuntu 64-bits.

---

### Post by joelstitch on 2011-03-23
> **gandaran said:**
> you have ubuntu 64-bits so it's better to install 64-bits flash.
use this [firefox addon flash-aid]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/") to remove the flash already installed and install the correct flash for ubuntu 64-bits.

That worked! thanks a million!

---

### Post by thokchom on 2011-04-09
Hi, i hav successfully installed adobe flashplayer (v 10,2,153,1) and everything is working fine. But, problem is - while playing songs on some streaming jukebox service player, the songlists/playlists are NOT listed (only the current playlist is showing and others are not shown). My system is a dual boot ( ubuntu 10.10 (2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux) with window XP.** On both Os I can play the songs on streaming jukebox service player supported by adobe flashplayer. While using window XP, I can see all the playlist but on ubuntu, I can see only the current playlist not all the playlists.** I tried to reinstall the flashplayer/plugins for mozila but still the problem is there for ubuntu. Plz someone help me how to rectify this problem.:KS

---

