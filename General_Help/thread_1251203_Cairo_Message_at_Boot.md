---
title: "Cairo Message at Boot"
date: 2009-08-27
forum: General Help
---

### Post by Quarkrad on 2009-08-27
I have configured Cairo-Dock (ver 2.0.8) to auto launch at Desktop (9.04) boot with OpenGL.  but,I keep getting this message:

**OpenGL allows you to use the hardware acceleration, reducing the CPU load to the minimum. It also allows some pretty visual effects similar to Compiz.  However, some cards and/or their drivers don't fully support it, which my prevent the dock from running correctly. Do you want to activate OpenGL?  (To not show this dialog, launch the dock from the Application menu, or with the -o option to force OpenGL and -c to force cairo).**

My graphics card is  Nvidia 9200 and I have the ver 180 (recommended) driver installed.  I would rather not launch via the Application Menu but have it automatic.  What does the -o and -c options in the last sentence mean in the message above?  What and where do I make these changes?

Thanks.

---

### Post by MickS on 2009-08-27
Cant help I'm afraid but I am interested in the answer because I have a similar problem.


Mick

---

### Post by fabounet on 2009-08-28
go to the menu to add program at startup (you've alerady added Cairo-Dock it seems)
find the Cairo-Dock's entry, edit it, add -o or -c to the command, apply.

if you haven't add it to startup yet, it's even easier : right click on the dock -> cairo-dock -> launch at startup ;-)

---

### Post by Quarkrad on 2009-08-28
Wow - it worked, just as you said (I only added -c after the command).  Much appreciated, many thanks :)

---

