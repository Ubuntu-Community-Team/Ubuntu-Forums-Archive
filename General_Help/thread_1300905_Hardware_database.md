---
title: "Hardware database"
date: 2009-10-25
forum: General Help
---

### Post by P4man on 2009-10-25
hardware database

The more I read the forums here, the more I think ubuntu could really use a new integrated hardware tool, that serves several purposes. Since each pci and usb device has a unique identifier, I was thinking something like this:

Since no one likes reading longs texts, here are 2 illustrations  I quickly drafted:

[IMG]http://img59.imageshack.us/img59/9381/hwdb.png[/IMG]

[IMG]http://img25.imageshack.us/img25/543/hwdb2.png[/IMG]


Each (known) device is put in a database online. That database contains information such as:
- whether or not the device works out of the box with a given ubuntu version
- requires tweaks, in which case it has links to known solutions
- requires drivers, with links to available drivers

This tool could be fed by something resembling the current "system testing" app, only more functional and more in detail. It could also be fed through a community wiki, as there already are countless (usually very difficult to maintain and confusing wiki's). instead youd get a nice gui app testing your network, sound, webcam and askiing if if its working. Results are automatically uploaded and can give statistical results back (eg "your soundcard works with no issues with 98% of the users)

The database could also be fed through Canonical's hardware testing, which already exists. Or so it seems,  but no where can I find results of that testing (ie, certified hardware). If its tested by canonical it could get some official "ubuntu certified" logo or whatever, if not it could get a "ubuntu community approved" stamp. 

That database could then  be referenced through a web interface so that prospective hardware buyers can look up if a given soundcard or webcam actually works, or with what restrictions or how to make it work (think about it, it could eliminate 80% of the questions here!)

If you make the database hierarchical, you can define a motherboard as a combination of mb + onboard video + pnboard audio etc or an entire systems (say laptops) as a number of other hardware components, so once a laptop is entered in the system, other users could look it up and see (eg) the soundcard needs a tweak, the wifi requires a driver and suspend/resume problems are solved by adding kernel parameter x (This could later even be expanded to allowing scripts to do this automatically?).

With these results, the ubuntu or canonical site could then recommend hardware for you. That would give an incentive to oems to get their act together, fix their bioses, provide or opensource drivers and/or have their hardware certified by canonical. With 2 or 5 or whatever % of the market, oems feel they can pretty much ignore us, but if a simple bios tweak and/or certification process gets you to become one of few laptops or webcams that is recommended to an audience of millions, it **is** a tangible incentive. TBH I think its outrageous canonical is currently testing hardware and not advertising the systems they approved!

Anyway, the same database could also be referenced by jockey ("hardware drivers" app in system > administration) so that after a fresh install, the system could test your machine running somehting like lspci and lsusb and check in the  db and provide you with a list of drivers or workarounds or known not working hardware.

I can only see advantages here. And big one's. For everyone, for us, for ubuntu, for oems, for end users. .

Now Im thinking of writing this out in detail, make some sketches and stuff, but before I do, I was wondering what you think. What pitfalls do you see, what idea's you have. Or if perhaps something like this is already being worked on somewhere?

---

### Post by vinutux on 2009-10-25
Thanks...........:)

---

### Post by P4man on 2009-10-25
Dont thank me. Im just floating an idea. Thank the people that one day implement it :)

---

### Post by vinutux on 2009-10-25
> **P4man said:**
> Dont thank me. Im just floating an idea. Thank the people that one day implement it :)

mmm... i just say thanks for that info......

---

### Post by P4man on 2009-10-25
No one else to give any ideas or criticism? I guess its a bit too long to read and I should have titled it "ubuntu sucks" :p

---

### Post by P4man on 2009-10-26
I submitted it here as a solution;
[http://brainstorm.ubuntu.com/idea/21938](http://brainstorm.ubuntu.com/idea/21938)

solution n4

Please vote it if you think its a worthwhile idea.

---

