---
title: "Loads of errors"
date: 2009-10-15
forum: General Help
---

### Post by nipunreddevil on 2009-10-15
I recently tried to increase space in my wubi install.I tried some scripts.
One such script made a copy of my home folder and now i am in big problems.Programs not working properly and also disabled write access on home

---

### Post by kavon89 on 2009-10-15
What scripts did you run, and as root? Post it here with code tags around them.

If you can get to a command prompt, try this:

```

sudo -i
chown -R username /home/username
chmod 700 /home/username/.ssh           #this one might not be necessary
exit

```

---

### Post by nipunreddevil on 2009-10-15
Third command on this script you wrote is not being allowed.I have now a folder called home.backup and it has all the data from my home folder.I want to revert back to normal though

---

