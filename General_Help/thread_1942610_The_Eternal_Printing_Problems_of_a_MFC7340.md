---
title: "The Eternal Printing Problems of a MFC7340"
date: 2012-03-17
forum: General Help
---

### Post by terrykiwi83 on 2012-03-17
Well as the title suggests I have been plagued with problems using my Brother MFC 7340 printer on Ubuntu since 10.04. All 64bit variants.

So my solution in 10.04 - 11:04 was to set the printer driver to a different driver which seemed to allow me to print.

No in 11.10 I am not able to choose a printer driver anymore.

In System Settings > Printers it says MFC-7340 is Ready and is using the following driver:

```

Brother MFC-7225N BR-Script3

```

That driver was automatically selected I guess when I plugged it in. Now the  problem is that it doesn't work, doesn't even initialize the printer. The driver from memory is somewhere in the 6000 models.

I have searched through the Printer settings and cannot find anywhere were I can browse for and select a different driver, so my question is does anyone have any suggestions or ways to help me get this printer going.

Currently running version 11.10 64bit

Note: Before anyone suggests going to the brother website and going through the Cups... Installation of the printer, it doesn't work :( have tried this on every version of Ubuntu and never worked. I just need to be able to browse the available drivers and select one.

Thanks

---

### Post by kurt18947 on 2012-03-18
I looked on openprinting.org's list of supported printers and MFC7340 isn't there.

[http://www.openprinting.org/printers/manufacturer/Brother](http://www.openprinting.org/printers/manufacturer/Brother)

You may be able to use another model's drivers but I have no experience.   I've always used Brother's drivers and have had quite good success.  11.10 has some fixable scanning issues but printing should work.  When using a 64 bit O.S., do pay attention to:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004).

These appear to be the major items on current Ubuntu distros:

**ia32-libs** or **lib32stdc++** is required to be installed.
**csh** or **tcsh** is required to be installed.

It seems that Brother's printer drivers are 32 bit so require 32 bit support to be installed and also command line install using " --force-all".  I hope you're able to work this out.  I've read of people using PCL5 with Brother lasers but have no idea how to implement that.

---

### Post by terrykiwi83 on 2012-03-18
> **kurt18947 said:**
> I looked on openprinting.org's list of supported printers and MFC7340 isn't there.

[http://www.openprinting.org/printers/manufacturer/Brother](http://www.openprinting.org/printers/manufacturer/Brother)

You may be able to use another model's drivers but I have no experience.   I've always used Brother's drivers and have had quite good success.  11.10 has some fixable scanning issues but printing should work.  When using a 64 bit O.S., do pay attention to:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004).

These appear to be the major items on current Ubuntu distros:

**ia32-libs** or **lib32stdc++** is required to be installed.
**csh** or **tcsh** is required to be installed.

It seems that Brother's printer drivers are 32 bit so require 32 bit support to be installed and also command line install using " --force-all".  I hope you're able to work this out.  I've read of people using PCL5 with Brother lasers but have no idea how to implement that.

Thanks for the info, I have followed all the instructions on the Brother website and no luck. Am just really looking at finding how to select a printer driver instead of the OS picking one for me. There has to be a way like with previous versions to browse a list of drivers?

Any takers?

---

### Post by terrykiwi83 on 2012-03-18
FIXED. And this is how I fixed it.

Obviously CUPS was installed, so I went to the web admin interface at [http://localhost:631/admin](http://localhost:631/admin)

Selected Add Printer, this then allowed me to select a driver so I selected the following driver:

```

Brother HL-5070N Foomatic/hpijs-pcl5e

```

Works great now.

---

