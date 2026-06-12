---
title: "banshee doesn't recognize my ipod"
date: 2009-11-02
forum: General Help
---

### Post by vaskark on 2009-11-02
This is what podsleuth gives:

```
Found an iPod device, but it is not known by PodSleuth:
   Error: org.podsleuth.* properties are missing
   UDI:          /org/freedesktop/Hal/devices/volume_uuid_FE82_C3F8
   Block Device: /dev/sdb2
   Mount Point:  /media/IPOD NANO

   Cause: PodSleuth may not be installed properly, the HAL daemon may need
          to be restarted and/or the device needs to be refreshed.
```I have the iPod Nano, 2nd Gen, 8 GB Black. Everything worked fine in Jaunty and my ipod worked fine in Banshee (my preferred player). Can anyone offer some guidance?

Thanks.

---

### Post by tylerannosaurus on 2009-11-03
I am having similar issues, when I ran Banshee in terminal, it says that it's being mounted:

[HTML][Info  00:37:59.915] Running Banshee 1.5.1: [Ubuntu karmic (development branch) (linux-gnu, i486) @ 2009-10-19 14:46:07 UTC]
[Info  00:38:02.401] All services are started 2.049042s
[Info  00:38:05.504] nereid Client Started
[Info  00:38:24.362] Received device command: action = Activate, device = /media/SGT[/HTML]

Running podsleuth in terminal gives me a slightly different output than what was posted above:

[HTML]$ podsleuth
No iPods were found in the HAL device tree[/HTML]

Rhythmbox can load my iPod, but not Banshee... after scouring the web, it seems this is a common problem, something to do with Banshee and not my iPod. I'm also running 9.10 (the problem started when I upgraded) and my iPod is one of the 30GB videos when they first came out.

Another site mentioned this as a possible solution (or something to try to see if it worked): [https://bugzilla.gnome.org/show_bug.cgi?id=586508](https://bugzilla.gnome.org/show_bug.cgi?id=586508)

Another site had this workaround: [https://bugzilla.redhat.com/show_bug.cgi?id=495240#c20](https://bugzilla.redhat.com/show_bug.cgi?id=495240#c20)

I'd definitely rather have this fixed than having to mount all volumes as the work around would have me do and I don't understand what's being said in the first link.

---

### Post by Bonster on 2009-11-03
Heres the fix for that i guess [http://www.omgubuntu.co.uk/2009/11/ipod-doesnt-work-karmic.html](http://www.omgubuntu.co.uk/2009/11/ipod-doesnt-work-karmic.html)

---

### Post by vaskark on 2009-11-03
> **Bonster said:**
> Heres the fix for that i guess [http://www.omgubuntu.co.uk/2009/11/ipod-doesnt-work-karmic.html](http://www.omgubuntu.co.uk/2009/11/ipod-doesnt-work-karmic.html)

Sadly, this didn't work for me.

---

### Post by navneeth on 2009-11-05
> **Bonster said:**
> Heres the fix for that i guess [http://www.omgubuntu.co.uk/2009/11/ipod-doesnt-work-karmic.html](http://www.omgubuntu.co.uk/2009/11/ipod-doesnt-work-karmic.html)

Thank you for the link. :) It worked for me.

---

### Post by mkeyes001 on 2009-12-21
> **Bonster said:**
> Heres the fix for that i guess [http://www.omgubuntu.co.uk/2009/11/ipod-doesnt-work-karmic.html](http://www.omgubuntu.co.uk/2009/11/ipod-doesnt-work-karmic.html)

so if this does work, is this something your have to do everytime your plug your ipod in?

---

### Post by Docaltmed on 2009-12-27
Ipod can be seen and music added, but playlists remain untouchable.

---

### Post by Leonfayte on 2010-03-01
> **Bonster said:**
> Heres the fix for that i guess [http://www.omgubuntu.co.uk/2009/11/ipod-doesnt-work-karmic.html](http://www.omgubuntu.co.uk/2009/11/ipod-doesnt-work-karmic.html)

been looking everywhere for this. thanks!

---

### Post by rob22941 on 2010-03-10
This doesn't work for me. I have a 30gb Ipod video... Any ideas I do prefer Banshee to rhythmbox and others.

---

### Post by tareksobh on 2010-04-16
You won't believe how stupid is the solution to this problem!! I'm not 100% sure, but it worked for me...
To solve this issue, open Rhythmbox and you'll find that the iPod is connected, right? Now, there is a button above in the menu that says "Eject"... Just click on that, close Rhythmbox and run the other application normally!! I tried it with Listen and it worked...

---

### Post by bestusername on 2010-04-30
> **tareksobh said:**
> You won't believe how stupid is the solution to this problem!! I'm not 100% sure, but it worked for me...
To solve this issue, open Rhythmbox and you'll find that the iPod is connected, right? Now, there is a button above in the menu that says "Eject"... Just click on that, close Rhythmbox and run the other application normally!! I tried it with Listen and it worked...

Didn't work for me.

---

### Post by platinumlolita on 2010-05-04
> **bestusername said:**
> Didn't work for me.

ne neither... when I eject in rhythmbox it just ejects my ipod before I can get into banshee...

---

