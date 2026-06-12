---
title: "How to change screen size of my Ubuntu server (vmware)"
date: 2012-05-14
forum: General Help
---

### Post by agrayray on 2012-05-14
i created an ubuntu 10.4.4 server as a vmware virtual machine with vmtools installed...boots up to console just fine...however it always seems to be stuck in 640x480.

Has anyone else done this and figured out how to resize the screen?

I dont have x11 installed nor want it in this case just want a nice big console screen and get out of 480x mode?

so..is there a way I can set this manually?

not sure what resolution my monitor supports as i have tried adding vga=ask  and a cpl other GRUB vga settings in my /etc/default/grub file but still it keeps coming up in 640x480...?

Thanks in advance.

---

### Post by raja.genupula on 2012-05-14
[http://askubuntu.com/questions/86561/how-can-i-increase-the-console-resolution-of-my-ubuntu-server](http://askubuntu.com/questions/86561/how-can-i-increase-the-console-resolution-of-my-ubuntu-server)

try that one ,:)

---

### Post by coldraven on 2012-05-14
I read lots of threads about that problem but I could not get it to work. In the end I just log in to the server with PuTTY. One benefit is that you can copy and paste the code that you find on the internet.

---

### Post by agrayray on 2012-05-18
Yep...after so many days I give up too...plus frustrated that I posted it several times on vmware fourm with no replies...thanks to the ones here :) !!!

I have tried making those changes in /etc/grub but each time it just boots up to black screen after the vmare bios flashes...

If anyone ever comes up with something that works please pass on..i figure there's gotta be lots of folks using server with vmware and not sticking to that small text area (even if you stretch the screen).

Thanks again all!

---

### Post by Cheesemill on 2012-05-18
> **agrayray said:**
> i figure there's gotta be lots of folks using server with vmware and not sticking to that small text area

I'm guessing that's because they all connect using ssh instead.

---

