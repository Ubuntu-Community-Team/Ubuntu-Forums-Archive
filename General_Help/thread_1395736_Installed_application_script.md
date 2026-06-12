---
title: "Installed application script"
date: 2010-02-01
forum: General Help
---

### Post by ushills on 2010-02-01
I need to get a script to check if rdiff-backup is installed and if not install it,  if it is I want the script to continue.

I think I need this but I am missing the conditional step

```
# Check that rdiff-backup is installed
if [gpkg -l | grep rdiff-backup]  # need to check if not installed
true    # if rdiff-backup is not installed then install it
apt-get install rdiff-backup
fi

# continue script
```

---

### Post by bluefrog on 2010-02-01
dpkg -l rdiff-backup | grep ii
if [[ $? == 1 ]]; then
 aptitude install rdiff-backup
fi

---

### Post by ushills on 2010-02-01
Thanks

---

