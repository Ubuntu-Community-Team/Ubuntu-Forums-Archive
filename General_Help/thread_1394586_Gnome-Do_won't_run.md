---
title: "Gnome-Do won't run"
date: 2010-01-30
forum: General Help
---

### Post by Jabrouwer on 2010-01-30
I have it set to run at startup, but it won't start.  I also can't open it from the main menu.  When I try to run it from the terminal, I get the following error:

(/usr/lib/gnome-do/Do.exe:2584): GLib-WARNING **: g_set_prgname() called multiple times
Could not locate Skype on D-Bus. Make sure Skype is running                            
Could not locate Skype on D-Bus. Make sure Skype is running                            
Could not locate Skype on D-Bus. Make sure Skype is running                            

(/usr/lib/gnome-do/Do.exe:2584): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.



So I ran Skype, but then i got the error:

(/usr/lib/gnome-do/Do.exe:2613): GLib-WARNING **: g_set_prgname() called multiple times
>> SEARCH RECENTCHATS
<< CHATS
Recent Chat [1]: CHATS
>> SEARCH MISSEDCHATS
<< CHATS
Missed Chat [1]: CHATS
>> SEARCH BOOKMARKEDCHATS
<< CHATS
Bookmarked Chat [1]: CHATS

(/usr/lib/gnome-do/Do.exe:2613): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

What does this mean, and what can I do about it?

---

### Post by stinkeye on 2010-01-30
Try disabling the skype plugin in gnome-do.

---

### Post by The_Eddster on 2010-01-31
I've got the same problem, except it's nothing to do with Skype:

(/usr/lib/gnome-do/Do.exe:2791): GLib-WARNING **: g_set_prgname() called multiple times

(/usr/lib/gnome-do/Do.exe:2791): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

The only unofficial plugin I have enabled is 'Remember The Milk', but it doesn't look like it's causing the problem. 
Any ideas on how I can get gnome-do to run?

---

### Post by The_Eddster on 2010-01-31
Actually nevermind, it seems to be working now

---

### Post by stinkeye on 2010-01-31
> **The_Eddster said:**
> I've got the same problem, except it's nothing to do with Skype:

(/usr/lib/gnome-do/Do.exe:2791): GLib-WARNING **: g_set_prgname() called multiple times

(/usr/lib/gnome-do/Do.exe:2791): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

The only unofficial plugin I have enabled is 'Remember The Milk', but it doesn't look like it's causing the problem. 
Any ideas on how I can get gnome-do to run?
You could try delaying the start of gnome-do.
Disable autostart in gnome-do preferences and add your own entry in startup applications with```
sleep 30 && gnome-do
``` 
in the command box.

---

### Post by Jabrouwer on 2010-01-31
Well, I didn't do anything and it appears to be working fine now.

---

### Post by stinkeye on 2010-01-31
Can someone shoot me.......







Ohh never mind, I'm feeling alright now....](*,)

---

