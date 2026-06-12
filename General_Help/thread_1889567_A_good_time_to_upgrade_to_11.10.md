---
title: "A good time to upgrade to 11.10?"
date: 2011-12-01
forum: General Help
---

### Post by hardisty on 2011-12-01
I've been running 11.04 and had some trouble when I used the 11.10 beta. When the official release came out, I know many people had bugs. I was recommended to wait until the next upgraded version came out. Is it a good time to jump on to 11.10 yet in terms of stability?

Thanks!

---

### Post by Frogs Hair on 2011-12-01
I have had no problem with my clean installation and there has been many updates since release day . There have been many upgrade difficulties reported here on the forum , but without seeing reports of successful upgrades it is hard to gauge a success rate.

Make sure to remove or disable PPAS and backup your files because you will be moving from Gnome 2 to Gnome 3 . Many things in Gnome 3 are different or removed all together so do some research about the differences before pressing the key !

---

### Post by BC59 on 2011-12-01
I agree with @Frogs Hair that we are in a point that looks all the major bugs are solved.

Two suggestions before the jump:

First, do a fresh install. You will avoid 50% of possible problems.

Second, run a Live CD to see if Ubuntu 11.10 is compatible with your hardware.

Then, Good Luck!

---

### Post by philinux on 2011-12-01
> **hardisty said:**
> I've been running 11.04 and had some trouble when I used the 11.10 beta. When the official release came out, I know many people had bugs. I was recommended to wait until the next upgraded version came out. Is it a good time to jump on to 11.10 yet in terms of stability?

Thanks!

I would personally recommend a clean install including home. I got round the home thing by deleting all .config folders except FireFox evolution and a couple of others.

---

### Post by Bobhuber on 2011-12-01
I've done a LOT of tweaking and the Gnome3 desktop is extremely stable now in spite of me.

---

### Post by hardisty on 2011-12-01
Thanks all. Is a clean install really that necessary instead of Update Manager? I don't think I'm going to have a day that isn't 100% packed with stress for the next two months or so and I really can't add that headache on top.

---

### Post by Bobhuber on 2011-12-01
> **hardisty said:**
> Thanks all. Is a clean install really that necessary instead of Update Manager? I don't think I'm going to have a day that isn't 100% packed with stress for the next two months or so and I really can't add that headache on top.
Yes or add another 100% to the stress level.

---

### Post by hardisty on 2011-12-01
> **Bobhuber said:**
> Yes or add another 100% to the stress level.

But that's more than my daily required intake! I thought Ubuntu was good at updating! How difficult is a full upgrade?

---

### Post by 3rdalbum on 2011-12-01
> **hardisty said:**
> I've been running 11.04 and had some trouble when I used the 11.10 beta.

The first thing I'd do if I was you would be to check the bug reports that you filed when you tested the beta, and see if they have been fixed yet.

If you didn't file bug reports and nobody else ran into your troubles... then there's pretty much no possibility that they've been fixed! Developers release the betas so people will test them AND report bugs.

If you can't handle any more stress, then "better the devil you know". Don't modify your computer until you're out of the stressful situation. Just a note, though: Ubuntu generally upgrades well with few/no issues, as long as you're going from one final release to another. I've never had a release -> release upgrade go badly, only a release -> alpha upgrade.

However, using the Ubuntu 11.10 CD to do an "Upgrade install" is so quick and painless that I'd probably recommend that instead. Basically, you run the Ubuntu installer and choose the "Upgrade" option. It preserves your /home directory, makes a note of what programs you've installed, and then performs a clean install. Afterwards, it automatically reinstalls the programs you had before except for ones in third-party repositories (such as Medibuntu).

Definitely the best way of doing it these days: All the advantages of a clean install (reliability, cleanliness, speed) plus the advantages of a dist-upgrade (/home is preserved, your existing programs are these afterwards). The Upgrade Install option from the Ubuntu 11.10 installer is the way to go.

---

### Post by wolfen69 on 2011-12-01
> **hardisty said:**
> I don't think I'm going to have a day that isn't 100% packed with stress for the next two months or so and I really can't add that headache on top.

If the upgrade *doesn't* go well, you're going to have A LOT more headaches and you'll wish you had done a clean install. Good luck.

---

### Post by ernestj on 2011-12-02
I originally did an upgrade and had so many problems that I went ahead and did a clean install. All my problems went away. Just back up all your files first.

---

### Post by hardisty on 2011-12-03
> **3rdalbum said:**
> The first thing I'd do if I was you would be to check the bug reports that you filed when you tested the beta, and see if they have been fixed yet.

If you didn't file bug reports and nobody else ran into your troubles... then there's pretty much no possibility that they've been fixed! Developers release the betas so people will test them AND report bugs.

If you can't handle any more stress, then "better the devil you know". Don't modify your computer until you're out of the stressful situation. Just a note, though: Ubuntu generally upgrades well with few/no issues, as long as you're going from one final release to another. I've never had a release -> release upgrade go badly, only a release -> alpha upgrade.

However, using the Ubuntu 11.10 CD to do an "Upgrade install" is so quick and painless that I'd probably recommend that instead. Basically, you run the Ubuntu installer and choose the "Upgrade" option. It preserves your /home directory, makes a note of what programs you've installed, and then performs a clean install. Afterwards, it automatically reinstalls the programs you had before except for ones in third-party repositories (such as Medibuntu).

