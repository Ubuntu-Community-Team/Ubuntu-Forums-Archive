---
title: "VM to try out different OS's"
date: 2010-06-02
forum: General Help
---

### Post by dayalsoap on 2010-06-02
I'm interested in trying out different operating systems, but running off of the live CD is slow.

I'm sure it's much quicker to just run the .ISO disk image inside a virtual machine, is this correct?

What would I need to install so that I can try these different operating systems inside a virtual machine?  Is using the .ISO files the best way?

Thank you

Edit:  I'm using 10.04 64-bit

Edit 2: 
I guess my next question (which I should have asked originally):  Is it  possible to install software, then re-package the image so that I can  use it later with the same software installed?

---

### Post by bodhi.zazen on 2010-06-02
I suggest Virtualbox

iso are perfect, test them out, if you like what you see, go ahead and install the OS onto what will be a virtual disk.

VBox is easy to user, although some reading will be required.

---

### Post by dayalsoap on 2010-06-02
> **bodhi.zazen said:**
> I suggest Virtualbox

Thank you for your response.

Is the .ISO the best choice? or do different distros commonly release a VM image?

---

### Post by bodhi.zazen on 2010-06-02
> **dayalsoap said:**
> Thank you for your response.

Is the .ISO the best choice? or do different distros commonly release a VM image?

iso are fine. You can dl some virtual hard drivers, but, IMO that is inefficient as they are larger then iso and usually require updates so they really do not offer much.

---

### Post by dayalsoap on 2010-06-02
> **bodhi.zazen said:**
> iso are fine. You can dl some virtual hard drivers, but, IMO that is inefficient as they are larger then iso and usually require updates so they really do not offer much.


That's what I needed to know, thank you.

I guess my next question (which I should have asked originally):  Is it possible to install software, then re-package the image so that I can use it later with the same software installed?

I guess, is it possible to use Virtual Box it create and launch virtual appliances?

---

### Post by bodhi.zazen on 2010-06-02
You can do all that yes.

---

### Post by dayalsoap on 2010-06-02
> **bodhi.zazen said:**
> You can do all that yes.

Excellent!  Thanks for the quick responses!

---

### Post by dayalsoap on 2010-06-03
When trying to do Fedora 13 64bit, I have the DVD in the drive, and it begins the installl, but then the Fedora 13 installer says there's no DVD in the drive...??

Is there a good tutorial on how to use this?  Even openSUSE starts but then fails but asks me to insert a disk...

I've tried loading the ISO directly to Virtual Box, I've tried using GMount, and I've tried it with a real DVD....

---

### Post by dcstar on 2010-06-03
> **dayalsoap said:**
> When trying to do Fedora 13 64bit, I have the DVD in the drive, and it begins the installl, but then the Fedora 13 installer says there's no DVD in the drive...??

Is there a good tutorial on how to use this?  Even openSUSE starts but then fails but asks me to insert a disk...

I've tried loading the ISO directly to Virtual Box, I've tried using GMount, and I've tried it with a real DVD....

Please do not ask non-Ubuntu questions in this forum.

The Virtualization forum also has information on all VM related issues, which is where all Ubuntu VM questions should be.

---

### Post by VastOne on 2010-06-03
> **dayalsoap said:**
> When trying to do Fedora 13 64bit, I have the DVD in the drive, and it begins the installl, but then the Fedora 13 installer says there's no DVD in the drive...??

Is there a good tutorial on how to use this?  Even openSUSE starts but then fails but asks me to insert a disk...

I've tried loading the ISO directly to Virtual Box, I've tried using GMount, and I've tried it with a real DVD....

It looks as if you are not correctly identifying where the iso is located.

You should have something like this [[COLOR="Red"]_image_[/COLOR]]("http://vavai.net/wp-content/uploads/2009/01/virtualbox-iso2.jpeg") in your settings, and as you can see you can open a location to the exact file.

[_[COLOR="Green"]Here[/COLOR]_]("http://www.virtualbox.org/wiki/Downloads#manual") you can find the VBox User manual

---

### Post by ThesaurusRex on 2010-06-03
If you're using VM, I found it easier to use Daemon Tools to mount the .iso as a virtual drive. No sense in wasting CD/DVD-Rs on distros you just want to play with briefly.

---

### Post by bodhi.zazen on 2010-06-03
> **ThesaurusRex said:**
> If you're using VM, I found it easier to use Daemon Tools to mount the .iso as a virtual drive. No sense in wasting CD/DVD-Rs on distros you just want to play with briefly.

You may use the .iso as a CD directly, you do not need to burn it or use Daemon Tools.

[img]http://farm1.static.flickr.com/145/416553085_9f9ab0ca92.jpg[/img]

---

