---
title: "synaptic package manager and add\remove dont work"
date: 2009-08-16
forum: General Help
---

### Post by tanindigo on 2009-08-16
as i said:synaptic package manager and add\remove dont work.When ever i try to use synaptic it says:
[IMG]http://img201.imageshack.us/img201/6853/snapshot1hzt.png[/IMG]
It says this in xubuntu and ubuntu.[i haven't checked kubuntu]
Also Add/remove gives me the same error message.
Anyways how do i go about fixing this?

---

### Post by plucky on 2009-08-16
Have you tried doing what it says?

Open a terminal **Applications > Accessories > Terminal** and input ```
sudo dpkg --configure -a
``` and see what that does.Then try ```
sudo apt-get update
``` and post output to forum if any errors occur.

Good Luck

---

### Post by tanindigo on 2009-08-16
First line of code worked.
Thanks!

---

