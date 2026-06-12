---
title: "installing firefox on ubuntu 9.10"
date: 2009-11-07
forum: General Help
---

### Post by dyyyy on 2009-11-07
hi i removed firefox from my ubuntu machine, and now i can't get it back, my software centre doens' work
and when downloading it from the synaptic package manager, iget it in the menu but when i launch it i get 
Could not launch 'Firefox Web Browser'
Failed to execute child process "firefox" (No such file or directory)

i noticed also that the folder doesn't exist in my /opt folder

---

### Post by wilee-nilee on 2009-11-07
Do you have all the partners enabled in software sources, and then run a refresh in synaptic. For the time being if this doesn't work you can just down load the Linux version from Mozilla. I wonder if your marking the correct file in synaptic to install. You can also try sudo apt-get install firefox 3.5 in a terminal.

---

### Post by ricardo.gloe on 2009-11-07
Uninstall and reinstall Firefox through the Synaptic Package Manager. 

If that doesn't work, check the launcher command, it should read "firefox %u". 

If it still doesn't work, might be a corrupt profile. Uninstall Firefox again. Then, open your home folder and View - show hidden files, find the .mozilla folder. Delete it. Then reinstall Firefox.

Note: Deleting this folder will eliminate any bookmarks and other configurations you have/had on Firefox, so backup the content of the folder somewhere else before deleting.

---

### Post by pastalavista on 2009-11-07
Make sure you download Firefox-3.5 because that's what comes with Karmic now. Check /etc/apt/sources.list to see if you have Karmic repositories or still have Jaunty ones because it uses Firefox 3.

---

### Post by dyyyy on 2009-11-07
hi thank you for ur responses
i downloaded it from mozilla and it worked

just for info
i tried sudo apt-get install firefox 3.5
i got this,
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 3.5

i uninstalled it, removed .mozilla from home and tried again, again nothing.
the launcher command was actually "firefox %u".
the main probelm was i guess that i removed firefox directly by deleting it from /opt

---

### Post by pastalavista on 2009-11-07
If you installed it from Mozilla with a .deb file ok. The actual name in the repo's is firefox-3.5 (with a dash)

---

### Post by wilee-nilee on 2009-11-07
You are right about the dash, my bad, ;)

---

### Post by ratcheer on 2009-11-07
I have always just downloaded Firefox directly from Mozilla and installed it, myself. It works perfectly.

Last night, I checked for updates in the Firefox Help menu, did one click, and upgraded from 3.5.4 to 3.5.5. Then, I restarted FF and the new version came up and left me on the same web page as when I started. Smooth!

[http://www.mozilla.com/en-US/products/download.html?product=firefox-3.5.5&os=linux&lang=en-US](http://www.mozilla.com/en-US/products/download.html?product=firefox-3.5.5&os=linux&lang=en-US)

Tim

---

### Post by scouser73 on 2009-11-07
> **dyyyy said:**
> hi i removed firefox from my ubuntu machine, and now i can't get it back, my software centre doens' work
and when downloading it from the synaptic package manager, iget it in the menu but when i launch it i get 
Could not launch 'Firefox Web Browser'
Failed to execute child process "firefox" (No such file or directory)

i noticed also that the folder doesn't exist in my /opt folder

[[COLOR="Red"]**Downlowd Firefox**[/COLOR]]("http://www.mozilla-europe.org/en/firefox/")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

---

