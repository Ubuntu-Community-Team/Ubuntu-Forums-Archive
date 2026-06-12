---
title: "Can I dynamically specify a prompt when running a subshell (without touching .*shrc)?"
date: 2009-10-01
forum: General Help
---

### Post by brownbat on 2009-10-01
This might be a trick question, watch out. 

I've read up a bit on subshells, and I'm looking to see if I missed something in my brief overview.

Let's say I have a machine where I'm highly reluctant to modify any data, but I nontheless want to control the format of the subshell prompt. Can this be done? "Script" doesn't take a commandline argument for modifying the subshell prompt. Do other, similar commands allow such a thing, is it handled some other way, or is it just all set by .*shrc, a file I'm reluctant to touch?

---

### Post by Littleweseth on 2009-10-01
I'm not sure what you want.... is it the shell prompt that you want to modify? I.e. the "lws@caradoc ~ $" at your shell?

This is set by the $PS1 environment variable (in bash, at least.) You can look at what's in there by typing '$PS1' at the prompt, and you can modify it with 'export PS1=...........'. This only affects the current shell.

Apologies if I'm answering a completely different question to what you posed (maybe some clarification is in order?)

- L.

---

