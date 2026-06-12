---
title: "I need help finding a program"
date: 2010-05-12
forum: General Help
---

### Post by Slantzalot on 2010-05-12
I need a program that can burn an .nrg file, is there one for Ubuntu? Would I be better off just running Nero through WINE? I'm using Lucid, if it matters.

---

### Post by dv3500ea on 2010-05-12
You can install a (command line) program called [nrg2iso]("apt:nrg2iso") to convert it to a .iso file ([see this tutorial]("http://www.ubuntugeek.com/howto-convert-a-nrg-nero-file-to-a-iso-file-in-ubuntu.html")) and then burn the iso to a disk using the default burner software.

---

### Post by Slantzalot on 2010-05-12
> **dv3500ea said:**
> You can install a (command line) program called [nrg2iso]("apt:nrg2iso") to convert it to a .iso file ([see this tutorial]("http://www.ubuntugeek.com/howto-convert-a-nrg-nero-file-to-a-iso-file-in-ubuntu.html")) and then burn the iso to a disk using the default burner software.

I'm still new to Ubuntu, could you explain this tutorial? I'm a bit confused by it.

---

### Post by Darkdelusions on 2010-05-12
Nero also has a native linux application which can be found [here]("http://www.nero.com/enu/promo-linux.html?NeroSID=363bb03a7000059102fd3e87c342c149&utm_id=8596") But it will run you 20 bucks and I have never used it before

---

### Post by dv3500ea on 2010-05-12
> **Slantzalot said:**
> I'm still new to Ubuntu, could you explain this tutorial? I'm a bit confused by it.

It is explaining what commands to use. If you don't like the command line you can [click here to install]("apt:nrg2iso") and once it has installed press Alt-F2.
Copy and paste this:
```
perl -e 'my $nrg = `zenity --title "choose a nrg image to convert" --file-selection`;my $iso = $nrg;$iso =~ s/nrg$/iso/;system("nrg2iso \"$nrg\" \"$iso\"");sleep(5);'
```
into the text box, tick 'run in terminal' and click run.

To burn the .iso file to disk you can right click it and click '_W_rite to Disk...'

---

### Post by Mark Phelps on 2010-05-13
Nero Linux is well worth the $20 they want for a license.

It's not the bloated everything-in-it-but-the-kitchen-sink app typical of recent Nero versions; instead, it's more of a Nero "lite" -- with only the burning features you need.

I use it all the time in Ubuntu and it's great!

---

