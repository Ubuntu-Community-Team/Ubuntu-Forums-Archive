---
title: "Is it possible to permanently lock launcher icons?"
date: 2012-07-12
forum: General Help
---

### Post by AleveSicofante on 2012-07-12
I have installed Ubuntu onto my parents laptop. They are  around their 80s. They manage to remove icons from the launcher  accidentally again and again. I have to put them back manually, only to  find them removed again two weeks later. Of course they'll swear "they  did nothing like that". They also reorder the icons accidentally, so  remote support becomes harder, although that isn't nearly as bad.


  Is it possible to lock icons to the launcher so the user can't remove  them? Just removing the option on the quicklist to unlock the icon  would be fine.
  

Locking its position would be great too.

---

### Post by mc4man on 2012-07-12
There is something in dconf that 'supposedly' allows the locking of individual dconf keys but I've seen no comfirmed instance where this will work in Ubuntu

info page - [https://live.gnome.org/dconf/SystemAdministrators](https://live.gnome.org/dconf/SystemAdministrators)

There are at least 2 threads in ask ubuntu that suggested & implied that dconf lockdown would work, I've not seen it confirmed
Here's 1 where apparently it didn't work based on the OP filing a bug
*though the bug report is a bit 'confused' as I just commented on
 [http://askubuntu.com/questions/132175/how-to-store-a-dconf-key-as-read-only](http://askubuntu.com/questions/132175/how-to-store-a-dconf-key-as-read-only)

Edit: - even if dconf  lockdown worked I'm not sure how it could prevent removing and or moving icons. So at best it may only be the same as below which should reset to desired on every login

In lieu of that you could do something  else though you'd need to test a bit for any unintended stuff
You could create a small startup script that resets the unity launcher's favorites config upon login using a gsettings set command.

This way if anything was changed or moved it would be set back to how you've set it
Pretty easy to do, let me know if need be

---

### Post by Vaphell on 2012-07-13
maybe add a script to autostart, it would set desktop.unity.launcher.favorites in dconf to the predefined value every time user logs in. It wouldn't prevent removing and reordering stuff but would autofix the launcher with simple logout/login. It would be a decent half-measure i think.

edit: i haven't noticed mc4man already suggested such a solution

---

