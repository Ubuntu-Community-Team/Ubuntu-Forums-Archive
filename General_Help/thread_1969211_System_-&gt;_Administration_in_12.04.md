---
title: "System -&gt; Administration in 12.04"
date: 2012-04-29
forum: General Help
---

### Post by gr8 on 2012-04-29
How do I get to "system -> administration" in 12.04. It doesn't exist anymore in 11.10 or 12.04.

---

### Post by Zukaro on 2012-04-29
All the system settings should be under the system settings list (there should be a gear with a screwdriver or wrench in the launcher; click that and you'll get to the systems settings spot which should include administration settings).  Something like that.

---

### Post by CharlesA on 2012-04-29
Hit dash home and type in system settings.

That should get you there.

---

### Post by gr8 on 2012-04-29
Thanks for the help guys. You are both correct and those two things will get me into the system settings. Unfortunately the "Administrator" icon is no longer available. It used to be on older versions of Ubuntu but it has been removed in Unity. How do I get to these settings now?

---

### Post by CharlesA on 2012-04-29
The administrator menu had stuff like login, update manager and the like, right?

I don't have a gnome 2 box in front of me atm.

---

### Post by audiomick on 2012-04-29
If you click on the Ubuntu symbol at the top left of the screen, you get the Dash. All applications are available there. 

Here, it is possibly easier if you look at this.
```
https://help.ubuntu.com/12.04/ubuntu-help/unity-dash-intro.html
```

That was linked from here
[https://help.ubuntu.com/12.04/ubuntu-help/index.html]("https://help.ubuntu.com/12.04/ubuntu-help/index.html")

---

### Post by gr8 on 2012-04-30
I can try administrator in the dash but the app has been removed by Canolical. The application "Administrator" that used to be in the system settings is gone in Unity. Does anybody know how to get it back? If not, what is the equivalent?

---

### Post by pqwoerituytrueiwoq on 2012-04-30
administration was a sub menu not a app 
which program do you want in the menu?

---

### Post by gr8 on 2012-04-30
Basically I got the following printer error and Ubuntu is telling me to

"Enable the 'Publish shared printers connected to this system' option in the server settings using the printing administration tool. To start this tool select System->Administration->Printing from the main menu."

But I can't select this in Unity. What do I do?

---

### Post by kurt18947 on 2012-04-30
> **gr8 said:**
> Basically I got the following printer error and Ubuntu is telling me to

"Enable the 'Publish shared printers connected to this system' option in the server settings using the printing administration tool. To start this tool select System->Administration->Printing from the main menu."

But I can't select this in Unity. What do I do?

If you're looking for the app I think you're looking for, there are a couple ways.  In unity, I tap the 'windows'(super) key then type "printing".  I favor gnome-shell over unity and the 'printers' app is weak.  I open a terminal and type "system-config-printer".  There are two functions I miss from gnome 2 to gnome 3.  Printer administration is one, users and groups is the other.  It's possible to get both back, just takes some google time.

---

### Post by koolkatkiwi on 2013-02-26
> **kurt18947 said:**
> If you're looking for the app I think you're looking for, there are a couple ways.  In unity, I tap the 'windows'(super) key then type "printing".  I favor gnome-shell over unity and the 'printers' app is weak.  I open a terminal and type "system-config-printer".  There are two functions I miss from gnome 2 to gnome 3.  Printer administration is one, users and groups is the other.  It's possible to get both back, just takes some google time.

Thanks for this. I have been Googling and searching for ages on how to cancel a corrupted print job - such a simple matter in the past. Finally found this thread that tells me how to access System-Administration-Printers. I'm using the Classic Gnome Desktop because Unity is crap (IMO). WHY do they take away great functionality, just to muddy up things and make a person search for ages about how to do a simple job?

---

