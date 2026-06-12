---
title: "Terminal colour's: ubuntu style/gentoo style"
date: 2009-09-06
forum: General Help
---

### Post by TheConsaw on 2009-09-06
hi guys, i was wondering is there any way to make my ubuntu terminal look like my sabayon terminal, both gnome
i have tried playing around with profile options with not much luck, thanks in advance

---

### Post by scion xd on 2009-09-06
Did you try terminal Preferences, you can do the first one in there but i dont know how to do the second one.

---

### Post by TheConsaw on 2009-09-06
> **scion xd said:**
> Did you try terminal Preferences, you can do the first one in there but i dont know how to do the second one.

well ya the first one is my ubuntu terminal edited through terminal pref, i want it to output like screen 2 does, that s my sabayon linux default, very pretty !!:P but no options i can find in ubuntu to make it so afaik

---

### Post by Ayuthia on 2009-09-06
If I recall correctly, you will need to edit the .bashrc file in your /home/<username> directory.  Look for:
```
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

```
I think it said xterm-color.  You will need to change it to xterm:
```
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm) color_prompt=yes;;
esac

```

EDIT: You will need to close out the Terminal or open another Terminal session to test it out.  The current session won't see the changes because it was not activated in that session.

---

### Post by mrgnash on 2009-09-06
If you want a pretty terminal in Ubuntu, then I suggest you consult [this guide](http://tuxtraining.com/2009/07/28/how-to-have-a-lightweight-beautiful-functional-terminal) :)

Example:

[[img]http://omploader.org/vMmE1bA/verb1_thumb.png[/img]](http://omploader.org/vMmE1aQ)

---

### Post by geoffp on 2012-12-13
Just found this thread, and thought I'd update it with the latest solution.

There's already a fancy colored prompt in your ~/.bashrc, at least as of 12.10, and I think 12.04. Look for this (for me, it's on line 43):

```

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_color_prompt=yes

```

"force_color_prompt=yes" is commented out by default. Just uncomment it and you'll have a great-looking bash prompt, just like in Gentoo.

Cheers!

---

### Post by howefield on 2012-12-13
Old thread back to sleep.

---

