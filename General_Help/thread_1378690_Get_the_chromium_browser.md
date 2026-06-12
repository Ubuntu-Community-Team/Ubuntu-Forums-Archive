---
title: "Get the chromium browser"
date: 2010-01-11
forum: General Help
---

### Post by ubudog on 2010-01-11
Hello, I want to get the chromium browser (not google chrome).  I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=1213601]("http://ubuntuforums.org/showthread.php?t=1213601") on the second post, I did the apt-update, but at the end it had an error message about "GPG key"  Any help? It worked on the computer I was using then, but now I am using 8.10.

---

### Post by NoaHall on 2010-01-11
Run this command ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5
```

---

### Post by ubudog on 2010-01-11
> **NoaHall said:**
> Run this command ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5
```

Thank you, will try it in a minute and post back.

---

### Post by ubudog on 2010-01-12
OK, I did your previous post and did apt-update, everything worked, no problems.  Then I did sudo apt-get install chromium-browser.  It said "Broken Packages"  Any help?

---

### Post by gradinaruvasile on 2010-01-12
Just use the script i attached. 

It will download or update(if run after the first installation) the latest Chromium dev build in your home directory and make shortcuts in the menu for it. Launch the script from a terminal WITHOUT sudo.

---

### Post by ubudog on 2010-01-12
> **gradinaruvasile said:**
> Just use the script i attached. 

It will download or update(if run after the first installation) the latest Chromium dev build in your home directory and make shortcuts in the menu for it. Launch the script from a terminal WITHOUT sudo.

Ok thanks.  Will try it.

---

### Post by Maheriano on 2010-01-12
Why are you making this so difficult? Go to [www.google.com/chrome](www.google.com/chrome) and download the installer.

---

### Post by Digikid on 2010-01-14
Because he wants [B]Chromium and not Chrome.
[/B]

---

### Post by ubudog on 2010-01-14
> **Digikid said:**
> Because he wants [B]Chromium and not Chrome.
[/B]

Yeah, I want an open source browser besides firefox, even though firefox is pretty awesome.

---

### Post by ubudog on 2010-01-17
Got 9.10 and everything works now.  Thanks for the help!

---

