---
title: "CLI issues..."
date: 2011-09-28
forum: General Help
---

### Post by MG&amp;TL on 2011-09-28
I'm interested in running a minimal install or a server in order to kick-start my Linux skills. However, I have two issues: one major, one just interest.

Major problem: I have a wireless USB adapter for the web (via my router). It does not require a driver, it automatically pops up in network manager on a normal GNOME desktop. BUT it never shows up in the installer, and how do I connect with it via command-line?

minor problem: I understand the command-line interface does not have an X server: does that mean there is no way of viewing images? Not a problem, just something I need to work around.

And yes, I will have a graphical laptop for when it all goes wrong.

---

### Post by Dangertux on 2011-09-28
As far as wifi goes you could use iwconfig to connect with it so long as the drivers are loaded. 

I am not sure about the images bit not something I've ever had the need to do.

---

### Post by marshag63 on 2011-09-28
Are you interested in trying a live cd of a all CLI distro based on ubuntu lucid?  You can view pictures and connect to internet - its all setup, plus great tutorials -- I sure have leaned some great stuff.  

I suggest you work through the tutorials and then just play - its really awesome what you can do via CLI.

Here's a direct link:
[http://inx.maincontent.net/devel/unstable/inx-unstable-1.17.iso](http://inx.maincontent.net/devel/unstable/inx-unstable-1.17.iso)

Hope you find this useful :)

MDG

---

### Post by MG&amp;TL on 2011-09-28
Thanks, marshag. Looks interesting. Your project? OK, I'll try the iwconfig on my current desktop. Thank you!

---

### Post by MG&amp;TL on 2011-09-28
How do I find out what to put for the values in iwconfig?

---

### Post by haqking on 2011-09-28
> **MG&TL said:**
> Thanks, marshag. Looks interesting. Your project? OK, I'll try the iwconfig on my current desktop. Thank you!

Use a virtual machine and use a USB wifi adapter instead of the host networking.

---

### Post by MG&amp;TL on 2011-09-28
Err...sorry haqking, don't follow?

Setup in Vbox and practice there? Do they have a virtual USB wireless adapter?

---

### Post by sanderd17 on 2011-09-28
If your main goal is to learn, try Arch.

The most positive side of Arch is the big amount of information on their wiki. You could also use the Arch wiki with other distros, the only difference will be the packages that are preinstalled and the package manager itself.

---

### Post by haqking on 2011-09-28
> **MG&TL said:**
> Err...sorry haqking, don't follow?

Setup in Vbox and practice there? Do they have a virtual USB wireless adapter?

yeah, with VM you can have multiple ones, easier to practice in a CLI VM with access to all your learning resources on your host.

you dont need a virtual wifi adapter.

It is a USB device you are mounting directly in the VM like a ext HDD

---

### Post by MG&amp;TL on 2011-09-28
Ah...okay, cool, I shall maybe try both Arch and ubuntu CLI. Arch has always sounded mysterious.

---

### Post by haqking on 2011-09-28
> **MG&TL said:**
> Ah...okay, cool, I shall maybe try both Arch and ubuntu CLI. Arch has always sounded mysterious.

well with a VM you can do both at the same time and maintain your host desktop for learning resources.

have them both use 2 seperate USB wifi adapters ;-)

---

### Post by MG&amp;TL on 2011-09-28
Ubuntu CLI's in a Vbox now, Arch is downloading. :D Thanks, guys.

---

### Post by haqking on 2011-09-28
> **MG&TL said:**
> Ubuntu CLI's in a Vbox now, Arch is downloading. :D Thanks, guys.

easy peezy lemon squeezy ;-)

Enjoy

---

