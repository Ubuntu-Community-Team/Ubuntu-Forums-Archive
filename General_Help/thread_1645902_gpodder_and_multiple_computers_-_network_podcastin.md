---
title: "gpodder and multiple computers - network podcasting"
date: 2010-12-15
forum: General Help
---

### Post by NertSkull on 2010-12-15
So I haven't found a great podcatcher for linux yet, but gpodder isn't horrible.  So I've been playing around with it.

But I'm wanting to make it work across my two computers at home and share resources.  So that if I listen to a podcast on one computer, the other one will show its been listened to.  That way I don't have to keep track mentally what I have or have not listened to.  Is this possible?

I already have the two computers set up with NFS so both drives are shared with both computers and are automatically mounted on eachother as network shares on startup.  So the machines have access to eachothers files.

So I was thinking I could just take the download directory and make it the same between the two.  Thats easy enough to do in the gpodder configuration editor.

But is there another "database" I need to sync between the two so it knows what has been played or not?  I figure since most things are file based there has to be a way to just point the second computers gpodder's configuration files to the same files already mounted through the network from the main computer.

Anyone have any idea what I need to get this working?  Thanks

---

### Post by stinkeye on 2010-12-15
gpodder has a built in synchronizing service. Preferences > gpodder.net
Episode states (such as played, downloaded, etc) are synchronized across all devices.

Not sure if this is in the version from the ubuntu repos because I have 
the gpodder ppa enabled. [**_[COLOR="DarkRed"]https://launchpad.net/~thp/+archive/gpodder[/COLOR]_**]("https://launchpad.net/~thp/+archive/gpodder")

Register here: [**_[COLOR="#8b0000"]http://gpodder.net/[/COLOR]_**]("http://gpodder.net/")

---

### Post by NertSkull on 2010-12-15
well thats pretty excellent.  don't know how I missed that.

its not perfect, but it works reasonably well.

Also I pointed the secondary computer's download directory to the same (network share) drive as the main computer.  So it still thinks it needs to download the episode and put it in the database, but after downloading it just replaces what is already there.  So both computers are using the same source file.  Which is nice because I only have the podcasts in one location (although I have to download them twice).

Thanks for pointing me to that, definitely works for about 90% of what I wanted.  Thanks

---

### Post by stinkeye on 2010-12-15
I hven't tested the synchronization yet as I only have the one computer
but I thought if you added the 2 computers to gpodder.net the status of downloaded would synchronize.

---

### Post by NertSkull on 2010-12-15
It does.  At least for me it does.

But you can't add a subscription to one computer and have it show up on the other.

You have to add it on one computer.  Go to the other computer and delete all subscriptions, and then re-add all subscriptions.  At least thats that only way I can figure out on mine.  A minor annoyance, and definitely not something that will stop me from using it.

So I'm happy

---

### Post by stinkeye on 2010-12-15
What if you add the subscription through your gpodder.net page?

---

### Post by NertSkull on 2010-12-16
I don't know.  Their site was unbearable slow and kept giving me server errors so I had to stop using it.  If its like that all the time its pretty pathetic.

But it does appear that you can add shows remotely.  If you add one online, or on one of the computers.  You then can go online and assign that show to one of your devices that sync with the site.  Next time you open that device it asks if you want to add that show.  So thats nice.

But syncing is pretty hit and miss with keeping track of what shows have played.  Again I don't know if its because the site was slow yesterday or if its always that way.  But about half the time if I mark something as played on one computer, it doesn't sync through to the other.

Anyway, its still useful so I plan to keep using it.  It just doesn't feel like a 2.10 type of a program.  It feels like a beta release.  But I feel pretty optimistic with it.

---

### Post by NertSkull on 2010-12-20
Well, after a few days of messing around with it, I've found that the sync doesn't really work for me at all.  If I listen to something on one computer, it doesn't update as being played on the other computer.  Maybe if I was generous I could say 1 out of 20 times it works, but I doubt its even that much.

Hopefully it will get better.  That or I can find something that works better.

---

