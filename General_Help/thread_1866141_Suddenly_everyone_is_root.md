---
title: "Suddenly everyone is root"
date: 2011-10-21
forum: General Help
---

### Post by ctdahle on 2011-10-21
It appears that all of the users I have on my computer have the power of root since I upgraded to Oneiric.

Except for at start up, I have not been prompted to enter a password for any upgrade, package install, or system change.

Other user accounts also seem to have full administrative authority. Surely this is not right!

Any thoughts, Anyone?

---

### Post by experience on 2011-10-21
Have you checked the sudo configuration file for problem?

---

### Post by gsmanners on 2011-10-21
> **ctdahle said:**
> ... I have not been prompted to enter a password for any upgrade, package install, or system change.

Update Manager doesn't require a password anymore, so that's working as designed. What system changes are you referring to?

---

### Post by dcstar on 2011-10-22
> **ctdahle said:**
> It appears that all of the users I have on my computer have the power of root since I upgraded to Oneiric.

Except for at start up, I have not been prompted to enter a password for any upgrade, package install, or system change.

Other user accounts also seem to have full administrative authority. Surely this is not right!

Any thoughts, Anyone?

Do you mean existing users that did not have Admin rights in your previous system now do after the upgrade procedure, or users added in your new system get Admin rights by default?

If it is #1, then that would be a **major** security bug.

---

### Post by ctdahle on 2011-10-22
I guess there is some rational to allowing update manager to run without authentication, but I can also install software (in the software center) from my 9-year-old's account without entering the root password.

This is troubling.

---

### Post by gsmanners on 2011-10-22
> **ctdahle said:**
> I guess there is some rational to allowing update manager to run without authentication, but I can also install software (in the software center) from my 9-year-old's account without entering the root password.

This is troubling.

More troubling than Bing image search? :p

---

### Post by cryptotheslow on 2011-10-22
That doesn't sound right :confused:

When logged on with your kid's account, open a terminal and enter the command:
```
 id 
```

That will list what permission groups the account belongs to. Seems like the sensible place to start.

---

