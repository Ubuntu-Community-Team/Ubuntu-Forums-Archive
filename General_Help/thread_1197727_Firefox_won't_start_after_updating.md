---
title: "Firefox won't start after updating"
date: 2009-06-26
forum: General Help
---

### Post by mikeyy on 2009-06-26
I just installed ubuntu and did an update.  Now, Firefox won't start.  I click on it and it says, it starting but then nothing happens and it just disappear.

I type firefox at the terminal and nothing.  The system monitor doesn't show firefox.

---

### Post by DeMus on 2009-06-26
> **mikeyy said:**
> I just installed ubuntu and did an update.  Now, Firefox won't start.  I click on it and it says, it starting but then nothing happens and it just disappear.

I type firefox at the terminal and nothing.  The system monitor doesn't show firefox.

When using terminal do you get an error? If so, what does it say?

---

### Post by mikeyy on 2009-06-26
> **DeMus said:**
> When using terminal do you get an error? If so, what does it say?
It doesn't say anything.  I type firefox and got nothing.

---

### Post by DeMus on 2009-06-26
> **mikeyy said:**
> It doesn't say anything.  I type firefox and got nothing.

Maybe you have to uninstall Firefox and install it again. Did you make bookmarks already, or any other personal settings?
If not, open your home folder, type ctrl-h and delete the .mozilla folder also.
If you have made personal settings, rename the .mozilla folder so you can always get it back.
Then open Synaptic, search Firefox and un-install it and install it again.
See how that goes.

---

### Post by mikeyy on 2009-06-26
> **DeMus said:**
> Maybe you have to uninstall Firefox and install it again. Did you make bookmarks already, or any other personal settings?
If not, open your home folder, type ctrl-h and delete the .mozilla folder also.
If you have made personal settings, rename the .mozilla folder so you can always get it back.
Then open Synaptic, search Firefox and un-install it and install it again.
See how that goes.
No, I just installed ubuntu and did no bookmarks or any personal settings.

Do I need to delete the .mozilla folder first???...because I did the Synaptic uninstall and install already and still nothing?


How do I open the home folder?  Sorry, I'm new to this.

---

### Post by mikeyy on 2009-06-26
Please, can someone help me?

I switch to guest account and firefox works.  I think it's a permission issue.

---

### Post by lovinglinux on 2009-06-26
> **lovinglinux said:**
> 

**[size="5"][color=#CC0000]Troubleshooting[/color][/size]**

Several Firefox problems are related to corrupted profiles and can be easily fixed by restoring a profile backup (see Backup section), by deleting the corrupted profile or deleting specific files inside the profile. Usually, there is no need to re-install Firefox.

Several posts in these forums recommend to delete the ~/.mozilla folder to solve problems with profiles. While this will certainly solve many problems, it's not usually necessary. Additionally, the ~/.mozilla folder is the place where other Mozilla applications stores their profiles (Thunderbird, Sunbird, etc), so deleting this folder will delete their settings too. Besides you will loose all Firefox settings, extensions, themes, bookmarks and so on. As a last resort, you could delete only the profile folder, located under ~/.mozilla/firefox/, which will have the same effect of deleting ~/.mozilla without excluding other applications profiles.


So, close Firefox, delete the folder ~/.mozilla/firefox/ and start it again.

---

