---
title: "POP pasword required all of a sudden in Evolution"
date: 2012-01-22
forum: General Help
---

### Post by beanco on 2012-01-22
Hi Everybody,

I am on  Ubuntu 10.10 with a HP laptop.

When trying to check my new emails in Evolution I get the *Please enter the POP password for XXXXX.

I have no idea why this is popping up.. I did not make any changes and I did not have any problems with is previously.

Any ideas?


Thanks

Rob

---

### Post by dcstar on 2012-01-23
> **beanco said:**
> Hi Everybody,

I am on  Ubuntu 10.10 with a HP laptop.

When trying to check my new emails in Evolution I get the *Please enter the POP password for XXXXX.

I have no idea why this is popping up.. I did not make any changes and I did not have any problems with is previously.

Any ideas?


Did you put the password in?

---

### Post by 3rdalbum on 2012-01-23
If the mail server is having some downtime or problems, it might send back the "Authentication Error" message. Evolution assumes that this means that the password is incorrect; this isn't necessarily what's happened.

In short, the problem is probably at the mail server end, and it will probably be fixed pretty quickly. If you still have this trouble tomorrow where it is not accepting your password, then you could try going into the Evolution settings and changing the authentication type for POP. There are several types and it's possible that the server administrator has changed the one that the server uses.

Most mail programs can figure it out on their own, but for some reason Evolution needs to be told. So you might need to try changing the Authentication Type in Evolution and seeing if this fixes the problem.

---

### Post by beanco on 2012-01-24
Thanks Guys,

I enteredt eh password and got in, that was no problem.. ...

I just did not understand why it was happening.

AFter my original post, I remembered that this happened to me about a month or two ago as well... it went on for several days.. ... That's actually when I was just about to upgrade to this version of Ubuntu... Immediately following the upgrade things were fine until now.


Robi

---

### Post by beanco on 2012-07-10
It's back again!

Just started this morning. No idea why... 

I am still on Meerkat... been meaning to upgrade but I really do not think that is the reason Evolution is doing this, .... Or is it?

Robi

---

