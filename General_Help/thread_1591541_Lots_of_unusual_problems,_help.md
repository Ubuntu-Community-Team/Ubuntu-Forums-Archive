---
title: "Lots of unusual problems, help?"
date: 2010-10-09
forum: General Help
---

### Post by Aspiring_Failure on 2010-10-09
I have Ubuntu dual-booted with Windows.

But whenever I start-up the computer, linux is listed *twice*! D:
Right after I installed it, I was told I needed 200+ MB worth of updates, so I got them, and since then, it's been listed twice in the start-up OS booter thingy. But selecting the one with lower numbers doesn't boot up anything, It just stops at a scary screen with a blinking cursor.

AND, since the beginning, I have never been able to browse folders from the places menu, OR access the Start-up Applications manager. Can anybody tell me why and how to fix this?

Ubuntu also seems to slow down randomly, and then speed back up. Starting up applications makes it unusually laggy for the period of time that they're starting up, and I'd like to know if Ubuntu is usually so slow on machines like mine...

AMD Sempron 3000+ CPU @ 1.8 GHZ
811 Mib RAM
ATI Xpress 200 Integrated graphics.

I also get errors every time I try downloading anything. This is all really frustrating and I'd love any help.

---

### Post by UnterUn on 2010-10-09
I presume you've used WUBI?

Anyway backup your data and Go into Windows and go to 'Add and remove Programs' and see if WUBI or something simular appears twice. If so you could try and remove one of them.

OR if it appears only once remove it and reinstall (Back up your data!) and then just don't do any huge updates.

---

### Post by ubunterooster on 2010-10-09
Linux is listed twice because it has multiple kernels "just in case" This part is normal

As for the other errors, I am not sure but your PC should be plenty sufficient.

---

### Post by Aspiring_Failure on 2010-10-09
I installed via a liveCD. Will this still appear under Windows' Add/Remove programs in any way?

Edit: Didn't see Rooster's post. It's good to know that much is normal, but there's not anything I can do about the Places not working? (I'll select a place, say, Home, everything will slow down and the cursor will be busy as if It's loading it, but then it suddenly stops and nothing comes up.)

---

### Post by ubunterooster on 2010-10-09
No, it will only appear if you installed from *inside* Windows

---

### Post by Aspiring_Failure on 2010-10-09
Trying to download software works fine, but somewhere in the un-packaging step I get this error:

installArchives() failed: dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error 

If it helps, at all.

---

### Post by Aspiring_Failure on 2010-10-11
I guess I'm not getting any help on this?

I hate to double-post, but I'm not gonna be able to help myself here, and I don't want this thread to be buried and forgotten. D:

---

### Post by oldos2er on 2010-10-11
Can you run ```
gnome-session-properties
``` in a terminal, and post the output here?

---

### Post by Aspiring_Failure on 2010-10-14
Actually, a few days ago (Before OldOS's reply), I decided to just format the entire partition and re-install it.

Now it works great. I feel silly making a thread over something with such a simple solution, though. I'm not sure why it was going slow, but I think somewhere the installation didn't work right. (The actual installation the first time took well over a few hours, whereas the second time was quite fast.)

Ubuntu is great, by the way. :)

---

