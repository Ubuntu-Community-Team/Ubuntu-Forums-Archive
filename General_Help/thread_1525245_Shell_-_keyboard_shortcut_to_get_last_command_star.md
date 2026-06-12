---
title: "Shell - keyboard shortcut to get last command starting with initial segment?"
date: 2010-07-06
forum: General Help
---

### Post by Zorgoth on 2010-07-06
In matlab, there is a very nice feature where if you type a few characters and then press <up> you will get the last command starting with those characters rather than the last command.  Clearly you could get a list of such commands in the shell by doing something with history, but is there a quick keyboard shortcut with the same functionality?

---

### Post by Brandon Williams on 2010-07-07
By default, bash runs in emacs command line mode. This means that command-line editing and history searching is done with emacs keystrokes. Thus, Ctrl+R starts a reverse incremental search.

After pressing Ctrl+R, you get a prompt that says "(reverse-i-search)". Just start typing and bash will search backwards through your command line history to find the first command line that contains the string you've typed so far.

After you've typed the full string you're searching for, if you want to skip back further in the history to the next most recent command line with that string, just press Ctrl+R again.

---

### Post by Zorgoth on 2010-07-09
Cool!  I'll try it when I get to work.

---

### Post by Zorgoth on 2010-07-09
It works!  Thank you!

---

