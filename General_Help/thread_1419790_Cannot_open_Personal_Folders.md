---
title: "Cannot open Personal Folders"
date: 2010-03-02
forum: General Help
---

### Post by masternosaj on 2010-03-02
Hello all,

I had such good luck fixing my last problem here, I thought this would be the first place to come for my current problem.

Last night I was transferring some files from my external USB hard drive onto my laptop (running 64bit Karmic), and my laptop froze up for whatever reason.  Everything on the screen stopped and the Scroll Lock and Caps Lock LEDs began flashing.  Not knowing anything else to do, I hard booted off with the power switch.

At this point, I was concerned if anything on either hard rive would be damaged.  I booted my laptop back up, and all seemed well until I trued to open my Documents folder.  For some reason, Ubuntu will no longer open any folders at all.  I can't click on Computer, Documents, Music, etc.  When I do, a tab opens in the taskbar that says Opening folder.  It stays on screen for about 20 seconds, and then goes away and the folder never opens.  The weird part is if I open gEdit and try to load a file, I can see and get to everything.  It doesn't make any sense.

I am at work today, but I will try to answer any questions I can about the situation.  I am a Linux newbie, but I'll try to answer anything I can.  Thanks!

---

### Post by zeroseven0183 on 2010-03-02
Sounds like you have a problem with the file manager. I want you to try this and see if it fixes the problem. 

1. Open **Synaptic Package Manager** from **System** > **Administration**
2. Type your password when asked
3. search for "nautilus" in the Quick Search bar
4. select "nautilus" from the results, right-click on it and select **Mark for Reinstallation**
5. click **Apply**

What happen after reinstalling **Nautilus**?

---

### Post by masternosaj on 2010-03-02
That's an idea.  I will try it when I get home.  Thanks for the suggestion.

---

### Post by masternosaj on 2010-03-02
I tried to reinstall nautilus, but this did not solve the problem.  I still cannot open any folders.  Any other ideas?

---

### Post by masternosaj on 2010-03-02
Well, I didn't actually solve the problem, however, I just booted from the CD and backed up everything and then reformatted.  Oh well!

---

