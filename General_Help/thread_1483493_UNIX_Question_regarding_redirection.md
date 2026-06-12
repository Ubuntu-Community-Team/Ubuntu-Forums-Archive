---
title: "UNIX Question regarding redirection"
date: 2010-05-14
forum: General Help
---

### Post by nelio2k on 2010-05-14
Hi guys,

I have a question about UNIX shell in general.
I understand that when we redirect STDIN, we usually do it after a call.
For example...

   $ echo foo < /dev/null  > /tmp/bar 2>&1

My question is, will I be able to move the "< dev/null" to the front?

   Does:
   $ echo foo < /dev/null  > /tmp/bar 2>&1

   performs the same thing as:

   $ < /dev/null echo foo > /tmp/bar 2>&1
   

I'm trying to do some automation and for Interix running SUA, I need to redirect STDIN whenever I do a redirection of a STDERR, else the SUA will crash. This is for Windows 2008 R2 SUA.

I figured I'll ask this UNIX question here for any of you UNIX experts.

Thanks.

---

### Post by gmargo on 2010-05-14
> **nelio2k said:**
> My question is, will I be able to move the "< dev/null" to the front?


I'm not sure what you are trying to accomplish, but that would not be valid syntax.  But you could use cat to feed the stdin through a pipe, like:
```

cat < /dev/null | echo foo > /tmp/bar 2>&1

```(Of course, "echo foo" ignores it's stdin, but I assume that is rhetorical.)

---

### Post by -humanaut- on 2010-05-14
I'm some what familiar with Solaris Unix I don't think < ***** > would return anything but an error atleast in KSH. what shell are you using?

---

### Post by nelio2k on 2011-02-03
Thanks for helping. I think there was a Windows box running SUA that I'm trying to talk to via RSH and the connection would hang if I do some redirection. I've avoided that for now.

---

