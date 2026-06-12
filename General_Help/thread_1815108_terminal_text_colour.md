---
title: "terminal text colour"
date: 2011-07-30
forum: General Help
---

### Post by tomgnu on 2011-07-30
Hello, would you be kind enough to tell me how to make the text in the terminal green please.
Ta very much.
(natty)

---

### Post by drs305 on 2011-07-30
If you are using gnome-terminal you can edit the profile. From a running terminal: Edit > Profiles > Edit (Default or New) > Colors tab. Untick the 'Use colors from system theme' and make your selection.

---

### Post by AlphaLexman on 2011-07-30
Are you trying to make a specific output green or just make everything green ??

By everything green I mean the output of 'ls' and 'cat filename' will be green ??

Please advise.

---

### Post by zero2xiii on 2011-07-31
```

tput setaf 1; #set text colour to red
tput setaf 2; #set text colour to green
#..etc
tput setaf 9; #set text colour to default (as under the profile your terminal is using)

```

Use this to change the colour of the terminal for the current session (as well as in scripts to change the font color)

Other wise use the method drs305 explained:
> If you are using gnome-terminal you can edit the profile. From a running terminal: Edit > Profiles > Edit (Default or New) > Colors tab. Untick the 'Use colors from system theme' and make your selection.

---

### Post by tomgnu on 2011-08-01
> **zero2xiii said:**
> ```

tput setaf 1; #set text colour to red
tput setaf 2; #set text colour to green
#..etc
tput setaf 9; #set text colour to default (as under the profile your terminal is using)

```

Use this to change the colour of the terminal for the current session (as well as in scripts to change the font color)

Other wise use the method drs305 explained:

lovely cheers, thanks for your time

---

