---
title: "restore splash screen at bootup"
date: 2012-09-02
forum: General Help
---

### Post by dragonfly41 on 2012-09-02
Minor problem .. just mildly irritating.

After hitting "disk too full" (I was recovering some files on an external USB ubuntu with limited partition size - 21 GB) I found that after releasing some more file space my boot up [COLOR=Navy]ubuntu 10.10 logo[/COLOR] .. splash screen .. did not display as it used to.   

The display "ubuntu 10.10" is in text.   Otherwise I can progress o.k. into desktop.

How can I restore the splash screen to original?

---

### Post by d.atanasov on 2012-09-02
Hi, 

look at the plymouth package in synaptic. If it is removed just install it 

cheers

---

### Post by dragonfly41 on 2012-09-02
Thanks for suggestion .. but **[COLOR=Navy]Plymouth[/COLOR]** was already installed.   I did try reinstalling Plymouth in case it was corrupted but to no avail.

I installed **[COLOR=Navy]startup-manager[/COLOR]** and that didn't help other than changing resolution.  in fact after using startup-manager I found I was booting straight into memory test (on the Grub menu) and I had to run boot-repair-disk to correct this.

So I'm back to a corrupted bootup screen .. thereafter ubuntu is o.k. when in desktop.

[COLOR=DarkRed][Edit]  I found that in using Startup-Manager I had in error selected Memtest from Grub menu as default kernel .. and this explains why ubuntu booted into Memtest after using Startup-Manager.   Be careful on choice of default kernel.   Changes have to be applied to each separate kernel.  I still have no logo.  Only text.   [/COLOR]

---

### Post by ajgreeny on 2012-09-02
You would seem to have removed the **plymouth-theme-ubuntu-logo** package and now possibly have just the **plymouth-theme-ubuntu-text**

---

### Post by dragonfly41 on 2012-09-02
Thanks for that pointer .. I went into Synaptic Package Manager and found I had both of above themes enabled.

I uninstalled both .. then reinstalled only [COLOR=Navy]**plymouth-theme-ubuntu-logo**[/COLOR]
.
I'm now back to the seeing the default Ubuntu logo .. so again thanks for that.

---

