---
title: "microsoft office 2007 in wine?"
date: 2010-01-21
forum: General Help
---

### Post by bds28338 on 2010-01-21
hey there, I was wondering, how well does Microsoft Office 2007 work under WINE? My mother is a school teacher for younger children, so she really only needs Microsoft Office 2007 and a browser. For the life of me, I've never met anyone that gets more viruses and problems with her computer. So I'm wondering if I can switch her over to Linux and use Microsoft Office 2007 in WINE. OpenOffice isn't a possibility, I'm already pushing it asking her to learn how to use Linux. (I know it isn't hard, I use it myself, but she will fight to the death about using Microsoft Office) So how's Office in WINE?

---

### Post by reiki on 2010-01-21
Office 2007 should install fine using the latest Wine. Depending on what programs from Office you want to use, some will work better than others. Word and Excel seem to be fine. Access won't work if I remember correctly. Powerpoint is a maybe. I think it works but not sure to what degree. Go to the wine website and look it up in the apps database. [www.winehq.org](www.winehq.org) and tehn browse apps. You'll get the latest information on what works and what doesn't

---

### Post by bds28338 on 2010-01-21
yeah, all she uses is Excel & Word. I'm really looking for someone with first hand experience, I checked the AppDB on WINE but it kind of varies what info and how reliable it is on there, from my personal experiences with it.

---

### Post by Yogotiss on 2010-01-21
The best way to install Office 2007 would be to go to this site ([http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)) Here you can specify the Linux operating system you are using and version.[COLOR=Lime] PlayonLinux[/COLOR] uses wine... Just add the following repos in the terminal as a command. For instance:

_**Karmic **_

Type the following commands:

"**[COLOR=Blue]sudo wget [http://deb.playonlinux.com/playonlinux_karmic.list](http://deb.playonlinux.com/playonlinux_karmic.list) -O /etc/apt/sources.list.d/playonlinux.list[/COLOR]**"

"**[COLOR=Blue]sudo apt-get update[/COLOR]**"

"[COLOR=Blue]**sudo apt-get install playonlinux**[/COLOR]"

_**Jaunty**_

"**[COLOR=Blue]sudo wget [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list) -O /etc/apt/sources.list.d/playonlinux.list[/COLOR]**"

"[COLOR=Blue]**sudo apt-get update**[/COLOR]"

"**[COLOR=Blue]sudo apt-get install playonlinux[/COLOR]**"

---

