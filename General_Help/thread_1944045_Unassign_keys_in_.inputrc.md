---
title: "Unassign keys in .inputrc"
date: 2012-03-20
forum: General Help
---

### Post by pderocco on 2012-03-20
I'm trying to set up my Terminal window to use different key assignments, by editing ~/.inputrc. I want to assign "\C-x" (ctrl-X) to something, but the assignment table is already full of two-key functions starting with it, like "\C-x\C-e": edit-and-execute-command.
I used bind -p to spit out a list of all key assignments, put all of them into ~/.inputrc, and deleted everything after each colon, hoping this would clear out the assignments, but it doesn't work. I've read everything I could find on Readline and inputrc files, and can find no mention of any way to eliminate an existing key binding, other than to bind it to a different command, which is NOT what I want to do.
So how do I get rid of all 150 unused key assignments, short of 150 invocations of "bind -r" in my startup script?

---

