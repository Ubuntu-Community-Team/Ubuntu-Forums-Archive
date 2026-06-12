---
title: "vitual machine"
date: 2009-07-18
forum: General Help
---

### Post by volter on 2009-07-18
I want to install windows on virtual machine but I don't know which one to choose.Help!!! 

If it's help I'm using ubuntu 9.04.

---

### Post by TuckLive on 2009-07-18
You have a few options to choose from as far as programs to run the virtual machines.  VMware and VirtualBox are two popular options.

---

### Post by volter on 2009-07-18
How I completely delete the old version of VirtualBox (2.1.4)

---

### Post by TuckLive on 2009-07-18
If Jaunty lists it in the repos then you can go to System > Administration > Synaptic Package Manager and mark VirtualBox deletion.

---

### Post by volter on 2009-07-18
Can you explain me please how to install -> VMware Workstation 6.5.2(Linux 32-bit._rpm_)

---

### Post by howefield on 2009-07-18
> **volter said:**
> Can you explain me please how to install -> VMware Workstation 6.5.2(Linux 32-bit._rpm_)

Being an rpm, it won't install to your Debian based system which uses .deb pacakges. You could use a program called Alien to convert the .rpm to .deb but no guarantees of it working.

Or download the .bundle package and install from there.

---

### Post by TuckLive on 2009-07-18
[http://www.vmware.com/pdf/ws65_manual.pdf]("http://www.vmware.com/pdf/ws65_manual.pdf").  Page 45 starts with how to install a rpm.  Later in the manual will explain how to install a guest os.  Hope this helps. :D

Page 43 shows how to install a bundle.

---

### Post by volter on 2009-07-18
In the installation 

```
su
password:<my user pw> 
su: Authentication failure
```

How to fix it? I  have only one user/pw.

---

### Post by howefield on 2009-07-18
> **volter said:**
> How to fix it? I  have only one user/pw.

You have been told that you cannot install an .rpm to your Debian based system. 

The instructions referred to by TuckLive will not help you unless you are using the .bundle package.

---

### Post by volter on 2009-07-18
I installed VMware-Workstation-6.5.2-156735.i386.bundle 
but now it want a serial number. 
there isn't free version of the program???????

---

### Post by howefield on 2009-07-18
I think most VMware products are commercial, coming with a hefty price tag, although most come with a trial period and VMware Player is free.

Any reason why you didn't stick with Virtualbox ? You seem to have been using an old version, why not get the current version from Virtualbox.org, download the .deb package for your system (presumably Jaunty 32 bit) and the file will install with a double click. 

Much easier and no cost/serials ect to worry about.

---

### Post by volter on 2009-07-18
> **howefield said:**
> 
Any reason why you didn't stick with Virtualbox ?


I couldn't install windows on it(VirtualBox),it just gave me some error during windows installation.I even get new working cd.

---

### Post by SecretCode on 2009-07-18
> **volter said:**
> In the installation 

```
su
password:<my user pw> 
su: Authentication failure
```

How to fix it? I  have only one user/pw.

I could be wrong, but I think that form is disabled on Ubuntu.

Instead of 
```
su
<password>
command
```
try
```
sudo command
<password>
```

VMWare Server is free but you have to register and enter a licence key. 

I think VirtualBox should work - maybe try again?

---

### Post by 3rdalbum on 2009-07-18
> **volter said:**
> I couldn't install windows on it(VirtualBox),it just gave me some error during windows installation.I even get new working cd.

There are many reasons why the Windows installer could give you an error message when running in a virtual machine, and most of them are due to not setting up the virtual machine correctly.

If you try a different virtualiser, you could well have the same problem.

What error message are you getting?

---

