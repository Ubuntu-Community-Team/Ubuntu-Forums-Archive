---
title: "How do I stop Update Manager from installing unwanted material."
date: 2011-01-26
forum: General Help
---

### Post by wallaroo on 2011-01-26
In order to keep my system clean, normally if Update Manager wants to update a package I don't want or never use, I use this as a trigger to first go to Synaptic Package Manager and de-install the unwanted package, then refresh Update Manager and continue with the wanted updates.

However when it wants to install something completely new that clearly I don't want or need, how do I tell Update Manager to permanently remove it from the update list?

---

### Post by garvinrick4 on 2011-01-26
> **wallaroo said:**
> In order to keep my system clean, normally if Update Manager wants to update a package I don't want or never use, I use this as a trigger to first go to Synaptic Package Manager and de-install the unwanted package, then refresh Update Manager and continue with the wanted updates.

However when it wants to install something completely new that clearly I don't want or need, how do I tell Update Manager to permanently remove it from the update list?Are you talking about the apps that come with Ubuntu's install?

---

### Post by garvinrick4 on 2011-01-26
This will give you all the packages installed in your system it will show
up as a file in Home.
How do you know if a package you do not want is a dependency on a package
you need? Are you that short on space to take that risk? Any which way here
is all installed package's you can sudo apt-get remove (package name) any one
you want. Good luck to you. Would not advise to do this:

```
sudo dpkg --get-selections > installedsoftware
```## My advice would be to use:
```
sudo apt-get autoclean
```

---

### Post by wallaroo on 2011-01-26
Thanks for the reply garvinrick4,

Yes I'm familiar with the utilities you mention and I use them too.

But its more about controlling the Update Manager, I examine each and every update presented and satisfy myself about why the update is necessary (its my job), particularly the Security updates, and several turn out to be just adding to the clutter. (Remember these updates are coming from many different sources). 

Even that monster 'Windows' allows the user to tell it's update manager to stop pestering  them about updates they don't need, so I expected the same courtesy from the Ubuntu update manager.

---

### Post by wallaroo on 2011-02-05
Last chance for anyone to offer a way to control the Update Manager. Is there some way to tell Update Manager to permanently disregard a particular update? or are we to be forever pestered to install unwanted stuff?

---

### Post by 3rdalbum on 2011-02-05
If any new packages are installed, it is because they are dependencies of a new version of another package.

Find what package it is, go to Synaptic and use the "lock version" function to lock it at the older version. You won't be "pestered" anymore.

However, if it's listed under "important security updates" or "recommended updates" then you would best be advised to leave it alone. If a package brings in a new dependency then it's probably for a really good reason, such as "fixes a crash" or "should have been included in the first place". It's not like Update Manager frivilously installs multi-megabyte programs just to frustrate you.

---

### Post by wallaroo on 2011-02-05
Thanks 3rdalbum

The 'lock' suggestion is part of what I'm looking for.

I can't however accept the "Thou shalt not question the almighty Update Manager" philosophy adopted by so many.

Linux and Open Source is all about control and choices but I'm afraid update manager does not adhere to this.
As I have already pointed out updates are sourced from your 'Sources List' which generally contain 'controlled' sources like Canonical and 'uncontrolled' sources via third party sites, necessary because Canonical can't support all Linux software.

For example: Updates like language support that usually adds megabytes of data each are generally unnecessary and should be optional, we don't all have terabytes of storage available. (There was a recent update adding a new 48mb file for 'Japanese True Type fonts' which I definitely don't require - but there is no way to disable this addition, its forced upon you).

There is a division in Update Manager labelled 'Recommended Updates', how can this be called that when there is no way to say 'No I don't want this one', if you don't have control over updates then your system is potentially compromised.

Where are the choices (that's why I gave windows the flick).

</end of rant>

---

### Post by negativequity on 2011-03-26
thank you so much 3rdalbum i had been looking for a way to stop Adobe Air from updating and this did the trick

---

