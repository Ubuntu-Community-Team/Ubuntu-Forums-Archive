---
title: "Strange user - Who or what is it?"
date: 2009-06-28
forum: General Help
---

### Post by VastOne on 2009-06-28
Upon every boot up, I have a terminal window that opens with nothing telling it to open that I have enabled or setup.

The weird thing is, monitor and gkrellem both tell me that I have two users when it is open and if I open another terminal, a 3rd user is now there and on and on.

If I open 10, I would have 10 users....

What bringeth this weirdness?

---

### Post by Yumi on 2009-06-28
I found the same on this morning startup. "Unknown Application" and can not close it.

---

### Post by moster on 2009-06-28
I would say that some library corrupted another and they are multiplying now ...

Honestly, I do not know, but I seen crazy things in corrupted systems. Hope you will solve this up in easy way :)

edit:
look into menu system-preferences-system startup.

---

### Post by Yumi on 2009-06-28
> menu system-preferences-system startup this was my first check. Everything seems normal there. No rouge program instantly recognised

---

### Post by VastOne on 2009-06-28
> **Yumi said:**
> this was my first check. Everything seems normal there. No rouge program instantly recognised

Same here...Nothing out of the ordinary

---

### Post by VastOne on 2009-06-28
> **Yumi said:**
> I found the same on this morning startup. "Unknown Application" and can not close it.

Are you saying it is a terminal session as well?

---

### Post by jerome1232 on 2009-06-28
As far as the users thing, every terminal you have open will count as another user, you open up ten terminals you will probably have 11 users, 1 for your x session, and 1 for each terminal you have open. This is normal behavior.

As far as the terminal opening up on startup I'm not sure, my first thought has already been checked, I still think it's one of your programs set to startup doing it though.

---

### Post by capscrew on 2009-06-28
> **VastOne said:**
> Upon every boot up, I have a terminal window that opens with nothing telling it to open that I have enabled or setup.
Not sure what this is, but some code is spawning a terminal session.> 

The weird thing is, monitor and gkrellem both tell me that I have two users when it is open and if I open another terminal, a 3rd user is now there and on and on.

If I open 10, I would have 10 users....
This is normal.  When a terminal session is started the process is owned by  a new iteration of the original user.> 

What bringeth this weirdness?

The only weirdness is what is asking for a terminal to be launched.

---

### Post by Yumi on 2009-06-28
> Are you saying it is a terminal session as well? 
Sorry, misread your post slightly. Mine is a window with the titel <unknown> and empty as you describe it. But a terminal window would have a heading and a menu bar.

Will open a new threat. Sorry!

---

### Post by VastOne on 2009-06-28
Thank you to Jerome1232 and capscrew for the education on term behaviour.  I will try to find what is starting it and relay it back to you

---

### Post by philcamlin on 2009-06-28
do you have remote desktop enabled?

one time i had it enabled and some guy got in and tried alot of things. i ended up reinstalling.

maybe its just a corrupt library is my guess but it doesnt seem like an intrusion

---

### Post by VastOne on 2009-06-28
> **philcamlin said:**
> do you have remote desktop enabled?

one time i had it enabled and some guy got in and tried alot of things. i ended up reinstalling.

maybe its just a corrupt library is my guess but it doesnt seem like an intrusion

No RD enabled at all. It seems to have started after I went to the 2.6.30 kernel if I recall correctly

I use kernelcheck for all kernel upgrades but have never seen this before using it

---

### Post by michy99 on 2009-06-28
1. Make sure all applications are closed.

2. Go to System->Preferences->Startup Applications.

3. Click Options tab.

4. Make sure 'Automatically remember running applications when logging out' is checked.

5. Reboot.

6. Go to Startup Applications again and uncheck box.

---

### Post by VastOne on 2009-06-28
> **michy99 said:**
> 1. Make sure all applications are closed.

2. Go to System->Preferences->Startup Applications.

3. Click Options tab.

4. Make sure 'Automatically remember running applications when logging out' is checked.

5. Reboot.

6. Go to Startup Applications again and uncheck box.

Worked like a charm....

Thanks

---

