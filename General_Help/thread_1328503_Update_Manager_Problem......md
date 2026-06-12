---
title: "Update Manager Problem....."
date: 2009-11-16
forum: General Help
---

### Post by wbee on 2009-11-16
Hello,

From habit,when I boot up the computer for the day,I check the update manager.

Yesterday,I got a red explanation mark within a red triagle on my upper panel. It asks me to check my update information manually by clicking on that icon.

I did so,and it brought up the Synaptic Package Manager,not the update manager.

Bringing up the update manager from the System>Administration,it says my last update was nine days ago,when my last update was Saturday. I hit the button,entered the password to retry,and it showed my system up to date--again,nine days ago,not the usual less than an hour ago it reads when it's working properly.

I went into the Synaptic Package Manager and reinstalled the Gnome update manager. The same malfunction occurred.

Is this something Canonical is working on? Is it a bug I should report to Launchpad?

Is there some terminal code I can use to remove and reinstall the update manager function to see if that fixes it?

------------

Thank you.

---

### Post by Giblet5 on 2009-11-16
There was an update to update-manager about a week ago...

Bring up a terminal window (Applications -> Accessories -> Terminal) and enter this command:

```
sudo apt-get update && sudo apt-get upgrade
```

Any errors? If not, then you're fully updated.

---

### Post by wbee on 2009-11-16
Giblet5 and Others,

The terminal read out showed an error.

So others with the same problem will know,let me post this next part:

Checking with the "search" feature for "Update Manager",I found the solution and fixed it this way:

System>Administration>Synaptic Package Manager>Settings>Repositories>Ubuntu Software>**unclick the check mark besides the cd-rom box(I hope that was just an aberration and does not happen again.)>reload>close synaptic package manager.

That done,it worked perfectly,and as Giblit5 said,now that it's working  correctly,the terminal read out confirmed it.

Thank you Giblet5:-)

---

