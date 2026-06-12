---
title: "Docky 3D Background corrupt"
date: 2010-05-19
forum: General Help
---

### Post by iridium21 on 2010-05-19
Hi there,

Ah, another day, another problem with Ubuntu :( The day rapidly approaches where I put XP back on this old machine, unfortunately :(

Anyway, does anyone know why Docky's 3D background looks like this?  

[IMG]http://img682.imageshack.us/img682/6697/screenshotig.png[/IMG]

---

### Post by themusicalduck on 2010-05-19
Firstly, do you have compiz enabled? (in System > Preferences > Appearance. Tab visual effects) If anything other than none is selected then compiz is on.

I'm not sure why Docky would do that, but if Compiz is enabled, you could try updating to the latest version of Docky to see if it works better.

```
sudo add-apt-repository ppa:docky-core/ppa
``````
sudo apt-get update && sudo apt-get install docky
```
Bear in mind though that it is a development version, so Docky may crash occasionally (but not too often).

---

### Post by iridium21 on 2010-05-19
Hi there,

Thanks for the reply & help. I've checked that compiz is on - it is and I've updated to the Docky version you suggested but the problem remains :(

---

### Post by iridium21 on 2010-05-20
Docky did some kind of update today, however it still looks like this when the 3D background is selected :confused: 

[IMG]http://dl.dropbox.com/u/6232429/Pictures/Screenshot-2.png[/IMG]


Does anyone have *any* ideas what might be going on please?

---

### Post by themusicalduck on 2010-05-20
I'm not sure what else to suggest :(

It looks like it's been recognised as a bug here - [https://bugs.launchpad.net/docky/+bug/543859](https://bugs.launchpad.net/docky/+bug/543859)

but the Importance is set to Low, so it might not be fixed for a while. You could set the bug to be affecting you (if you have a launchpad account) to help draw some attention to it.

---

### Post by iridium21 on 2010-05-21
> **themusicalduck said:**
> I'm not sure what else to suggest :(

It looks like it's been recognised as a bug here - [https://bugs.launchpad.net/docky/+bug/543859](https://bugs.launchpad.net/docky/+bug/543859)

but the Importance is set to Low, so it might not be fixed for a while. You could set the bug to be affecting you (if you have a launchpad account) to help draw some attention to it.

Well thanks very much for your help anyway. I've just added myself to the list of people experiencing this bug so... Anyway, I'm going to try a Nvida 6600GT in this old machine - that may help. yes?

---

### Post by themusicalduck on 2010-05-22
I'm not sure if it's likely using another card would help, but could give it a try. The 6600GT is quite old though, so it might not be that well supported on Ubuntu (but I think probably is in some way, as I used to have one).

It might be to do with how it's configured in gconf or how your desktop is setup or other hardware. Seems like there hasn't been enough investigation done into the bug yet to guess though.

---

### Post by tom.swartz07 on 2010-05-22
Just an FYI- I did notice this same problem, but it was cleared up after an update if you build it from source.


I ran into similar problems a few times, so I just decided to build from source, its super stable, and you could even change things if you dont like it!


Granted, its not as easy as running the update manager, but you only have to remember 4 commands to run from the terminal (uninstall, autogen, make, make install)...

[http://wiki.go-docky.com/index.php?title=Installing#Installing_From_Source](http://wiki.go-docky.com/index.php?title=Installing#Installing_From_Source)

---

### Post by inso_741 on 2010-05-23
or you could try AWN...;)

---

### Post by itachi46 on 2010-10-15
reviving thread here.. had the same problem and i fixed it by closing it then opening it again

---

### Post by GeissT on 2011-01-20
Sorry to revive the thread, but i did what the poster above me did and it worked for a bit then it stuffed up again.

I have also viewed the bug report and have added myself to the list of affected users.

GeissT

---

### Post by jjinco33 on 2012-11-03
Old thread, but after being annoyed with the 2d background for 2 years decided to look it up, and yes, simply quitting Docky and relaunching it resolved the issue. :P

---

