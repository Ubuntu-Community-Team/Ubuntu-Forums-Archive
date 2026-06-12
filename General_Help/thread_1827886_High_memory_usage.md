---
title: "High memory usage"
date: 2011-08-18
forum: General Help
---

### Post by zcacogp on 2011-08-18
Chaps, 

This thread may be quite vague as I'm not too sure of the details of the problem I am asking about, and I am also not too technical (I nearly posted this in the beginner forum!)

I am running 11.04 on three machines, and one of them seems to be using quite a lot of memory. It is never below 50% (not even on first boot-up, with no applications running), and it feels sluggish to use; applications are slow to open and close, and things like moving between tabs in Chromium or Adobe PDF Viewer don't happen instantly. 

The machine in question is running 64-bit 11.04, and a screenshot from System Monitor looks like this: 

[IMG]http://i76.photobucket.com/albums/j14/zcacogp/Screenshot-SystemMonitor.png[/IMG]

The computer is only running Chromium browser, with three tabs open, and yet is showing 1.2GB of memory used. 

I know that Ubuntu uses memory differently to the way that Windows uses memory, and the two aren't comparable, but the other two machines I have (both of them lower-spec, both of them running 32-bit 11.04) both use less memory. (They use less memory, and a lower percentage of the memory they have, despite having less memory installed ... if that made sense.) 

The CPU usage isn't particularly high, and the machine appears to run as it should. It's just ... sluggish. I think that it has become more sluggish over the last few weeks, and it was investigating this sluggishness that led me to check the memory usage. FWIW, the machine has a dual-core AMD 5600 chip, but has started to feel slower than a much lower-spec single-core X61S laptop I have. 

On this basis, I think there is something wrong, but am not sure what or where to go looking. I have searched on here and on other sites, without much luck. I have found a program called HTOP, which gives this result: 

[IMG]http://i76.photobucket.com/albums/j14/zcacogp/Screenshot-ogpdesktop.png[/IMG]

... but this doesn't mean a lot to me, other than to give the impression that Chromium is using all the memory in a lot of very small bits. 

All help welcomed. Please do ask if you need more details about my system. 

Many thanks, in advance. 


Oli.

---

### Post by dino99 on 2011-08-18
chromium seems to be blamed, kill its processes and watch the difference

---

### Post by zcacogp on 2011-08-18
Dino, 

Ah, thanks. That  helped - bought it down to nearer 30% memory usage. Is that around normal? 

So is the advice not use Chromium, 'cos it's a memory hog? Has it always been so, or have there been changes made to it recently which have cause it to change? 

Maybe I need to go back to firefox ... hmm ... >thinks<

Thanks very much for your help. 


Oli.

---

### Post by Smart Viking on 2011-08-18
> **zcacogp said:**
> Dino, 

Ah, thanks. That  helped - bought it down to nearer 30% memory usage. Is that around normal? 

So is the advice not use Chromium, 'cos it's a memory hog? Has it always been so, or have there been changes made to it recently which have cause it to change? 

Maybe I need to go back to firefox ... hmm ... >thinks<

Thanks very much for your help. 


Oli.
Yeah that's ok, looks like dropbox also takes a lot of memory, but that doesn't really matter if the computer is responsive and fast.

---

### Post by HereInOz on 2011-08-18
30% of 1.7GB seems a nice number.  510MB is a good memory usage.  As a matter of interest I use Firefox, and it is currently using 85MB of RAM.  It doesn't start off at that, but the more you use it, the more RAM it wants to grab.  Chromium is similar but it can have a memory leak and just keep starting up processes and grabbing RAM.

You could try removing Chromium, remove the profile folder in your home folder (it will be a hidden folder starting with a . but I can't remember what it is called - just .chromium I think, but can't be sure as I have removed it) then re-install Chromium.  See if that helps, if you want to keep using Chromium.

---

### Post by blind2314 on 2011-08-18
If you use a lot of extensions or plug-ins, chrome/chromium will fork a new process for each extension or plug-in it loads. That could be part of the problem.

---

### Post by zcacogp on 2011-08-18
Chaps, 

Thanks for the further answers. 

Dropbox is quite useful ... if may use memory but I am happy as it doesn't use enough to affect performance. 

I don't use many extensions or plug-ins for Chromium. In fact, I don't think I use any! I do know that I moved to Chromium as I had a problem with firefox, but can't now remember what that problem was. Hmmm. I bet I find it as soon as I go back to FF ... !

HereInOz - thanks. I'll try your method of reinstalling Chromium. 


Oli.

---

### Post by zcacogp on 2011-08-18
OK, back to this one again; I've removed Chromium and the home directory for it, and am using Firefox. But I still seem to see some fairly high memory usage. 

This machine has been running for about 10 minutes (I rebooted it as the memory usage was high, and wanted to see if a re-start made any difference. One thing I noticed before rebooting is that opening things increases the memory usage, but closing them doesn't seem to reduce it.) I am currently running Firefox and nothing else, and the various monitoring systems say this: 

[IMG]http://i76.photobucket.com/albums/j14/zcacogp/Screenshot-SystemMonitor-1.png[/IMG]

... and htop says this: 

[IMG]http://i76.photobucket.com/albums/j14/zcacogp/Screenshot-ogpdesktop-1.png[/IMG]

Immediately after I rebooted it was using a (more healthy) 33% of the memory, but it climbed rapidly to his situation. I have also stopped Dropbox as well, as that was a bit memory-hungry as well.

(I also notice that since taking those screenshots, putting them into photobucket and writing this post, the memory usage has grown even more - it is now at 77.4%). 

Is this all as it should be? 

Thanks again for any help. 


Oli.

---

### Post by dave01945 on 2011-08-18
i use google chrome and it doesnt use nearly that much maybe you should try that i've heard a few people have a similar problem with firefox

---