Definitely the best way of doing it these days: All the advantages of a clean install (reliability, cleanliness, speed) plus the advantages of a dist-upgrade (/home is preserved, your existing programs are these afterwards). The Upgrade Install option from the Ubuntu 11.10 installer is the way to go.

SO for the sake of clarification, do I *need* to back up all my files, or would that just be a precaution?

---

### Post by oldtimer7777 on 2011-12-03
> **hardisty said:**
> I've been running 11.04 and had some trouble when I used the 11.10 beta. When the official release came out, I know many people had bugs. I was recommended to wait until the next upgraded version came out. Is it a good time to jump on to 11.10 yet in terms of stability?

Thanks!

Just don't do it.  Stick with 11.04 until the LTS. Do yourselves a favor unless you like being a bug tester. lol

---

### Post by hardisty on 2011-12-03
> **oldtimer7777 said:**
> Just don't do it.  Stick with 11.04 until the LTS. Do yourselves a favor unless you like being a bug tester. lol

I do not know what this means

---

### Post by oldtimer7777 on 2011-12-03
> **hardisty said:**
> I do not know what this means

The Long Term Support version Ubuntu will be here in April... just a few short months away.  Stick with what works for now.  11.10 is still pretty buggy from my recent experience, especially if you want to install something like Gnome 3 Desktop Environment. Unity is great for tiny little notebook computers, I guess.  I'm recommending 11.04 for now if you want a stable system. Just my opinion, btw.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by Larkspur on 2011-12-03
> **hardisty said:**
> I've been running 11.04 and had some trouble when I used the 11.10 beta. When the official release came out, I know many people had bugs. I was recommended to wait until the next upgraded version came out. Is it a good time to jump on to 11.10 yet in terms of stability?

Thanks!

I've been using 11.10 since it came out and, other than some slight issues in the first couple of weeks, it is now as solid as a rock for me.  I'd agree with others on this thread who suggest a clean install.  It avoids any conflicts can could arise (especially due to the move from Gnome 2 to 3) and it's also quicker than an upgrade, in my experience.

To set your mind at rest regarding instability, try searching for your computer model here or on google and see if any issues have been reported, or check out [Ubuntu Friendly]("https://friendly.ubuntu.com/"), which shows the results of tests users conducted on their machines to see how well 11.10 worked.

---

### Post by oldtimer7777 on 2011-12-03
> **Larkspur said:**
> I've been using 11.10 since it came out and, other than some slight issues in the first couple of weeks, it is now as solid as a rock for me.  I'd agree with others on this thread who suggest a clean install.  It avoids any conflicts can could arise (especially due to the move from Gnome 2 to 3) and it's also quicker than an upgrade, in my experience.

To set your mind at rest regarding instability, try searching for your computer model here or on google and see if any issues have been reported, or check out [Ubuntu Friendly]("https://friendly.ubuntu.com/"), which shows the results of tests users conducted on their machines to see how well 11.10 worked.

I was using Ubuntu 11.10 since Beta 2.  I installed Gnome 3 PPA because that is what I want for my desktop environment.  I don't like many things about Unity in general..  For example:

 [http://www.cc-c.de/german/linux/ubuntu.php](http://www.cc-c.de/german/linux/ubuntu.php)
 and this
 [http://www.zdnet.com/blog/perlow/why-ubuntu-1110-fills-me-with-rage/19103](http://www.zdnet.com/blog/perlow/why-ubuntu-1110-fills-me-with-rage/19103)

To be perfectly honest, I don't know if I am going to install the LTS when it rolls out in April myself, if it keeps getting more bloated, and dumbed down.  I will probably go with Debian if it gets anymore limited and inflexible for what I need it for.  If all I was going to do is surf the internet on a tiny little 10 inch screen device Unity would be perfect for that task.  However I do production work, programming, writing, video editing, on multiple monitors, and I like to have a nice clean desktop without that menu stuck to the left side of my screen always popping in my face each time I need to work with a window somewhere else on the screen in that general vicinity.  I miss the GTK2 themes I had before that were clean and simple. I miss the way I could enable Compiz quickly and easily in Appearance. I really hope Gnome 3 is more tightly integrated, or they revamp Fallback ubuntu to be more like Gnome 2 was when it comes to having a more flexible old school desktop environment.  Just read the above two links to understand what people need sometimes.  When they first rolled out Unity I was thinking it was only as a replacement for the Ubuntu Remix version of Ubuntu, but they made it default DE for Ubuntu for now.

I'm back with 11.04 because I can't deal with the changes yet.  I know other users are telling me, change is "good"..  I don't know at this point.  I miss the flexibility that the old Gnome 2 so elegantly provided me.

[URL="http://www.zdnet.com/blog/perlow/why-ubuntu-1110-fills-me-with-rage/19103"]
[/URL]

---

### Post by hardisty on 2011-12-04
Well, I booted from my 11.10 flash disk but it appears that it still has the problem in which the backlight if off on startup, and needs to be turned up manually every time. Chances are this is just for certain laptops similar to mine (HP Pavilion G6) but I've done more googling and yet to find a solution. It's a small annoyance, but I think it's enough to deter me from 11.10 until it's fixable.

---

### Post by 3rdalbum on 2011-12-05
Report it as a bug, otherwise no developer will ever know there was a problem.

I'd also like to add, just in general to others in the thread, that "waiting until 12.04" is a bit like the Fool's Errand. Just because it's an LTS doesn't mean that it's less buggy than 11.10. However, it *might* be if people test it BEFORE it gets released.

---

