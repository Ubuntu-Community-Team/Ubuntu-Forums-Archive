---
title: "Installing latest TeX Live on Ubuntu"
date: 2012-02-26
forum: General Help
---

### Post by Nickolai_Leschov on 2012-02-26
I have trouble installing latest TeX Live on Ubuntu. I need the latest version of TeX Live, so I install with the install-tl installer, not from the [repositories](http://packages.ubuntu.com/search?keywords=texlive).

My system is Ubuntu 11.04 i386, later I intend to install on 9.04 i386 too.

I try to follow the instructions "[TeX Live and Debian/Ubuntu](http://www.tug.org/texlive/debian.html)", section "Integrating vanilla TeX Live with Debian". First, how do I install "as root, system-wide"? I do "sudo ./install-tl" Is this right? Then, how do I "ensure that the only Debian TeX Live packages installed are tex-common, texinfo, and perhaps lmodern"?

Unfortunately, after following the instructions the latex command cannot be found after reboot. How do I add latex to the path permanently?

I tried to reinstall in wizard mode with "./install-tl -gui wizard" but it says "(default not allowed or not writable - please change!)" about the installation directory. Is this because the "sudo" I added? How do I fix it?

---

