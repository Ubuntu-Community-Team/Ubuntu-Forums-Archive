---
title: "Speeding up firefox with a slow SSD"
date: 2010-05-26
forum: General Help
---

### Post by marshmugger on 2010-05-26
I have an Acer Aspire One A110 netbook. Presently, it runs Ubuntu Netbook Remix 9.10 and Firefox 3.5.8. The A110 is an early model with a slow SSD (solid state drive). Firefox was slow and often paused (froze for a moment). I tried several hacks in the Ubuntu forums and elsewhere to speed up Firefox. Some were not effective at all, some were very technical and at least one produced instability. I tried Google Chrome, which started out fast but turned slow. Emptying browser caches did not fix my problems.

I thought the slow disk must be the problem and moved the browser cache to a dedicated SDHC card. I've since been running with a dedicated cache for a month or two now, have never emptied the cache and Firefox still runs fast. I mean fast enough that it doesn't slow down my browsing (I'm not trying to set world speed records).

The A110 has two SD slots. I have a 16 GB SDHC card in the 'Storage Expansion', which is my data disk. The second is a card reader slot. I didn't want to mess with my data disk. I bought a fast (Transcend, Class 6) 4 GB SDHC, put that in the card reader slot and set up my Firefox cache there:

[INDENT]1. Type about:config in the Firefox address bar.
2. Tell Firefox where your new cache is. For me:
browser.cache.disk.enable true
browser.cache.disk.parent_directory /media/BD2C-8BD5/firefox (I created a directory /firefox on the card)
3. Tell Firefox to increase the size of the cache:
browser.cache.disk.capacity 512000 (formerly 51200)
4. Check the cache is enabled, type about:cache in the Firefox address bar. For me it returns:
/media/BD2C-8BD5/firefox/Cache
[/INDENT]
To get the name of the cache directory easily and accurately, open this directory with the File Browser, toggle to a text-based location bar and there it is.

Cheap SD cards can be purchased on feebay. Select carefully, they're not all fakes. SDHC Class 6 is fine for a browser cache, handling small blocks of data. Cards only slow down when you do a massive file transfer. 2GB or 1GB should be adequate but fast and small cards are rare. Other memory cards can be used of course, but speeds vary between different technologies.

Happy browsing.

---

### Post by pjalegria on 2011-04-03
what about Firefox 4, can i apply this tweaks??

---

### Post by linuxnewb2 on 2011-04-03
What about just increasing the size of the cache in firefox itself ?

Was using 3.6 of firefox, but went ahead and updated to firefox 4.0 recently. There are controls for setting the browser cache in firefox itself. 

(firefox version 4.0)
Edit>Preferences>Advanced and then click the network tab. Should be able to define the size of the browser cache there.

Note: Though I am using linux mint version 10. Not ubuntu ... shrugs. Should still be the same surely. I mean firefox 4.0 is firefox 4.0 and mint is based on ubuntu linux. So see no reason you wouldn't be able to set the size of the cache in firefox itself in either one. The cache controls used to be under Tools>Options>Advanced in the 3.6 version of FF.

Also note having a bigger cache for your browser certainly doesn't necessarily translate into massive speed gains fellas. Are some other tweaks people can do in about:config though. Plenty of info available about it online already. lol .. in fact thanks for reminding me. Hadn't gotten around to playing with this one yet.

---

