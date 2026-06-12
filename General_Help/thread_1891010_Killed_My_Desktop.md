---
title: "Killed My Desktop"
date: 2011-12-04
forum: General Help
---

### Post by NM5TF on 2011-12-04
I was trying to get rid of an extra icon on the Gnome Desktop Panel at top of screen....I right-clicked on the icon, or so I thought, and told it to
delete this panel....it did NOT do what I expected...it deleted the ENTIRE Gnome Desktop Panel and now I can NOT access any app or do anything with it

I had to install a backup copy on a CD to be able to access this forum...

I run Lucid 10.04.3 LTS normally, but this Cd is 10.04.2 LTS so it wanted
install alongside 10.04.3 and did NOT try to repair what I screwed up...

any help would be appreciated to get it back where it was before I "fixed" it...:(

Tom

---

### Post by oldtimer7777 on 2011-12-04
Drop to the recovery console at bootup in Ubuntu.

Drop to the command line in recovery console.

type the command:

sudo apt-get install gnome-session-fallback

And then reboot and change your login session default to Classic Ubuntu. The little gear icon you need to click next to where you enter you password to normally login in LightDM will allow you to change your session.  It should allow you to use a drop down menu at the bottom of the LightDM Login screen to change your session to classic ubuntu desktop environment.   Or you can just add LXDE or some other desktop environment from within recovery console as well. 


> **NM5TF said:**
> I was trying to get rid of an extra icon on the Gnome Desktop Panel at top of screen....I right-clicked on the icon, or so I thought, and told it to
delete this panel....it did NOT do what I expected...it deleted the ENTIRE Gnome Desktop Panel and now I can NOT access any app or do anything with it

I had to install a backup copy on a CD to be able to access this forum...

I run Lucid 10.04.3 LTS normally, but this Cd is 10.04.2 LTS so it wanted
install alongside 10.04.3 and did NOT try to repair what I screwed up...

any help would be appreciated to get it back where it was before I "fixed" it...:(

Tom

---

### Post by NM5TF on 2011-12-04
thanx...will try that.....

---

### Post by carranty on 2011-12-04
Wooowwww, hold on a minute.  Restoring your gnome panel should be a very simple job.  Firstly Ubuntu 10.04 has two panels, one at the top, and one at the bottom.  Did you delete both?

If you've still got the bottom one just right click on it and choose 'new panel'.  If you haven't, open a terminal (right click on desktop > Open Terminal) and type in the below

[INDENT]```
gconftool-2 --shutdown
 mv  ~/.gconf/apps/panel  ~/.gconf/apps/panelBak 
 pkill gnome-panel

```

That'll get them back
[/INDENT]

---

### Post by oldtimer7777 on 2011-12-04
Well he could just uninstall and then reinstall the DE, correct?

sudo apt-get remove ubuntu-desktop
and then
sudo apt-get install ubuntu-desktop 

right?

> **carranty said:**
> Wooowwww, hold on a minute.  Restoring your gnome panel should be a very simple job.  Firstly Ubuntu 10.04 has two panels, one at the top, and one at the bottom.  Did you delete both?

If you've still got the bottom one just right click on it and choose 'new panel'.  If you haven't, open a terminal (right click on desktop > Open Terminal) and type in the below
[INDENT]```
gconftool-2 --shutdown
 mv  ~/.gconf/apps/panel  ~/.gconf/apps/panelBak 
 pkill gnome-panel

```That'll get them back
[/INDENT]

---

### Post by carranty on 2011-12-04
> **oldtimer7777 said:**
> Well he could just uninstall and then reinstall the DE, correct?

sudo apt-get remove ubuntu-desktop
and then
sudo apt-get install ubuntu-desktop 

right?

Quite possibly, I wouldn't like to try it in case it didn't, but I can confirm that the way I mentioned in post #4 definitely does.  I just did it myself and I'm using 10.04.

---

### Post by oldtimer7777 on 2011-12-04
> **carranty said:**
> Quite possibly, I wouldn't like to try it in case it didn't, but I can confirm that the way I mentioned in post #4 definitely does.  I just did it myself and I'm using 10.04.

I think it would be easier to remember the commands for it at the recovery console my way, but yeah. :)

---

### Post by collisionystm on 2011-12-04
orrr... just press ALT + F2 and type gnome-panel and hit enter?

then just right click and add the items back

---

### Post by NM5TF on 2011-12-04
> **oldtimer7777 said:**
> Drop to the recovery console at bootup in Ubuntu.

Drop to the command line in recovery console.

type the command:

sudo apt-get install gnome-session-fallback

And then reboot and change your login session default to Classic Ubuntu. The little gear icon you need to click next to where you enter you password to normally login in LightDM will allow you to change your session.  It should allow you to use a drop down menu at the bottom of the LightDM Login screen to change your session to classic ubuntu desktop environment.   Or you can just add LXDE or some other desktop environment from within recovery console as well.

tried that....did NOT work...got error msg saying it could not find pkg 
"gnome-session-fallback"...:confused:

also tried sudo apt-get install ubuntu-desktop....it told me I already had the latest DE installed....:(

---

### Post by carranty on 2011-12-04
> **oldtimer7777 said:**
> I think it would be easier to remember the commands for it at the recovery console my way, but yeah. :)

I didn't mean to imply your suggestion wasn't valid, my comment was referring more to the fact he'd burnt a recovery CD which really is overkill. The gnome panels can be re-initialised in just a few seconds without even needing to restart.  Apologies if I sounded hostile, as far as I'm concerned the more variety of suggestions the better! :)

