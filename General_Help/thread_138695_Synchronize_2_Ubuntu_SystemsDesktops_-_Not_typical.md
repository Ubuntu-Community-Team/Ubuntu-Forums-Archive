---
title: "Synchronize 2 Ubuntu Systems/Desktops - Not typical!"
date: 2006-03-02
forum: General Help
---

### Post by Futurama56 on 2006-03-02
I have a laptop and desktop both running Ubutunu as the full time operating systems.  What would be the best way to synchronize the desktops of these computers.  I hate for example, coming home from school after I changed something, or installed an application on my laptop, that it is not mirrored on my desktop.  Yes, I know, that sounds like a big task, but here are my goals.

Sync Evolution:
 There is no reason why my calendar on my desktop is different than that of my laptop.

Sync Application Menus/Look and Feel:
 Backgrounds, icons, locations, and general look and feel should be the same

Home folder/Documents:
 These should mirror eachother.

Firefox:
 Plugins/Bookmarks should all be same, saved pass's, etc...

GAIM:
 Mirrored.  IN particular, the logs.  

I have a very fast pipe, 20mb and 1mb upload, also these machines connect to the same LAN at home, 100mbit.  So syncing should not be an issue of speed.  Any ideas, starting places?  Please be as specific as possible.  Thank you!

---

### Post by jms830 on 2006-03-16
I just wanted to bump this b/c I am very interested as well. I use to use microsoft's Synctoy for this kind of stuff, but now that I'm in Ubuntu, I don't know what to use

---

### Post by Azrael on 2006-03-16
You can just rsync (sudo apt-get install rsync) the directories you want.

---

### Post by walmartshopper67 on 2006-08-14
Hey if you're still reading this - I'm actually just finishing a script for exactly what you want (I have the same problem you do). If you want it, let me know.

---

### Post by honeydew on 2006-08-14
I would appreciate the script as well, Im looking for something with the same functionality.

---

### Post by walmartshopper67 on 2006-08-15
Sure. I'll have it done and cleaned up at some point tomorrow, then I'll post a link here.

---

### Post by walmartshopper67 on 2006-08-16
Well I just kicked myself in the *** whe I said I would post it tommorow. I ran into a few goofy syntax rules. When I  wake up tomorrow, and it will be my first prior.ity =)

---

### Post by jaypeasy on 2006-08-16
You could also try using unison. It's in the ubuntu repositories.

---

### Post by walmartshopper67 on 2006-08-18
Ok, I (finally) finished it. It works, and it's not too terribly complicated. Being a script, it's easy to change (as opposed to a binary). Just untar the file ($tar xfvz Sync50.tar.gz) and follow the directions in the README.txt. If you have any suggestions/comments (constructive please) or want me to email you when I write new versions/make changes my email address and AIM screen name is in the README.txt. Hope this helps someone = )

You can download it at: [ghettonet.no-ip.org/dev/Sync50.tar.gz]("ghettonet.no-ip.org/dev/Sync50.tar.gz")

** One bug I just found - the help (-h) and version (-v) don't work right.:(

---

### Post by bornakke on 2007-01-11
Can't open your tar.gz file - any ideas?

---

### Post by walmartshopper67 on 2007-01-11
Try this here (newer): [http://ghettonet.no-ip.org:8080/~gdev/modules/wfdownloads/viewcat.php?cid=3](http://ghettonet.no-ip.org:8080/~gdev/modules/wfdownloads/viewcat.php?cid=3)

Readme: [http://ghettonet.no-ip.org:8080/~gdev/modules/wiwimod/index.php?page=gnsync+Synchronization+Utility&back=WiwiHome](http://ghettonet.no-ip.org:8080/~gdev/modules/wiwimod/index.php?page=gnsync+Synchronization+Utility&back=WiwiHome)

---

### Post by walmartshopper67 on 2007-01-12
Crap. I just saw that the other link was broken too (go me](*,) ) - it's working now though.

sorry:(

---

### Post by tweedledee on 2007-01-13
> **walmartshopper67 said:**
> Crap. I just saw that the other link was broken too (go me](*,) ) - it's working now though.

sorry:(

If you want a GUI and don't mind java, there are three downloads (maybe more) through sourceforge you can use:
jfilesync
capivara
fullsync

---

### Post by eivind on 2007-01-15
This is something I have been looking for for quite some time. I have a somewhat far future plan to buy another laptop, and I want to keep everything synchronized between my two laptops. It seems this would come in handy. Now, I've read the gnsync readme, and if I understand the purpose of the script right, it is to keep directory trees across two computers exactly the same. With this in mind, let me present the following wish/scenario for you:

For me, the ideal synchronization would be something like unison, but simpler. I simply want to keep /home the same on two laptops, and ideally, I wouldn't have to care what files are on which computer. Better explained:
- If file A exists on one computer, copy it to the other computer, regardless of which computer gnsync is run from.
- If file A exists on both computers, copy whichever is the newest version to the other computer, still regardless of which computer gnsync is run from.

As it is now, I have to specify which computer to copy to and from. That, by all means, is no bad solution, but maybe my suggestion could make the synchronization task simpler, especially if the goal is identical directory trees? I like the gnsync idea, maybe because I am looking for something simpler than unison. Or maybe just because I'm curious.

Thanks for the good work so far! Keep it up!

Cheers,

Eivind

---

