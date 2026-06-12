---
title: "Issues authentication Softwarecenter ..."
date: 2010-10-20
forum: General Help
---

### Post by benste on 2010-10-20
HI guys, I'm getting error messages or a password querry withouht entry box, if i want to apply admin changes on my system in gui tools

e.g.
[LIST]
[*]Software Center
[*]Language Settings
[*]free - gdm settins
[*]users & groups
[/LIST]

gksu and sudo are working with my user - it was the 1st user on the system, today i got the following message:
> org.freedesktop.PolicyKit.Error.NotAuthorized: ('system-bus-name', {'name':  ':1.122'}): org.debian.apt.install-or-remove-packages

and sometimes the box apears multiple times and shakes like it does if entering a wrong password - and ends up with failed

I'd be pleasant to get some help as it looks like most of the people in the german IRC don't know what to do as they thought like me these software parts would use gksu

---

### Post by gokulvarma on 2010-10-20
[How to fix software center problem in ubuntu 10.10]("http://open-help.blogspot.com/2010/10/how-to-fix-software-center-problem-in.html")

Hope it helps you

---

### Post by benste on 2010-10-20
You're absolutely right, if I'd change everyhing in gksu i would be able ot get in. but i could also use APT or something else on the command line, my question is about solving this issue that i can't use the default GUI tools, which is kinda annoying

---

