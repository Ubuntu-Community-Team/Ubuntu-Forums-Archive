---
title: "natty keeps crashing at random"
date: 2011-04-28
forum: General Help
---

### Post by u-noob-tu on 2011-04-28
today i upgraded to ubuntu 11.04. it was a somewhat successful install (see here, another thread i made about the install itself: [http://ubuntuforums.org/showthread.php?p=10731595#post10731595](http://ubuntuforums.org/showthread.php?p=10731595#post10731595)). now, however, unity (or ubuntu itself?) is crashing and going to a blank screen for seemingly no reason. the screen will freeze for about 3 seconds, and then it all goes black, no error text/message or anything. it seems though, that ubuntu is still running, because i was able hit ctrl-alt-f1 and it worked. this has happened about 5 times in the past two hours. its kind of making me worry, what with all this stuff happening in one day.

---

### Post by u-noob-tu on 2011-04-28
*BUMP* the crashing continues to happen, and I'm having to manually turn off my computer.

---

### Post by sdewittofm on 2011-04-29
I'm having a similar problem.  I'm randomly working on something and the screen suddenly shuts down on my laptop and I can't get it to reactivate.  I'm working on a laptop with integrated graphics and I did a clean install of Natty.

---

### Post by u-noob-tu on 2011-04-29
> **sdewittofm said:**
> I'm having a similar problem.  I'm randomly working on something and the screen suddenly shuts down on my laptop and I can't get it to reactivate.  I'm working on a laptop with integrated graphics and I did a clean install of Natty.

my issue may be that i didnt have a clean install (mine gave me an error at the end of the "installing new packages" phase, but for some reason it still installed). i have integrated graphics as well, but if that was the problem i would think we wouldnt be able to do anything. im considering doing a clean wipe and reinstall if the issue persists. its stopped for now, it seems.

---

### Post by sdewittofm on 2011-04-30
I would try using the Ubuntu classic option with Gnome instead of Unity.  I switched yesterday after repeated problems with blank screens and haven't had any problems since.  You can still use compiz to manage other effects without problems, at least I have.  I suspect the problem is that there are still unresolved bugs in Unity that are causing problems.  Disappointing given all the hype over unity.

---

### Post by KegHead on 2011-04-30
Hi!

A couple of things:

1. Update your bios if needed

2. Make sure your video card is compatible

3. Update your system

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

KegHead

---

### Post by u-noob-tu on 2011-04-30
I jus went ahead and reinstalled natty. Fixed everything. Not sure what my install was so troublesome.

---

