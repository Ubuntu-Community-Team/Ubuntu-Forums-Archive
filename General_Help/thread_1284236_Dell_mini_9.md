---
title: "Dell mini 9"
date: 2009-10-06
forum: General Help
---

### Post by Dai777 on 2009-10-06
I had a look at my friends mini 9 as she was having trouble updating it.
I had to run dpkg --configure -a just to get updates to install now her mini 9 is chocka it's absolutely full not even room to save a text file let alone anything else. 

Can you tell me why it is full after running some updates surely dell should be running a cut down version of ubuntu.

8.0.4 LTS is what the dell uses.

any help would be appreciated.

---

### Post by Brandon Williams on 2009-10-06
I'm assuming that you friend has a 4GB drive. The standard Dell install uses over 3GB of that (IIRC), so that doesn't leave too much for other things, including package files downloaded for updates.

After updating, make sure that you 'sudo apt-get clean' to get run of the debs for the packages that were just installed. Some mini-9 users with the small SSDs move their home directories onto SD cards to leave more space for the OS.

---

### Post by Dai777 on 2009-10-06
She has a 6GB drive and no I didn't run sudo apt-get clean even so like you say it doesn't leave a lot of room for anything let alone work  she has one file on there a spread sheet. When I looked at it the updater was not working but now after runing updates it's full and i mean full, cannot even save a text file with basic instructions.

Surely there must be a better OS specially designed for net books. one that's not so big but with plenty of stuff in it. I'm sure Ubuntu makes one.

---

### Post by Brandon Williams on 2009-10-06
It must be an 8GB drive if it's not a 4GB drive. They don't sell them with 6GB. I assumed that it must be a 4GB drive because I have two dell minits (a 9n and a 10v), both with 8GB SSDs, and I've never had an update problem with either one. If she just has the base software on it and not much in the way of files, then something else is wrong if you're running out of space on an 8GB drive.

Run 'du -s -k /*' to figure out which base directory is giving you trouble, and then work your way in from there to find the specific part of the directory tree that's using up all the space.

---

### Post by snowpine on 2009-10-06
"Dellbuntu" 8.04 is terrible (sorry). The best thing you could do for your friend is to reinstall using "regular" Ubuntu. This site has some good how-to's: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

If your friend wants a larger drive, I've heard good things about the Runcore drives available at mydigitaldiscount.com (never tried them personally, my factory-installed 8gb is plenty for my needs).

I am also a big fan of CrunchBang linux, which is a stripped down version of Ubuntu. The "lite" version would be a great choice for a Mini 9 with a small drive.

I'm currently running Arch Linux on my Dell mini 9, but I can't recommend it in this case. ;)

Good luck, ask if you have more questions.

---

### Post by Dai777 on 2009-10-10
> **Brandon Williams said:**
> It must be an 8GB drive if it's not a 4GB drive. They don't sell them with 6GB. I assumed that it must be a 4GB drive because I have two dell minits (a 9n and a 10v), both with 8GB SSDs, and I've never had an update problem with either one. If she just has the base software on it and not much in the way of files, then something else is wrong if you're running out of space on an 8GB drive.

Run 'du -s -k /*' to figure out which base directory is giving you trouble, and then work your way in from there to find the specific part of the directory tree that's using up all the space.

I'll try this in the week when I see her next. I can't see how updates would fill her drive up but it has. She is getting on to Dell to see about it as it's still under warranty. I doubt very much that she would let me reformat into another system for her.

---

### Post by milton1 on 2009-10-10
If you are considering reformat, ubuntu netbook remix workes well on the mini 9, leaving more room on the 4GB drive than dell's version. In fact, I am using it right now.

---

### Post by Brandon Williams on 2009-10-12
For an alternate point of view ...

I have not had a good experience on the mini with anything other than Dell's Ubuntu and the lpia version of jaunty. The graphics/flash performance with i386 jaunty was bad enough that I went back to Dell's version (on my mini 10v) and lpia jaunty (on my mini 9n). Other folks running jaunty on the mini are insistent that there is no appreciable difference between the i386 and lpia architecture installations, but that has not been my experience, at least not where graphcis and flash are concerned.

The mini 9n and 10v, as shipped, require a large volume of updates immediately. It should not be enough to cause trouble on an 8GB SSD, but has been known to cause trouble on a 4GB SSD. The output from du would be very helpful in diagnosing the problem. So would output from df.

---

