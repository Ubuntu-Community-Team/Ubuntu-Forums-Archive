---
title: "Unity no longer displaying multiple windows"
date: 2012-05-09
forum: General Help
---

### Post by Fraoch on 2012-05-09
It must have happened with the most recent Unity update.  When there are multiple windows open Unity correctly displays two carats pointing to the program icon in the sidebar as it always has.

I used to be able to switch between the multiple windows by clicking the program button which would bring up the multiple windows in thumbnail form - I'd select the window I wanted.  Now nothing happens when I click on the program.

I'm forced to minimize all the other windows to get the window I want but once I do that I can't get the other windows back again until I quit the current one.

This makes typing webmail which pops up a new window very difficult if you want to consult any other mail message or webpages.

Anything I can try to get this rather essential functionality back?

Thank you.

---

### Post by apochry on 2012-05-09
Do you have the two windows on the same workspace? If they are on different workspaces this will not work by default.
Try to play a bit with the setting in CCSM / Ubuntu Unity Plugin / Switcher.

- Christo

---

### Post by Fraoch on 2012-05-09
> **apochry said:**
> Do you have the two windows on the same workspace? If they are on different workspaces this will not work by default.
Try to play a bit with the setting in CCSM / Ubuntu Unity Plugin / Switcher.

- Christo

Yes, they're in the same workspace.

I've played around with CCSM a bit but CCSM is scary.  Usually any setting I alter crashes Unity or freezes the UI completely...

I'll gingerly poke around it though.  Thank you!

---

### Post by Peter09 on 2012-05-09
in a terminal type
 
```
unity reset
```
 
see if that clears it.

---

### Post by Fraoch on 2012-05-09
> **Peter09 said:**
> in a terminal type
 
```
unity reset
```
 
see if that clears it.

That does clear things up when Unity crashes, thanks.  But I still can't find a setting in CCSM that resolves my issue.

However I notice that the recent Unity update resolved something with ALT+TAB switching.  I've never used ALT+TAB switching before and I tried it.  It cycles through open applications but most importantly if I pause over an application with multiple windows open it allows me to select a different window.

That's a workaround but it would still be nice to be able to do things as before.

---

### Post by apochry on 2012-05-09
You might want to check this out. --> [http://ubuntuforums.org/showthread.php?t=1967822](http://ubuntuforums.org/showthread.php?t=1967822)
The ppa there provides a patched version of unity with added 'dodge windows' and 'maximize/minimize from launcher' behaviors. I guess this will fix your issue, try if you don't mind the min./max. behavior.

Credits go to [isaacj87]("http://ubuntuforums.org/member.php?u=285971").

- Christo

P.S.: Did you upgrade or install clean?

---

### Post by Fraoch on 2012-05-09
> **apochry said:**
> You might want to check this out. --> [http://ubuntuforums.org/showthread.php?t=1967822](http://ubuntuforums.org/showthread.php?t=1967822)
The ppa there provides a patched version of unity with added 'dodge windows' and 'maximize/minimize from launcher' behaviors. I guess this will fix your issue, try if you don't mind the min./max. behavior.

Credits go to [isaacj87]("http://ubuntuforums.org/member.php?u=285971").

- Christo

It was worth a try but it made no difference.  Thanks for pointing that out though.

> P.S.: Did you upgrade or install clean?

It was a clean install but I kept my old /home and it must be using old configuration files...for one thing it already was dodging windows.

I installed completely clean on another machine and it does not dodge but the multiple windows behave as expected.

Maybe I should consider deleting Unity configuration files out of my /home?  I guess I should uninstall and purge all Unity files and reinstall Unity?

---

### Post by apochry on 2012-05-10
> **Fraoch said:**
> 

Maybe I should consider deleting Unity configuration files out of my /home?  I guess I should uninstall and purge all Unity files and reinstall Unity?

I think reinstalling Unity is the right thing to do. This here looks like a nice way to do it
--> [http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity](http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity)

- Christo

---

### Post by Fraoch on 2012-05-10
> **apochry said:**
> I think reinstalling Unity is the right thing to do. This here looks like a nice way to do it
--> [http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity](http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity)

- Christo

Ohh boy - I did all that with absolutely no effect whatsoever?  I logged out and back in to make sure the changes took hold.

I haven't been able to find where the Unity preferences are stored.

---

### Post by Fraoch on 2012-05-10
OK, this is weird - what seemed to bring everything back to normal was a simple unity --reset.  It hung on "setting update "run_key" " but behaviour is back to normal.

Not sure why I didn't think of that because I have heard of the reset command before.  Also I'm surprised this persisted across reboots and restarts.

Marking thread as solved, thank you for your help!

---

### Post by mosaic2s on 2012-08-03
i tried
```
unity reset
```

it went on for some time but did not help. then i tried

> unity --reset

it hung for sometime. I closed the terminal window.

everything is fine now.

---

