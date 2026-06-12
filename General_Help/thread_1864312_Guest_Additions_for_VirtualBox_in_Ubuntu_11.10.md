---
title: "Guest Additions for VirtualBox in Ubuntu 11.10"
date: 2011-10-18
forum: General Help
---

### Post by khurtsiya on 2011-10-18
Trying to install and getting this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204764&d=1318982232[/IMG]

---

### Post by haqking on 2011-10-18
you dont need to download it ?

if you have the Vbox installed then open up your VM and once it is running go to devices menu and choose vbox additions, it automounts within the VM

or you are getting this message when download virtualbox ?

latest version is 4.1.4 and can be found here [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

also download the extensions pack

additions is built into Vbox

---

### Post by khurtsiya on 2011-10-18
I do not have ISO and it fails to download.

---

### Post by haqking on 2011-10-18
> **khurtsiya said:**
> I do not have ISO and it fails to download.

you dont have .iso of what ?

---

### Post by khurtsiya on 2011-10-19
Don't you see screenshot in OP?

I do not have VBoxGuestAdditions_4.1.2_Ubuntu.iso

---

### Post by keithy on 2011-10-19
sudo apt-get install virtualbox-guest-additions-iso

mount the ISO in virtualbox before you run the VM

it should be in /usr/share/virtualbox/VBoxGuestAdditions.iso

it will then install in your VM without the error

HTH

---

### Post by khurtsiya on 2011-10-19
Thank You! I think this should be marked as SOLVED

---

### Post by GapInTheClouds on 2011-10-19
Thanks. That was spot on :)!

---

### Post by keithy on 2011-10-22
Glad I could help :)

---

### Post by ilantal on 2011-10-24
I had the same problem and used your answer. There is a slightly easier way if you use Synaptic Package Manager. There is the guest additions there as well and it will install it properly for you.

Once I saw you doing it in the terminal I wondered if synaptic would do it as well, and it does.

Ilan

---

### Post by rkrinfo on 2011-12-13
thanx

---

### Post by SynonM on 2012-01-30
=d> ;)

Great post.

---

### Post by fagulhaspt on 2012-03-21
> **keithy said:**
> sudo apt-get install virtualbox-guest-additions-iso

mount the ISO in virtualbox before you run the VM

it should be in /usr/share/virtualbox/VBoxGuestAdditions.iso

it will then install in your VM without the error

HTH


Thanks - that solved it :)

---

