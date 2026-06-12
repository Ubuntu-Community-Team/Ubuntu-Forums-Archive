---
title: "Install Older Version Of Flash?"
date: 2012-04-02
forum: General Help
---

### Post by atticadayz on 2012-04-02
This version seems to hate my guts, and I feel the same about it. The only way I can think of to keep flash from crashing every which way is to revert to an older version, the one previous to this one. I've downloaded the file from adobe site, but I have no idea how to install and run it on my computer. I'm very noob, but I really would love it if this problem could be solved.

---

### Post by PhantomTurtle on 2012-04-02
What type of file did you get? You should have gotten a .deb file, which can be installed through the Ubuntu Software Center or using the terminal. Terminal command(as long as you got a deb file) is,
```
sudo dpkg -i packagenamehere.deb
```

---

### Post by winh8r on 2012-04-02
For anyone experiencing the latest problems with Flash player and needing to install an older version like the OP

The Canonical archive is here:

[http://archive.canonical.com/pool/partner/a/adobe-flashplugin/]("http://archive.canonical.com/pool/partner/a/adobe-flashplugin/")

The 11.1.102.62 versions seem to working OK

Just ensure that you download the correct one for your release of Ubuntu.

Double click on the .deb archive and it will install.

Hope this helps.

---

### Post by atticadayz on 2012-04-02
winh8r, there doesn't seem to be a 11.1.102.62 version in that list.
Edit: I'm running oneiric, the list also only has the newest version :/

---

### Post by winh8r on 2012-04-02
scroll down a bit and you will see them.

---

### Post by atticadayz on 2012-04-02
Thanks, I don't quite know how I missed those :3

---

### Post by atticadayz on 2012-04-03
I've installed 11.1 version but chrome is still using 11.2, what can I do about that?

---

### Post by PhantomTurtle on 2012-04-03
> **atticadayz said:**
> I've installed 11.1 version but chrome is still using 11.2, what can I do about that?

Google Chrome comes it's own flash player bundled. You can use Chromium or disable the one that is bundled with chrome and use the one on your system. Type in "chrome://plugins/"(without quotes) into the address bar in Google Chrome. On the right side there should be a plus and details. Click that. Next scroll down, and you should see two Shockwave Flash (or maybe more). Disable the one for chrome. This will disable the flash player plugin that comes bundled with chrome.

---

### Post by atticadayz on 2012-04-11
Is there a way to get chrome to use an older flash version?

---

### Post by lovinglinux on 2012-04-11
See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by PhantomTurtle on 2012-04-11
> **atticadayz said:**
> Is there a way to get chrome to use an older flash version?

The only way to do that is to disable the internal flash plugin and use an older one that is already installed on your system. Instructions on how to do this is posted in one of my posts above this one.

---

