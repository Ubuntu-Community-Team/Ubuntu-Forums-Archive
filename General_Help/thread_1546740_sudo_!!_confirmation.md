---
title: "sudo !! confirmation"
date: 2010-08-05
forum: General Help
---

### Post by Folk Theory on 2010-08-05
In Ubuntu, When i type sudo !! and hit enter, the new command will appear on the command line, instead of simply executing.

This is different from other operating systems I've used, such as older ubuntu's, mac osx and debian.

Is there a way of disabling this confirmation and having it simply execute the command?

---

### Post by clhsharky on 2010-08-05
Folk Theory


> Is there a way of disabling this confirmation and having it simply execute the command?
Yes, but not recommend.

I cant help you as I use sudo as install by default,  but have seen many threads ,just search forum.

Sharky

---

### Post by WorMzy on 2010-08-05
I don't think OP is complaining about the password prompt, but rather the way that !! recalls the previous command. It prints the command that it's running before executing. I think that the output is coded into the shell itself; both zsh and bash have the same behaviour, while dash doesn't even recognise the command. Unfortunately I don't know how to surpress the output, and a google search is less than helpful.

---

### Post by lisati on 2010-08-05
Perhaps an alternative is using the up arrow to recall the previous command, and then editing the command line to include sudo if required.

---

