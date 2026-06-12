---
title: "Firefox does not play youtube videos"
date: 2010-02-08
forum: General Help
---

### Post by sarin_cv on 2010-02-08
I have firefox 3.6 installed and it does not play videos from youtube...it plays other flash contents... I have tried installing adobe flash plugin, flash plugin nonfree and mozilla flash player...none of them are working... google chome does not have any issue in playing youtube videos...but I don't want to switch just for playing videos...plz help

---

### Post by lovinglinux on 2010-02-08
For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by sarin_cv on 2010-02-08
still not working....

---

### Post by tamccullough on 2010-02-08
I just updated this morning and now flash no longer works for me either.
The plugins are installed, but when I visit pages that use flash, it prompts to install missing plugins.
When I chose to install it, I'm told that it is already installed.

---

### Post by tamccullough on 2010-02-08
> **lovinglinux said:**
> For 32bit see [this]("http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2").

For 64bit see [this]("http://ubuntuforums.org/showthread.php?t=1358591").

This worked. Thanks.

But I think that maybe something needs to be looked into when the updates cause problems in this manner.

---

### Post by lovinglinux on 2010-02-08
> **tamccullough said:**
> This worked. Thanks.

But I think that maybe something needs to be looked into when the updates cause problems in this manner.

You can report a bug at [launchpad.net](https://bugs.launchpad.net/).

---

### Post by lovinglinux on 2010-02-08
> **sarin_cv said:**
> still not working....

How did you install Firefox 3.6? Is it 32bit or 64bit?

---

### Post by dullard on 2010-02-08
> **sarin_cv said:**
> still not working....

Did you accidentally sign up for the HTML5 Beta experiment?

Opt in/out page here:
[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by CronoDekar on 2010-02-08
I'm glad I'm not the only one haven't recent problems.  I'm on Hardy Heron, and every site with flv I've been on hasn't been working.  It'll load and play for a certain number of seconds (no more than 20), and then stop.  So far, I've tried Youtube, Vimeo, and Collegehumor to no success.  The exact same situations happens in all browsers I've tried (Firefox, Epiphany, and Opera).  Doing the optimizations previously discussed actually makes it so less video loads.

I've had this problem for the past couple days, and the only change I can think of that it might be related to is linux modules et al recently installed.  It's rather frustrating, especially since at about the same time my printer driver had spontaneously stopped working.  I was able to work around that by selecting a different driver, but it's rather annoying that setups that have served me well for the past two years have been failing on me.

---

### Post by sarin_cv on 2010-02-09
> **lovinglinux said:**
> How did you install Firefox 3.6? Is it 32bit or 64bit?
32 bit... I downloaded the tar file rom mozilla home page and extracted the contents to .mozilla/firefox directory after removing my old .mozilla/firefox directory.. I copied the profile and plugins from my old firefox directory to the new one..

I have tried almost all the different possible ways such as..

1. adobe flash plugin from synaptic
2. flash plugin nonfree from synaptic
3. mozilla flash player from synaptic
4. mozilla mplayer from synaptic
5. flash plugin from adobe website
6. copied libflashplugin.so to all mozilla plugins folders I have seen

---

### Post by kregg on 2010-02-09
> **sarin_cv said:**
> 32 bit... I downloaded the tar file rom mozilla home page and extracted the contents to .mozilla/firefox directory after removing my old .mozilla/firefox directory.. I copied the profile and plugins from my old firefox directory to the new one..

I have tried almost all the different possible ways such as..

1. adobe flash plugin from synaptic
2. flash plugin nonfree from synaptic
3. mozilla flash player from synaptic
4. mozilla mplayer from synaptic
5. flash plugin from adobe website
6. copied libflashplugin.so to all mozilla plugins folders I have seen
Have you tried using [Ubuntuzilla]("http://techdrivein.blogspot.com/2010/02/ubuntuzilla-repository-makes-firefox-36.html")? It was initially a script, but now it is a repo of the latest Mozilla Firefox build.

I would at least try to uninstall the old Firefox first by running ```
sudo apt-get remove firefox
```

---

### Post by frodriguez96 on 2010-02-09
[B][COLOR="Navy"]Type the following command to re-install flash player:

  **[COLOR="DarkOrange"]sudo apt-get install flashplugin-nonfree[/COLOR]**

Now flash player should be working. Visit youtube or any other site to view flash content.[/COLOR][/B]

[B][COLOR="Red"]Troubleshooting tip* 

Update: This issue only relevant to older Ubuntu Linux version such as 6.04.

Some people may find voice is not working with newly installed flash player. Type following commands to solve this problem (thanks to macewan.org):
  
  [B][COLOR="SeaGreen"]sudo apt-get install alsa-oss
  gksudo gedit /etc/firefox/firefoxrc[/COLOR][/B]

Find line that read as FIREFOX_DSP and set to:
**[COLOR="Magenta"]FIREFOX_DSP="aoss"[/COLOR]**

Save and close the file.

Close Firefox and restart it again.[/COLOR][/B];)

---

### Post by CronoDekar on 2010-02-10
Well I feel like I have my foot in my mouth -- my problem appears to have been because I was running out of room on my / partition and flash videos were trying to save files in /tmp.  I didn't notice it until I had tried to download Google Chrome (since op mentions that it works for him), and I got an error saying I didn't have enough room in /tmp.   Which is probably why I started getting problems after the recent kernel update.  After removing some old kernel images, Flash works fine (and while I haven't tried testing it yet, it probably had to do with my printer problems also).

Unfortunately, I don't think my problem is the same as op, because I had the problem regardless of the browser I opened.  That said, I'm posting this in case somehow it helps someone who goes troubleshooting.

---

