---
title: "Server Virtual machine host KVM VNC problem"
date: 2010-04-18
forum: General Help
---

### Post by blackalegator on 2010-04-18
Could anyone help me with the problem which I encounted during installation the Ubuntu 9.10 desktop on the Virtualization host on my Ubuntu 9.10 server edition (KVM).

Steps that I`ve done:

1. Installed the Virtual Machine Host using tasksel
Success

2. Checked if my server supports virtualization using this command
[B]egrep '(vmx|svm)' /proc/cpuinfo
[/B]
I got the output, so it should[B]
success
[/B]
3. Downloaded the Ubuntu Desktop[B]
wget ...
[/B]success
4. Installed extra packages that I`ve needed[B]sudo apt-get install kvm libvirt-bin python-virtinst bridge-utils
[/B]success
5. Checked if KVM was installed properly[B]virsh -c qemu:///system list --all
[/B]I got the output like[B]
Connecting to ... qemu:///system
Id name state:
--------------------------------------------
[/B]As it should be
Success6. Made a bridge in the interfaces[SIZE=3][B]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 172.16.4.24
        netmask 255.255.255.192
        network 172.16.4.0
        broadcast 172.16.4.63
        gateway 172.16.4.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

success
[/B][/SIZE]6. rebooted
success

7. Installed the VM
**sudo virt-install -n vsrv1 -r 384 -f vsrv1.img -s 10 -c ubuntu-9.10-desktop-i386.iso --accelerate --os-type=linux --os-variant=generic26 -v --vnc -w bridge:br0**

I got the output like
[I]Starting install…
Creating domain… 0 B 00:01
/usr/lib/python2.6/dist-packages/virtinst/Guest.py:1086: DeprecationWarning: integer argument expected, got float
 for ignore in range(1, (5 / .25)): # 5 seconds, .25 second sleeps
Unable to connect to graphical console: virt-viewer not installed. Please install the 'virt-viewer' package.
Domain installation still in progress. You can reconnect to
the console to complete the installation process.[/I]

success

8. I didnt want to install the virt-viewer, though I`ve enabled the VNC for my VM. So now I tried tried to connect to my VM using the UltraVNC and kitty (putty)

In the kitty I choosed all the options I usually choose when I connect to my server using SSH and also aded the port forwading from 59000 to localhost:5900 (easier for me)

9. I start the UltraVNC viewer in the adress I put localhost:5900
and...
**It asks for a password!!! My user`s password is too long for VNC, so I have no idea what to do at all**

10. (If I am trying to install vnc-server (tightvnc or vnc4server) it also wants to install X11 which I dont need. **Help ME PLEASE!!!**

---

