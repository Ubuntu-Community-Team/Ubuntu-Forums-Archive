---
title: "sudden appearance of Install RELEASE menu"
date: 2011-01-21
forum: General Help
---

### Post by Jechem on 2011-01-21
Hi,

I'm not sure if this is the proper thread.

I recently noticed a menu on Administration>Install RELEASE. I've seen this on LiveCD's Install Ubuntu option but this should not be present when installed on the HDD. I'm not sure when this menu popped up but I am sure this was not here last time I checked. Can anyone shed some light on this? Is this something new that I am not aware of?

Thanks

I have attached screenshot.

---

### Post by Rubi1200 on 2011-01-22
Have a look at Software Sources and make sure the options to upgrade are set to normal releases.

Not suer of this helps, but that is where I would start looking.

---

### Post by Jechem on 2011-01-27
It's set for LTS only so it should not show other releases.

---

### Post by QLee on 2011-01-27
[QUOTE=Jechem]...
I recently noticed a menu on Administration>Install RELEASE. I've seen this on LiveCD's Install Ubuntu option but this should not be present when installed on the HDD. I'm not sure when this menu popped up but I am sure this was not here last time I checked. Can anyone shed some light on this? Is this something new that I am not aware of?
...[/QUOTE]

Did you use remastersys to create a custom live CD? Did you install this system from a remastered system live CD?

---

### Post by Jechem on 2011-01-27
> **QLee said:**
> Did you use remastersys to create a custom live CD? Did you install this system from a remastered system live CD?

I tried remastersys to backup my drive but it did not work properly so I uninstalled it remastersys. This is my default install from the 10.04 LiveCD not from remastersys.

So remastersys was the one that put the menu in the system, how do I delete it? I used remastersys to clean its temp folder so it should have been deleted also right?

---

### Post by QLee on 2011-01-28
[QUOTE=Jechem]..., how do I delete it?...[/QUOTE]

What I would try would be go to the System-->Preferences-->Main Menu app and drill down to the item on the Administration menu and delete it from there or have you already tried that?

---

### Post by Jechem on 2011-01-28
I can delete it from there but it will not delete wherever it is getting the installation from. However from what I see from Disk Analyzer there is no large file which means no ISO is in my system. I'll mark this solved then. I'm just baffled at how this menu got in here. Thanks.

---

### Post by QLee on 2011-01-28
[QUOTE=Jechem]I can delete it from there but it will not delete wherever it is getting the installation from. ...[/QUOTE]

Before you delete it check the Properties, the Command field should show the filepath to the executable.

---

### Post by Jechem on 2011-01-28
> **QLee said:**
> Before you delete it check the Properties, the Command field should show the filepath to the executable.

This is the path from the menu:

ubiquity --desktop %k gtk_ui

It's still like from the LiveCD

---

