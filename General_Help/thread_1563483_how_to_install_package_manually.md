---
title: "how to install package manually"
date: 2010-08-29
forum: General Help
---

### Post by same.500 on 2010-08-29
Hello; Any one can tell me how to download burn app to usb and then install it to ubuntu manually using dpkg in terminal, because my package manager is not working and i try to install  package using terminal but i failed.

---

### Post by James78 on 2010-08-29
Get a deb file onto your system, switch to the terminal, cd to the directory the deb file is in, and..
```
sudo dpkg -i foobar.deb
```

---

### Post by realzippy on 2010-08-29
You have to download also the dependency packages for your package 
and install them in the right order,or this will fail.From *burn.app*:

*Before you download [I]Burn.app* please keep in mind that you need a couple of other packages to be able to work with *Burn.app*.

For sure you'll need the GNUstep suite (gnustep-make, gnustep-base, gnustep-gui, gnustep-back). You find GNUstep at GNUstep.org.
You also need to download CDPlayer.app and Cddb.bundle from Burn.app's dowload location at Sourceforge. Remember, to always get the latest releases.
Finally, you must have Enrico Sersale's GWorkspace. Otherwise you will not be able to add any data except tracks from an existing audio CD to your CD description.
To download Burn.app go to it's download location at Sourceforge. 
[/I]

BTW,*burn.app* is pretty dead (2005),dunno if it works with newer linux OS.
I highly recommend for CD burning *k3b* since *brasero* never worked right for me.

Generally a manually .deb install is not such a good idea;
what happened to your synaptic (packet manager)?

---

### Post by same.500 on 2010-08-29
I don't know what did happened with my package manager it just till me an error occur and i have to run package manually . I have brasero installed as burning application but it's not workig two.

---

### Post by ex_isp on 2010-08-29
[QUOTE=Generally a manually .deb install is not such a good idea;
what happened to your synaptic (packet manager)?[/QUOTE]

Why is manual .deb package not a good idea?  Encourages command line use, which strengthens cli understanding, which can ONLY be good...

---

### Post by realzippy on 2010-08-29
If you run in terminal:

```
sudo apt-get install k3b
```

What should install k3b,then an error should occur if apt is broken.Can you post this error?

What happens when running:

```
sudo apt-get update
```

??

---

### Post by realzippy on 2010-08-29
> **ex_isp said:**
> Why is manual .deb package not a good idea?  Encourages command line use, which strengthens cli understanding, which can ONLY be good...

All this is true.
But if not so experienced (or new to linux) it is *real* fun to
install manually a dependency tree in correct order.Especially here with *burn.app* where OP had to compile dependencies I guess...
Generally improper use of dpkg may break the package management database (...why is OP's apt broken?)

---

### Post by jerome1232 on 2010-08-29
So the real issue here seems to be getting your package manager back up and running rather than working around it.

An exact error message would be great. Why not try the install command listed above and post the output back at us.

---

### Post by same.500 on 2010-08-29
> **realzippy said:**
> If you run in terminal:

```
sudo apt-get install k3b
```

What should install k3b,then an error should occur if apt is broken.Can you post this error?

What happens when running:

```
sudo apt-get update
```

??
I will answer you  later ,but i want to say that i fixed the synaptic problem before but  unfortunately i can't remember how i did it.

---

### Post by same.500 on 2010-08-29
> **realzippy said:**
> If you run in terminal:

```
sudo apt-get install k3b
```

What should install k3b,then an error should occur if apt is broken.Can you post this error?

What happens when running:

```
sudo apt-get update
```

??
I thing this picture will help.

---

### Post by chaanakya_chiraag on 2010-08-29
> **same.500 said:**
> I thing this picture will help.
Run the command ```
sudo dpkg --configure -a
``` and see what it does.  If that gives you an error, please post it back here.

---

### Post by varunendra on 2010-08-30
Hmm.... I get those "could not resolve" messages only when the urls are dead, or when I'm not connected to them.

Pardon for a totally 'alien' suggestion but are you able to ping archive.ubuntu.com?
```
ping archive.ubuntu.com
```

Or, if your synaptic problem is something like [this]("http://ubuntuforums.org/showthread.php?t=104906"), then I think the solution also should be same as there (post #5):
```
sudo rm var/cache/apt/*.bin
```

Otherwise, I'll wait for the outputs of the commands others already suggested to you (including error message after **sudo synaptic**).

Like others, me too believe that your synaptic problem is more serious than what you originally asked for & fixing it will automatically provide a better solution to your original problem.

However, if you are really 'only' concerned about a manual installation, I think all you need is to follow what realzippy suggested with k3b.

---

### Post by same.500 on 2010-08-30
Any idea? :confused:a

---

### Post by realzippy on 2010-08-30
Run the command in post #11...what happens?

---

### Post by same.500 on 2010-08-30
> **chaanakya_chiraag said:**
> Run the command ```
sudo dpkg --configure -a
``` and see what it does.  If that gives you an error, please post it back here.
Thank you! It works ( i try this command before but i didn't write it will ).

---

### Post by chaanakya_chiraag on 2010-08-30
No problem!  If your problem is solved, please mark this thread as solved by going to Thread Tools ->Mark as Solved.  Thanks! :)

---

