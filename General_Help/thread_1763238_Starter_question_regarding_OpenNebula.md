---
title: "Starter question regarding OpenNebula"
date: 2011-05-20
forum: General Help
---

### Post by mysticado on 2011-05-20
Hello people, I don't really know if this is the right forum to post my message, but I assume that I can get good help here as well :)
[FONT=monospace]
[/FONT]I constructed my cloud according to the Ubuntu howto, which can be found here: [https://help.ubuntu.com/community/OpenNebula](https://help.ubuntu.com/community/OpenNebula)
I now got stuck in the part with the header "How to launch a VM".I managed to create my front-end and clusters, but the last step - the virtual machine part just won't do as I want it to. That's why I'm asking for your kind help.
I have 3 PC's, one of them hosts the front-end and contains 2 disk-LUNs, each of them used as an iSCSI drive for one cluster. The idea is when I migrate the VM that no actual LAN-migration needs to take place, but only some movement inside the front-end, as well as the main memory-migration. But that's unimportant for now...

Did I understand correctly, that everything described in this section needs to be performed on the front-end host? Ok, I created the "vmnet.template" file, but there is already one thing I didn't really understand- the LEASES ip-address! Should I type in the actual address of this PC, or should I take one "free" ip address of the address-range in which my PC is? And the "eth0" part - should I type the current eth-card with which I have internet-access? Because in my case, I use the eth2-card for internet access.

The next step would be the template for the VM. In my case I altered the example a little bit and now got this:

    NAME   = ubuntu_vm
    CPU    = 1
    MEMORY = 2048
    OS     = [
       kernel   = "/boot/vmlinuz-2.6.32-28-generic",
       initrd   = "/boot/initrd.img-2.6.32-28-generic",
       root     = "sda1" ]
    DISK   = [
       source   = "/opt/nebula/images/ubuntu.img",
       target   = "sda1",
       readonly = "no" ]
    NIC    = [ NETWORK = "Private LAN" ]



Is this enough? Somehow I have the feeling that I'm still missing a thing here. The HOWTO mentioned above is complete, isn't it? Also, I have a question about the VM-image file. Is it sufficient to just download an .iso-file, or should the image be correctly created for KVM? 

Maybe it's easier to do all these steps with "virt-manager"??? 


The problem I'm having right now is that the command  "onevm list" gives me the created VM, but with the state "pending", and it stays like this the whole time, until I kill it myself. When I try to deploy the VM myself, it immediately changes state to "failed". Unfortunately even the logs ( /var/log/one/oned.log) don't give me anything.

I know that there are a bunch of questions here, but I assume since these are the first steps, that it shouldn't be that hard to help me here out? I would really appreciate some help, because I got stuck here and just don't know what to do next!! Thanks in advance for helping! :)

---

