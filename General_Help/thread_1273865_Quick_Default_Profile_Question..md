---
title: "Quick Default Profile Question."
date: 2009-09-23
forum: General Help
---

### Post by Roasted on 2009-09-23
I understand the Ubuntu "default profile" is /etc/skel.

What do I do exactly? Do I set up an account the way I want, log in as another user, and copy the finalized home directory + hidden files to /etc/skel? Is that how that works?

---

### Post by dcstar on 2009-09-25
> **Roasted said:**
> I understand the Ubuntu "default profile" is /etc/skel.

What do I do exactly? Do I set up an account the way I want, log in as another user, and copy the finalized home directory + hidden files to /etc/skel? Is that how that works?

AFAIK, yes. You probably need to use sudo privileges to copy to that directory - and check the permissions after you complete the copy.

---

### Post by arrange on 2009-09-25
You could still bump into a few problems as the files in your *home* directory may contain references to your user name etc. Check it with e.g. *grep* command or try [this untested method]("http://ubuntu.ubuntuforums.org/showthread.php?t=1271894").

---

### Post by Roasted on 2009-09-25
> **arrange said:**
> You could still bump into a few problems as the files in your *home* directory may contain references to your user name etc. Check it with e.g. *grep* command or try [this untested method]("http://ubuntu.ubuntuforums.org/showthread.php?t=1271894").

Yeah, but I ran into these same issues with XP, and in our case it wasn't a big deal because we set the profile up on administrator, and that local administrator account stays.

I mean after all, I could create a local administrator account, set it up, copy to default (/etc/skel) and then everybody's settings in Ubuntu would be defaulted to administrator, right? Which is the exact issue we had in XP - but in our environment it wasn't a big deal at all anyway.

---

### Post by Roasted on 2009-11-02
So uh... it didn't work.

I copied the entire contents of /home/administrator to /etc/skel and created a new user. I definitely don't have the profile. I don't have anything. I just have the basic theme that any new user would get.

What am I doing wrong?

---

### Post by danastasio on 2009-11-02
nothing is there at all? no themes backgrounds etc.

---

### Post by Roasted on 2009-11-02
> **danastasio said:**
> nothing is there at all? no themes backgrounds etc.

It's like it's the regular profile. Kind of like when you boot to a LiveCD how it's just kind of plain looking, that's how it is. On my "administrator" account, I have the Moomex theme, system monitor in the upper taskbar, different icons in the upper taskbar for quick launch, etc.

Honestly, I'm sure I did something wrong. I just don't know what...

---

### Post by Roasted on 2009-11-04
up :popcorn:

---

### Post by Roasted on 2009-11-09
WOOP! Up. ):P

---

