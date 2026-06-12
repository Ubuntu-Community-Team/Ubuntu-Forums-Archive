---
title: "first post: how to view .flv files properly"
date: 2009-11-02
forum: General Help
---

### Post by abqhandyman on 2009-11-02
Hello forum,

I've been on ubuntu now for a couple weeks, have e-mail and a newsreader configured somewhat, and am looking to polish up this new install.  Every day shows me some new thing that I like about this platform, but my skill level is still very low.

I try not to relapse to windows to do anything now.  Right now, my media player is unable to view .flv files correctly.  Am I peeking at smut on the internet? yes, ok, shoot me.  Neither in the browser nor in the movie player does it come up correctly.  

Fishing for tips on how to correct this.  Cheers,

---

### Post by Old *ix Geek on 2009-11-02
Totem Movie Player works fine for me. What have you tried? And what were the results?

I'm using KDE 4.2 on Ubuntu 9.04.

---

### Post by abqhandyman on 2009-11-02
Thanks so much for your reply OG.  I did go back and see that the movie player *does* work, so it could be just a problem with firefox, as opposed to something that has to do with ubuntu.

I'll try to seek out a firefox forum somewhere.

---

### Post by maggoteer on 2009-11-02
On hardy 8.04, I think all one needs for flv/swf playback in firefox is to install the "adobe-flashplugin" package from the repository. It may reside in the medibuntu repository rather than main ones.

Indeed, I see no problem with flv playback in firefox, though some problems with the standalone players. I've had the best luck with vlc playing most flv files, and xine playing the least. Don't know why, and don't know if my experience is typical. I'm under the possibly delusional impression that the browsers make use of the above mentioned plugin from adobe, while the stand alone players are using their own codec/driver thingees. Hope that helps...well, isn't completely useless.

---

### Post by abqhandyman on 2009-11-03
Thx, mag.  This is one of the things that's hard for me.  I made a screenshot.  I don't see any obvious choices for what I would download.

---

### Post by jesuisbenjamin on 2009-11-03
You may need to enable repositories and download few updates: check this thread and see if it helps: [** Comprehensive Multimedia & Video Howto**]("http://ubuntuforums.org/showthread.php?t=766683")

There is also a series of plug-ins you need to be able to view some video in your browser. Firefox should prompt you when a plug-in is required and you should be able to download it.

If not you should see if you can find the treasure you seek in the cave of Mozi-baba: [**plugins for firefox**]("https://addons.mozilla.org/en-US/firefox/browse/type:7")

---

### Post by maggoteer on 2009-11-09
Weird. You've got flash-plugin installed, and it's listing version 10.32.18, same as mine. So...not sure why it's not working in firefox for you. I'm using the version of firefox in hardy, version 2.0.022. Two random things I can think of. First check under Firefox Preferences (under Edit/Preferences), look in the "Content" tab and click on the "Manage" file types button. See if it's listing "SWF" and "SPL" files as openable with shockwave flash. 

Second possibility - I think I've had problems with viewing flash IF javascript is off. I think its just because the flash is embedded in some javascript, so no javascript, no flash. If that doesn't help....I've completely exhausted my two cents.

---

