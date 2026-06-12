---
title: "Network Manager Missing"
date: 2011-04-24
forum: General Help
---

### Post by drmota on 2011-04-24
Hi,

I recently installed Ubuntu 11.04 Beta 2. With it came several questions:

1. I need to set myself a static IP address which is outside the DHCP range. My DHCP range is from .2 to .245 with .255 being reserved. The gnome network manager doesn't accept IP's larger than .255 - WHY?

2. Ok, I wanted to try it another way and I accindentally uninstalled gnome network manager. Going into Synaptic Package Manager isn't much help as it says that I have an installed version of it - meaning it was just disabled. Anyone know where I can find and enable the gnome network manager; to be able to use it again?

Thanks in advance to answering my two questions :)

---

### Post by hal8000 on 2011-04-24
> **drmota said:**
> Hi,

I recently installed Ubuntu 11.04 Beta 2. With it came several questions:

1. I need to set myself a static IP address which is outside the DHCP range. My DHCP range is from .2 to .245 with .255 being reserved. The gnome network manager doesn't accept IP's larger than .255 - WHY?

2. Ok, I wanted to try it another way and I accindentally uninstalled gnome network manager. Going into Synaptic Package Manager isn't much help as it says that I have an installed version of it - meaning it was just disabled. Anyone know where I can find and enable the gnome network manager; to be able to use it again?

Thanks in advance to answering my two questions :)



1. Not sure what you're talking about?
If you're quoting the last octet then please say so. You cant have any address greater than 255 as an IP address is made up of 4 decimal numbers separated by full stops. Each number has 8 binary bits so possible range is 0 to 255 for any octet assuming you are talking about (IPV4).

2.  Try opening a terminal and typing nm-applet

---

### Post by drmota on 2011-04-25
Yes, you understood correctly, thanks. About the first one, if my range (last octet) is from .2 to .254 with .255 reserved; then there is no change for me to pick a static IP outside of the DHCP range? If i change the range to .100 - .254; will that affect the computers have their last octets at, say, .10? Is there any risk of affecting something internet-regarding when I change the range? And when I do change the range, my static IP can be something under 100?

Thanks a bunch :)

---

