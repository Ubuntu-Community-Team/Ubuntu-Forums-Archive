---
title: "Installing applications not in a repository and keeping them up-to-date"
date: 2009-12-11
forum: General Help
---

### Post by SushiBoiNL on 2009-12-11
Hi guys,

Fairly new to ubuntu but enjoying it so far.

I have a quick question really, applications such as Thunderbird 3.0 and Chrome browser are not (yet) in the repository, so downloaded the deb file from the website and installed succcessfully, but if these applications are added to the main repository in the future, will these applications I downloaded as deb packages automatically be kept up to date?

My question essentially is, how do I keep applications installed outside of the repositories up-to-date e.g. Skype? If these applications are added to the repositories at a later stage, do my existing applications then get updated?

Sorry if it seems thick, but just want confirmation.

Cheers

---

### Post by SushiBoiNL on 2009-12-12
> **SushiBoiNL said:**
> Hi guys,

Fairly new to ubuntu but enjoying it so far.

I have a quick question really, applications such as Thunderbird 3.0 and Chrome browser are not (yet) in the repository, so downloaded the deb file from the website and installed succcessfully, but if these applications are added to the main repository in the future, will these applications I downloaded as deb packages automatically be kept up to date?

My question essentially is, how do I keep applications installed outside of the repositories up-to-date e.g. Skype? If these applications are added to the repositories at a later stage, do my existing applications then get updated?

Sorry if it seems thick, but just want confirmation.

Cheers



Bump.

Nobody?

---

### Post by wangsuda on 2009-12-12
sorry for the delay. It's quite simple, actually, as I also use a couple (ok, more than a couple) of apps that aren't in the repositories. I'll use one of the more common ones as an example - VirtualBox. When downloaded from the VirtualBox website and installed, it includes a tab for manually updating. Additionally, the site provides a key that can be added to your software sources, so (I believe) updates can be automatic. For other programs that do not include update features built in, you can always check for the latest version at the program's own website, or through the Ubuntu package search

---

### Post by SushiBoiNL on 2009-12-12
So when updating by downloading the latest version at the program's own website, do I need to first uninstall the existing version, or is overwriting ok? 

Thanks very much for your help!

---

### Post by wangsuda on 2009-12-12
> **SushiBoiNL said:**
> So when updating by downloading the latest version at the program's own website, do I need to first uninstall the existing version, or is overwriting ok? 

Thanks very much for your help!If you download a .deb package and use the GDebi Package Installer (applications>system tools>GDebi Package Installer) then the program will be automatically overwritten to the newer version. I don't know about .tar packages, sorry.

---

### Post by slakkie on 2009-12-12
If you install a .deb it will be updated as soon as a normal repository (read the official repo's and/or ppa's you defined in /etc/apt/sources.list /etc/apt/sources.list.d/*.list) has a higher version of that package.

If you compiled applications from source it will not be updated through apt, since it doesn't know about them.

What you can do however, if you compile from source, is to use checkinstall. Which can create a .deb package from the stuff you have compiled:

./configure && make && make test && sudo checkinstall make install.

Then it will be the same as the .deb's you've installed outside the repo's.

---

