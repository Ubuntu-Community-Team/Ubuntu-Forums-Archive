---
title: "problems uninstalling"
date: 2011-01-15
forum: General Help
---

### Post by watgrad on 2011-01-15
Hi - 
Sorry for the multiple posts - my forum connection keeps getting 'reset' when I submit...

I need to uninstall a software package, but cannot do it in the usual ways.  I installed SoftMaker Office 2008 by forcing the architecture, I run 64 bit ubuntu, the software is 32 bit.

Now I would like to remove the package because I'm using LibreOffice.

I cannot uninstall Softmaker with apt-get remove, through the Software Centre, or through synaptic.

I can see the package with dpkg --list  it is called Softmaker-office-2008

Any ideas how I could remove this?

Thanks

---

### Post by TGBaker on 2011-01-15
> **watgrad said:**
> Hi - 
Sorry for the multiple posts - my forum connection keeps getting 'reset' when I submit...

I need to uninstall a software package, but cannot do it in the usual ways.  I installed SoftMaker Office 2008 by forcing the architecture, I run 64 bit ubuntu, the software is 32 bit.

Now I would like to remove the package because I'm using LibreOffice.

I cannot uninstall Softmaker with apt-get remove, through the Software Centre, or through synaptic.

I can see the package with dpkg --list  it is called Softmaker-office-2008

Any ideas how I could remove this?

Thanks

Have you tried sudo dpkg -r softmaker-office-2010_i386  from a terminal?

---

