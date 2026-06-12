---
title: "installing apps _other than_ the latest version?"
date: 2010-05-16
forum: General Help
---

### Post by axe.gs1 on 2010-05-16
Hi all
I am running Ubuntu 10.04 on my laptop and been pretty happy with it so far.  I also run Mythtv on many machines in the house, but they are running on 9.04-Intrepid.  I didn't do the upgrade to 9.10 or 10.04 there because of the Mythtv change in version... 
-->Trust me, while this is specifically a question for my 10.04 (or previous 9.10 laptop) install and MythTV, it is a more general question that I have had in the past as well...

Anyway, I want to install an older version of the Mythtv environment on my 10.04 laptop, but the repos only have the latest and greatest.  I have added a repo that has older versions, but I cannot get Synaptic to display the older revs.  

Specific question:
Is there a way to get synaptic to display *all versions *of any app rather than just the latest one?  Or can I tell it to display a specific version (ie OOo 3.0 not 3.2 for *other* instance)?
Can I do an apt-get install and call a specific deb file, or would I use dpkg (but I'd be missing some of the checks-and-balances apt-get has vs dpkg...)

Any info is useful of course :) 
 Thanx
AXE

---

### Post by lidex on 2010-05-16
In synaptic select the package and go to the 'Package>Force Version' menu entry. You can choose from available versions using the dropdown in that dialog. To simply see what is available, right-click on the package and select properties then click the version tab. Watch out for dependency conflicts!!

---

