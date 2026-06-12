---
title: "Another environment variable question: LANG"
date: 2009-08-26
forum: General Help
---

### Post by dmonkey on 2009-08-26
OK so I'm pretty exhausted. After reading the very nice information at

[https://help.ubuntu.com/community/EnvironmentVariables]("https://help.ubuntu.com/community/EnvironmentVariables")

I thought that I was in a position to once and for all set the LANG variable to something that wouldn't mess things up every time I tried to compile C code or use SVN. So I did the following: I added the line

LANG="C"

to /etc/bash.bashrc. So far, so good, since now I can compile C code and use SVN in a terminal without messages about LANG being set incorrectly being posted to my screen. Then comes the problem. I like to start emacs by using

Alt+F2 emacs ENTER

The problem with this is that it does not seem to "see" the environment variables set by bash.bashrc. Put it in /etc/profile you say? Did that, no help. "Oh, but you should have put it in /etc/environment". Nope, no good. "Ah, the problem is that you need to change /etc/default/locale, and then all is well". Unfortunately not.

So, the question after my lengthy diatribe is, where (in hell) might one override this bloody LANG variable once and for all, so that no mention of this "en_GB.UTF-8" is ever seen again.

And yes, I do know that if I wanted to I can just run emacs from a terminal window and have all the environment vars inherited, or replace emacs exec with a small script that essentially does the same, or in fact any other variation on this theme, but I actually do want to DESTROY this variable and send it back to hell from whence it came. Help is appreciated.

---

### Post by dmonkey on 2009-08-27
*BUMP* So is it really that hard?

---

