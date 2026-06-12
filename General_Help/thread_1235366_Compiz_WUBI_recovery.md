---
title: "Compiz WUBI recovery"
date: 2009-08-09
forum: General Help
---

### Post by SPARTAN-118 on 2009-08-09
Hi everybody,

I recently tried enabling the "Blur Windows" effect in Compiz-Config Settings Manager.
However, when I did so, my screen became extremely pixelated (meaning, some of the screen was black, some was a jumble of random colours, and just I couldn't see a thing).

Unfortunately, I have a WUBI install (and, if I *do* find a way out of this, I'll try doing a native Ubuntu install on seperate partitions), so I can't go into recovery mode.

Even if I could, what would I do? (First question)

Is there a way to access a Wubi install's files from the Live CD? (again, no recovery mode) (Second question)

Can I back up my files - from within either Windows or the Live CD - and back them up, then uninstall WUBI completely, and create seperate partitions? Is there even a program that allows you (in Windows) to access a WUBI partition? (Third and fourth questions)

All I can tell you is, I'm not doing a clean install without first backing up my files.

SPARTAN-118

---

### Post by CatKiller on 2009-08-09
You can probably just switch window managers to fix it. Alt-F2 will open the Run dialogue. Type in ```
metacity --replace
``` (you might need to do it blind if the display is really bad) and press Enter, which will stop Compiz and run Metacity instead. You should then be able to run CCSM again to disable the Blur plugin.

There are other ways to achieve it, but this is by far the easiest.

---

### Post by SPARTAN-118 on 2009-08-09
> **CatKiller said:**
> You can probably just switch window managers to fix it. Alt-F2 will open the Run dialogue. Type in ```
metacity --replace
``` (you might need to do it blind if the display is really bad) and press Enter, which will stop Compiz and run Metacity instead. You should then be able to run CCSM again to disable the Blur plugin.

There are other ways to achieve it, but this is by far the easiest.

*Smacks himself* I just realized you *can* get into recovery mode in Wubi;
pressing "Esc" after selecting Ubuntu in Windows Boot Manager, which takes you to GRUB. Then you can select the recovery mode option for your kernel.

Now, about your solution....

Every time I press the combination "Alt-F2", my mouse pointer turns into a text pointer, and I *think* I can type in it.

However, when I *do* type in the field to open *anything* (Terminal included) and error sounds (I guess it was smart to enable Sound Effects, so I know these kinds of things, huh?).

I'll try that method, but is there a way to do that via recovery mode -> drop to root/drop to root with networking?

SPARTAN-118

---

### Post by computerkid2000 on 2009-08-09
I had the same problem and no one answered why???

---

### Post by SPARTAN-118 on 2009-08-09
> **computerkid2000 said:**
> I had the same problem and no one answered why???

Try running compiz-check or compiz check (can't as root, I *think* you can press Ctrl+d to become normal user): ```
sudo ./compiz-check
```Or ```
sudo ./compiz check
```I myself will try this, if it works, then we can troubleshoot our problems; see what is wrong.

Thanks to abhilashm8 for this troubleshooting tip.

Also, if you can log in, try Alt+F2 and type metacity --replace or metacity --replace &.
Not sure what the '&' is for, but will try both.
I'll have to do it blind, since I have zero visibility.

EDIT: Great news! I couldn't run compiz check, but, by some stroke of luck, I managed to type "metacity --replace" while completely blind.

Then, after disabling Blur Windows, I again replaced Metacity with Compiz, and suddenly everything just *works* now.

Now, what was I saying about replacing WUBI with a complete install...?
Anybody got a tut for that?

---

### Post by CatKiller on 2009-08-09
> **SPARTAN-118 said:**
> but is there a way to do that via recovery mode

For reference, I'll tell you another way to do it, but it isn't as neat as the method I recommended earlier.

(If you're using the GConf backend) the list of Compiz plugins that are active is stored in the /apps/compiz/general/allscreens/options/active_plugins key. GConf key/value pairs are stored as XML files in ~/.gconf. Whilst gconf-editor is by far the easiest way to manipulate these values, you can also do it by using gconftool or by editing the files directly. Since Recovery mode logs you in as root, you'd need to use su to switch to the problem user to use gconftool, but you can still use nano as root. Something like ```
nano /home/<username>/.gconf/apps/compiz/general/allscreens/options/%gconf.xml
``` would do it. It's possible that you'd also need to check the permissions on that file after you've saved it as root.

> **SPARTAN-118 said:**
> Now, what was I saying about replacing WUBI with a complete install...?
Anybody got a tut for that?

I've never used Wubi, but [this]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") might help.

---

### Post by CatKiller on 2009-08-09
> **computerkid2000 said:**
> I had the same problem and no one answered why???

You posted in a sub-forum that gets a bit less traffic than this one, you didn't post as much detail about your problem's cause, and your writing style makes it difficult to follow what you're saying. I'd imagine that these were all factors, as well as the variable population of the community; you don't know for sure that someone who knows how to fix a given problem will happen to be reading the forums at the time that you post your problem.

We're all volunteers here, and no one has a chance to read and interpret every message that gets posted. Anything that you can do to direct people that might be able to help you to your post and to make it clear in your post exactly what your problem is, and what the cause might be, will pay off. [This]("http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/") might give you some idea of the kind of thing I'm talking about.

---

### Post by SPARTAN-118 on 2009-08-09
Well, thank you very much CatKiller, I will keep everything you've said in a text file somewhere for future reference, in case I or anyone else need help with compiz.

As I said in my Edit, your method of replacing the X Window Manager from Compiz to Metacity worked, and now my system (as far as being able to see what I'm doing) runs without a hitch.

Now, question is, should I mark this thread as solved...?

---

### Post by CatKiller on 2009-08-09
> **SPARTAN-118 said:**
> 
As I said in my Edit, your method of replacing the X Window Manager from Compiz to Metacity worked, and now my system (as far as being able to see what I'm doing) runs without a hitch.

Yeah, I saw that. Just thought you might like the information anyway. Glad you're up-and-running again.

>  Now, question is, should I mark this thread as solved...?

I don't see why not :) Your problem's been solved, as I see it.

---

### Post by SPARTAN-118 on 2009-08-09
Okay, will mark as solved after I ask you this:

CatKiller, with your permission, is it okay if I could create a guide and post links to it, using what you've told me?

I've already made a personal copy for myself, and most of it are direct quotes from you.

Would you like me to send it to you for review?

SPARTAN-118

---

### Post by CatKiller on 2009-08-10
> **SPARTAN-118 said:**
>  CatKiller, with your permission, is it okay if I could create a guide and post links to it, using what you've told me?

Sure. Anything that I've said here is public record, and is largely gleaned from these forums in the first place. I don't think I've said anything especially ground-breaking, but if you're able to distil it into something that's useful for others then by all means do.

---

### Post by SPARTAN-118 on 2009-08-10
Ok, but should I give credit to you, or Ubuntu Forums as a whole? From what you just told me, it seems like giving credit to the Ubuntu Forums would seem wiser, as you originally got this information from here.

---

### Post by CatKiller on 2009-08-10
Don't mind at all.

---

### Post by SPARTAN-118 on 2009-08-10
Alright, marking as [SOLVED].

Thanks for your help!

Erm... how do you change the title for the whole thread? I changed it for the first post, but it didn't appear any different when viewed from General Help.

SPARTAN-118

---

