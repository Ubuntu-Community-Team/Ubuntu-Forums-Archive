---
title: "Empathy Messaging Menu integration messed up"
date: 2010-10-12
forum: General Help
---

### Post by clicker4721 on 2010-10-12
I use 64-bit Ubuntu 10.10 Maverick Meerkat stable. The 'Chat' entry in the Messaging Menu has disappeared. I tried a quick fix by placing a file of no extension titled 'empathy' in '/usr/share/indicators/messages/' with contents as folllows:> /usr/share/applications/empathy.desktopAll this did was add a static entry to the menu saying 'Set Up Chat...'. The icon loaded fine, but the text doesn't change to 'Chat' like it should. Also, Empathy appears in the Notification Area, which is redundant since I use the Indicator Applet Session that includes the Me Menu. 
:(
How can I get Empathy out of the Notification Area and into the Messaging Menu--the right way? I'm cautious to try a reinstall because I don't want to have to re-enter all my accounts' details because of the tedious process that is when one uses randomly generated passwords as I do.

EDIT: I think the issue has much less to do with the Messaging Menu than with Empathy. Cloud Services Notifications, which I recently installed, cannot appear in the messaging menu. On no previous editions of Ubuntu have I had this error.

---

### Post by clicker4721 on 2010-10-13
Wow, really? Bump.

---

### Post by clicker4721 on 2010-10-13
Aha! I found the culprit! I was using the Telepathy PPA; a simple ppa-purge fixed it. I feel kinda stupid, but I suppose this can make a great lesson to anyone else that encounters the problem. :D

---

### Post by LeRenard on 2010-10-14
Had the same problem ! 

Thanks

---

### Post by shan23 on 2010-10-23
> **clicker4721 said:**
> Aha! I found the culprit! I was using the Telepathy PPA; a simple ppa-purge fixed it. I feel kinda stupid, but I suppose this can make a great lesson to anyone else that encounters the problem. :D

clicker4721,
Well, I'm facing the same problem - the "Chat" entry is missing from the messaging menu. Googling leads me to this post consistently, and you seem to have the answer - can you please explain in detail what exactly is involved in a "ppa-purge" which has fixed the problem ? I didn't wan't to open up a new thread for this as you have the answer, chose to ask you directly!

---

### Post by Nosferax on 2010-10-23
ppa-purge is an application that will help you get rid of a manually added ppa and revert back to the versions of packages available from the ubuntu repositories. 

This could be the solution to the problem, but first, tell us, did you add the telepathy ppa to your ppas (it's the empathy repository). If you didn't then, reverting packages from a ppa you didn't use hardly could be the solution.

---

### Post by shan23 on 2010-10-23
Thanks to both Nosferax and clicker4721 (who replied to my PM), the problem is solved - it *was* the result of the Telepathy-PPA, which I purged using Ubuntu Tweak.
Details (along with screenshot) of how to do that can be found here
[http://www.webupd8.org/2010/07/ubuntu-tweak-055-released-features-ppa.html]("http://www.webupd8.org/2010/07/ubuntu-tweak-055-released-features-ppa.html")

Thanks everyone for the speedy responses !

---

