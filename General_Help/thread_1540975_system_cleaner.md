---
title: "system cleaner"
date: 2010-07-28
forum: General Help
---

### Post by nads_da_man on 2010-07-28
hi there....could anyone please suggest any good GUI system or junk cleaners apart from janitor and bleachbit as these two gave me problems with ms office...i would really appreciate..Thanks :)

---

### Post by Cavsfan on 2010-07-28
I use beachbit run as "sudo bleachbit" and I think that may be different from running bleachbit as root.
I can select what I want to have cleaned and am in complete control. You might try that.
It has always worked perfectly for me, but I do not have ms office on here either.
How did you get that to work with wine?

---

### Post by nads_da_man on 2010-07-29
i actually got it to work with crossover it's pretty good...bt one disadvantage i haven't yet found a workaround getting ms access to work bt the rest works quite well..

---

### Post by dino99 on 2010-07-29
> **nads_da_man said:**
> i actually got it to work with crossover it's pretty good...bt one disadvantage i haven't yet found a workaround getting ms access to work bt the rest works quite well..

you need to pay attention on the settings you choose on the left side

---

### Post by Cavsfan on 2010-07-29
> **nads_da_man said:**
> i actually got it to work with crossover it's pretty good...bt one disadvantage i haven't yet found a workaround getting ms access to work bt the rest works quite well..

Are you saying you got bleachbit to work? As "sudo bleachbit"?

> **dino99 said:**
> you need to pay attention on the settings you choose on the left side

If it's bleachbit he's using, will it list microsoft stuff?

---

### Post by Metal Madness on 2010-07-29
> **nads_da_man said:**
> hi there....could anyone please suggest any good GUI system or junk cleaners apart from janitor and bleachbit as these two gave me problems with ms office...i would really appreciate..Thanks :)
The OMG! Ubuntu readers have voted for Ubuntu Tweak as the best cleaner
[http://www.omgubuntu.co.uk/2010/04/best-system-cleaner-ubuntu-tweak-vote.html](http://www.omgubuntu.co.uk/2010/04/best-system-cleaner-ubuntu-tweak-vote.html)
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by bodhi.zazen on 2010-07-29
> **nads_da_man said:**
> hi there....could anyone please suggest any good GUI system or junk cleaners apart from janitor and bleachbit as these two gave me problems with ms office...i would really appreciate..Thanks :)

No, these tools all cause problems if you do not understand your system, they will delete things too aggressively.

In general, Linux does not need to be "cleaned" and if you are going to try you need to understand what you are doing.

Blindly deleting files without such an understanding causes problems on all OS.

See : 

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

