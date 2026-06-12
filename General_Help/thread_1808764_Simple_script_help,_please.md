---
title: "Simple script help, please"
date: 2011-07-20
forum: General Help
---

### Post by Diametric on 2011-07-20
Hi,

I have been creating my first package and I need some help with a section.  In the %pre section of the package (yes, it's an .rpm, but I dig this site that much more than the Fedora site!) I would like this script to check if the named service is running, start it if it is not already running and make sure it runs upon a reboot.  I'm still working on my scripting skills; and while I can rock a mean "hello world" script, I think I'll need a little help here.

Thank you kindly...

---

### Post by Diametric on 2011-07-20
"None shall pass"?

---

### Post by galvatron408 on 2011-07-20
why are you using rpm to do that?

---

### Post by Diametric on 2011-07-20
Because I'm creating an rpm package.

---

### Post by galvatron408 on 2011-07-21
then, you'll probably want to make named a dependency

first part

if ! pgrep named; then
    #do your thing
fi

second part

/sbin/chkconfig named add
#not sure if you need this since i'm on ubuntu and can't test for you
/sbin/chkconfig named --level 2345 named on

---

