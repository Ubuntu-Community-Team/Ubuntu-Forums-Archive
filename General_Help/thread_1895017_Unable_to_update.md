---
title: "Unable to update"
date: 2011-12-13
forum: General Help
---

### Post by Mazate on 2011-12-13
I went to try to install the latest updates just now and I got an error.  See the attached image.  Here's the list of things (I assume) it's talking about with regard to the error.


gcalctool gedit gedit-common gir1.2-networkmanager-1.0 gnome-keyring gnome-session gnome-session-bin gnome-session-common gnome-session-fallback hpijs hplip hplip-cups hplip-data indicator-sound libgck-1-0 libgcr-3-1 libhpmud0 libnm-glib-vpn1 libnm-glib4 libnm-util2 libpam-gnome-keyring libsane-hpaio network-manager

---

### Post by 73ckn797 on 2011-12-13
If you are willing, go ahead and authorize the installation. I have ran into that message a few times but was using Synaptic Package Manager. No problems were subsequent to doing that.

---

### Post by Mazate on 2011-12-13
> **73ckn797 said:**
> If you are willing, go ahead and authorize the installation. I have ran into that message a few times but was using Synaptic Package Manager. No problems were subsequent to doing that.

I'm more than willing but as you can see in the image, no such option is offered to me.

---

### Post by dmizer on 2011-12-13
It's not an error message, it's an information message. Once you close it, you should be able to continue with the update.

---

### Post by bluexrider on 2011-12-13
> **Mazate said:**
> I went to try to install the latest updates just now and I got an error.  See the attached image.  Here's the list of things (I assume) it's talking about with regard to the error.


gcalctool gedit gedit-common gir1.2-networkmanager-1.0 gnome-keyring gnome-session gnome-session-bin gnome-session-common gnome-session-fallback hpijs hplip hplip-cups hplip-data indicator-sound libgck-1-0 libgcr-3-1 libhpmud0 libnm-glib-vpn1 libnm-glib4 libnm-util2 libpam-gnome-keyring libsane-hpaio network-manager

just run 

```
sudo apt-get update && sudo apt-get upgrade

```

shouldn't have an issue

---

