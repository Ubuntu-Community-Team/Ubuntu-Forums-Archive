---
title: "is it possible to run server and desktop at the same time"
date: 2010-01-06
forum: General Help
---

### Post by jwxie on 2010-01-06
I have a dual boot - server edition and desktop on the same computer.

I don't want to use GUI (minimize the resource), so I MUST use server edition. (IT IS A MUST, sorry... I know I can run server on desktop)

Is it possible to run both server and desktop on the same screen? 

Or...  virtual?? Maybe??

---

### Post by teward on 2010-01-06
nope.

---

### Post by jwxie on 2010-01-06
> **TrekCaptainUSA said:**
> nope.

then how does virtual box really works?

let say i install it on my desktop edition
can i switch back to desktop while letting the server edition running in the background?

---

### Post by dcstar on 2010-01-07
> **jwxie said:**
> then how does virtual box really works?

let say i install it on my desktop edition
can i switch back to desktop while letting the server edition running in the background?

You either look in the Virtualization forum or web search the question.

---

### Post by tripolitan on 2010-01-07
You shouldn't, but you can. I have a desktop running on server packages/kernel.

boot into your server and, apt-get install the desktop packages (start with ubuntu-minimal, ubuntu-standard, xorg then ubuntu-desktop and all their dependencies)  you must have main,restricted universe and multiverse repositories setup.

Once everything is installed (or before) you might want to reclaim hard drive space that was occupied by the desktop distro.

---

