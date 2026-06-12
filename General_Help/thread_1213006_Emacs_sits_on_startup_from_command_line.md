---
title: "Emacs sits on startup from command line"
date: 2009-07-14
forum: General Help
---

### Post by InkyDinky on 2009-07-14
I'm remotely logging into my home computer via ssh (using SecureCRT as the ssh client...its what is installed at school). After running gnu screen on the school unix machine and then sshing into my home computer when I try to run emacs it just sits there at the command line.  I'm pretty sure it has to do with how SecureCRT handles the error messages or messages sent back to SecureCRT.  I've come to this conclusion as using putty as the client and performing the same steps produces no such problems.  However I do not see an X11 forwarding error like SecureCRT was displaying.  I'm not sure what putty does with the error or if it handles such problems more gracefully somehow.

I hope this anyone with similar problems.

Nick

Here is the original post:
I've been remotely logging in to my home computer to work on my thesis. Just recently (Friday?? I think) when invoking emacs from the command line emacs just sits and hangs showing ```
nicolae@nicolae-desktop:~/Documents/svncontrolled/puthesis$ emacs introduction.tex
```
and never shows the textual curses-like interface.
I am running screen from the school *nix machine to run multiple windows from the command line and then sshing into my home computer.  I am using SecureCRT as the *nix terminal client.
Strangely enough when I do *not* use screen emacs starts up fine. 
SecureCRT does pass on the warning that a X11 forwarding request is being rejected.  This didn't show up when using screen.
I'd like to continue to use screen as it is forgiving when I forget to save things and the ssh connection times out on me.
If the X11 warning message is the culprit is there a way to suppress it?
If that isn't the culprit what is the best way to debug to find out what is causing the hiccup.

Thanks,
Nick

---

### Post by InkyDinky on 2009-07-17
Also when using SecureCRT I'd have to use the ESC key for Meta in emacs whereas I can use the Alt key when I use putty.

---