---

### Post by carranty on 2011-12-04
> **collisionystm said:**
> orrr... just press ALT + F2 and type gnome-panel and hit enter?

then just right click and add the items back

That doesn't work, deleting the gnome panels doesn't actually kill the process, you have to kill it and then it'll automatically restart, but you need to remove the config file first.  Hence my post.

---

### Post by carranty on 2011-12-04
> **NM5TF said:**
> tried that....did NOT work...got error msg saying it could not find pkg 
"gnome-session-fallback"...:confused:

also tried sudo apt-get install ubuntu-desktop....it told me I already had the latest DE installed....:(

I think [oldtimer7777]("http://ubuntuforums.org/member.php?u=1478375") is thinking of a later version of Ubuntu, I may be wrong but I don't think 10.04 has a gnome-session-fallback.

---

### Post by NM5TF on 2011-12-04
> **carranty said:**
> Wooowwww, hold on a minute.  Restoring your gnome panel should be a very simple job.  Firstly Ubuntu 10.04 has two panels, one at the top, and one at the bottom.  Did you delete both?

If you've still got the bottom one just right click on it and choose 'new panel'.  If you haven't, open a terminal (right click on desktop > Open Terminal) and type in the below

[INDENT]```
gconftool-2 --shutdown
 mv  ~/.gconf/apps/panel  ~/.gconf/apps/panelBak 
 pkill gnome-panel

```

That'll get them back
[/INDENT]

OK, will try this next....

I think that I only deleted the TOP panel....I don't think that "open terminal" showed up when I right-clicked on desktop...will check again

---

### Post by carranty on 2011-12-04
> **NM5TF said:**
> OK, will try this next....

I think that I only deleted the TOP panel....I don't think that "open terminal" showed up when I right-clicked on desktop...will check again

To be honest, even if you still have the bottom panel I would just use the second option (terminal commands), otherwise you'll have to add everything back to the top panel manually.

I may have installed something to give me terminal access by right clicking, just press ALT + F2 if you can't.

---

### Post by NM5TF on 2011-12-04
> **carranty said:**
> To be honest, even if you still have the bottom panel I would just use the second option (terminal commands), otherwise you'll have to add everything back to the top panel manually.

I may have installed something to give me terminal access by right clicking, just press ALT + F2 if you can't.

I did find the bottom panel...told it to open new panel...and yes, I am
having to reload everything manually....:(

are you saying that if I use the above terminal commands it will put everything back as it was before my screw up??? :confused:

---

### Post by collisionystm on 2011-12-04
isnt there a .gnome folder in your home directory that stores your config for the panels?

If you delete that folder Ill bet it would just default your panels.

---

### Post by carranty on 2011-12-04
It will put the panels as they appear on the live cd i.e. panels at the top and bottom, with the applications menu,.clock etc.

Feel free to try it and see, if you don't like the result you can easily revert back to how you are now. My method doesn't delete anything, simply renames your current configuration file to something else. We can restore it if necessary (though we won't need to).

---

### Post by carranty on 2011-12-04
> **collisionystm said:**
> isnt there a .gnome folder in your home directory that stores your config for the panels?

If you delete that folder Ill bet it would just default your panels.

That's exactly what those commands are doing!

---

