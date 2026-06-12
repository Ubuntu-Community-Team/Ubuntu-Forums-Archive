---
title: "Easiest way to use Turbotax with Ubuntu"
date: 2010-08-07
forum: General Help
---

### Post by alex_dc on 2010-08-07
[FONT=Courier 10 Pitch]Hi,

I know this question comes up often, but I had something a little more specific that I was hoping I could get help with.

I will be moving a user from Vista to Ubuntu shortly. This should be no problem for the user except for the fact that she must use Turbotax for her taxes each year (it must be Turbotax, and she must use the hardcopy edition, not the web edition). I am investigating possible solutions for this before I go through with the install, and my research has thus far pointed me to two working solutions:

1. Run Turbotax through a Windows virtual session

2. Keep a small Windows partition for Turbotax

The first seems like the preferable solution, but the user to whom which I am referring is pretty computer illiterate, and as I have never had the need to run a virtual session before, I was wondering if someone could fill me in as to how "simple" this process is.

The second is more of a fallback solution, but workable if need be. However if anyone else has come with a creative way to run this software, I will be glad to hear it!

Thanks in advance![/FONT]

---

### Post by HermanAB on 2010-08-08
Howdy,

If the machine already has Windows on it, do *not* destroy it.  Partition the disk and make the machine dual boot, with Linux as the default.

If the machine doesn't have Windows anymore, make a virtual machine with WinXP.

---

### Post by QIII on 2010-08-08
The difficulty with using a virtualized OS is in the setup of the environment, not in using it.  If someone were willing to set up the environment for the user, the user would not need to be particularly computer literate to use it.

See [http://www.virtualbox.org](http://www.virtualbox.org).  Their documentation is pretty straight forward and there are a lot of us here who would be willing to help with any difficulty you might have. 

Advantages:

1.  If the only thing the user would be doing on Windows is using the one application, it might not be worth the risks of installing a dual boot and taking a chance on screwing up the Windows partition. 

2.  You can take frequent "snapshots" of the virtual disk which makes it very easy to restore a previous version if things go south -- a virus infection, for instance.

Disadvantages:

1.  Virtualization limits the "hardware" to the virtualized hardware, so some of the eye candy might not be available.

2.  You need the actual retail installation disk for Windows.  For one thing, an OEM disk may not install (some check to be sure that you are using their hardware.)  For another, Microsoft's licensing expressly forbids installation in a virtual environment from an OEM disk.  (In this case, HermanAB's advice not to destroy Windows is *extremely* important!)

Once properly set up, running the OS is as simple as (with VirtualBox):

1.  Start VirtualBox.

2.  Select the OS.

3.  Click Start.

4.  Log in as usual.
 
Whatever the solution you arrive at, it is extremely important to save any important data to removable media before you do *anything*.  Historical tax records would be critical here.

---

### Post by alex_dc on 2010-08-08
[FONT=Courier 10 Pitch]I think there may have been a misinterpretation of my question. I know about virtualization, I have just never used it personally. I know that theoretically it should be as easy for the user as QIII mentions, but I'm more concerned as to whether this piece of software has generally run error free under such an environment. I don't want to be stuck tracking down bugs every year.[/FONT]

---

### Post by bodhi.zazen on 2010-08-08
> **alex_dc said:**
> [FONT=Courier 10 Pitch]I think there may have been a misinterpretation of my question. I know about virtualization, I have just never used it personally. I know that theoretically it should be as easy for the user as QIII mentions, but I'm more concerned as to whether this piece of software has generally run error free under such an environment. I don't want to be stuck tracking down bugs every year.[/FONT]

I can see no reason it will not run in VBox.

---

### Post by BlueVark on 2010-08-08
Turbo Tax runs perfectly in Sun VirtualBox.

---

### Post by alex_dc on 2010-08-08
That's what I wanted to know!

Thank you!

---

### Post by soldier1st on 2010-08-08
did you try running it through wine at this address [http://appdb.winehq.org/objectManager.php?sClass=application&iId=623](http://appdb.winehq.org/objectManager.php?sClass=application&iId=623)
also there are alternatives to turbotax like TaxCut TaxAct so check them out and see if they would fit the bill.

---

