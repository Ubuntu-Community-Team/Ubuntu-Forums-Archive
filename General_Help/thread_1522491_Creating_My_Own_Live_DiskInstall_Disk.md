---
title: "Creating My Own Live Disk/Install Disk"
date: 2010-07-02
forum: General Help
---

### Post by amnite on 2010-07-02
Well I'm running a Lucid Wubi system and I just got everything exactly the way I like it. My brother was having a hard time with Windows and I recommended Linux. Well being the inpatient person he is, he wasn't impressed with it "right out the box". But he's seen my setup and still wants to give it a shot. So I was curious if there was a way to create a Live CD from the way I have it already instead of downloading the "start-up" version from the site? I think they call them distros but I'm not for sure. This would be great I think to help introduce my brother and others to this awesome OS, and plus when I mess with the wrong things(which I have, and will again) I could re-install it from where I was instead of having to redo everything.

---

### Post by philinux on 2010-07-02
You could try this. Not sure how or if it works in wubi .
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

[edit]

Apparently remastersys will not work with wubi.

---

### Post by amnite on 2010-07-02
This looks like what I needed. I downloaded it and think you answered my question. I don't have the time at this exact second to test it, but I will later tonight and let you know the results for Wubi so then you know for later. TY!!!!! Super-Stoked!

---

### Post by philinux on 2010-07-02
Other thing that might work is this.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by amnite on 2010-07-05
yea remastersys killed my linux. dunno it just totally killed all my memory and crashed... ill try the other one and see what rrsults i get.

---

### Post by bcbc on 2010-07-05
copy your root.disk - c:\ubuntu\disks\root.disk (or d:, e: depending on where you put wubi)

Then have your brother install wubi normally. After that, just copy your root.disk over his. They'll be identical.

I assume you'll want to create a new user for him and delete your own, update the wifi connection etc. etc. but other than that they'll be the same.

Edit:
There may be some issues if the hardware is different. In my experience ubuntu is great moving to and from different machines, but if you've got e.g. custom nvidia drivers and your brother's machine has an different graphics card you may have some issues there. If you plan for that then it should work ok ... 

But moving a 64bit version to a 32bit machine... probably not so good.

---

