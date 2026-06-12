---
title: "Deluge and Magnet Links"
date: 2012-04-28
forum: General Help
---

### Post by TimEnid on 2012-04-28
I have deluge installed to handle my torrents. I set it as the default. But when i try to open a magnet link, transmission pops up and tries to open it. Before updating to 12.04, deluge automatically opened. Any suggestions?

---

### Post by Vaphell on 2012-04-28
you open them from firefox? Check its preferences to see what program is assigned to magnet links.

---

### Post by TimEnid on 2012-04-28
Im using Chrome

In deluge, under preferences, there is an option to associate magnet links with deluge, i checked that as well.

---

### Post by TimEnid on 2012-04-28
In firefox, under preferences, applications, i see the content type Magnet. Transmission is set as the default. When clicking the tab, it says Use Other, and brings me to the file browser. So, where do i locate the file that for Deluge to choose?

---

### Post by Vaphell on 2012-04-28
try this
```
gvfs-mime --set x-scheme-handler/magnet deluge.desktop
```
it should assign deluge to magnet links on the OS level.

deluge - /usr/bin/deluge (binary) or /usr/share/applications/deluge.desktop (launcher)
non-essential programs are usually in /usr/bin, core system stuff is in /bin

---

### Post by TimEnid on 2012-04-28
> **Vaphell said:**
> try this
```
gvfs-mime --set x-scheme-handler/magnet deluge.desktop
```
it should assign deluge to magnet links on the OS level.

deluge - /usr/bin/deluge (binary) or /usr/share/applications/deluge.desktop (launcher)
non-essential programs are usually in /usr/bin, core system stuff is in /bin

thanks, this worked for firefox, but when i try to open it with chrome, tranmission still opens up. I tried your first suggestion as well, but still nothing.

---

### Post by TimEnid on 2012-04-28
also found some information on this page
[http://askubuntu.com/questions/44849/how-to-configure-chrome-to-open-magnet-urls-with-deluge](http://askubuntu.com/questions/44849/how-to-configure-chrome-to-open-magnet-urls-with-deluge)

Its working now. Thanks for the help.

---

### Post by T3kG33k on 2012-09-11
I did a lot of searching and nothing helped me with my Deluge vs Transmission problem in 12.04 and Unity.  I had to uninstall Transmission in order for chrome, chromium, srware iron to use Deluge to open magnet links.

---

