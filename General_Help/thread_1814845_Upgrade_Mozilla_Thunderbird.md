---
title: "Upgrade Mozilla Thunderbird"
date: 2011-07-30
forum: General Help
---

### Post by Gordonisnz on 2011-07-30
You are using Ubuntu 10.04 LTS
                - the Lucid Lynx - released in April 2010 and supported until April 2013.
    

Hello. I'm running Mozilla Firefox 3.6.17 

Can someone tell me the easiest way to upgrade to a newer version ?

When I search on Google, I get ;lots & lots of pages & they give me 20-different instructions on how to do it & i'm confused. Not sure which command to use 

(There is no "upgrade" option in the "tools" area of Firefox.)

Do we upgrade in the command-line ?

---

### Post by howefield on 2011-07-30
You could add the PPAs for Thunderbird and Firefox. (Your thread title mentions Thunderbird but the post content mentions Firefox).

Easiest way would be to add the relevant PPAs via the command line.

Open a terminal and type (copy/paste) the following commands to upgrade Thunderbird.

```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

And then to get the latest Firefox.

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by Gordonisnz on 2011-07-30
Thanks - looks complex.

(i want to upgrade the browser.. - Firefox) - Sorry...

---

### Post by pqwoerituytrueiwoq on 2011-07-30
or just do all at once
```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable;sudo add-apt-repository ppa:mozillateam/firefox-stable;sudo apt-get update;sudo apt-get upgrade
```that is quicker to copy/paste and you only [FONT=Courier New]sudo apt-get update[/FONT] once saving bandwidth and a couple seconds
one line firefox
```
sudo  add-apt-repository ppa:mozillateam/firefox-stable;sudo apt-get update;sudo apt-get upgrade
```one line thunderbird
```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable;sudo apt-get update;sudo apt-get upgrade
```

using the GUI
system->administration->software sources
other sources tab
click add
paste this  *ppa:mozillateam/firefox-stable*
click add source
close
wait for the update manager to come up

---

### Post by howefield on 2011-07-30
If I recall you might get an error with xul-ext-ubufox, I uninstalled the old Firefox (and  xul-ext-ubufox) before upgrading.

It's really easier than it might look ;-)

---

### Post by Gordonisnz on 2011-07-30
I'm now on firefox 5.0 (browser)

---

### Post by lovinglinux on 2011-07-30
For future reference see [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

