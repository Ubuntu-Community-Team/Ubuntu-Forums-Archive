---
title: "PXE with network manager?"
date: 2011-01-29
forum: General Help
---

### Post by r+9 on 2011-01-29
Perhaps this is just so obvious no one bothers to mention it.

I've got a home wireless network, and a lot of old computers with failing CDROMs.  I'd like to keep installing new distros (playing) and I really like the concept of PXE server installs etc.

I haven't had a lot of luck, but it seems to me that networkmanager (the default in ubuntu) serves as dhcp when I link another computer with crossover (or switch) but it's never addressed in any tutorial.

Eventually I'd like to config a laptop as a mobile installer station, but I'm stuck.

Is there something key missing from networkmanger, and is it conflicting with my attempts to install dhcp3 (that keeps failing no matter which tutorial I used)?

Has anyone done this (and maybe knows of a good tutorial?)

---

### Post by mbarak on 2011-01-31
I am trying to do the same thing.
I know that network-manager uses dnsmasq as its dhcp server
dnsmasq also has a tftp server, which is what you need for pxe booting
everything is already there in the default ubuntu install
the problem is that I don't know how to configure dnsmasq without installing full blown dnsmasq and disrupting the "share with other computers" network-manager feature

network-manager runs dnsmasq with it's own configuration. if we could change the way it runs dnsmasq we would be able to add the option to start it's tftp server and install over the network using network-manager.

any ideas?

---

### Post by r+9 on 2011-02-01
That is a useful tidbit!

I'll see what I can discover.

---

### Post by r+9 on 2011-02-20
So I'm still working on this.  I'm new to DHCP and most of the instructions assume I'm not.

Still no success but PXE aside I haven't gotten DHCP to work.

Does anyone know if there is a specific conflict running DHCP for one device (eth0) and NetworkManager for the wireless?

---

