---
title: "Configuring GRUB-PC"
date: 2010-03-01
forum: General Help
---

### Post by klasjosh30 on 2010-03-01
I was installing updates and after this popped up, what do I do?

my pc is dual booted with windows 7 and ubuntu.

[IMG]http://i303.photobucket.com/albums/nn133/noway-fatcow/Screenshot-1.png[/IMG]

---

### Post by oldos2er on 2010-03-01
Which version of Ubuntu are you running? If there's a kernel update, you'll want to choose 'install package maintainers' version' (or words to that effect).

---

### Post by klasjosh30 on 2010-03-01
> **oldos2er said:**
> Which version of Ubuntu are you running? If there's a kernel update, you'll want to choose 'install package maintainers' version' (or words to that effect).

There was that option but I just clicked "Keep the locally version currently installed"

EDIT: I have ubuntu 9.10

---

### Post by oldos2er on 2010-03-02
Then you'll need to manually edit /etc/default/grub to add the new kernel.

---

### Post by Kingfield on 2010-10-19
How would you do that? im currently upgrading and i made the same mistake... could you help me? pretty urgent

---

### Post by Mecasickle on 2010-10-19
type in

$ sudo update-grub

---

