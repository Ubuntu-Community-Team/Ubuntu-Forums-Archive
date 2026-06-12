---
title: "VirtualBox 3.1.8 - Virtual Machine hangs during boot"
date: 2010-05-13
forum: General Help
---

### Post by pete_countryman on 2010-05-13
I recently installed VirtualBox 3.1.8 r61349 from the deb file virtualbox-3.1_3.1.8-61349~Ubuntu~lucid_amd64.deb onto a recent clean install of Lucid Lynx on my HP p6210f (6144 MB RAM, AMD Athlon II X4 620 CPU). I then imported a friend's VM and tried to boot it. The VM consistently hangs with the following showing on the console (this is the last 3 lines, for context):

NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
NET: Registered protocol family 2

I thought initially it was a problem with my friend's VM, so I decided to create a new VM from scratch, and boot from a CentOS-5.4-i386-DVD instead, which I have done before with previous versions of VirtualBox. When I do that, I'm able to select my installation method (so I know it's booting from the CentOS ISO), and then it hangs at exactly the same point. I couldn't find any other mention of this problem, but it's a pretty recent release of VirtualBox - I think just days old.

The VM: OS Type=RedHat (presumed 32-bit), 1 processor, 1024 MB RAM

Anyone else having this problem? Thanks!!

---

### Post by pete_countryman on 2010-05-16
Since 3.1.8 was installed from a deb (from the virtualbox.org web site), I removed it (using Synaptic) and installed the default VirtualBox for Lucid, i.e. Version 3.1.6_OSE r59338 from the repository. Created a new VM as before, with the CentOS install ISO attached. Still hangs on boot from the ISO at the same place.

I then created a new account with a fresh home directory, created a new Linux/RedHat/32-bit/1024M/single-processor VM and booted from the CentOS-5.4-i386-bin-DVD. Still hangs on boot. I re-checked the sha1sum for my copy of the DVD ISO, and the ISO is fine.

This one sure beats me!

---

### Post by Ocxic on 2010-05-16
make sure you don't have any iso images mounted at boot.  that seems to make Win7 hang for me.

---

### Post by dcstar on 2010-05-17
And what is in the Virtualization forum about this?

---

### Post by pete_countryman on 2010-05-17
Thanks, David, for pointing out its existence. I'll check it out.

Cheers,
Pete

---

### Post by pete_countryman on 2010-05-18
OK, I'll just make one more observation, then I'll shut up.

Apparently my VM has a problem with the CentOS 5.4 i386 bin DVD.
I'm able to boot and run various Ubuntu Live CDs on the same VM with no problem at all.

I only experience the hang when booting the CentOS DVD, whether from a burned copy in my drive or mounted from my hard disk. This in spite of the fact that I specified that this VM would host a 32-bit RedHat Linux distro (which should work for CentOS). And the ISO is not corrupt - I checked the MD5, and it is correct:

071e18754c2fb066c526672f9aea0515  CentOS-5.4-i386-bin-DVD.iso

Thanks to all who responded.

-Pete

---

