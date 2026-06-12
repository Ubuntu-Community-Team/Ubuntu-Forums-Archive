---
title: "arrow keys not working in nano"
date: 2011-02-16
forum: General Help
---

### Post by willroberts on 2011-02-16
Hi all,

When using nano in the terminal, I can't seem to navigate text using the arrow keys - everything I have read about nano says I should be able to do this.

My Ubuntu installation has no GUI, so I can't use the mouse for navigation.

Any ideas?

---

### Post by gmargo on 2011-02-16
What "terminal" are you using?  Are you logged in at the console?  Are you SSHed in through Putty? Direct install?  Inside Virtualbox?

---

### Post by willroberts on 2011-02-16
To be precise, I am running Ubuntu Server 10.10 64-bit inside VMware Workstation. When my SSD ships in I'll have it directly installed on that, and then I will be using the server via SSH.

---

### Post by willroberts on 2011-02-18
Adding xkeymap.nokeycodeMap = true is recommended when running VMware inside Ubuntu, but adding to my .vmx file in my host OS didn't help. I may try VirtualBox to see if it responds differently.

---

### Post by willroberts on 2011-02-18
VirtualBox exhibits the same issue, so it's not the virtualization that's causing the problem. I can only hope that this problem doesn't occur when I switch over to Ubuntu Server as my primary server OS. :/

---

### Post by willroberts on 2011-02-25
I just tried plugging a USB keyboard into my laptop, it didn't help. Pressing the down arrow sends the RETURN signal, all other arrow keys do nothing while inside nano or vim.

---