[http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

---

### Post by Cavsfan on 2010-07-29
I agree! If I were not paying attention running "sudo bleachbit" I could have lost all my FF favorites and passwords.
That by itself would be a huge loss! But, I like bleachbit and it hasn't failed me yet.
Maybe you need some horsepower to run it though. I don't have the biggest and 
baddest CPU, but I have a core 2 quad and the 4 cpus help. It takes maybe 20 or 
so minutes and that is only if I choose to overwrite the free disk space. 
Otherwise it takes just a few minutes.

And I have removed all other languages except my own, so it makes my system pretty lean afterwards.

I'll have to look into Ubuntu Tweak's way of cleaning...

---

### Post by Cavsfan on 2010-07-29
> **bodhi.zazen said:**
> 

[http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

**bodhi.zazen**, I just wanted to mention that the 3rd link is dead. It says the blog has moved.

---

### Post by WorMzy on 2010-07-29
If bleachbit is a GUI app, which I believe it is, then you shouldn't be using "sudo" to run it in any case. Use "gksu" or "gksudo" instead if you need to run it as root, "sudo" should only be used for command line tools.

I second what bodhi.zazen said, Linux doesn't need cleaning, and if you think it does, then you should do it manually and only if you know what you're doing.

---

### Post by bodhi.zazen on 2010-07-29
> **Cavsfan said:**
> **bodhi.zazen**, I just wanted to mention that the 3rd link is dead. It says the blog has moved.

Too bad ... =(

---

### Post by Cavsfan on 2010-07-29
> **WorMzy said:**
> If bleachbit is a GUI app, which I believe it is, then you shouldn't be using "sudo" to run it in any case. Use "gksu" or "gksudo" instead if you need to run it as root, "sudo" should only be used for command line tools.

I second what bodhi.zazen said, Linux doesn't need cleaning, and if you think it does, then you should do it manually and only if you know what you're doing.

I use sudo because I want it to work from my Home directory. If I use the GUI Bleachbit (as Root) or use  "gksu" or "gksudo" it works from root's Home directory.
So, I will have to respectfully disagree with you on this one.

Running it as "sudo bleachbit" also had most of the desired checkboxes already checked. It remembers them the next time I run it also.
At least it did for me. Running it as root has all of the checkboxes unchecked and I would not want to have to go through over and over and select which ones to check.
I have ran it as "sudo bleachbit" many. many times and it does it's job very well.
I definitely agree that you must pay attention to what is checked before you run it though.

---

### Post by bodhi.zazen on 2010-07-29
> **Cavsfan said:**
> I use sudo because I want it to work from my Home directory. If I use the GUI Bleachbit (as Root) or use  "gksu" or "gksudo" it works from root's Home directory.
So, I will have to respectfully disagree with you on this one.

Running it as "sudo bleachbit" also had most of the desired checkboxes already checked. It remembers them the next time I run it also.
At least it did for me. Running it as root has all of the checkboxes unchecked and I would not want to have to go through over and over and select which ones to check.
I have ran it as "sudo bleachbit" many. many times and it does it's job very well.
I definitely agree that you must pay attention to what is checked before you run it though.

Root's directory should not need cleaning at all =)

If you run graphical applications as root (bleachbit in this case), use gksu (rahter then sudo).

---

### Post by Cavsfan on 2010-07-29
> **bodhi.zazen said:**
> Root's directory should not need cleaning at all =)

If you run graphical applications as root (bleachbit in this case), use gksu (rather then sudo).

I know and I don't want to mess with Root's directory and that is what the application that is in Application > System Tools > Bleachbit (as Root) does.

sudo bleachbit is the only way it uses my Home directory and retains my settings from the last time I ran it. 
gksu bleachbit does not have any boxes checked when it starts, so it would be more labor intensive.

I have heard this mentioned before but, can you tell me what harm using sudo vs gksu can cause.

---

### Post by WorMzy on 2010-07-29
This link sums it up pretty well: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Cavsfan on 2010-07-29
> **WorMzy said:**
> This link sums it up pretty well: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Thanks a lot! I have always wondered about this.

---

### Post by Cavsfan on 2010-07-29
Ok thanks! I'm convinced! I will use gksu on bleachbit from now on and will hopefully think 
more about which to use when root privileges are required.

I would hate to have to do a clean install because of something I did. Been there and done that about twice.
But, at least I'm learning and I love that part.  :)

---

### Post by endotherm on 2010-07-29
I've generally found that "bleachbit as root" cleans the system (wipe pagefile, scrub ram, shred rotated logs, etc), whereas bleachbit as user shreds the users profile MRUs like ff cache and items, flash cookies (that is much of why I use it), application mrus, etc.

---

### Post by Cavsfan on 2010-07-29
> **endotherm said:**
> I've generally found that "bleachbit as root" cleans the system (wipe pagefile, scrub ram, shred rotated logs, etc), whereas bleachbit as user shreds the users profile MRUs like ff cache and items, flash cookies (that is much of why I use it), application mrus, etc.

Me too, but it won't run w/o root, so "gksu bleachbit" it is from now on. I think in preferences you just have to tell it 
where your Home dir. is and check the desired boxes. I just hope that after setting it up once, it remembers the settings.

---

### Post by nads_da_man on 2010-07-29
thanks people for your replies...i'll better first take note what to delete first...;)

---

