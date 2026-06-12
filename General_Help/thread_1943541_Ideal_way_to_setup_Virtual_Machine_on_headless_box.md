---
title: "Ideal way to setup Virtual Machine on headless box?"
date: 2012-03-19
forum: General Help
---

### Post by Lawlcat on 2012-03-19
I've got Ubuntu Server (11.04 with 2.6.38-13-generic i686) running on a laptop that is essentially headless.  Assume for the sake of things that the keyboard and monitor are out of action.

I use the server as a simple game/webhost and it works great, accessing it via PuTTY for all my command line needs.

However I am wanting to setup a Windows server as well (for ASP.Net 4.0 and MicrosoftSQL 5.0+) to use a specific web application, but I've run into a bit of a snag.  That snag being I only have a command line access to this machine.

I've considered installing an X Server and then what is it, Cygwin? I'm not sure the entirety of the process, but whatever is necessary to allow me to view/use the X window over SSH, and then trying to setup a virtualbox that way.

I was hoping there may be a better way to set this up so that in the end I can just RDP into the box and access the Windows Server virtual machine.

Any ideas?

---

### Post by linoseros on 2012-03-19
install qemu and create a VM on which you install Windows :p

---

### Post by BertN45 on 2012-03-19
I have a headless VM server and it runs Ubuntu 12.04 desktop. As VM software I use virtualbox. More importantly it runs with or without virtualisation hardware. It is fast, robust and it has a built-in rdp server. I control it in two ways:

[LIST]
[*] The easy way using xrdp and any windows- or ubuntu rdp client working with it.
[*] The other way. I use ssh and start the virtual machine using vboxheadless command from virtualbox. In that case I use rdesktop to go into the VRDP server supported by virtualbox. I even provide the voxheadless command as part of the ssh command line.
[/LIST]
I did install the system by temporarily connecting a display, mouse and keyboard, but took it away after the installation. I power up the box and it halts at the log-in screen. If I use ssh, the desktop will not be loaded and I have almost all memory available. If I use xrdp, the desktop will be started of course.

You can support windows in this way using a virtual machine, but I wanted to have a look at Windows 8 and the PC had no AMD-V support. So I use windows 8 in a dual boot headless configuration with my VM server, by putting the default partition to boot not to "0" or "1", but to "saved". That allows you to change the default boot for one time. By issuing "sudo grub-reboot 5" and "sudo reboot" to actually reboot. Windows will be booted for once and I use RDP to control it.

---

