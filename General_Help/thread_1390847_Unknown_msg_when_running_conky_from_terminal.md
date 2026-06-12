---
title: "Unknown msg when running conky from terminal"
date: 2010-01-26
forum: General Help
---

### Post by houserparker on 2010-01-26
Does anybody know what this means or how to fix it?

ben@ben-laptop:~$ conky
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.
ben@ben-laptop:~$

Thanks in advance

---

### Post by KeLa on 2010-01-26
There is something wrong in your .conkyrc file.
I got many error messages like this before i could find all mistakes/errors from config file.

---

### Post by houserparker on 2010-01-26
> **KeLa said:**
> There is something wrong in your .conkyrc file.
I got many error messages like this before i could find all mistakes/errors from config file.

Thanks for your reply. 

I wish it was just the .conkyrc but it was running fine with the .conkyrc the way it is and nothing had changed before i removed what i thought were unused libraries..

Does anyone have any other ideas?

---

### Post by rnerwein on 2010-01-26
> **houserparker said:**
> Thanks for your reply. 

I wish it was just the .conkyrc but it was running fine with the .conkyrc the way it is and nothing had changed before i removed what i thought were unused libraries..

Does anyone have any other ideas?

hi
you sayd you removed som unused libraries.
try: ldd /usr/bin/conky
and you'll see if they was realy unused !
ciao

---

