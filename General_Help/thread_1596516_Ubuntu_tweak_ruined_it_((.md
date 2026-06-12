---
title: "Ubuntu tweak ruined it :(("
date: 2010-10-14
forum: General Help
---

### Post by petrasflorin on 2010-10-14
Installed Ubuntu Tweak
Selected sources: Xorg PPA and Compiz PPA, updated them both, can't enable compiz now (Selecting normal visual effects gives me the error Desktop Effects could not be enabled).

uninstalled, reinstalled, overinstalled, xorg, compiz and my nvidia driver. still nothing.

ran some script compiz-check, says everything is ok.
I'm now running with metacity compositing manager provided by ubuntu tweak (which actually works fine but whatever I want compiz back).

Ideas ?!

---

### Post by DeltaUK on 2010-10-14
I have the same issue

---

### Post by tjeremiah on 2010-10-14
the package for compiz in Ubuntu Tweak, is broken for 64bit. First, if you havent already, purge the PPA in Ubuntu Tweak. Then try going to System > Administration > Synaptic Package Manager > type compiz and download that package.

As for Xorg, I dont know anything about it but by looking at my Ubuntu Tweak, it said its for TESTING ONLY.

---

### Post by DeltaUK on 2010-10-14
> **tjeremiah said:**
> the package for compiz in Ubuntu Tweak, is broken for 64bit. First, if you havent already, purge the PPA in Ubuntu Tweak. Then try going to System > Administration > Synaptic Package Manager > type compiz and download that package.

I am running 32 bit Ubuntu, but I will try this.

---

### Post by petrasflorin on 2010-10-14
there are two Xorg , one for testing, one ... stable. So they say.

---

### Post by petrasflorin on 2010-10-14
When purging that PPA compiz was automatically downgraded so my compiz from synaptic is already installed. still not working.

---

### Post by Frogs Hair on 2010-10-14
Some  Compiz and other PPAs have not been upgraded for 10.10 yet . Check at launch pad before adding any. Ubuntu Tweak will enable a source but won't tell you if the ppa is compatible and you may end up with broken packages .   Go into Synaptic Pkg  manager> custom filters check for broken pkgs right click and mark for repair. Also check for missing  dependencies and missing recommended pkgs that are Compiz related.

---

### Post by praveenthivari on 2010-10-14
I too had the same problem. It's with compiz packages, because I had enables only tht.

Purge the Compiz pack using Ubuntu tweak. It will automatically downgrade those to previous version. Logout & then login. Then change the visual effects. It worked

---

### Post by Bluebearbevis on 2010-10-15
Hello again,

I've tracked you guy's to here from no, min, max, close.  I have an nVidia G105M, are we waiting for an upgrade?  I didn't reactivate the x.org stable after 10.10 upgrade, perhaps I'll try that.  Next, to the System76 forum.

Thanks again,  Richard

---

### Post by Bluebearbevis on 2010-10-15
Back again,

Alas, after enabling x Updates in Ubuntu Tweak, 5 updates where available for my NVidia card and I again waxed hopeful. Extras still can't be enabled.:(  I haven't activated the UT compiz ppa again after a total uninstall/reinstall of Adv Desktop.  Perhaps a combination of both?  I'm leary of this after reading some of the posts up the page.  

?!?  Richard

---

### Post by theLegend on 2010-10-16
I too had this problem after upgrading to 10.10 Maverick where I blindly enabled the compiz ppa in ubuntu tweak 0.5.7 because I was after the cylinder effect when rotating the cube. I didn't realise it wasn't available for 64 bit version of 10.10 (although I had it working fine in 10.04?) so I purged the PPA via Ubuntu Tweak, uninstalled everything to do with compiz in Synaptics manager (thought they were getting rid of this in Ubuntu?) and then reinstalled all things compiz. Rebooted and all is well in UbuntuWorld again!

Thanks for the tips people!

---

