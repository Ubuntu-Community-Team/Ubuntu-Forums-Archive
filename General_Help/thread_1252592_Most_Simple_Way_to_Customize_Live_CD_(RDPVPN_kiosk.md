---
title: "Most Simple Way to Customize Live CD (RDP/VPN kiosk terminal)?"
date: 2009-08-29
forum: General Help
---

### Post by web1b on 2009-08-29
We need to make a live CD for employees to connect to their Windows desktop machine in the office using a Remote Desktop connection over VPN. 

The CD needs to boot and log on automatically with internet access and have a completely empty interface with nothing but 3 shortcut icons on the desktop plus a button to log off/shutdown.
No menus other than what's needed to log off or shutdown should be available.

It a needs shortcut to launch a partially preconfigured VPN connection (IP address and group login/password preconfigured into the CD image) the user will be required to enter their personal VPN user name and password each time.
It needs to have a shortcut to Firefox on the desktop with the homepage set to the company web page.  The primary purpose of having the browser is to have a very simple and easy to understand way for the user to verify the internet connection is working before they try to connect to the VPN.


It also needs to have the Remote Desktop shortcut on the desktop setup so all they need to do is click on it and type in the IP address of their office workstation once they have connected to VPN.  They would then do all their work through the Remote Desktop window.

All other parts if the Ubuntu OS on the live CD should be hidden.

Is this possible and how?

---

### Post by DFlame on 2009-08-29
It's definitely possible. You'd need time and research to do it "in house" though. As your request encompasses a lot of topics, I'll provide some links that should get you started.

[Ubuntu Customization Kit (UCK)](http://uck.sourceforge.net/)
[VPN in Ubuntu](https://help.ubuntu.com/community/VPNClient)
[gnome-rdp (also in Ubuntu repositories](http://sourceforge.net/projects/gnome-rdp/)
[Ubuntu Help on LiveCD Customization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by web1b on 2009-08-30
> **DFlame said:**
> It's definitely possible. You'd need time and research to do it "in house" though. As your request encompasses a lot of topics, I'll provide some links that should get you started.

[Ubuntu Customization Kit (UCK)](http://uck.sourceforge.net/)
[VPN in Ubuntu](https://help.ubuntu.com/community/VPNClient)
[gnome-rdp (also in Ubuntu repositories](http://sourceforge.net/projects/gnome-rdp/)
[Ubuntu Help on LiveCD Customization](https://help.ubuntu.com/community/LiveCDCustomization)

That looks extremely difficult and time consuming to go through all those sites and attempt to cobble it together.  I was hoping something at least similar to what I want had already been done.
I am surprised I am the first person to want something like this.

---

