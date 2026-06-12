---
title: "gstreamer"
date: 2009-09-21
forum: General Help
---

### Post by jwkungfu on 2009-09-21
Hi folks,
Bit of a lame glitch here but I was wondering if anybody else has noticed this...?

When I'm doing an Update with Update Manager there always is an update called...

gstreamer0.10-plugins-bad

I can't seem to highlight it to be able to download/delete it?

What is it?
Do I need it?
How do I get rid of it?

:confused:

Cheers!

JW.

---

### Post by mcduck on 2009-09-21
The package contains some less common plugins for Gstreamer  (and thus brings ability to play those media formats in all your applications that se Gstreamer).

Since the update Manager offers you the update, yes, you should update it. And if you don't want to, then uninstall the package (with apt-get, Synaptic or whatever package manager tool you prefer).

The Update Manager will only offer updates for packages that you have installed, and there's rarely any reason not to install the updates. Even less when you consider Ubuntu's policy of only offering updates for security reasons and to fix serious bugs.. :)

(I have no idea why  you are not able to install the update, but try updating it with Synaptic Package Manager, or by running "sudo apt-get update && sudo apt-get dist-upgrade")

---

