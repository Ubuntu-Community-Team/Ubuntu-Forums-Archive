---
title: "Software Install ERROR!  PLEASE HELP!!!"
date: 2011-10-26
forum: General Help
---

### Post by LanceRooke on 2011-10-26
dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.   

This is the error I keep getting anytime I want to install anything.  It won't even let me update and upgrade.  How do I correct this?

---

### Post by satanselbow on 2011-10-26
have you opened a terminal and entered that command?

from "man dpkg"

```

--configure package...|-a|--pending
              Configure  a package which has been unpacked but not yet config&#8208;
              ured.  If -a or --pending  is  given  instead  of  package,  all
              unpacked but unconfigured packages are configured.

```

---

### Post by 3rdalbum on 2011-10-26
> **LanceRooke said:**
> dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.   

This is the error I keep getting anytime I want to install anything.  It won't even let me update and upgrade.  How do I correct this?

Go into the terminal by pressing Control-Alt-T, or search for "terminal" in the Unity Dash.

Type (or copy and paste) the following:

```
sudo dpkg --configure -a
```

Hit Enter. Type your password and press Enter, there will be no indication that you're typing anything at this stage. After hitting Enter you should see a lot of activity in the terminal. When all the activity is done, you should be able to install software again.

---

