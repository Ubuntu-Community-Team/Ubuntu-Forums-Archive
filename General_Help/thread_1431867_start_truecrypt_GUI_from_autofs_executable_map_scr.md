---
title: "start truecrypt GUI from autofs executable map script"
date: 2010-03-17
forum: General Help
---

### Post by rduke15 on 2010-03-17
I guess the real more general question is: "How to start a GUI app on a user's desktop from a script running without a terminal as root?"

I have an automount executable map for SMB mounts. This needs passwords which are stored in files on a truecrypt volume. If the truecrypt volume has not been mounted yet, the passwords cannot be found, so the automount obviously fails.

What I have tried in my auto.cifs script is:

```
credfile="/media/truecrypt1/smb.$key"
creddir=$(dirname "$credfile")

# if the truecrypt volume isn't mounted, mount it
[[ -d "$creddir" ]] || {
    # call the script which mounts the TC volume
    /home/user/bin/tc on
}

```

The "/home/user/bin/tc" script with the "on" argument simply does
```
truecrypt $my_tc_filename
```

When run in a terminal started from the GUI, whether as myself or as root (after sudo -s), the "/home/user/bin/tc" script does start a truecrypt GUI window on my desktop, where I can enter the TC password. That's what I would like to achieve from the automount script.

When the tc script is run from the automount script, it just exits with error code 1. No TrueCrypt window appears.

---

