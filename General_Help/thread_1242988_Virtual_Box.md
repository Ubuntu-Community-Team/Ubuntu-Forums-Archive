---
title: "Virtual Box"
date: 2009-08-17
forum: General Help
---

### Post by BrandonArchangel on 2009-08-17
I am going to install Ubuntu with the program Virtual Box and the only thing I am curious about is the RAM and HD space required. I have plenty 4gb and 240 gb. But what does virtual box do with the space i give it? Does it take the RAM only when running the virtual ubuntu or does it take it all together? Same with the hard drive space. If so do I get it back when i uninstall virtual box or what?

---

### Post by ssanders4917 on 2009-08-17
It only uses it when you are running your virtual session. It uses drive space in 2 ways; either the size you give it all at once or it gives up space as you need it. I forget the name for it.

---

### Post by howefield on 2009-08-17
You VMs will only use ram when loaded, and release it back to the host when you shut down the VM.

The space you allocate to the vm hard disk will stay on the disk, as ssanders4917 said, there are two ways to do this, firstly by allocating a set amount of space to the virtual drive, say 10 gig which will use up 10 gigs, funnily enough, or by creating a dynamically expanding drive which as the name suggests will start small and grow as your vm needs it up to a predefined maximum that you set when creating the vm.

The dynamically expanding option takes a slight hit on performance, but whether you would notice it or not is debatable.

---

### Post by BrandonArchangel on 2009-08-17
So how do I retain the hard drive space, or does it just never leave basically? Thanks to both of you, it is greatly appreciated.

---

### Post by howefield on 2009-08-18
> **BrandonArchangel said:**
> So how do I retain the hard drive space, or does it just never leave basically?

Not sure what you mean ?

Eg, once you have created your virtual machine hard disk, you will see it as a file in your ./Virtualbox folder (assuming you select the default path - you can create the virtual disk on a seperate partition or disk if you wish).
 
This file won't go away unless you delete it.

---

### Post by BrandonArchangel on 2009-08-18
Thanks all I needed to know.

---

