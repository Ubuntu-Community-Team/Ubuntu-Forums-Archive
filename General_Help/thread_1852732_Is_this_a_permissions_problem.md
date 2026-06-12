---
title: "Is this a permissions problem ?"
date: 2011-09-30
forum: General Help
---

### Post by JCM_Pico on 2011-09-30
Hi there,

  Recently I have been forced to format and since I had a backup of my home partition saved in an external HD I've decided to copy the backup from there to my new ubuntu install.
  But since my external HD is an NTSF file system all my home files are now executable (like chmod 777).
  My questions now are: How does this affect my system functioning? How can I revert this to the normal permissions?

---

### Post by MG&amp;TL on 2011-09-30
Copy the files across, then:

```
cd <directorycontaining"executable"files>
chmod -x *
```

---

### Post by JCM_Pico on 2011-10-01
> **MG&TL said:**
> Copy the files across, then:

```
cd <directorycontaining"executable"files>
chmod -x *
```

Thank you for the reply, but that's no solution, if I do that, and there are folders within the directory they will lose their executable permission and I won't be able to cd into them ....

---

### Post by SavageWolf on 2011-10-01
I think `chmod u+X` (With a capital) only affects folders, though I'm not sure...

Although, are there any executable files that should be executable in home folders?

---

### Post by JCM_Pico on 2011-10-01
> **SavageWolf said:**
> I think `chmod u+X` (With a capital) only affects folders, though I'm not sure...

Although, are there any executable files that should be executable in home folders?


This way I'm able do cd but not to ls within the folder :(

---

### Post by JCM_Pico on 2011-10-01
I partially solved the problem, with ```
  find folder/* -type f -print0 | xargs -0 chmod 644 
``` I was able to change all file permission except the folder ones....
The only downside is that every executable file like .sh has been changed to. Although this kind are less.

Thank you all

---

### Post by MG&amp;TL on 2011-10-01
Sorry, JCM, I'd forgotten about the directories needing to be executable. forgive me if I caused any inconvenience. :)

---

### Post by JCM_Pico on 2011-10-01
MG&TL no problem and no  inconvenience

Thank you :D

---

