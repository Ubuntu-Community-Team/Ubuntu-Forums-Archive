---
title: "Pidgin issue (Error 0x0024)"
date: 2010-07-25
forum: General Help
---

### Post by altjx on 2010-07-25
Anyone ever get this error when logging on to their AIM account?
```
Error Changing Account Info

Error 0x0024: Unknown error.
```

I can reproduce the issue just by simply unchecking the AIM account to logoff, and then checking it again to logon.

---

### Post by Z3ro3X on 2010-09-16
> **altjx said:**
> Anyone ever get this error when logging on to their AIM account?
```
Error Changing Account Info

Error 0x0024: Unknown error.
```

I can reproduce the issue just by simply unchecking the AIM account to logoff, and then checking it again to logon.
I get the same error when my friend signs on her @aol.com account on my computer on the same Linux account but not when I sign on my AIM account.

---

### Post by Dexi on 2010-11-15
> **altjx said:**
> Anyone ever get this error when logging on to their AIM account?
```
Error Changing Account Info

Error 0x0024: Unknown error.
```

I can reproduce the issue just by simply unchecking the AIM account to logoff, and then checking it again to logon.

This has been plaguing me for a while. I did a little googling and a little creative thinking. Check your capitalization and spacing in the username.

---

### Post by red_five on 2011-01-19
I agree with Dexi. I've been having the same problem for several days. I've had my AIM screen name for over a decade, and I've always entered it in CamelCase. 2 minutes ago, I tried it in all lower-case, and no more error.

---

### Post by rockerZ71 on 2011-02-19
Thanks, that fixed it for me as well.

---

### Post by h2oman256 on 2011-03-18
This is an old thread but it is also top on google so I am leaving this here hoping people will find it. Another cause for this issue was the domain suffix. Removing @aol.com from the username did it for me. so:

Original: [email]example@aol.com[/email]

fixed: example

---

### Post by hifly1231 on 2011-08-19
> **h2oman256 said:**
> This is an old thread but it is also top on google so I am leaving this here hoping people will find it. Another cause for this issue was the domain suffix. Removing @aol.com from the username did it for me. so:

Original: [email]example@aol.com[/email]

fixed: example

It won't let me remove the @aol.com from my username.

---

