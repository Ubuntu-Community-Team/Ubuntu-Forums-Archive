---
title: "No Suspend Option"
date: 2010-05-20
forum: General Help
---

### Post by Irrelephant on 2010-05-20
I recently installed 10.04 LTS and I have no option to suspend my desktop.  I have always had the option before.  I have Ubuntu installed on two other machines that can all suspend.  Has this happened to anyone else?  Could it be hardware or would a re-install fix the issue?

---

### Post by ubunterooster on 2010-05-20
Does this computer have SWAP space?

---

### Post by Irrelephant on 2010-05-20
> **ubunterooster said:**
> Does this computer have SWAP space?

I believe it does.  I let the installer do the partitions, and under system monitor it shows 17.1GB of swap.  Although I am not sure if this is exactly what you mean?

---

### Post by ubunterooster on 2010-05-20
That was what I meant. Hmm, are all of the computers you use ubuntu on Lx11 (lubuntu) or are the others gnome (regular ubuntu)? I can't remember if lx11 has the option to suspend/hibernate.

I hope someone else can be more helpful quickly as I am currently literally to tired to think straight.

---

### Post by pqwoerituytrueiwoq on 2010-05-20
gonf-editor
/apps/indicator-session/suppress_logout_menuitem
make sure it is not checked

---

### Post by Irrelephant on 2010-05-21
> **pqwoerituytrueiwoq said:**
> gonf-editor
/apps/indicator-session/suppress_logout_menuitem
make sure it is not checked

It's not checked

---

### Post by Irrelephant on 2010-05-21
> **ubunterooster said:**
> That was what I meant. Hmm, are all of the computers you use ubuntu on Lx11 (lubuntu) or are the others gnome (regular ubuntu)? I can't remember if lx11 has the option to suspend/hibernate.

I hope someone else can be more helpful quickly as I am currently literally to tired to think straight.

I appreciate the help.  As far as I know all the computers I have installed ubuntu on are not Lx11, they are gnome.  I'm don't want to, but I might just do a fresh install and see if that fixes the issue.  I'll see if the live CD shows suspend as an option.

---

### Post by ubunterooster on 2010-05-21
just add the Ubuntu-desktop via synaptic and log in to that one; don't reinstall.

Edit: this is not the same as a dual-boot

---

