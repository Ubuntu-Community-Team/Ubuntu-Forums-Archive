---
title: "virtualbox not recognizing usb... lucid"
date: 2010-07-26
forum: General Help
---

### Post by owners4life5 on 2010-07-26
hello,

can anyone tell me how i can get my virtualbox to recognize my usb?

thanks

---

### Post by CharlesA on 2010-07-26
What version are you using? The OSE or the "non-free" version from virtualbox.org?

---

### Post by owners4life5 on 2010-07-26
i got it off of their website... so i guess the non-free version... but it was free.. if that makes sense

---

### Post by lukeiamyourfather on 2010-07-26
If you got it from their website its the non-free version and should see USB devices. Have you specifically forwarded the device to the virtual machine (in the toolbar at the top of the virtual machine)? If you don't specifically forward devices to the virtual machine they will not be usable. Cheers!

---

### Post by CharlesA on 2010-07-26
Yeah, makes sense.

Open virtualbox and select whatever VM you want to add a usb device to and then click on USB and add a device filter from there. It'll let the VM see that device.

---

### Post by lukeiamyourfather on 2010-07-26
Also I think the guest needs the VirtualBox additions, if the guest is Ubuntu those are in the repository. For other guests you'll need to install them manually. 

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

---

### Post by CharlesA on 2010-07-26
Yeah, you need the guest additions installed as well. You can install them from the the "devices" menu.

---

### Post by owners4life5 on 2010-07-26
thanks guys. worked like a charm. marking as solved.

---

### Post by VH-BIL on 2010-07-26
Run VirtualBox with sudo to use it with USB. It is weird because you do not have to do this in VMware.

---

### Post by bowens44 on 2010-07-26
> **VH-BIL said:**
> Run VirtualBox with sudo to use it with USB. It is weird because you do not have to do this in VMware.

You don't need to run it with sudo to use it with USB. Just be sure that you are a member of the virtualbox user group.

---

### Post by lukeiamyourfather on 2010-07-26
> **CharlesA said:**
> Yeah, you need the guest additions installed as well. You can install them from the the "devices" menu.

Is there an echo in here or is it just me? :-k

---

### Post by VH-BIL on 2010-07-26
> **bowens44 said:**
> You don't need to run it with sudo to use it with USB. Just be sure that you are a member of the virtualbox user group.

Thanks so much, I have always had a sudo VirtualBox set up for this. Always learning, I love this forum :)

---

