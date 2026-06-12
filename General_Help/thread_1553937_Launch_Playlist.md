---
title: "Launch Playlist"
date: 2010-08-15
forum: General Help
---

### Post by bug67 on 2010-08-15
Hey all you experts,

I'm trying to set up the Alarm Clock app to automatically launch Rhythm Box and begin playing a specific internet play lists I have there.  I have one template set up to launch Pandora and I could probably get it to launch Rhythm Box but, how do I get it to launch Rhythm Box *and* begin playing a certain radio station playlist?  Thanks.

**_EDIT_**:

I imagine this can be done with a shell script or some such but, I am clueless in that regard so, thanks again for any help.

:popcorn:

---

### Post by bug67 on 2010-08-16
Bumping to hopefully get an answer or be directed as to where to go to get one.):P

---

### Post by jv2112 on 2010-08-16
-Write Script

-Set as Cron Job


> 
!# /bin/bash

rhythmbox [http://radio.foo.com/channel.pls](http://radio.foo.com/channel.pls)




---

### Post by bug67 on 2010-08-16
Is that something I copy and paste to the terminal or what?  Where do I save this so I can use it over and over?  You are assuming I have a clue what to do with the info you gave me.  Thanks though.  I do appreciate it.  ;)

---

### Post by jv2112 on 2010-08-17
Yes.

Step 1->

Open Gedit 
copy paste
Save As "Script"

in Terminial 

chmod a+x Script

Step 2 -->

in Terminal 
crontab -e

check out link below for options

[http://adminschoice.com/crontab-quick-reference]("http://adminschoice.com/crontab-quick-reference")


Hope this helps

---

### Post by bug67 on 2010-08-17
jv2112,

No.  This is all way over my head.  Thanks for trying though.

On my Mac, I just add the radio station's .plst to start up items.  Then, I can set the computer to start up at whatever time I want.  Bam!  Computer boots, iTunes launches, .plst begins to play

I have no idea what to do in order to follow your directions.  You pointed me to a web site that had a bunch of code stuff that is way over my abilities.

In the application "Alarm Clock" I am able to set Pandora to launch by adding its path to "command" in the Alarm Clock GUI.

I thought I might be able to do the same thing by setting the radio station's .plst to default open with Rhythm Box and then add the .plst's path to the run command option in Alarm Clock.  Sounds simple and logical, right?  Well, it didn't work.  

There's also an option to run a script but, I don't know how to write scripts and I don't have time to pour through a web site whith thousands of options and hopefully, come away with something that does what I want.  Again, thanks for trying.  I'm sure it all makes perfect sense to you.  Maybe I shoulda posted this in the "I'm a complete n00b" forum.

---

### Post by bug67 on 2010-08-17
Now we're talkin'

[http://nedrebo.org/code/rhythmbox/alarm_clock/](http://nedrebo.org/code/rhythmbox/alarm_clock/)

**_EDIT_**:

Apparently,  This plugin isn't available at the above listed url any longer.  However, upon further review, I found this post with a zip file made available.  Works like a charm!  :)

[http://ubuntuforums.org/showthread.php?t=1396652](http://ubuntuforums.org/showthread.php?t=1396652)

---

