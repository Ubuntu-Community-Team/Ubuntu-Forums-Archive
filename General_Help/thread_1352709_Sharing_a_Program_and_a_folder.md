---
title: "Sharing a Program and a folder"
date: 2009-12-11
forum: General Help
---

### Post by mikemikemike on 2009-12-11
I am brain fried after sitting here for 3 hours trieing to figure it out, so please bare with me and ask questions if Im not clear.

I installed a program [http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4329&start=0](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=4329&start=0) with those instructions under account 'mike'. Only thing different is I created a folder in /usr/lib64/PlayStationMediaServer.   The broadcast folder is located at /home/mike/movies


Everything runs great until I try and run the program under 'family'. The program opens but something is not allowing it to run correctly. (Specifically finding the PS3.) Family has full access to network controls. I manually changed every single file in the /usr/lib64/PlayStationMediaServer folder so that others have full control as well. I am baffled.

Thanks in advance,

Mike.

---

### Post by mikemikemike on 2009-12-12
bump

---

### Post by nothingspecial on 2009-12-12
I really have no idea about this but I would try putting the broadcast folder in /media. Then create a group eg ps3. Then make mike and family members of that group.

Make it so that mike owns the folder but ps3 is the group.

Then make the permissions on the broadcast folder so that you can rwx and ps3 can r--.

Just guessing really.

---

### Post by mikemikemike on 2009-12-12
yea thats the issue, already tried something similar. I didn't make a PS3 group but put everyone in the usr group and did exactly what you said. I will be completely honest I love Linux but I think the whole permission thing is a little over-the-top.

---

### Post by mikemikemike on 2009-12-13
bump

---

### Post by tcchris on 2009-12-13
If family cannot access /home/mike/movies then add family to mike group and give group read access to movies folder

---

