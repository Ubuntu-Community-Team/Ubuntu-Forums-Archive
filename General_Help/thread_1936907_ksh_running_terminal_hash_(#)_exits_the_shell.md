---
title: "ksh running terminal: hash (#) exits the shell"
date: 2012-03-06
forum: General Help
---

### Post by rpaskudniak on 2012-03-06
This is WILD! :mad:

Under Ubuntu (where I am cross-posting this problem) I have lately noticed by terminal windows/tabs closing unexpectedly. I finally caught it: I was composing a complicated command so I practices it a few times commented out - that is, with a # at the start of the line. What is now happening is as follows:

    If I start the line with #<white-space> i.e. a space or tab following the #, the shell abruptly exits.
    If I start with the # and a letter, say l, it traces down my history for all old commands that started with l. When I add a letter to that - e.g. s, the list is pared down to all old commands [in my history] that had started with ls. As soon as my typed comment becomes fails to match anything in my history, it exits.
    If there are any command lines in my history that did start with blanks (I've been experimenting) it pops those up, paring the list as I type characters, until it hits something not in my history. Then it exits. This is essentially the same as my point above.

This appears to be a bizarre setting or option in my history; that the hash activates a history search.

I don't want it! What is it and how do I turn it off? ](*,)

The version I'm using is "Version JM 93u 2011-02-08".

This does not happen with bash; the first time I have found bash behaving better than ksh. Furthermore, after searching the ksh man page, it occurred to me to set -o emacs and try it. I still get the history search but it does not exit the shell upon confirmed mismatch.

Thanks for diagnosis/advice/help.

---

### Post by Khayyam on 2012-03-06
For ksh, zsh, bash (all the bourne family shells) "#" serves the same function, a comment, so I'm not sure what is happening in your case. History search is cntr -r so its difficult to see how a history search was run in absence of it being called. Do you have your own .kshrc, if so, perhaps move it to one side and use the system default and see if the problem persists, you'd then be able to narrow the problem down to something in the rc, and not an actual bug with ksh.

Also, have you tryed to reproduce this with another terminal?

best ... khay

---

### Post by rpaskudniak on 2012-03-06
Khayyam,
I have been working almost exclusively with ksh as my shell for many years, on many flavors of Unix/Linux, including Ubuntu since release 9.4.  This is totally new to me and I only realized the pattern a few minutes before I posted my missive.  (Hey, it's actually shorter than most of my posts; I'll take that beer!)

My whole .kshrc is two aliases.  No, this is a new shtick.

---

### Post by Khayyam on 2012-03-07
> **rpaskudniak said:**
> I have been working almost exclusively with ksh as my shell for many years, on many flavors of Unix/Linux, including Ubuntu since release 9.4.  This is totally new to me and I only realized the pattern a few minutes before I posted my missive.  (Hey, it's actually shorter than most of my posts; I'll take that beer!).My whole .kshrc is two aliases.  No, this is a new shtick.

It was a longshot on my part. I'm not a ksh user and so it was advice given without being able to even attempt to reproduce.

The beers are on me ... cheers! ... khay

---

### Post by kevdog on 2012-03-07
Could you make an alias for it?

---

