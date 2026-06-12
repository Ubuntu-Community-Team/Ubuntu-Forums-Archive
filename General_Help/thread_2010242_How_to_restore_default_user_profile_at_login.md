---
title: "How to restore default user profile at login?"
date: 2012-06-25
forum: General Help
---

### Post by kpatz on 2012-06-25
I tried searching using various keywords and didn't come up with anything, so here goes.

We have a friend who has a laptop currently running Windows 7 and she's not computer savvy at all.  She uses it mainly for web surfing (Facebook, webmail, etc.)  The problem is she tends to mess things up by randomly clicking things, requiring me to pay a visit to fix things up, only to have her mess things up again a week later.  She's blocked images in her browser inadvertently, and she even messed up her Firefox profile so badly I had to delete and re-create it from scratch last time around.  And of course, she gets trojans and spyware from time to time.

So anyway, I'm looking to make her system more fool proof.  Ideally, I'd like a setup where every time the computer is turned on, it reverts to a baseline configuration that works.  That way, if she messes something up, she only has to restart (or log off/on) to bring things back to normal.

I'm thinking of switching her to Ubuntu, hence my post here, but was wondering how to set things up so that her user profile (including all GUI settings, Firefox or Chrome settings, etc.) can be restored to a baseline on every login.  And make it so she can't "permanently" screw things up.  I'm thinking maybe setting things up and then making a copy of her home directory in a safe area (unwritable by her account) and then having that overwrite hers when she logs in.  Is there a way to do this?  I know there's .bash_profile and .bashrc scripts that run when you log in from a console, terminal or SSH but is there a script that can run when logging in from the GUI?  Preferably before the GDM starts up, so I can restore her profile?

Thanks,
KJP

---

### Post by rajan on 2012-07-03
Linux is your best bet for protecting people who don't have much of an idea of how to do it themselves. I've never had a virus problem (knock on wood) yet. 

The difficulty will be to tailor the system in such a way that the things she actually wants to modify are writeable, but the things that are fairly critical are not. In general, linux doesn't allow modification of core/vital pieces of software (the /usr/bin folder, for example). This means that she can probably write and save things on the desktop, which is writeable and doesn't really affect the operation of the system as a whole. 

The various profiles will be difficult though, because they will need to be readable and frequently writeable (chmod 644) so that programs like firefox can do so. This will mean that any user will be able to alter them. I'm not sure that there's any way to get around that, but it's at least much less to worry about. 

good luck!

---

