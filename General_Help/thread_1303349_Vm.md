---
title: "Vm?"
date: 2009-10-28
forum: General Help
---

### Post by Anonymousable on 2009-10-28
Does anyone know a VM that works on ubuntu other than qemu?

I tried that, and it was hellishly slow running 32-bit ubuntu.

Any ideas why, or suggestions for others?

VirtualBox is also no-go.

---

### Post by yeats on 2009-10-28
> VirtualBox is also no-go.

So, what are the specs of the machine you're running?  Perhaps your memory is limited...?

---

### Post by kellemes on 2009-10-28
> **Anonymousable said:**
> VirtualBox is also no-go.

Why?
I never found anything better.

---

### Post by Anonymousable on 2009-10-28
> **chrissharp123 said:**
> So, what are the specs of the machine you're running?  Perhaps your memory is limited...?
Meh, it obviously doesn't display my signature... >.>
4GB RAM, Intel Core 2 Quad Q8200 2.33GHz, nVidia GeForce 7300GS.
> **kellemes said:**
> Why?
I never found anything better.
Hmm... It just didn't work for some reason.

---

### Post by kellemes on 2009-10-28
> **Anonymousable said:**
> Meh, it obviously doesn't display my signature... >.>
4GB RAM, Intel Core 2 Quad Q8200 2.33GHz, nVidia GeForce 7300GS.

Hmm... It just didn't work for some reason.

Since specs is no issue you need to find the problem with Virtualbox, you won't find anything easier or faster. Speed with VirtualBox should be near-native.

---

### Post by yeats on 2009-10-28
> Hmm... It just didn't work for some reason.

What is it (not) doing?

---

### Post by Anonymousable on 2009-10-28
Well, the problem with virtualbox was I couldn't get it up and running.

---

### Post by kellemes on 2009-10-28
> **Anonymousable said:**
> Well, the problem with virtualbox was I couldn't get it up and running.

My advise:
Just give it another go and report back with your issues.

[https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

---

### Post by P4man on 2009-10-28
qemu emulates a cpu. Its bound to be slow, but it does let you run for instance PowerPC code on an x86 cpu. VMWare and Virtualbox dont do  such binary translation which makes them a LOT faster. Most apps (other than 3D stuff) will work close to native speed. 

In short, as mentioned above, fix your problem with virtualbox. Its in the repositories, install it from there and report any problems you would have.

---

### Post by Anonymousable on 2009-10-28
So using it, I *can* run 32-bit ubuntu all the same?

---

### Post by The Cog on 2009-10-28
> **Anonymousable said:**
> So using it, I *can* run 32-bit ubuntu all the same?

I'm not sure that that question meant. But I use VirtualBox on a 32-bit Ubuntu no problems. Unless you want the guest OS to access USB resources, it's probably easier to go for the version in the repositories (System->Administration->Synaptic) rather than the downloaded binary form the VB website.

---

### Post by P4man on 2009-10-28
> **Anonymousable said:**
> So using it, I *can* run 32-bit ubuntu all the same?

What do you mean? I guess any way I can read that question, the answer is yes. If you have a 32 or 64 bit host OS (ubuntu, windows or OS-X), you can run 32 bit ubuntu as guest in a VM, or 64 bit. Even the opposite is possible, you can run a 64 bit guest OS on a 32 bit host (provided the cpu supports 64 bit), but its not recommended.

---

### Post by Simian Man on 2009-10-28
I'd advise getting it right from th Virtualbox site rather than through the repositories.  The version Ubuntu ships is missing features and is out of date IIRC.

---

### Post by Anonymousable on 2009-10-28
Thanks for all the help. I've now tried again... It works, good speed, and I have no idea why it didn't work last time.

Are there any machine emulators that work like QEMU but are more efficient?

---

### Post by P4man on 2009-10-28
> **Anonymousable said:**
> Thanks for all the help. I've now tried again... It works, good speed, and I have no idea why it didn't work last time.

Are there any machine emulators that work like QEMU but are more efficient?

*Simulating *a cpu is never going to be anything remotely like efficient. Never ever. Its a miracle it even works.  Binary translation in software can be somewhat efficient (remember FX32 on Alpha CPUs) and can be fairly efficient with the right hardware support (think transmeta crusoe).

---

### Post by cb951303 on 2009-10-28
Try KVM instead of Qemu. Same application with virtualization capabilities.

---

### Post by Anonymousable on 2009-10-29
OK, I have all my questions answered - thanks for the help!

---

