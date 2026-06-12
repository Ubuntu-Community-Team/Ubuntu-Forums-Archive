---
title: "Bash script to rename files according to SFV"
date: 2009-11-20
forum: General Help
---

### Post by blacksunseven on 2009-11-20
I'm pretty new to bash scripting (having only modified a few to slightly better suit me) and need some serious help after one of my partitions took a dive. A lot of the archives I had on the affected partition had SFV files and the files, for the most part, seem to have made a full recovery. Trouble is, they're all now labeled six-eight digit numbers like #749399 or whatever. I can't check their integrity with the SFVs until the filenames match so I need to rename them. Wouldn't be a problem except there are 100s of them. I'm looking for a very friendly bash scripter who might be able to help me solve this problem. Any one who wants to contribute in even a small manner is welcome to offer suggestions.

simple step-through to better illustrate what I'm looking for:
```
run cksfv/cfv on all files in current dir
compare checksums with example.sfv filenames
rename files in directory according to checksum matches
```

---

### Post by blacksunseven on 2009-11-25
Bump.

---

