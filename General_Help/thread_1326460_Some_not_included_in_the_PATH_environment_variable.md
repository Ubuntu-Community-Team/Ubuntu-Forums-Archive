---
title: "Some not included in the PATH environment variable."
date: 2009-11-14
forum: General Help
---

### Post by listerofsmeg1 on 2009-11-14
Hi there,

I'm one of many Karmic users disappointed with the new version of gdm (no theming makes dick a dull boy) so I installed SLiM from the Jaunty repos.  Which worked fine but leads to another problem.

Some commands no longer work unless the full path is used.  Here's an example of the message i receive

Command 'fortune' is available in '/usr/games/fortune'
The command could not be located because '/usr/games' is not included in the PATH environment variable.
fortune: command not found

Anyone know a way to fix?

Thanks

---

### Post by dabang on 2009-11-14
I'm not quite sure, why your $PATH should have changed in the first place, but to change it, edit ".profile" in your home dir and add to the bottom of it:

PATH=$PATH:/usr/games:/what/ever1:/what/ever2

---

### Post by listerofsmeg1 on 2009-11-14
Worked like a charm.  Thanks a bunch. :)

---

