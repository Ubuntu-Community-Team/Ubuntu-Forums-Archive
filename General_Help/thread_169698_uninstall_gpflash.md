---
title: "uninstall gpflash?"
date: 2006-05-03
forum: General Help
---

### Post by eeried on 2006-05-03
How do I uninstall GPLFlash that I installed from source as explained in the Wiki : Restricted format: [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b)

Very easy to install if you follow the instructions but the plugin doesn't work at all: grey bits or pages where the flash animations sould be.

I have a deb package which I should be able to uninstall through dpkg but when I type the command it says gplflash doesn"t exist.

Do I need to cd to a specific dir?

i'd llike to reinstall the run-of-the-mill non free Flash to see how it works with firefox 1.5.0.3

8) 
Cheers

---

### Post by zba78 on 2006-05-03
On Dapper I removed it using the Synaptic Package Manager standard way of uninstalling.

I do recommend using the official flash player from macromedia as I found it works much better then the GPL one (same thing with official realplayer vrs GPL Helix player)

If you can't remove the entire flash GPL package you can always just remove the plugin files from the /usr/lib/firefox/plugins directory

---

### Post by eeried on 2006-05-04
Many thanks, zba78, for your answer.

I'm not sure I could uninstall via APT if I firest compiled the sources then created a DEB file which I installed via DPKG.

What I did finally was remove the files shown in the doc file somewhere in /usr/share/gplflash.

Is this all right?

I know you're right about gplflash versus macromedia flash but I try  to keep "free" -- not very easy though especially with those blasted restricted multimedia formats. :twisted: 

cheers

---

