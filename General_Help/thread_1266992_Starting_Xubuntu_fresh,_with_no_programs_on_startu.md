---
title: "Starting Xubuntu fresh, with no programs on startup?"
date: 2009-09-15
forum: General Help
---

### Post by ssouthparkk on 2009-09-15
Hello, I am fairly new to Ubuntu/Xubuntu, and I can't seem to figure out how to shutdown this OS without saving the session.  (When I start Xubutu again, all my programs are still opened, Firefox, etc.)  And I also can't get Pidgin to NOT come on on startup.  And anyone that uses IM knows that you don't want to just log in and get caught by your contacts and drug into a conversation. lol

Any help is appreciated.  Thank you.

---

### Post by ssouthparkk on 2009-09-15
Sorry for the double post, but I still can't figure this out.... :confused:

---

### Post by MelDJ on 2009-09-15
tried unchecking in sessions-startup-programs?

---

### Post by ssouthparkk on 2009-09-15
I see some options in there, under "restart style".  I see "Always", "Never", "Immediately", and "If Running".

Is this where you disable them?  Do I just set them to "Never"?

---

### Post by MelDJ on 2009-09-15
are you sure you are in the right place? i am not using xfce now so i cant really say. but i believe the option should be under system-preferences-sessions-startup programs

---

### Post by sisco311 on 2009-09-15
Go to Xfce Menu -> Settings -> Session and Startup and uncheck the *Automatically save session on logout* option.

To start a clear session, delete the files from ~/.cache/sessions

---

### Post by ssouthparkk on 2009-09-15
> **sisco311 said:**
> Go to Xfce Menu -> Settings -> Session and Startup and uncheck the *Automatically save session on logout* option.

To start a clear session, delete the files from ~/.cache/sessions
It is already unchecked.  But I unchecked "Prompt on logout", maybe that will help.  I am trying right now.  Will report back.

---

### Post by ssouthparkk on 2009-09-15
I think I figured out the problem.  It seems that while customizing my panels, I deleted my "Shut Down" button, and I have been turning the PC off by "quitting" (the green running man).  And then shutting down from the logon screen.

Now, I have tried to add it back, but it is not in the list of addable items.  How do I get it back on a panel?

EDIT:

After doing some searching around, I found out this is a common problem with Xfce, so I am just installing Gnome.  Thanks for your help, though.  (Linux can be a pain to use. lol)

---

