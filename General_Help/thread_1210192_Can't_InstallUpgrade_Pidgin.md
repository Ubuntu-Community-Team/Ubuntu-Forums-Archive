---
title: "Can't Install/Upgrade Pidgin"
date: 2009-07-11
forum: General Help
---

### Post by NooBeee on 2009-07-11
Pidgin hasn't been able to connect to yahoo so I decided to upgrade. I followed the instruction on the pidgin website for Ubuntu but even though the upgrades seemed to show up in the update manager, the system said something about only being to do a 'partial upgrade' (the pidgin stuff was all left unchecked). I did that and pidgin was removed.

Now I can't even install pidgin. Ubuntu keeps complaining about dependencies.

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: libdbus-glib-1-2 (>= 0.78) but 0.74-2 is to be installed
          Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is to be installed
          Depends: libpurple0 (>= 1:2.5.8-1ubuntu2~pidgin1.9.04) but it is not going to be installed
          Depends: perl (>= 5.10.0-19ubuntu1) but 5.8.8-12ubuntu0.4 is to be installed
          Depends: perlapi-5.10.0 but it is not installable
E: Broken packages


How can I overcome this?

---

### Post by carml on 2009-07-11
Maybe with ```
sudo apt-get update && sudo apt-get upgrade
``` to correct the broken package.

---

### Post by NooBeee on 2009-07-12
It says:
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by carml on 2009-07-12
Have you tried to visit the homepage of Pidgin? Maybe there is some suggestion for your problem of connection,also check the forum because someone else had your same problem.

---

### Post by NooBeee on 2009-07-13
I've already done that stuff. That's what caused the whole problem. It promised that 'updates' would show up in the update manager and instead when I ran all the possible upgrades, it removed pidgin and prevented its reinstall.

See the weird thing is that all the apt-get update, etc claims that my system is up to date and I suppose it is except that I don't have pidgin. And I when I try to install it it gives me those dependency errors.

---

### Post by carml on 2009-07-13
Did you perform a search in the forum about the problem with Pidgin and Yahoo? There's for sure a thread on this matter.

---

### Post by NooBeee on 2009-07-14
The problem with pidgin and yahoo isn't the issue though. (They solution was to upgrade to the latest version of pidgin. The problem is that Updates Manager has removed my old pidgin and somehow messed things up along the way so that pidgin cannot be (re)installed.


I wonder if I should be considering the "if it's broke, reinstall" approach...

---

### Post by tacantara on 2009-07-14
> **NooBeee said:**
> The problem with pidgin and yahoo isn't the issue though. (They solution was to upgrade to the latest version of pidgin. The problem is that Updates Manager has removed my old pidgin and somehow messed things up along the way so that pidgin cannot be (re)installed.
 
 
Based on that reply, I'm assuming that you tried to reinstall the previous version of Pidgin?  About 2 weeks ago, some updates were sent out (I have the auto update feature running on my system) and that took care of Yahoo problems on Pidgin.

---

### Post by NooBeee on 2009-07-16
I meant reinstalling the OS...something I haven't had to do since Windows (and never over something so trivial).

---

### Post by tacantara on 2009-07-16
> **NooBeee said:**
> I meant reinstalling the OS...something I haven't had to do since Windows (and never over something so trivial).


I agree, reinstalling the OS to get Pidgin running would be over the top.  Have you checked the Pidgin website?  They might have previous versions available for download.  If so, download and install it that way.  If you've been receiving your updates automatically, the update that corrected the problem with Pidgin (which was a Yahoo-created problem when they removed obsolete protocols from their IM network), everything should fall in line.

---

### Post by metalf8801 on 2009-07-16
Have you tried to use the Synaptic Package manager to fix the broken packages? 

System > Administration > Synaptic Package manager 
you will need to enter your password 
Then look on the left you should see **All** then below that Broken 
Click on broken and see if anything is listened if nothing is listed try clicking the reload button 
If you do see stuff list check it and click Apply (I think I haven't had a broken package in while and I didn't have this problem when I upgrade pidgin a few weeks ago) 

I hope that helps 
Dan

---

### Post by metalf8801 on 2009-07-16
> **NooBeee said:**
> I meant reinstalling the OS...something I haven't had to do since Windows (and never over something so trivial).

Reinstalling Ubuntu wont fix Pidgin because you will still need the newer version of Pidgin

---

### Post by NooBeee on 2009-07-19
Nope no "Broken".

Besides my system has never complained of broken packages just "unresolvable dependencies" .... whatever that means.

---

### Post by helmut0 on 2009-07-19
Same problem here.Can't install older version or new version of pidgin without dependences issues.

---

### Post by curig on 2009-07-28
I've upgraded to Ubuntu 9.04 and in the process have lost pidgin and I get the same error regarding dependencies when trying to reinstall. Would be interested in any solutions!

---

