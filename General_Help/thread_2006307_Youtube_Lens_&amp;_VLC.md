---
title: "Youtube Lens &amp; VLC"
date: 2012-06-18
forum: General Help
---

### Post by evilsoup on 2012-06-18
I'm using the Youtube lens as described [here]("http://www.omgubuntu.co.uk/2012/01/unity-youtube-lens-updates-with-browser-free-video-playback"), in conjunction with VLC. It works well enough, except for high-definition videos: VLC insists on using the highest-quality stream available from a given youtube link, and the limited hardware of my poor little netbook can't bear 720p, let-alone full-on 1080p.

It is possible to force VLC to use 360p by appending '&fmt=34' to the end of the youtube url, but of course having to copy & paste around the URL would remove all the convenience from the youtube lens.

So. Is there any way to either
1. set the youtube lens to append '&fmt=34' to the end of the youtube links it uses (please point me in the general direction of what I'd need to look at, if nothing else); or
2. set VLC to automatically use (for example) the 360p stream from a provided youtube link

---

### Post by evilsoup on 2012-06-19
Well I managed to find a solution myself, it's in the VLC preferences (TOOLS->PREFERENCES).

I had to tick the box to show all settings, and then go to 'Input/Codecs' in the sidebar-list: there's an option labelled 'Preferred video resolution', which is automatically set to 'highest possible' but which I changed to 'Standard Definition'.

---

