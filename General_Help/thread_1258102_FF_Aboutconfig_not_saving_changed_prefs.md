---
title: "FF About:config not saving changed prefs"
date: 2009-09-04
forum: General Help
---

### Post by sports fan Matt on 2009-09-04
When I alter items in about:config they dont stay.  Anyone know why this is?

---

### Post by mikewhatever on 2009-09-04
Can you post the output of **ls -l .mozilla**.

---

### Post by sports fan Matt on 2009-09-04
Sure I can...total 20
-rw-r--r-- 1 office office  335 2009-09-02 14:41 appreg
drwx------ 3 office office 4096 2009-09-02 12:22 extensions
drwx------ 4 office office 4096 2009-09-02 12:56 firefox
drwx------ 4 office office 4096 2009-09-02 12:56 firefox-3.5
drwx------ 3 office office 4096 2009-09-04 13:00 p

---

### Post by Gen2ly on 2009-09-04
Yeah your file and folder permissions got bjorked.  Here's mine on my arch system (they will be different on Ubuntu):

```
ls -l ~/.mozilla
total 28K
drwx------   3 todd users 4.0K 2009-08-26 03:46 eclipse
drwx------   3 todd users 4.0K 2009-08-13 07:06 extensions
drwx------   4 todd users 4.0K 2009-08-13 07:10 firefox
drwx------   5 todd users 4.0K 2009-08-24 23:00 .
drwx------ 170 todd users  12K 2009-09-04 16:52 ..
```

You'll need to change the permissions recursively:

```
chown -R username:usergroup ~/.mozilla
```

Substitute your username and usergroup.  Not sure what your usergroup in Ubuntu is though (someone else should be able to help though).

On a side note, you might want to check permissions on other files/folders in your home directory and see if they didn't get changed too.

---

### Post by sports fan Matt on 2009-09-04
Thats what I was afraid of..Is there any way I can do this without a reinstall?

---

### Post by winotree on 2009-09-04
browser.preferences.instantApply;true  -- What does your setting look like in **about:config** ??

---

### Post by sports fan Matt on 2009-09-04
browser.preferences.instantApply;true is what about:config shows

---

### Post by winotree on 2009-09-04
Well -- hmm.  Reckon I'll dig around some more and see if I can still help...  ;)

You don't think that using your file manager as root would allow you to change the permissions -- like changing one folder at a time.  Just a thought.

---

### Post by mikewhatever on 2009-09-04
If office is your username, there isn't a problem with permission.

---

### Post by sports fan Matt on 2009-09-04
office is my username..Im confused..does that mean there is another reason why as gen said "Yeah your file and folder permissions got bjorked."

---

### Post by sports fan Matt on 2009-09-04
ok..since you say there isnt a problem with that, then why does it seem that the prefs dont stay set..and Would a screenshot help?

---

### Post by Gen2ly on 2009-09-04
Ooop, my bad was thinking your username was soxfan or something else. :)  You might want to check your firefox and firefox 3.5 folders below that and be sure they have the correct permissions though.  If worse comes to worse you can start with new configs and see if that solves the problem.

```
mv ~/.mozilla ~/.mozilla-original
```

---

### Post by sports fan Matt on 2009-09-04
I found something maybe..When I go to my Search>Find all threads..They arent alphabetical by time period.

---

### Post by sports fan Matt on 2009-09-04
And opera shows the same behavior as in the screenshot...Im getting scared..Really DON'T want to lose everything...takes me half a day to put it back in place...

---

### Post by sports fan Matt on 2009-09-04
It also completely wiped everything I had in Firefox..all my customizations...userscripts..after i closed it & restarted..

---

### Post by Vaphell on 2009-09-04
you mean you ran that mv command?
all it did was change the name of FF config directory so FF thinks it has to create brand new one. Check if your changes in about:config are kept now with new profile. Then we will restore your customizations.

---

### Post by sports fan Matt on 2009-09-04
ok, the settings were indeed saved.

---

### Post by sports fan Matt on 2009-09-04
but now everything is hijacked...I give up...I have to reinstall and waste my time again trying to get this right..sorry typing in frustration..Clearlux doesnt install right,...Ive never been this frustrated...The image is supposed to be clearlux but its about half of it haha

---

### Post by sports fan Matt on 2009-09-04
see screenshot

---

### Post by Vaphell on 2009-09-04
open nautilus and copy everything from .mozilla-original (renamed config dir) to .mozilla (new config dir). In case you don't see them in your home dir, show hidden stuff by CTRL+H - they are hidden because they have . at the beginning of the name

restart FF, check if your old profile is fully restored, about:config keeps values.
If everything is ok, you can delete .mozilla-original

EDIT:
only patience can save you :) when did that look change?
and calm down, reinstalling system is not necessary, these are some relatively minor config screw-ups, nothing that cannot be fixed.

---

### Post by sports fan Matt on 2009-09-04
Funny , after a reboot it changed with ClearLUX..and my apologies for earlier..:) I just thought I was gonna have to reinstall everything...

---

### Post by sports fan Matt on 2009-09-04
And as far as I know it got bonkers cause FF is starting with a clean profile...

---

### Post by Gen2ly on 2009-09-05
Might want to look at this sox:

[Restore Settings in a Broken Firefox]("http://linuxtidbits.wordpress.com/?p=858&preview=true")

---

### Post by sports fan Matt on 2009-09-05
Thanks for all the replies guys..I pretty much got it fixed.

---

### Post by Gen2ly on 2009-09-05
sox, might be a good idea to say just how so other users that have this problem know what to do.

---

### Post by sports fan Matt on 2009-09-05
All I honestly did was (after mozilla was corrupted, just deleted the profile and started fresh)  I had everything on pieces of paper for configurations so it was relatively easy to fix.

---

