---
title: "shiretoko"
date: 2009-10-01
forum: General Help
---

### Post by jtmedin on 2009-10-01
Downloaded shiretoko from mozilla, but forget how to install it. Its extension is firefox.sh so tried 'sh firefox.sh' but no bananna. What am i doing wrong? TIA

---

### Post by wojox on 2009-10-01
```
chmod 755 firefox.sh
```

---

### Post by scouser73 on 2009-10-01
> **jtmedin said:**
> Downloaded shiretoko from mozilla, but forget how to install it. Its extension is firefox.sh so tried 'sh firefox.sh' but no bananna. What am i doing wrong? TIA

Hi jtmedin, personally I wouldn't install Shiretoko I would recommend that you download [[COLOR="Red"]**Firefox 3.5.3**[/COLOR]]("http://www.mozilla-europe.org/en/firefox/")

Once you have downloaded it, right click and select **Extract** then enter this command in Terminal: **gksudo nautilus** then cut and paste it into **/opt**

Now go to **System > Preferences > Main Menu**, highlight **Internet** select **New Item**, in the Name field call it Firefox then in the Command field enter: **/opt/firefox/firefox**


That will have Firefox running no problem.

---

### Post by credobyte on 2009-10-01
```
sudo chmod +x firefox.sh
./firefox.sh

```

---

### Post by lovinglinux on 2009-10-01
Shiretoko is in the repositories.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm.

---

