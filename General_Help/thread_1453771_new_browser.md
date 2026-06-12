---
title: "new browser"
date: 2010-04-13
forum: General Help
---

### Post by cowboy7305 on 2010-04-13
Iam using Fire fox and have done for a few years but just recently i find its running slow and this morning it crashed had to restart system FF is 3.5.9
what i want is what is a good un bloated browser Easy to use and Download helper can run on 
any ideas

---

### Post by entikryst on 2010-04-13
Try Chrome [http://www.google.com/chrome](http://www.google.com/chrome)

---

### Post by lovinglinux on 2010-04-13
Video Download Helper won't run on Chrome. See [this discussion](http://www.chromeplugins.org/google/chrome-plugins/downloadhelper-plugin-chrome-135.html) about video downloader extensions in Chrome.

In my personal opinion, Chrome is extremely fast and definitely not bloated, but it is so "unbloated" that lacks simple features that you will miss a lot, like choosing the folder where to save your downloads or exporting your passwords.

I can't do what I do in Firefox with Chrome. So, what I recommend is optimizing your Firefox. For that I wrote a tutorial [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). 

Firefox works like a charm here and I have 51 extensions installed.

---

### Post by The Thunder Chimp on 2010-04-13
Propositions:

1) Try updating your Firefox to v3.6
2) Try Google Chrome
3) Try speed add-ons as proposed previously.

---

### Post by lyall on 2010-04-13
try Opera

---

### Post by ssulaco on 2010-04-13
I'm running the native Firefox  3.0.19
I did 2 things,and its pretty fast,actually think its faster than Chromium
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

quote from lovinglinux Firefox optimization thread:
> 32bit

Ubuntu comes with swfdec plug-in, but it doesn’t work on several sites. Installing the version from Adobe might solve this problem and improve performance.

First you need to enable the muliverse repository. Go to “System >> Administration >> Software Sources”, then tick the option “Software restricted by copyright or legal issues (multiverse)”, then click “Close” and then “Reload”.

To remove other flash plug-ins and install only the one from Adobe open “Applications >> Accessories >> Terminal”, then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree

---

