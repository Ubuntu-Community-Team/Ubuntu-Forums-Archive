---
title: "running 2 OSs at once"
date: 2009-12-19
forum: General Help
---

### Post by aeon.flux on 2009-12-19
hello, i have a spacefic question and don't know where to ask or even what to search for, so that's why i'm asking here.  :confused:
few weeks ago i've seen a girl who was usig a macbook with mac OSX and she needed some windows soft, so she used windows. but she told that she's running both systems at once. so my question is how to run both systems at once? i heard about wmware player and used it for few days, but i was too slow. is there any other way how to do that? actualy i'm using dual boot (win7+9.04) and sometimes i need to use both of them but restarting the system is too slow. i have pavilion dv6000 with dual core 1,7GHz and 2,5GB ram and i need it for modeling cars in 3Ds max, maya, rhino...

thanx a lot

---

### Post by jpeddicord on 2009-12-19
Moved to General Help. (Tutorials & Tips is not a place to ask questions.)

---

### Post by dcstar on 2009-12-19
> **aeon.flux said:**
> 
........
few weeks ago i've seen a girl who was usig a macbook with mac OSX and she needed some windows soft, so she used windows. but she told that she's running both systems at once. so my question is how to run both systems at once? i heard about wmware player and used it for few days, but i was too slow. is there any other way how to do that?


No is the simple answer. There are other VMs apart from VMware, look in the Virtualization forum.

---

### Post by Darael on 2009-12-19
By "both systems at once", she could only mean using a virtual machine. There is simply no other way. On a mac, that's most likely to have been Parallels, an Linux you've got masses of choice.

---

### Post by aeon.flux on 2010-01-07
thanx a lot, im using vmware :)

---

### Post by Lars Noodén on 2010-01-08
@ aeon.flux : you might want to look into upgrading to qemu or VirtualBox.  Both are Open Source and very easy to use.  

qemu-launcher is the name of the gui for qemu.  It also supports a fairly wide variety of architectures in case you would later like to get into trying some of the mobile and mobile phone distros written for arm or mips.

---

### Post by bodhi.zazen on 2010-01-08
qemu is much slower then VirtualBox.

If you have the hardware , go for KVM.

Light weight "bare bones" alternates include Xen and OpenVZ, but thes two are a little more technical and OpenVZ will not run Windows (not sure about Xen).

---

### Post by lincoln32 on 2010-01-08
another vote for virtualbox I love it and have it it several machines
but seldom use it as i have found linux programs  but keep VB just test win systems PS download from sun to get the fully featured version

---

### Post by chriswyatt on 2010-01-08
I'm sure I saw something in a magazine once that let you dump each OS to memory (bit like suspending) as it switched between them, if you get what I mean.  Can't remember what it was called or if I've just made it up.

Of course, that's not running 2 at once but it's a half-way house.

---

### Post by aeon.flux on 2010-01-09
Thanx a lot, but i tried virtualbox. i was 'using' it for over a week, but i didn't found out, how to use usb keys or share folders between ubuntu(host) and win7(guest) system, so i've downloaded vmware player. My brother told me to use it, he uses it at work and it should be ok. So i can ask him if i'll have any problem(like usb, mouse with 8 buttons of lcd tablet). He said that vmware doesn't need that much ram and cpu as virtualbox. What do you think about that? Do you agree?

---

### Post by J V on 2010-01-09
Possibly true, but the fact that its propreitary makes it inferior by default...

in '08 vbox was the only virtualization that had enabled hardware acceleration, and its still the best :)

---

### Post by Lars Noodén on 2010-01-09
Also look at the package [qemu-kvm](http://packages.ubuntu.com/karmic/qemu-kvm) about KVM for qemu.  

With either one, it helps speed a lot to make sure that the VM, VM swap, host swap, etc are on different devices.  Otherwise they fight over the drive.

---

