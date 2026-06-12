---
title: "How to clone an Ubuntu so I can reuse it as an image in Virtual Box"
date: 2011-11-29
forum: General Help
---

### Post by aliov_85 on 2011-11-29
Hello,

I put 5 hours to install and configure my new Ubuntu. I don't want to repeat those steps again. I'm looking for a solution which allows me to take an image of my recently installed Ubuntu and reuse it in VirtualBox. Do you have some Ideas guys?

Best REgards

---

### Post by moe19790 on 2011-11-29
i think remastersys will do the trick, make a live cd of what u have, then boot it inside ur VM

MOe!
[B][URL="http://www.psychocats.net/ubuntu/remastersys"]
[/URL][/B]

---

### Post by BC59 on 2011-11-29
There is the perfect solution for that and it's called Remastersys. You install it finding how here

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Then you execute it and check the choice to make a backup. Then it backs up everything and creates a .iso image which can burn on a CD or USB or use it directly to install your custom operating system to a virtual machine.

Only a catch. You have to move all the documents and personal files from Ubuntu before the backup because it has only the capability to backup files of the size of one DVD.

---

### Post by dandnsmith on 2011-11-29
Interesting - that link gets to a page which warns that remastersys is 'out of date' and there is a new product called relinux, still under development, and with bugs.
However, this is a good tutorial

---

### Post by raja.genupula on 2011-11-29
clonezilla also good , try that once.

---

### Post by BC59 on 2011-11-29
> **dandnsmith said:**
> Interesting - that link gets to a page which warns that remastersys is 'out of date' and there is a new product called relinux, still under development, and with bugs.
However, this is a good tutorial

You have right about the strange introduction of the writer, but it's working.

---

