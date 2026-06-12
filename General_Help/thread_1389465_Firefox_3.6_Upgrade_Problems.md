---
title: "Firefox 3.6 Upgrade Problems"
date: 2010-01-24
forum: General Help
---

### Post by Bugs318 on 2010-01-24
I generally use Epiphany because it is faster than Firefox, though the reviews saying 3.6 is much faster inspired me to give it a shot (as I do appreciate Firefox).

I followed [these instructions]("http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html/comment-page-1#comment-21268") and upgraded my rarely used Firefox to 3.6, but following the upgrade:

1) there was no longer a quick-launch link to start firefox and the firefox link in the applications/internet tab on gnome had also disappeared. It seems I now have to use search to find the application and start it from there and if I drag it to make a panel-launch button, it fails.

2) Firefox will not close or minimize via the buttons in the top-right corner, only via the file menu.

3) My Liferea feed reader no longer works and sends me a message upon boot reading &#8220;The application has been updated, but your version of SQLite is too old and the application cannot run.&#8221; before it closes.  I know this program relies on firefox, so how can a new version be too old?

and 4) Epiphany will no longer load any page from bookmarks or that has the address typed in manually, I can only follow links. 
I have no idea why upgrading Firefox would damage Epiphany but it seems to have since the problem started immediately following this upgrade! As soon as the upgrade finished I got frustrated with Firefox's new failings (see above) and started up my tried, tested, and true Epiphany only to discover this problem - which has never occured before and now always does - had kicked in at that very moment.

Can anyone help with any of these problems?  Thanks in advance for any helpful advice!

BTW: This problem is on my laptop which runs Hardy Heron (8.04 LTS)

---

### Post by nanotube on 2010-01-24
uninstall the stuff you installed from the daily ppa, which installs nightly builds, and instead use the ubuntuzilla repository to install the official mozilla release of 3.6. 

full instructions at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by Uncle Spellbinder on 2010-01-24
I added the [Firefox Stable Channel Packages](https://launchpad.net/~mozillateam/+archive/firefox-stable/) PPA repo to my sources.list.

```
#### Firefox - Stable Channel Packages
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu karmic main
```
 
Firefox was then upgradable to 3.6. No issues whatsoever.

[IMG]http://i46.tinypic.com/xmtks3.jpg[/IMG]

---

### Post by Bugs318 on 2010-01-24
Thanks!  Nanotube, your suggestion worked to fix the problems with Firefox itself, though liferea and Epiphany are still acting up.

I may not keep using Epiphany, but I may from time-to-time and would like it to work better.

To clarify: I uninstalled liferea, epiphany, and firefox.  Then I installed the ubuntuzilla firefox as suggested.  The I reinstalled both Epiphany and liferea.

Liferea still sends me the same error message regarding outdated SQLite and then forcibly closes.  This is a crucial piece of software for me and help on this would be greatly appreciated!

Epiphany is partially fixed in that bookmarks will load, but any manually entered url fails.  If I hit 'Enter' to attempt the page load it functions like 'tab' and switches onto the loaded page like the tab button would, yet if I click 'go' instead it simply does nothing - net even attempting to load the page.  This isn't as necessary but remains a pain.

---

### Post by Haber_Nir on 2010-01-24
ubuntuzilla is for 32 bit and what about 64bit??

---

### Post by nanotube on 2010-01-24
> **Haber_Nir said:**
> ubuntuzilla is for 32 bit and what about 64bit??

well, lucky for you, it seems that they just created a firefox-stable ppa. maybe that has 64bit packages?
[https://launchpad.net/~mozillateam/+archive/firefox-stable/](https://launchpad.net/~mozillateam/+archive/firefox-stable/)

---

### Post by FrancoNero on 2010-01-24
one other thing, why are you using Hardy Heron? is there  a reason for that?

---

### Post by nanotube on 2010-01-24
> **FrancoNero said:**
> one other thing, why are you using Hardy Heron? is there  a reason for that?

it's an lts release - nothing wrong with that...

---

### Post by FrancoNero on 2010-01-24
> **Uncle Spellbinder said:**
> I added the [Firefox Stable Channel Packages](https://launchpad.net/~mozillateam/+archive/firefox-stable/) PPA repo to my sources.list.

```
#### Firefox - Stable Channel Packages
## sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu karmic main
```
 

best trick ever! thank you! been googling for hours. mozilla could just have the decency to provide proper .deb downloads but noooooo as a linux user you have to go the whole ten miles

---

