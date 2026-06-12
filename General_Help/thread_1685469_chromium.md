---
title: "chromium"
date: 2011-02-10
forum: General Help
---

### Post by nush on 2011-02-10
hi
i have been using ubuntu 10.10 for some time now with my preferred browser chromium, everything was fine until today when i received an update.
now whenever i open a page in chromium that uses flash, flash player crashes immediately, when i use firefox i have no problem at all with flash player.

ive tried to disable flash plugin in chrome but then i cant watch youtube videos or any other online videos.

any of you clever people out there got a fix for me or do i have to change change browser
thanks

---

### Post by Habeouscorpus on 2011-02-10
Chromium is working fine for me, and I recently upgraded too. Are you using a development release of Chromium by accident?

---

### Post by nush on 2011-02-10
hi
dont know why, but yes i was, ive changed to stable release but still have the same problem.

when i start from terminal i get this message


(exe:12850): Gdk-WARNING **: XID collision, trouble ahead
[12850:12850:22033109310:FATAL:base/process_util_linux.cc(594)] Out of memory.

dont know if that helps anyone
thanks again

---

### Post by toff72 on 2011-02-12
> **nush said:**
> hi
dont know why, but yes i was, ive changed to stable release but still have the same problem.

when i start from terminal i get this message


(exe:12850): Gdk-WARNING **: XID collision, trouble ahead
[12850:12850:22033109310:FATAL:base/process_util_linux.cc(594)] Out of memory.

dont know if that helps anyone
thanks again

exactly same issue for me.
any workaround ?

---

### Post by nush on 2011-02-12
i have not found one yet,
i found some info that suggests the fault is with chromium itself but i am lost when it comes to putting it right, really is annoying when all the websites and login details are in one browser then i have to use another.
nush

---

### Post by nush on 2011-02-12
hi toff72
i have changed my nvidia driver via additional drivers and thats sorted the the flash crash, only problem for me is my offline movies are all blue (in colour that is) ha.
never thought that would be a problem.
nush

---

### Post by ankspo71 on 2011-02-16
> **nush said:**
> hi
i have been using ubuntu 10.10 for some time now with my preferred browser chromium, everything was fine until today when i received an update.
now whenever i open a page in chromium that uses flash, flash player crashes immediately, when i use firefox i have no problem at all with flash player.

ive tried to disable flash plugin in chrome but then i cant watch youtube videos or any other online videos.

any of you clever people out there got a fix for me or do i have to change change browser
thanks

You could try out Google Chrome.

Nevermind what I just said about upgrading Chromium. 
Flash 10.2 just started crashing in my Chromium 11 too. It was working great for a couple of hours and then nothing.

---

### Post by nush on 2011-02-19
hi ankspo71
thanks.
i tried other browsers and at first they were ok, then they started playing me up as well, i have now gone to the most recent nvidia driver, my online vids are ok but as i said before my other movies all have a blue tinge to them.
nush

---

### Post by WorMzy on 2011-02-19
If I remember correctly, Chromium now comes with it's own integrated flash plugin, which is probably why other web browsers aren't behaving the same way. Unfortunately, I don't think there's anyway around this, aside from downgrading to a version of Chromium that worked.

EDIT: Looks like I didn't read through the last well enough; Other browsers are behaving badly too, now? I think that that, coupled with the "Out of memory" error, signifies that your machine may be suffering from a hardware problem. Could you run a [memory test]("https://help.ubuntu.com/community/MemoryTest"), and see if that reports any problems?

---

### Post by nush on 2011-02-22
hi thanks
now done the mem test
found no problems.
its something i can live with, but would be happier if i could watch my own vids without them turning blue

nush

---

### Post by nush on 2011-02-22
hi
just reinstalled the nvidia driver and everything looks like its working fine now
thanks
nush

---

### Post by P1C0 on 2011-02-28
I have a small issue with Chromium. When I try to open xml files with chromium (doesn't matter if they have .xml or .rdf extension) it downloads them to the Downloads folder, it doesn't open them for viewing.

I installed XML tree for Chromium and it works when I find an xml page online, but when I try to open one from Desktop, it downloads it..

---

### Post by FrankenCub on 2011-03-14
> **ankspo71 said:**
> You could try out Google Chrome.

Nevermind what I just said about upgrading Chromium. 
Flash 10.2 just started crashing in my Chromium 11 too. It was working great for a couple of hours and then nothing.

Google Chrome was how I fixed Chromium too lol. Nothin else worked.

---

### Post by ankspo71 on 2011-03-14
Hi again... good news
Flash and Chromium is working for me again.:D I was using Firefox with the Flash-Aid addon, and the addon gave me an update for Flash 10.3 d180. This flash update is working good with Chromium 10.0.648 so far (and better than in firefox too IMOP).

---

### Post by FrankenCub on 2011-03-14
That's good to hear. I was quite happy with Chromium till the flash issues, yesterday was the worst for me. I couldn't even get my Photobucket account to load. I used to be a big Fire Fox advocate but a web site that I spend most of my time on and admin at was having some weird issues with. Other members who also use FF end up having the same issues.

I actually like Chromium better than Google Chrome because it has some really nice options to customize it. I'll try it out after some more updates to see if it's stable for me again.

---

