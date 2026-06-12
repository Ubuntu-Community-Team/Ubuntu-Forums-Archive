---
title: "Permission problems in Paradise. Can't see my administration menu under system."
date: 2010-04-25
forum: General Help
---

### Post by Young God on 2010-04-25
I've got a serious problem.

     Alright so one day I was reading my book called the Linux Bible (i'm in the learning stage of linux and it tells me to go to System-> Administration-> Log File Viewer. So I've browsed through the administration menu before because I needed to from the book and to my surprise the Administration menu isn't there! 
     So no sweat, I right click on the menu and click edit menus. I scroll down to the bottom and click on "System" and it displays the 3 menu items with one checked off which is "preferences" so I simply click to check off administration and bang it works... for 5 seconds! after I clicked it it checked off the box and then like literally 4 seconds after it automatically unchecks it. I tried rebooting logging in and trying it again. Check it, it's checked for 4 seconds, then it automatically unchecks. I'm guessing this happened because somehow may b my login permissions got switched so I can't edit the menu but how would I reverse this so that I do have permissions to edit this menu?
     Someone pleeeeeeeeeaaasee help it's seriously putting me behind in my learning about linux journey.

     Please and Thank You.

Young God
Linux User
Web Developer

---

### Post by quixote on 2010-04-26
Is the Linux Bible Ubuntu oriented?  Or RedHat?  because debian-based systems, like Ubuntu, have some big differences to the RedHat-based ones.  Using commands from one branch in the other could get you in serious trouble.

The problem you describe doesn't sound like a permissions problem.  Then it wouldn't let you do it at all.  I have no idea how to fix the problem you're having, since it involves the hairy process of dealing with gnome, but maybe somebody will jump in who does have a clue.

As for viewing log files, you don't need the GUI to do that, although it is more convenient.  All those logs are under /var/log/*filename*.  So if the book is telling you to check system messages for instance, that's in /var/log/messages which you can look at it in a text editor, or echo to the terminal.

---

### Post by Young God on 2010-04-27
> **quixote said:**
> Is the Linux Bible Ubuntu oriented?  Or RedHat?  because debian-based systems, like Ubuntu, have some big differences to the RedHat-based ones.  Using commands from one branch in the other could get you in serious trouble.

The problem you describe doesn't sound like a permissions problem.  Then it wouldn't let you do it at all.  I have no idea how to fix the problem you're having, since it involves the hairy process of dealing with gnome, but maybe somebody will jump in who does have a clue.

As for viewing log files, you don't need the GUI to do that, although it is more convenient.  All those logs are under /var/log/*filename*.  So if the book is telling you to check system messages for instance, that's in /var/log/messages which you can look at it in a text editor, or echo to the terminal.

so you do'nt know anything about gnome? because you are using kde i'm guessing... on another note why did you choose to use kde instead of gnome? and what pros and cons does kde have , also that it has towards or in comparison to gnome (especially for programming)? I'm fairly new to all this and I transfered over to the linux world in search of a complete OS that rears towards programming advantages cause I want to become a programmer. I've heard mixed reviews for both kde and gnome advantages towards programming, so let me know your thoughts.

Young God
Linux User
Web Developer

---

### Post by quixote on 2010-04-27
Sorry, I wasn't clear.  I use gnome.  It's just that if you want to do any real customizing, they hide the config files nine fathoms deep.  When something goes wrong with the GUI, like your missing Admin menu, it can be a real bear to figure out how to fix it.  If you haven't already, install gconf-editor using synaptic.  Run it, not as sudo, and see whether you can find any settings in there that relate to the problem.  (Running it as sudo would change the GUI root sees, and since you don't login as root in ubuntu, that's not usually useful.)

As for the pros and cons of gnome vs kde, I actually prefer kde.  Their philosophy is that everything is up to the user.  So there's options on top of options to do just about anything.  Plus kde4 is beautiful.  However, getting it all set up the way you want it takes a bit of time and knowhow.  

I started using gnome about two years ago because of one thing: they had an applet for wireless which made it much easier to connect, and it was a struggle in kde.  Since I have to make wireless connections daily, even hourly, that was a big deal.  I haven't switched back yet out of plain inertia.  Gnome's philosophy is that they're going to make everything super simple by deciding for you what you're going to do and not letting you do anything else.  Takes less time at setup, but leads to lots of cursing and muttering later.

---

