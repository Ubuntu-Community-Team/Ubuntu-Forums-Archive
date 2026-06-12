---
title: "can I ssh from one vm to another vm on the same computer?"
date: 2010-03-18
forum: General Help
---

### Post by blur xc on 2010-03-18
I'd like to learn more about ssh-ing and running a server-  Could I install Ubuntu Server Edition in a VM, fire it up, and SSH into it from another running VM on the same physical PC?  I'd be nice to get an understanding of all this before trying it out in a live environment.

Thanks,
BM

---

### Post by spiderbatdad on 2010-03-18
It sounds like a fun experiment...I haven't tried, but sounds doable. I would think you could get away with a minimal install and install openssh-server on each. You would need both vm running obviously.

---

### Post by blur xc on 2010-03-18
> **spiderbatdad said:**
> It sounds like a fun experiment...I haven't tried, but sounds doable. I would think you could get away with a minimal install and install openssh-server on each. You would need both vm running obviously.

I'm downloading Ubuntu Server 9.10 as I'm typing this...

I'll try sshing into it from my crunchbang vm (what I'm using right now as well).

BM

---

### Post by sebastianabate on 2010-03-18
Of course you can, as long as you setup the networking in the VM's to allow that, if you can ping one VM from the other, you can use any service installed on either. What virtualization solutions are you using?

---

### Post by KdotJ on 2010-03-18
Let us know how this goes please as I'd love to try it out too when I get some time. Good luck with it

---

### Post by M!K3_$ on 2010-03-18
Totally easy to do. If you're using VMware all you have to do is set the VMs' network interfaces to "Host-only" in the VM settings. Then give both VMs an IP on the same subnet. You'll have full connectivity.

---

### Post by blur xc on 2010-03-18
I'm using VBox and I've run into two problems so far- #1- I guess I can't install Ubuntu Server on a 32bit host- since it's  64bit.  #2- The Ubuntu Minimal install keeps failing...  A whole crapload of errors...  So, maybe I'll just try a normal Ubuntu install.  Fun stuff.... 

I was really looking forward to a command line only install, for other reasons as well.  I'd be happier with a blank system and go from there, rather than start w/ a bunch of junk to remove later.

BM

---

### Post by M!K3_$ on 2010-03-18
There is probably a similar option with VBox for a host-only network. To be honest to get sshd working you need to go

```

sudo apt-get install sshd

```


and you're done. it works. voila!

---

### Post by sebastianabate on 2010-03-18
> **blur xc said:**
> I'm using VBox and I've run into two problems so far- #1- I guess I can't install Ubuntu Server on a 32bit host- since it's  64bit.

You can install a 64bit guest in a 32bit host, if your processor supports Intel's VMX or AMD's SVM. You can check this with

cat /proc/cpuinfo |egrep svm  (for AMD)
or
cat /proc/cpuinfo |egrep vmx  (for Intel)

and make sure that the option is enabled in the BIOS

Or the easy option: download Ubuntu Server 32bit (click on the "Alternative download options" in the _[Ubuntu server download page]("http://www.ubuntu.com/getubuntu/download-server")_, and check the "32bit version" option)

>  #2- The Ubuntu Minimal install keeps failing...  A whole crapload of errors...  So, maybe I'll just try a normal Ubuntu install.  Fun stuff.... 

I was really looking forward to a command line only install, for other reasons as well.  I'd be happier with a blank system and go from there, rather than start w/ a bunch of junk to remove later.

BM

For virtualized systems you can use the _[8.04 JeOS iso]("http://cdimage.ubuntu.com/jeos/")_, or the Ubuntu Server iso (8.10 and above) and press F4 at the first screen and select "install a minimal virtual machine". It uses a optimized version of the kernel, and install a very basic ubuntu (very, very basic). More info _[here]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos")_.

---

### Post by dcstar on 2010-03-18
> **blur xc said:**
> I'd like to learn more about ssh-ing and running a server-  Could I install Ubuntu Server Edition in a VM, fire it up, and SSH into it from another running VM on the same physical PC?  I'd be nice to get an understanding of all this before trying it out in a live environment.


You will probably find more info in the Virtualization forum (where all VM issues should be) when it comes to configuring the VMs to access each other.

Once that is done then you are just using systems, and it won't matter if they are VMs or "real".

---

