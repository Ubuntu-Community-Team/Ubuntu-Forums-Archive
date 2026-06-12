---
title: "can not read ICEauthority? GNOME can't start"
date: 2004-10-21
forum: General Help
---

### Post by sfw5000 on 2004-10-21
Hi,

Logging in sometimes I get the GNOME failed to start message ("your session only lasted less than 10 seconds...") the error said that it could not read /home/sam/.ICEauthority

So, I log into a failsafe terminal and create an empty file called .ICEauthority in my home dir. Then, gnome can start in regular mode just fine. But when I restart the whole thing happens all over again. What the heck is this ICEauthority file?

---

### Post by triad169 on 2004-10-21
I think you will find answer here:

[http://www.ubuntuforums.org/viewtopic.php?t=1238&amp;highlight=iceauthority](http://www.ubuntuforums.org/viewtopic.php?t=1238&amp;highlight=iceauthority)

---

### Post by sfw5000 on 2004-10-22
Thanks! Unfortunately, looks like links are broken with the switch to the new forums -- do you remember which forum that post was in? I can't seem to find it (Searching for iceauthority doesn't seem to work)

Thanks again,

Sam

---

### Post by flygmaskin on 2004-10-22
Try doing "sudo chown sam /home/sam/.ICEauthority"

Atleast that worked for me.

---

### Post by sfw5000 on 2004-10-22
Thanks flygmaskin -- I think that will do the trick.

Does anyone know what causes the permissions of that file to change? It's happened two times now, and I'm wondering if there's anything I can do to prevent it.

Thanks,

Sam

---

### Post by mikew777 on 2004-10-23
[QUOTE=sfw5000]Thanks flygmaskin -- I think that will do the trick.

Does anyone know what causes the permissions of that file to change? It's happened two times now, and I'm wondering if there's anything I can do to prevent it.

Thanks,

Sam[/QUOTE]

Sam
If You are trying to burn CD's with K3B and not using this format that I listed in another post it will happen everytime if it is another program that is causing it I haven't run into it yet.
You can write in Ubuntu if you download K3B from universe. Then when you want to burn go to, Applications, System Tools, Root Terminal. Type in K3B then just wait till K3B comes up and it should have found all your drives, then burn away. You will get a error message that cdrdro wasn't found, you can disregard that message or go ahead and install it and you will not get the error. The burn will work either way. I can burn CD's and DVD's with no problems. If you don't use the above Root Terminal as suggested when you boot out you will no longer be able to log back in as it will change your ICE/.authority file. You then have to edit that file in a terminal B4 you can get back in. Doing it the way I have discribed you will have no problems. Hope this helps...

---

### Post by sfw5000 on 2004-10-24
Thank you so much! That's exactly the problem!

---

