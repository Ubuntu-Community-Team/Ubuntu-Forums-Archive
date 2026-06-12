---
title: "Make Bash play a sound on every new line output"
date: 2009-08-27
forum: General Help
---

### Post by blazemore on 2009-08-27
I'm a bit geeky and want Bash to play a short sound every time it prints a new line. Is this possible?

---

### Post by DaithiF on 2009-08-27
Hi, to beep every time a prompt is displayed:
```
export PROMPT_COMMAND=beep
```
you may need to install beep:
```
sudo apt-get install beep
```

but if you mean you want a beep every time a line of text is outputted to the console, then no, i don't know how you could do that.

---

