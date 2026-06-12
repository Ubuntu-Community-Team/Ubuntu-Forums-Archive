---
title: "Ubuntu 12.04 Unity Screensaver not working until manually started"
date: 2012-06-06
forum: General Help
---

### Post by Cavsfan on 2012-06-06
Every time I boot up into Ubuntu 12.04 Unity. There is no screensaver. It just goes dark after a preset duration.
I believe I had to install the xscreensaver from Synaptic, which I also had to install.

The problem with the screensaver not starting up at boot may have something to do with this error message I get when I go to System Settings > Preferences > Screensaver. 
I get this pop up box with this error message:
```
The XScreenSaver daemon doesn't seem to be running
on display ":0".  Launch it now?
```Cancel or OK
When I click OK everything works as expected until I logout again.
I have only one monitor. I installed the NVIDIA (post-release updates) (version current-updates) version 295.49 from Additional Drivers.

Any ideas?

---

### Post by Cavsfan on 2012-06-07
No one has an answer to this question? I have been researching and cannot find anything.
I have found where others have had this problem but, there was no solution that fixed my problem.
I removed gnome-screensaver and installed xscreensaver and everything that came along with it.
Also have it set in Startup Manager as ```
xscreensaver -nosplash
```Every time I login, the screen will only go blank until I click on Dash - screensaver and get the error mentioned above.
I click OK and the screensaver works OK until I logout or reboot.

---

### Post by VanillaMozilla on 2012-06-07
Keep searching.  I saw an answer out there somewhere.  It's reportedly possible to do this, and it may even work.

But basically, if the gods at GNU wanted you to have a screensaver, they would have given you one.  As far as I can tell, the problem is that a lot of the screensavers -- especially the best ones, it seems -- lock up the display or have other problems, and no one is expending the effort to fix them.  It may not be worth the effort.

---

### Post by Cavsfan on 2012-06-08
> **VanillaMozilla said:**
> Keep searching.  I saw an answer out there somewhere.  It's reportedly possible to do this, and it may even work.

But basically, if the gods at GNU wanted you to have a screensaver, they would have given you one.  As far as I can tell, the problem is that a lot of the screensavers -- especially the best ones, it seems -- lock up the display or have other problems, and no one is expending the effort to fix them.  It may not be worth the effort.

I read where the Gnome screensavers have not kept up or been maintained. However the xscreensavers have been.
They work just fine once I manually start it a 2nd time and click on OK to start the daemon.
I've also seen many answers as to how to fix this but, none of them worked.
I just noticed that it wasn't even running, even though I set it up to start in Startup Applications with **xscreensaver -nosplash**.
I pressed ALT+PF2 and entered that and it started. I wonder why it is not starting up from Startup Applications.
Hmmmmm.

---

### Post by Cavsfan on 2012-06-08
[ATTACH]219402[/ATTACH]

I fixed it. I simply added another startup command. Don't quite know why it takes two.
But, viola problem solved.

---

### Post by VanillaMozilla on 2012-06-08
> **Cavsfan said:**
> I read where the Gnome screensavers have not kept up or been maintained. However the xscreensavers have been.
No they haven't.  Some of them will lock up the GUI.  Bug reports just languish.  It doesn't seem to happen on every computer, though, so if it works for you, go for it.

Starting twice is not the usual method of fixing the problem, but so what? I guess, if it works.

---

### Post by peterx14 on 2012-07-01
> **Cavsfan said:**
> [ATTACH]219402[/ATTACH]

I fixed it. I simply added another startup command. Don't quite know why it takes two.
But, viola problem solved.

