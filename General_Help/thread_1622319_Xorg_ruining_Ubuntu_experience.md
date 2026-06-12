---
title: "Xorg ruining Ubuntu experience"
date: 2010-11-15
forum: General Help
---

### Post by gyre007 on 2010-11-15
Hi,
there is a lot of posts regarding flash/firefox/Xorg nastiness...yet no one has been able to resolve the issue for everyone. Ubuntu people are blaming Adobe - which in all fairness we all do - along with Stevie Jobs...however I don't understand one thing and I would be more than happy if some Ubuntu guru could explain it to me.
Once I run the flash site with adobe flash plugin enabled my CPU jumps to 100%...this is OK ....well OK...it's not but it would be if the problem with the high CPU usage disappeared right after I chicken out from the site on which im watching the flash content...
Funny and very inconvenient thing is that the problem continues even after I close the browser!...after I close the browser it takes about 2 seconds whooooa to start gnome-terminal - which is accompanied by big CPU spikes visible in top on the Xorg line. I had the impression that once the browser is closed I shouldnt be affected by this any more...so ok I though let's give Xorg a bash and restart it...but sadly I had to realize that this doesnt HELP AT ALL...simple xterm startup creates spikes on CPU again culprit identified is Xorg process....the only thing that helps is restarting the whole system which brings us back to Windowzzzz times....Im guessing that the problem might be a graphical card which in my case is some Intel onboard card (00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03))
Is there a way how I can investigate this further ? or how can I isolate the problem and say that this is 100% graphics card problem and not XOrg problem ? I thought that if I restart Xorg all the graphical drivers are unloaded and all the mem leaks should disappear...am I correct or no ?

---

### Post by pepsifx357 on 2010-11-15
I really wish I knew the answer to that problem.  I've noticed since my entry into Ubuntu 7.10 that flash was always an issue for some reason.  I remember when youtube was doing the html5 testing and you could sign up for it through chromium browser.  When running videos in HTML5, my CPU was running 20% or less.  When running in flash, 80% + percentage.  Adobe is a bloated piece of crap if you ask me.  But for now, we're stuck with it.

---

### Post by gyre007 on 2010-11-15
> **pepsifx357 said:**
>  When running videos in HTML5, my CPU was running 20% or less.  When running in flash, 80% + percentage.  Adobe is a bloated piece of crap if you ask me.  But for now, we're stuck with it.

That's all fine. Im not really fond of Adobe either - if anything then the exact opposite. What I really mind though is that Xorg is totally messed up after watching flash and even after closing the browser - that to me is a bit of a mystery...
It would be cool if someone could shed more light on this - because I've read tons of threads but none of them gives any proper answer - although I admit there might not be one...but at least a proper explanation would be highly appreciated not only by me...

---

