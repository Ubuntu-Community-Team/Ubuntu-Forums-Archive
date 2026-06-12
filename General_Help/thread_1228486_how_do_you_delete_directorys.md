---
title: "how do you delete directorys"
date: 2009-08-01
forum: General Help
---

### Post by stlsaint on 2009-08-01
how can i delete some directorys out of my /usr/local directory that some software made that i dont use anymore!!

---

### Post by MaxIBoy on 2009-08-01
It's better to avoid deleting those manually. Instead, do this:

[LIST=1]
[*]Pull up synaptic.
[*]On the sidebar, click on "not installed (residual config.)"
[*]Hit "ctrl+A" to select all the packages.
[*]Right click and select "mark for complete removal."
[*]Hit "apply" to get rid of all of these files.
[/LIST]
Keep in mind, if you choose to re-install the software later, any configuration you did before will be lost.

---

### Post by stlsaint on 2009-08-01
but i dont want to get rid of all packs...just these two folders that are bothering me!!

---

### Post by MaxIBoy on 2009-08-01
Which programs created those directories? You can find those programs in Synaptic and mark them for "complete removal," even if you previously had them marked for ordinary removal.

---

### Post by Chemical Imbalance on 2009-08-01
sudo rm -rf 'filelocationhere'

Make sure you really don't need those directories though.

---

### Post by Bonster on 2009-08-01
'sudo nautilus' or 'sudo dolphin' if ur on KDE, or use the 'gksu-nautilus' in the synaptic these should give u admins rights and delete those

---

### Post by razorboy5 on 2009-08-01
yup
not the best way but just do

gksudo -u root nautilus

should open up ur root folder and let u do watever u want without
asking for permission or trying to help u be "safe"

however this can be dangerous if u accidentally delete something u actually need

---

### Post by stlsaint on 2009-08-01
thanks to all of you for the support...the gksudo nautilus command did exactly what i needed...thank you again!!

---

### Post by stlsaint on 2009-08-01
> **razorboy5 said:**
> yup
not the best way but just do

gksudo -u root nautilus

should open up ur root folder and let u do watever u want without
asking for permission or trying to help u be "safe"

however this can be dangerous if u accidentally delete something u actually need


just fyi thru research i have found out that simply gksudo nautulis does the same thing just less typing for ya...just fyi!! thanks again tho it all worked out for me!!

---

### Post by jerome1232 on 2009-08-01
Whenever you delete things from a root nautilus session it actually gets moved to the root users trash. So for future reference if you hold shift it bypasses trash and actually deletes it.

Now I would gksu nautilus and clear up your root users trash (don't forget to hold shift)

I believe it's at /root/.local/Trash

---

### Post by stlsaint on 2009-08-01
> **jerome1232 said:**
> Whenever you delete things from a root nautilus session it actually gets moved to the root users trash. So for future reference if you hold shift it bypasses trash and actually deletes it.

Now I would gksu nautilus and clear up your root users trash (don't forget to hold shift)

I believe it's at /root/.local/Trash


already your starting to show my ignorance in this area...so i understand that .local is hidden but whenever i gksuo i cant access any root folders for trash or anything...says "action not supported!"

---

### Post by stlsaint on 2009-08-01
how do you access root trash folder!!! ie ./local

---

### Post by merlinus on 2009-08-01
```
gksudo nautilus
```View/Show Hidden Files (Ctrl+H)

---

