---
title: "Which program should be used to back up entire system and installed packages?"
date: 2012-05-31
forum: General Help
---

### Post by newhere_m on 2012-05-31
I am using ubuntu 10.04 LTS for almost one year. I have also installed several extra packages (using sudo apt-get install). However I have never created backup. How can I create back up of the entire system, including the extra packages I had installed so that (in case of disk crash), using that back up alone I will be able to make a fresh installation of ubuntu 10.04, and the previous packages? (of course the saved files should also be there.) Which program should I use for this job?

---

### Post by Cheesemill on 2012-05-31
You can use Clonezilla to make an image of your HD.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by tea for one on 2012-05-31
I would recommend remastersys for creating an iso of your software.

[http://www.remastersys.com/](http://www.remastersys.com/)

and Grsync (via Ubuntu Software Centre) for backing up data.

---

### Post by Hylas de Niall on 2012-06-02
> **tea for one said:**
> I would recommend remastersys for creating an iso of your software.

[http://www.remastersys.com/](http://www.remastersys.com/)

and Grsync (via Ubuntu Software Centre) for backing up data.

Yep. I've just done precisely this with the system on my desktop machine. It allowed me to save a live version of the whole system, including all the software i had installed, and all the updates and preferences as well.

I did have an issue that it didn't want to install to another machine though. The reason was that the ubiquity front-end wasn't present, and the installer would not run.

There is a way around this though: install ubiquity-frontend-gtk. I found that i couldn't do this from software centre (untrusted source ~ prolly my setup), but by logging out and then logging in to Xterm i could:

'sudo apt-get install ubiquity-frontend-gtk'

which installed it to the live system, then:

'ubiquity'

launched the installer for me, and when finished i could boot into the system.

Beats the hell out of installing fresh and then trying to remember everything i'd installed on the old machine, and getting all those megs of updates.

---

