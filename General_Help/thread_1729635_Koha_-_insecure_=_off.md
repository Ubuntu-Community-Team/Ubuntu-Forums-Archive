---
title: "Koha - insecure = off"
date: 2011-04-15
forum: General Help
---

### Post by matsyuf on 2011-04-15
Hello ,

I set up koha on my computer but accidentally set** insecure** to **off** and now it doesnt ask for login however I would like to turn this back to on.. but i cant how can i do it please help.


yusuf

---

### Post by Rubi1200 on 2011-04-15
> **insecure**

 _Default Value:_ OFF  
 Values:
 
[LIST]
[*]ON = Bypasses all authentication (staff client and OPAC included). Be careful!
[*]OFF = Requires authentication on the staff client and the OPAC
[/LIST]
 IMPORTANT: it is not recommend that this setting is changed after the initial installation of Koha.

[http://koha.org/documentation/manual/3.0/administration/global-system-preferences/admin](http://koha.org/documentation/manual/3.0/administration/global-system-preferences/admin)

Never used this, but according to the documentation you should be able to change settings under Global System Preferences > Admin

Hope this helps.

---

### Post by fred.pierre@smfpl.org on 2011-06-27
I experienced the same problem: While in testing, I switched to insecure mode because some of my test users were not logging in correctly. I hoped to gain more information about the problem, but ended up permanently disabling login. 

This looks like a bug: Once the preference is changed it cannot be switched back to secure login. It says I am not a logged in user, and won't let me pick a library, even though one exists, That means I cannot create a new patron and assign login priveleges. 

Although I manually reset the data field for the insecure preference to "No" (not insecure), the change did not propagate, and I still don't get a login screen, so my system is totally insecure and cannot be put into production.

---

### Post by fred.pierre@smfpl.org on 2011-07-01
The "insecure" setting propagates beyond the database itself.

We restored our Koha database using an earlier MySQL dump, and the setting still read "insecure." However after the restore we did get a login box on the Koha main page. We were able to log in successfully and reset the insecure setting to secure. After that login functioned normally.

This a goofy setting to have available, because while in insecure mode you lose access to your library, and cannot create libraries, patrons or new items. What's the point?

Anyway, we are back up and running!

---

