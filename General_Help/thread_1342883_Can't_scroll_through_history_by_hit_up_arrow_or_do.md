---
title: "Can't scroll through history by hit up arrow or down arrow key"
date: 2009-12-01
forum: General Help
---

### Post by hugebrush on 2009-12-01
I added a user to my customized live cd by useradd command. This new user can't scroll through history by hit up arrow key or down arrow key, I get a string "^[[A" if hitting up arrow key in the console. The "root" user from original live cd has no problem with scroll through history in this way.

---

### Post by rpaskudniak on 2009-12-01
hugebrush wrote:
> I added a user to my customized live cd by useradd command. This new user can't scroll through history by hit up arrow key or down arrow key, I get a string "^[[A" if hitting up arrow key in the console. The "root" user from original live cd has no problem with scroll through history in this way.
Interesting.

If you are using arrow keys to scroll through previous commands, you seem to be expecting emacs behavior for accessing your shell history.
At my previous job, where everyone used ksh as the default shell, this would happen if the history editor were not set.  Preferring vi to emacs, I did one of two things to get the behavior I wanted:
[LIST]
[FONT="Courier New"][*]export EDITOR=vi
[*]set -o vi[/FONT]
[/LIST]
Actually, I did both of these in my .profile. (Belt and suspenders :)  )

Since this is Ubuntu, I will assume the default shell is bash.  Still, I suggest you try these:
[FONT="Courier New"][LIST]
[*]set -o emacs
[*]export EDITOR=emacs
[/LIST][/FONT]
and then try the arrow keys for shell history. If that works, stick that into your .bashrc and open a new login session.

HTH.

---

### Post by hugebrush on 2009-12-01
> **rpaskudniak said:**
> hugebrush wrote:

Interesting.

If you are using arrow keys to scroll through previous commands, you seem to be expecting emacs behavior for accessing your shell history.
At my previous job, where everyone used ksh as the default shell, this would happen if the history editor were not set.  Preferring vi to emacs, I did one of two things to get the behavior I wanted:
[LIST]
[FONT="Courier New"][*]export EDITOR=vi
[*]set -o vi[/FONT]
[/LIST]
Actually, I did both of these in my .profile. (Belt and suspenders :)  )

Since this is Ubuntu, I will assume the default shell is bash.  Still, I suggest you try these:
[FONT="Courier New"][LIST]
[*]set -o emacs
[*]export EDITOR=emacs
[/LIST][/FONT]
and then try the arrow keys for shell history. If that works, stick that into your .bashrc and open a new login session.

HTH.
Thanks.
I tried "set -o emacs" and "export EDITOR=emacs" in a console window,but didn't solve the problem.

---

### Post by dcstar on 2009-12-01
> **hugebrush said:**
> I added a user to my customized live cd by useradd command. This new user can't scroll through history by hit up arrow key or down arrow key, I get a string "^[[A" if hitting up arrow key in the console. The "root" user from original live cd has no problem with scroll through history in this way.

And what shell is this user using?

Up and Down arrow history only works in BASH/DASH.

---

### Post by hugebrush on 2009-12-02
> **dcstar said:**
> And what shell is this user using?

Up and Down arrow history only works in BASH/DASH.

Thanks.
User I created use dash shell, which root user used is bash, I change shell for the user to bash, Up and Down arrow history works fine.

---

