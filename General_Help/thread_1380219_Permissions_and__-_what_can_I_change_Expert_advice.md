---
title: "Permissions and / - what can I change? Expert advice needed."
date: 2010-01-13
forum: General Help
---

### Post by mactece on 2010-01-13
I've got two kids (6 & 7) who use the computer. I want to stop them doing any damage. When they are in home they can get up to / and see all the files. I've no idea if they can change stuff but I'd prefer if they were discouraged. The big idea - change the "other users" access to "none" in / and restrict home folder access to the user only. I think this means that once they leave their home folder everything they see will be barred to them! Easy to do but what are the consequences? Do you know?

Many thanks if you can...

---

### Post by pastalavista on 2010-01-13
No user can see any other user's home directory unless/except they have specifically shared folders and no user can alter any system files without being in the root users group which is automatically reserved for the primary user.

If you'd like to be extra sure they can't mess up, use the built-in 'Guest Session'. They can't get into anything with it... except the internet

---

### Post by studmf on 2010-01-13
If I'm not mistaken I believe the newest version of Ubuntu Tweak helps to change permissions.

---

### Post by mactece on 2010-01-13
Thanks for the prompt reply. I need a bit more than help, though.

I've just today set up a pc for my kids and installed karmic and it has set all the directories on the system to allow "access" to "other" users. So I'd have to disagree although before today I would have said you were right. Is this a new protocol for karmic? I haven't done anything adventurous with the initial setup so I guess it must be.

Despite that I'm 95% confident my kids can't do any damage. But I'd like to be sure they are sandboxed and discouraged from exploring the system in case they decide to do that one day when I'm logged in but away from the pc (resuing the other one, for example).

Any more thoughts?

---

### Post by lykwydchykyn on 2010-01-13
You cannot make / unreadable, or the system will break.  All the program files and settings are outside their home directory, and must be readable in order to be run.

They are, by default, not writable however, so you don't need to worry about them messing with anything.  I doubt they're going to get much out of looking at /etc/ or /usr.

Are you mainly concerned about them getting into your files?  Or system files?  I'm not clear on that.

---

### Post by mk1w86 on 2010-01-13
As long as the account cannot use sudo normal users cannot edit system files.

---

### Post by doas777 on 2010-01-13
as a general rule, never change permissions in / without having a very specific reason for doing so. 

basically there is no good reason to try to lock them down too much further than the defaults. just make sure that each home is isolated to it;s user, and that is that.

---

### Post by mactece on 2010-01-13
Thank-you everyone. I'll just have to accept that they can go wandering but that they can't do any harm. I've locked the kids out of the other users in the home area so they can't see in there or mess with each others stuff so that should do it.

For those that are interested I used pessulus lockdown editor to restrict what they can do in their own area.

SOLVED

---

