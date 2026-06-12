---
title: "F1 please...Problem in Keryx project creation..."
date: 2009-11-24
forum: General Help
---

### Post by emigrant on 2009-11-24
hi all,
im having a problem in creating a keryx project. (tutorial [here]("http://crashsystems.net/2009/01/keryx-tutorial/"))
some days ago i was able to successfully create projects and install updates to my system. now i wanted to create a second project and i see the project creation is done 'swiftly' unlike the previous one which took a significant amount of time. so i doubt there is some problem in it here is the message:

```
$ python keryx.py  --create SecondOfflineUpdate debian
Loading config: /media/BigPen/keryx/linux/keryx.conf
[COLOR=Red]ColorMap.py failed to load.[/COLOR]
Plugin loaded: Debian v0.92.2
[COLOR=Red]Search.py failed to load[/COLOR].
Created project: SecondOfflineUpdate
Project created successfully.

```

thank you all for your time.

---

### Post by mac9416 on 2009-11-24
Howdy, emigrant!

Since it said "Project created successfully," I believe you should be OK. I am not sure, however, why those two plugins failed to load. Try taking Keryx to your online computer and loading the project. If all goes well, ignore the errors. If there are problems, I would suggest downloading Keryx again and starting afresh. If that does not work, we will go from there.

Let me know how it goes!

---

### Post by emigrant on 2009-11-24
Hi mac,
Writing from mobile so plz ignore the spellings.

I did for a fresh instal nd same thing.
Nd to see whether t wrks i wnt to windws nd tried vt mobile brdbnd nd t sms ok. Wt i wory s, to do the actual dwnld along vt some other new apps, tomorw i hv to trvl sm 65km to a faster intrnt place nd i dnt wnt to see ths shwng ny prob aftr i go thea.
Thnk u for ur help :)

---

### Post by EXCiD3 on 2009-11-24
> **emigrant said:**
> Hi mac,
Writing from mobile so plz ignore the spellings.

I did for a fresh instal nd same thing.
Nd to see whether t wrks i wnt to windws nd tried vt mobile brdbnd nd t sms ok. Wt i wory s, to do the actual dwnld along vt some other new apps, tomorw i hv to trvl sm 65km to a faster intrnt place nd i dnt wnt to see ths shwng ny prob aftr i go thea.
Thnk u for ur help :)

 You should be fine. The reason those two plugins don't load is because you created a project from the command line on a machine that does not have python-wxversion installed. Those two plugins require that to be used, but since they are only used for the graphical interface, they won't affect anything. If there weren't any errors and it said the project was created successfully, you should be okay. Good luck! :)

---

### Post by emigrant on 2009-11-24
In that case its ok then. Thank u very much :-)

---

