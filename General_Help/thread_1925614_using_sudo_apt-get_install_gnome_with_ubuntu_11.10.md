---
title: "using sudo apt-get install gnome with ubuntu 11.10"
date: 2012-02-14
forum: General Help
---

### Post by dellboy on 2012-02-14
hi i coming back to Ubuntu after an while away form it as i  mostly use mac know adays but my company needs more computers and we dont need them all to be macs so we where thinking off having the other computers as ubuntu computers as we dont need windows and because we dont want the problems that gose with it windows?

but i think for now till i get used to unity my self as the main admin am i right in thinking off if i install gnome via sudo apt-get install gnome and use the gear at the login screen to chose gnome if i need it for an while till i am used to unity i can still get full support form ubuntu and all the updates with out it bricking and messing up ? so in other words i am ok to use gnome in this way but being an mac user i think i could get use to unity it will just take an bit off time and i can see once you how to use it can be an lot faster and also give more room to work with its could be great.

thank you again for your help

---

### Post by cortman on 2012-02-14
> **dellboy said:**
> hi i coming back to Ubuntu after an while away form it as i  mostly use mac know adays but my company needs more computers and we dont need them all to be macs so we where thinking off having the other computers as ubuntu computers as we dont need windows and because we dont want the problems that gose with it windows?

but i think for now till i get used to unity my self as the main admin am i right in thinking off if i install gnome via sudo apt-get install gnome and use the gear at the login screen to chose gnome if i need it for an while till i am used to unity i can still get full support form ubuntu and all the updates with out it bricking and messing up ? so in other words i am ok to use gnome in this way but being an mac user i think i could get use to unity it will just take an bit off time and i can see once you how to use it can be an lot faster and also give more room to work with its could be great.

thank you again for your help

Unity is basically just a gnome plugin. Gnome comes bundled with Ubuntu, both in the up-to-date form and a fallback (gnome 2-esque) session. Like you said, click on the gear at the login screen and select your DE.

---

### Post by forrestcupp on 2012-02-14
What you want is Gnome Shell, not Gnome. Ubuntu already has Gnome installed underneath Unity. Try:

```
sudo apt-get install gnome-shell
```That should also get you Gnome Classic, which is supposed to be more like the old Gnome 2 desktop.

---

### Post by dellboy on 2012-02-15
so if have used sudo apt-get install gnome  i will still get all the updates and i can use the gear to chose if i just want normal gnome and this way when ubuntu comes to update norting will go wrong and i thought if you install gnome as the shell you cant update to the newest version or am i wrong ?

---

### Post by forrestcupp on 2012-02-15
> **dellboy said:**
> so if have used sudo apt-get install gnome  i will still get all the updates and i can use the gear to chose if i just want normal gnome and this way when ubuntu comes to update norting will go wrong and i thought if you install gnome as the shell you cant update to the newest version or am i wrong ?

In 11.10, there is no old version of Gnome at all. In this release, Gnome 3 with Gnome Shell *is* Gnome. Ubuntu comes with Gnome preinstalled because Unity uses Gnome, but it doesn't come with Gnome Shell by default.

In the releases before 11.10, Gnome Shell and Gnome 3 had to be installed with a PPA, and things didn't work as smoothly. Now, with 11.10, Gnome 3 and Gnome Shell are included in the repos, and everything works fine. So if you install Gnome Shell, you will still get updates just fine.

Just to reiterate, you need to **sudo apt-get install gnome-shell**, not just Gnome. Gnome is already installed. In that gear thing you're talking about, you won't get the options for Gnome Shell or Gnome Classic until you install Gnome Shell. And remember that Gnome Classic is not the old Gnome2 DE. It's Gnome3 with Gnome Shell that has been made to look like the old Gnome2. There's no Gnome2 anymore.

---

