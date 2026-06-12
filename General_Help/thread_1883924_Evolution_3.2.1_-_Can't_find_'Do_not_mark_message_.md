---
title: "Evolution 3.2.1 - Can't find 'Do not mark message as read when selection changes'"
date: 2011-11-20
forum: General Help
---

### Post by -Shuji- on 2011-11-20
I'm using Ubuntu 11.10.  Not satisfied with Thunderbird, I installed Evolution 3.2.1.  I hate it when Evolution marks the message as read only when the selection changes.  For some reasons, I can't find the option where I can tick 'Do not mark message as read when the selection changes.'  Does anyone know where it is?  Thanks.

Shuji

---

### Post by -Shuji- on 2011-11-20
> **-Shuji- said:**
> I'm using Ubuntu 11.10.  Not satisfied with Thunderbird, I installed Evolution 3.2.1.  I hate it when Evolution marks the message as read only when the selection changes.  For some reasons, I can't find the option where I can tick 'Do not mark message as read when the selection changes.'  Does anyone know where it is?  Thanks.

Shuji

It used to be in Edit - Preferences - Mail Preferences - General tab - Mark messages as read after <n> seconds.  Now it's gone.  Does anyone know where it is in Evolution 3.2.1?

---

### Post by WaltDjr on 2012-01-12
I'm looking for it also.

---

### Post by davemha on 2012-04-20
Did anyone ever solve this?

I saw one answer elsewhere:
...using gconf-editor to edit the key "/apps/evolution/mail/display/mark_seen_timeout".

But when I looked in the configuration editor, there was no entry for evolution under apps.

The devs are going down a bad road hiding configuration options like this.  This is LINUX!  We use it because it's highly configurable!

---

### Post by davemha on 2012-04-20
I figured out how to do it.  The config editor I was using was not gconf.  So either apt-get install gconf-editor or edit the file directly.  The file in question is:
~/.gconf/apps/evolution/mail/display/%gconf.xml

In that file, you should find mark_seen and mark_seen_timeout.  You probably only need to set mark_seen to false - but I also set the timeout to 0.

Have fun!

---

### Post by dcstar on 2012-04-21
> **davemha said:**
> 
........
The devs are going down a bad road hiding configuration options like this.  This is LINUX!  We use it because it's highly configurable!

Evolution is no longer the default e-mail client in Ubuntu, that combined with the ongoing loss of features from moving to Gnome 3 from Gnome 2 makes this sort of thing all too common (unfortunately).

I suppose if you gradually impair out of favour (out of fashion?) apps then people will just have to use the recommended ones, and then you can claim that the "Users have spoken" to justify the change.

---

