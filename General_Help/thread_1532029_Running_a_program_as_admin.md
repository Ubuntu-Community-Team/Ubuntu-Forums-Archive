---
title: "Running a program as admin"
date: 2010-07-15
forum: General Help
---

### Post by thabstract on 2010-07-15
I downloaded The Witcher for windows from Wine and I'm trying to run it but it says I have to run it as the admin the first time the game is ran. I don't know how to run it as admin lol. I've only been using ubuntu for about a week now. If you can let me know how to do it from the terminal AND from shortcuts, that would be great because I'm trying to know what all I can do with ubuntu. Thanks.

---

### Post by emoguitarist06 on 2010-07-15
You have a .exe file? and when you double click or right click open with wine it tells you that you must be admin is that correct?

---

### Post by prodigy_ on 2010-07-15
> **thabstract said:**
> it but it says I have to run it as the admin
Copy protection systems (Tages in this case) often don't work in Wine. That's why you see this message. Use a NoCD. Or, even better, update the game to v1.5. The last patch is supposed to remove CD checks.

---

### Post by thabstract on 2010-07-15
It's the enhanced edition and the regular start screen comes on to launch game, but when i launch it, it says "Insufficient Privileges: you must be administrator when you run this application for the first time" if i have to install v1.5 could you help me with that lol..

---

### Post by prodigy_ on 2010-07-15
I don't have the game at the moment, but there's [some info in Wine AppDB](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17527&iTestingId=51933&bShowAll=true):

[i]How to install the 1.5 patch

I suspect the installer has some trouble extracting the files inside it. Following a bid on the witcher site to use something called Universal Extractor, I extracted the installer and ran it's bundled setup manually. Patching finished without a hitch.
Note: the bundled setup is ${EXTRACT_PATH}/Disk1/setup.exe[/i]

Hope that helps.

---

### Post by thabstract on 2010-07-15
If you don't mind, can you get me a link for a no cd?

---

### Post by prodigy_ on 2010-07-15
Check PM.

---

