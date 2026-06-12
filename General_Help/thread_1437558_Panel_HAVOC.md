---
title: "Panel HAVOC"
date: 2010-03-24
forum: General Help
---

### Post by Winterbraid on 2010-03-24
Ubuntu has been working great the past few months, problems cropped up occasionally but I found solutions here on the forums. I ran into a problem that needed posting a few hours ago, and while tinkering with PlayOnLinux for starcraft I installed zlib, bzip2, libmpq, and mpq-tools. Soon after, I noticed that I couldn't open text files with edit. I restarted and half of my applets failed to load. I opted to try again, retarted, tried again, and then allowed them to be deleted instead. I restarted in both recovery and regular boot, now here I am.
 
When I click on a panel to add to it, both (top and bottom) panels blink off the screen briefly, then return; I can't add my deleted panel objects. Firefox is crashing too (related?). 
 
Have I downloaded some kind of virus? Has my U build developed schizophrenia? HELP!

---

### Post by bobcollard on 2010-03-24
> **Winterbraid said:**
> . 

Have I downloaded some kind of virus? Has my U build developed schizophrenia? HELP!
No, you have learned a valuable lesson.  When you install an applet or other things, there are some that are not compatible and somethings are removed.  When you allowed this,  (you did allow it when you said you let them be deleted instead) then you are at the mercy of the system.  Back up your home folder and reinstall the system.  Next time use Synaptic Package Manager and pay attention to when it says additional Packages will be added or some Packages may be removed.  We all go through this at least once, some of us many times.  If it ain't broke, fix it until it is then reinstall and do it again.

---

### Post by Winterbraid on 2010-03-25
A valuable lesson sorely learned. But, outside of backing up a reinstalling, relatively painless compared to xp crashes. 

Please tell me more about the home folder backup though - I was intending to restore my settings manually from a text file (e.g. Panel color blue hex ######, text color hex ######, for my personal "Blue Everything" theme etc.), and re-downloading my apps. Also USB for important files (that function still works).

Please elaborate on the home folder characteristics vis a vis my reload. Is it possible that the errors I created will be carried over? 

Also BobCollard, thank you very much for replying.

---

### Post by bobcollard on 2010-03-25
> **Winterbraid said:**
> A valuable lesson sorely learned. But, outside of backing up a reinstalling, relatively painless compared to xp crashes. 

Please tell me more about the home folder backup though - I was intending to restore my settings manually from a text file (e.g. Panel color blue hex ######, text color hex ######, for my personal "Blue Everything" theme etc.), and re-downloading my apps. Also USB for important files (that function still works).

Please elaborate on the home folder characteristics vis a vis my reload. Is it possible that the errors I created will be carried over? 

Also BobCollard, thank you very much for replying.

The general rule is nothing unseen gets backed up.  There are too many configuration files in the "Hidden" files, even in your home folder that can mess things up when you start over.  So, documents, pictures, videos, music, anything you have created or saved yourself gets backed up.  Your settings may be corrupted by whatever the problem is.
When you start adding your new applications do a few at a time and restart.  If you are using Terminal, use "sudo aptitude install" instead of "sudo apt-get install" so if you have to delete a package using aptitude and remove, it will remove all of the dependencies.  The same way when removing in Synaptic, both will show you exactly what is going to be removed and if you find something related to something else say NO.  Good luck and keep me posted.

---

### Post by Winterbraid on 2010-03-26
[B][I]Originally Posted by Bob:

"The general rule is nothing unseen gets backed up. There are too many configuration files in the "Hidden" files, even in your home folder that can mess things up when you start over. So, documents, pictures, videos, music, anything you have created or saved yourself gets backed up. Your settings may be corrupted by whatever the problem is."[/I][/B]

Based on this I figure I know enough about the backup step to avoid trouble (still nice when someone smarter confirms it though). Reinstalled and ran into absurd nothing problem: while setting up my applets I accidentally removed one I meant to keep: the Network Select/Monitor Bars* that is on panel by default. Can't find it in "add to panel," is there another way to restore it (short of re-reinstalling)?

Thanks for the support. Things are getting back to normal I'd say. :D

* it's the network connection utility that is displayed by default on live CD. when connected it shows four blue and/or white vertical bars, taller from left to right. Love it and lost it!

EDIT: Reinstalled, Good Times.

---

### Post by bobcollard on 2010-03-26
> **Winterbraid said:**
> [B][I]Originally Posted by Bob:

"The general rule is nothing unseen gets backed up. There are too many configuration files in the "Hidden" files, even in your home folder that can mess things up when you start over. So, documents, pictures, videos, music, anything you have created or saved yourself gets backed up. Your settings may be corrupted by whatever the problem is."[/I][/B]

Based on this I figure I know enough about the backup step to avoid trouble (still nice when someone smarter confirms it though). Reinstalled and ran into absurd nothing problem: while setting up my applets I accidentally removed one I meant to keep: the Network Select/Monitor Bars* that is on panel by default. Can't find it in "add to panel," is there another way to restore it (short of re-reinstalling)?

Thanks for the support. Things are getting back to normal I'd say. :D

* it's the network connection utility that is displayed by default on live CD. when connected it shows four blue and/or white vertical bars, taller from left to right. Love it and lost it!

EDIT: Reinstalled, Good Times.
Great, congratulations in order.  Please edit your first post and add [Solved] to the Title, that way others may benefit from your experience.

---

