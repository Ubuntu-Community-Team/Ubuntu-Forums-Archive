---
title: "Windows Media Player"
date: 2010-08-12
forum: General Help
---

### Post by abergmann on 2010-08-12
I have just installed ubuntu 10.04 on my laptop. But I have problems viewing videos from [www.lynda.com]("http://www.lynda.com"). I can see videos at cnn, youtube and other websites without problems. I get the following error at Lynda.com:

"Please install or activate the Windows Media Player Plugin!
For Internet Explorer you have to install [Windows Media Player]("http://www.microsoft.com/windows/windowsmedia/download/AllDownloads.aspx"). 
For Firefox on Windows install [the Microsoft Media Player Plugin]("http://port25.technet.com/pages/windows-media-player-firefox-plugin-download.aspx"). If it's already installed it may be disabled. 
To  check, go to Tools menu, choose Add-ons and then Plugins tab. There  look for Microsoft Windows Media Player Firefox Plugin and reenable it."

I'm new to Linux.

regards,
Allan Bergmann

---

### Post by sydbat on 2010-08-12
> **abergmann said:**
> I have just installed ubuntu 10.04 on my laptop. But I have problems viewing videos from [www.lynda.com]("http://www.lynda.com"). I can see videos at cnn, youtube and other websites without problems. I get the following error at Lynda.com:

"Please install or activate the Windows Media Player Plugin!
For Internet Explorer you have to install [Windows Media Player]("http://www.microsoft.com/windows/windowsmedia/download/AllDownloads.aspx"). 
For Firefox on Windows install [the Microsoft Media Player Plugin]("http://port25.technet.com/pages/windows-media-player-firefox-plugin-download.aspx"). If it's already installed it may be disabled. 
To  check, go to Tools menu, choose Add-ons and then Plugins tab. There  look for Microsoft Windows Media Player Firefox Plugin and reenable it."

I'm new to Linux.

regards,
Allan BergmannHave you installed "Restricted Extras"? Go into Software Sources (under System > Administration > Software Sources) and enable all the repositories on the first tab (Ubuntu Software). It will reload and you can search either the Software Centre or (much better) Synaptic, and download all the Restricted Extras you need.

Also, [this site]("http://medibuntu.org/") will help you alot, especially [this page]("https://help.ubuntu.com/community/Medibuntu")!

---

### Post by earthpigg on 2010-08-12
hi,

im able to play their videos.

try installing the 'totem-mozilla' package and restart firefox.

edit: i humbly suggest trying my suggestion before the suggestion of the poster above me. totem is the name of the ubuntu 'movie player' that you find in applications -> sound and video.

---

### Post by sydbat on 2010-08-12
> **earthpigg said:**
> hi,

im able to play their videos.

try installing the 'totem-mozilla' package and restart firefox.

edit: i humbly suggest trying my suggestion before the suggestion of the poster above me. totem is the name of the ubuntu 'movie player' that you find in applications -> sound and video.earthpigg, you are correct. 

I just figured adding the restricted reops would avoid alot of future problems. Both ways work.

---

### Post by abergmann on 2010-08-12
Thank you everybody - It was great and quick help. I installed the "restricted" pack. Now I can see the plugins in Firefox. (It seems that the totem-mozilla is installed as well).

At first it didn't work at lynda.com, but it turns out, that I can choose between different formats at their website (flash, quick time standard, quick time custom). The quick time standart setting works.

Allan Bergmann

---

