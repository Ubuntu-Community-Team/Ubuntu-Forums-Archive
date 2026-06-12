---
title: "Lost shiretoko bookmarks"
date: 2009-10-24
forum: General Help
---

### Post by alinux-lb22 on 2009-10-24
Hi
I did upgrade from 9.04 to 9.10 shiretoko is not available anymore, but firefox is...however I lost all of my shiretoko bookmarks and settings..anyway to retrieve those ?

Thanks

---

### Post by lovinglinux on 2009-10-24
I knew this was going to happen. I'm already adding the solution to the troubleshooting section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT011), because this will probably be a FAQ.

Shiretoko uses the directory **~/.mozilla/firefox-3.5** to store profile contents, while the default Firefox version on every release uses **~/.mozilla/firefox**. When you installed Shiretoko you didn't see any difference because Shiretoko was setup to make a clone of your Firefox 3.0 profiles. But in Karmic, there is no more Shiretoko and the default browser is already Firefox 3.5. So, close Firefox and replace the contents of **~/.mozilla/firefox** with the contents of **~/.mozilla/firefox-3.5**.

---

### Post by alinux-lb22 on 2009-10-24
Did do that but it did not restore the settings..thanks for your help.

---

### Post by Vaphell on 2009-10-24
how many profiles do you have in .mozilla/firefox?

---

### Post by alinux-lb22 on 2009-10-24
firefox and firefox-3.5.abandoned

---

