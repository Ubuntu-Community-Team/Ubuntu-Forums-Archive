---
title: "Why doesn't Ubuntu's terminal allow using Ctrl-Backspace?"
date: 2010-11-13
forum: General Help
---

### Post by cool-RR on 2010-11-13
Hello, I'm a Python developer and I've been working with Ubuntu for a few years. I am trying to work more efficiently with Ubuntu.

I have something that bothers me: Why doesn't Ubuntu's terminal allow using Ctrl-Backspace to delete a bunch of characters? I mean, sometimes I'll be typing a long command, and I'll want to delete (say) the last 30 characters of the command line. Holding down backspace would take a long time, like 5 seconds. I'm used to using Ctrl-Backspace to do these deletions fast, but why isn't that allowed on Ubuntu's terminal?


Thanks,
Ram.

---

### Post by dcstar on 2010-11-13
> **cool-RR said:**
> Hello, I'm a Python developer and I've been working with Ubuntu for a few years. I am trying to work more efficiently with Ubuntu.

I have something that bothers me: Why doesn't Ubuntu's terminal allow using Ctrl-Backspace to delete a bunch of characters? I mean, sometimes I'll be typing a long command, and I'll want to delete (say) the last 30 characters of the command line. Holding down backspace would take a long time, like 5 seconds. I'm used to using Ctrl-Backspace to do these deletions fast, but why isn't that allowed on Ubuntu's terminal?


gnome-terminal emulates a VT-220 terminal, if you don't like that particular emulation use one of the other terminal packages that actually does what you want.

---

### Post by cool-RR on 2010-11-14
David, I am not aware of any other terminal packages or emulation modes. Is there one which is just normal, for example allowing Ctrl-Backspace for word-delete, Ctrl-C for copy, Ctrl-V for paste, etc.?

---

### Post by WorMzy on 2010-11-14
I know this may not be the solution you're looking for, but Alt-Backspace deletes a word, Ctrl+Shift+C copies your selection, and Ctrl+Shift+P pastes your clipboard contents. There may be a way of mapping these functions to the key strokes you prefer, but I don't know you'd do this.

---

### Post by cool-RR on 2010-11-14
Thanks WorMzy! That's helpful.

If anyone knows of a way to get standard shortcuts for these actions, I'd be happy to hear.

---

