---
title: "OpenOffice.Org bug in Ubuntu Warty"
date: 2005-02-01
forum: General Help
---

### Post by ericsp on 2005-02-01
I think there is a prblem ith the openoffice.org in Warty. I initially believed it was due to my installation. But now I reinstalled everything on two different systems and I get the same error on both. OpenOffice.org cannot handle word documents that contain radiobuttons etc. When I started the Hoary live CD everything worked. Does anyone know about this bug and how to fix it????

Eric

---

### Post by crane on 2005-02-01
Is it a .doc file?
I was having problems reading one as well. I think the formatting of the file had something to do with it.

---

### Post by crane on 2005-02-01
I see a difference in versions.
Hoary --> OpenOffice 1.1.3
Warty --> OpenOffice 1.1.2

So how do we upgrade to 1.1.3 in warty? I don't want to take my main system to hoary yet.

---

### Post by ericsp on 2005-02-02
Yes it was a .doc file with checkbuttons. It works perfect under the window$ version of openoffice.org and also with the live CD. I just tried out upgrading to hoary on an isolated system. Doesn't solve my problem. I am now upgrading openoffice to version 2. I'll let you know what the result is.

Eric

---

### Post by ericsp on 2005-02-02
Openoffice2 fixes the problem of opening. However, the checkbuttons don't work as on the live CD. Does anyone know where to report this issue?

Eric

---

### Post by crane on 2005-02-02
[QUOTE=ericsp]Openoffice2 fixes the problem of opening. However, the checkbuttons don't work as on the live CD. Does anyone know where to report this issue?

Eric[/QUOTE]

Was upgrading an ubdertaking or was it fairly painless?

---

### Post by ericsp on 2005-02-05
The upgrade was painless! Check out [http://ubuntuguide.org/#upgradewartytohoary](http://ubuntuguide.org/#upgradewartytohoary)

I also upgraded openoffice to version 1.1.3 (not version 2!!!) and that solved my problem of the word doc forms..

Eric

---

### Post by macewan on 2005-02-05
can one upgrade to 1.1.3 from 1.1.2 but maintain warty usage?

any noticable differences with 1.1.3 OOo?

---

### Post by crane on 2005-02-05
[QUOTE=macewan]can one upgrade to 1.1.3 from 1.1.2 but maintain warty usage?

any noticable differences with 1.1.3 OOo?[/QUOTE]

I just tried this using apt and synaptic but no luck. Everytime I tried to just upgrade OOo it tried to upgrade everything.

This in my main computer and I don't want to run Hoary until it is stable.
I will look at OOo's website tonight and see if they have any suggestions on upgrading.

---

### Post by ericsp on 2005-02-07
I am not sure whether it is already in the backportproject. Check that one out.

Eric

---

### Post by crane on 2005-02-07
[QUOTE=ericsp]I am not sure whether it is already in the backportproject. Check that one out.

Eric[/QUOTE]


I have backports in my sources.list and it's not sowing there. (warty)

---

### Post by ericsp on 2005-03-07
I would then wait 3 to 5 weeks for the official release of hoary. I find it rather stable, though.

Eric

---

