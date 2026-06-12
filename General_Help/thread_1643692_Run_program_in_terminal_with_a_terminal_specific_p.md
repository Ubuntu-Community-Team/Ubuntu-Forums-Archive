---
title: "Run program in terminal with a terminal specific profile from GUI"
date: 2010-12-12
forum: General Help
---

### Post by frogotronic on 2010-12-12
Hello,

  I'd like to run a program ( [http://www.chkrootkit.org/](http://www.chkrootkit.org/) ) from the GUI menu (yes, I know I can run it from the command line).  I've gotten this to work by using a menu entry (see attached screenshot).

The command is:

```
gksu chkrootkit
```

with the option for **Type:** was selected as **Application in Terminal**

However, when chkrootkit is finished, the terminal immediately snaps shut according to the profile selection:

**When Commands Exits: Close terminal**

What I'd like to do is create another profile that causes the terminal to be held open (see screenshot) when the command exits *and be able to choose that profile from the GUI Menu entry.*

I believe the command when using the CLI is:

```
gnome-terminal --profile=<profile_name>
```

My question is how do I incorporate this within the **Command** entry line of the launcher?

Thanks,
CH

---

### Post by frogotronic on 2010-12-13
SOLVED HERE: [http://ubuntuforums.org/showpost.php?p=3296315&postcount=2](http://ubuntuforums.org/showpost.php?p=3296315&postcount=2)

---

