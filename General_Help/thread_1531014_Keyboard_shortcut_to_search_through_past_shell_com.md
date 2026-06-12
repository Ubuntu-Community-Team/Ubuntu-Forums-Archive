---
title: "Keyboard shortcut to search through past shell commands with regular expression?"
date: 2010-07-14
forum: General Help
---

### Post by Zorgoth on 2010-07-14
Note: I have made a thread similar to this before, but the title/contents were too botched to repair.

I know that using C-r you can search for past bash commands containing a particular string, but how would you search for past bash commands matching a particular regular expression?  Is there a keyboard shortcut for that or do you have to use a shell command?

---

### Post by uRock on 2010-07-14
```
history
```

---

### Post by Zorgoth on 2010-07-14
I know about history; I am wondering if there is a keyboard shot cut similar to Control R that works with regular expressions.

---

### Post by uRock on 2010-07-14
Sorry, I am a rookie with most of the CLI stuff(currently taking Intro to Unix/Linux class). If there is a file containing the previous commands, then maybe you can run a search command such as ```
grep 'TextYouWant' [filename]
``` I have tried to search the history file before, but I couldn't make it work.

---

### Post by Zorgoth on 2010-07-14
URock:
I think here for a command line thing you would do

history | grep '[regular expression here]'

But again, I am not looking for a command but a keyboard shortcut

---