The reason the one you didn't manually add doesn't work is very likely because of a typo in the instructions on a number of websites. See my explanation here:
[http://ubuntuforums.org/showpost.php?p=12067589&postcount=6](http://ubuntuforums.org/showpost.php?p=12067589&postcount=6)

---

### Post by Cavsfan on 2012-07-01
> **peterx14 said:**
> The reason the one you didn't manually add doesn't work is very likely because of a typo in the instructions on a number of websites. See my explanation here:
[http://ubuntuforums.org/showpost.php?p=12067589&postcount=6](http://ubuntuforums.org/showpost.php?p=12067589&postcount=6)

I added both manually.
Trust me it wasn't a typo.
A bug maybe, but definitely not a typo.

---

### Post by jarathomas on 2012-07-02
I was getting the same error message (about the xscreensaver daemon not running). When I followed the advice of peterx14 and changed "Applicaton" to "Application" in the 
/etc/xdg/autostart/screensaver.desktop file, the error message no longer appeared after upon restarting. Thanks, peterx14!

---

### Post by Cavsfan on 2012-07-03
> **peterx14 said:**
> The reason the one you didn't manually add doesn't work is very likely because of a typo in the instructions on a number of websites. See my explanation here:
[http://ubuntuforums.org/showpost.php?p=12067589&postcount=6](http://ubuntuforums.org/showpost.php?p=12067589&postcount=6)

Guess you were correct after all. I just now had time to look at it and sure enough application was misspelled.
I didn't know anything about a /etc/xdg/autostart/screensaver.desktop file.
I just knew that if both startup commands were in Startup Applications, it worked.

---

### Post by Jan Greeff on 2012-07-10
> **VanillaMozilla said:**
> No they haven't.  Some of them will lock up the GUI.  Bug reports just languish.  It doesn't seem to happen on every computer, though, so if it works for you, go for it.

Starting twice is not the usual method of fixing the problem, but so what? I guess, if it works.

My guess is that the second file had the spelling of "application" corrected, that's why it worked.

---

### Post by Cavsfan on 2012-07-10
> **Jan Greeff said:**
> My guess is that the second file had the spelling of "application" corrected, that's why it worked.

This was solved a while back.

---

### Post by 1976MrEMan on 2012-08-04
I have been trying to get xscreensaver to work without having to manually start it each time and i followed instructions from ubuntu forums and now any time i type commands into terminal i get this response:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Why can't i find a straight answer on anything ubuntu-related? Now I will most likely have to start over again from scratch because what am I going to do without the use of terminal?

---

### Post by Cavsfan on 2012-08-05
> **1976MrEMan said:**
> I have been trying to get xscreensaver to work without having to manually start it each time and i followed instructions from ubuntu forums and now any time i type commands into terminal i get this response:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Why can't i find a straight answer on anything ubuntu-related? Now I will most likely have to start over again from scratch because what am I going to do without the use of terminal?

That error generally means that either Update Manager or Synaptic Package manager is running.
Check that first.

Just create an item in Startup Applications:
Name: Screensaver
Command: xscreensaver -nosplash
Commant: Screensaver

See [[COLOR=blue]_this_[/COLOR]]("http://www.liberiangeek.net/2011/10/enable-screensavers-in-ubuntu-11-10-oneiric-ocelot/"). It is what I have used for Precise and Quantal

---

### Post by netgooroo on 2012-09-07
Thanks Cavsfan for posting up and, helping out about this. 

Appreciate it! ;)

---

### Post by Cavsfan on 2012-09-08
> **netgooroo said:**
> Thanks Cavsfan for posting up and, helping out about this. 

Appreciate it! ;)

You are welcome! I did a clean install of 12.04.1 and there is no longer any /etc/xdg/autostart/screensaver.desktop file.

Just adding **xscreensaver -nosplash** to startup commands is all it takes to get a working screensaver back. :wink:

---

### Post by nuclearj on 2012-09-30
> **Cavsfan said:**
> This was solved a while back.

You know what isn't solved?  Why these websites still have the incorrect spelling....

[http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/)

[http://www.ubuntututorials.com/add-screensaver-ubuntu-12-04/](http://www.ubuntututorials.com/add-screensaver-ubuntu-12-04/)

[http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html](http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html)

---

### Post by Cavsfan on 2012-09-30
> **nuclearj said:**
> You know what isn't solved?  Why these websites still have the incorrect spelling....

[http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/)

[http://www.ubuntututorials.com/add-screensaver-ubuntu-12-04/](http://www.ubuntututorials.com/add-screensaver-ubuntu-12-04/)

[http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html](http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html)

This thread was solved by fixing the missing "i" but, I do see what you mean about those 3 links. 
They must be copying and pasting the same exact spelling error "Applicaton" with the "i" missing from Applicat[COLOR="Red"][SIZE="6"]i[/SIZE][/COLOR]on.

However this appears to be an even bigger problem than just those 3 pages.
Google **ApplicatonExec** and many pages appear with that same missing i.

---

### Post by dwitkin on 2012-10-08
> **jarathomas said:**
> I was getting the same error message (about the xscreensaver daemon not running). When I followed the advice of peterx14 and changed "Applicaton" to "Application" in the 
/etc/xdg/autostart/screensaver.desktop file, the error message no longer appeared after upon restarting. Thanks, peterx14!

This worked for me. Thanks!

---

### Post by i_karpas on 2013-01-01
[SIZE=3]Thank u Cavsfan[/SIZE], ur solution may not be elegant but IT WORKS:D

---

### Post by Cavsfan on 2013-01-01
> **i_karpas said:**
> [SIZE=3]Thank u Cavsfan[/SIZE], ur solution may not be elegant but IT WORKS:D

I hope you are not referring to the double startup entries and that you read past that part.

---

### Post by ClientAlive on 2013-02-27
Thanks guys.

Did:

```

sudo less /etc/xdg/autostart/screensaver.desktop | grep Applicaton

```

Saw that there is that misspelled word in there.

Did:

```

sudo nano -w /etc/xdg/autostart/screensaver.desktop

```

Fix the misspelled word then

```

ctrl + x

then...

y

then...

<enter>

```

Restart and all is well.

Thanks

---

### Post by bluepicaso on 2013-03-31
works fine with TWO commands on startup

---

### Post by Cavsfan on 2013-04-01
> **bluepicaso said:**
> works fine with TWO commands on startup

This thread was solved by editing the file below and fixing the mispelled word _***application***_, not by having double startup entries.

```
gksu gedit /etc/xdg/autostart/screensaver.desktop
```

---

### Post by thatstheway on 2013-04-03
Actually, Cavsfan, the plot thickens! Look carefully at your screenshot and you'll see a difference: The first has "No Description," the second has "xScreensaver" as the Description. Wondering if this could be the culprit (for some crazy reason), I added just *one* item in Startup Applications, but I made sure to give it the same Description as you (This goes into the Comment field). Problem solved! But some of the mystery remains. ; )

---

### Post by Cavsfan on 2013-04-03
> **thatstheway said:**
> Actually, Cavsfan, the plot thickens! Look carefully at your screenshot and you'll see a difference: The first has "No Description," the second has "xScreensaver" as the Description. Wondering if this could be the culprit (for some crazy reason), I added just *one* item in Startup Applications, but I made sure to give it the same Description as you (This goes into the Comment field). Problem solved! But some of the mystery remains. ; )

The only thing that matters in startup commands is the command. The name and comment are just text that is not even required except for your own benefit.

Could an admin please close this old resolved thread?

---

### Post by Elfy on 2013-04-04
Closed at Op request.

---

