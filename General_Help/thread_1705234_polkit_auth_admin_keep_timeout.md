---
title: "polkit auth_admin_keep timeout"
date: 2011-03-11
forum: General Help
---

### Post by nixahn on 2011-03-11
I am wondering if there's a way to change the timeout of the auth_admin_keep "behavior" in polkit; I'm sorry if I use the word "behavior" but the polkit documentation is very obscure in terms of what to call it. I am not looking to edit an action and change say "auth_admin_keep" to "auth_admin" or "yes". What I want is to change the amount of time it takes for the retained privilege to expire; I understand this is specific, but polkit has no forum online and google just shows threads where people disable the authorization requests, which I consider dangerous. All I want is to be able to control the timeout, extend it a bit to something like 15 minutes, so that when I'm working in admin stuff I don't go crazy typing the password; I hope someone out there can help me out.

---

### Post by sisco311 on 2011-03-15
Hi and welcome to the forums!

As far as I know, the timeout is hard coded, so you can't change it without recompiling policykit.

EDIT: Yep, it's hard coded in  policykit-1-*version*/src/polkitbackend/polkitbackendinteractiveauthority.c:
```
...
  /* [COLOR="Red"]TODO: right now the time the temporary authorization is kept is hard-coded[/COLOR] - we
   *       could make it a propery on the PolkitBackendInteractiveAuthority class (so
   *       the local authority could read it from a config file) or a vfunc
   *       (so the local authority could read it from an annotation on the action).
   */
  **expiration_seconds = 5 * 60**;
...
```

Hopefully they will fix this soon. ;)

---

### Post by fitzhugh on 2012-01-28
That is a great find, though I don't like the answer. I find the timeout so annoying, defeats the purpose since I end up resetting all the policies to "yes". There should be a "once" option or something... one that says you have to enter the password once per session.

Again, thanks for finding the answer.

---

