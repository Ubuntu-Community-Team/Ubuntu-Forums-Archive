---
title: "VMware network &amp; internet broken"
date: 2005-02-13
forum: General Help
---

### Post by kurisutofaa on 2005-02-13
I can't use internet and network in vmware. I think problem is here:
```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
```

I have done this: [http://www.ubuntulinux.org/wiki/VMware](http://www.ubuntulinux.org/wiki/VMware) but here I will have to do "rm /etc/vmware/not_configured" twice. After " /etc/init.d/vmware start" I run that rm command again. Otherways it says my vmware is not configured.


```
You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] no

Do you want networking for your virtual machines? (yes/no/help) [yes]

Would you prefer to modify your existing networking configuration using the
wizard or the editor? (wizard/editor/help) [wizard]

Do you want to be able to use NAT networking in your virtual machines? [yes]

Do you want to be able to use host-only networking in your virtual machines?
[no]

Do you want this program to automatically configure your system to allow your
virtual machines to access the host's filesystem? (yes/no/help) [no]

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed

The configuration of VMware Workstation 4.5.2 build-8848 for Linux for this
running kernel completed successfully.

You can now run VMware Workstation by invoking the following command:
"/usr/bin/vmware".
```

And when I choose editor comes:

```
Would you prefer to modify your existing networking configuration using the
wizard or the editor? (wizard/editor/help) [wizard] editor

The following virtual networks have been defined:

. vmnet0 is bridged to eth0
. vmnet8 is a NAT network on private subnet 172.16.138.0.
```

I'm using win2000 pro as guest. When I'm running vmware win2000, that Ethernet0 doesn't blink (at bottom right vmware). Here is what comes when I run ipconfig on guest. [http://koti.mbnet.fi/bryzell/pics/vmware.png](http://koti.mbnet.fi/bryzell/pics/vmware.png)

Somebody please help me.
thanks!

---

### Post by TopDog on 2005-02-13
[Screenshot of my VMware](http://home.broadpark.no/~gholmin/temp/screenshot.jpg).

EDIT: Sorry, didn't read your post good enough... you have it the other way...  Ignore my post  :oops:

---

### Post by kirsche on 2005-05-17
What kind of HW are you using on your host?
Is the nic is activated during the bootup properly?

---

### Post by Patrick on 2005-05-21
[QUOTE=kurisutofaa]I can't use internet and network in vmware. I think problem is here:
```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
```

I have done this: [http://www.ubuntulinux.org/wiki/VMware](http://www.ubuntulinux.org/wiki/VMware) but here I will have to do "rm /etc/vmware/not_configured" twice. After " /etc/init.d/vmware start" I run that rm command again. Otherways it says my vmware is not configured.


```
You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] no

Do you want networking for your virtual machines? (yes/no/help) [yes]

Would you prefer to modify your existing networking configuration using the
wizard or the editor? (wizard/editor/help) [wizard]

Do you want to be able to use NAT networking in your virtual machines? [yes]

Do you want to be able to use host-only networking in your virtual machines?
[no]

Do you want this program to automatically configure your system to allow your
virtual machines to access the host's filesystem? (yes/no/help) [no]

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed

The configuration of VMware Workstation 4.5.2 build-8848 for Linux for this
running kernel completed successfully.

You can now run VMware Workstation by invoking the following command:
"/usr/bin/vmware".
```

And when I choose editor comes:

```
Would you prefer to modify your existing networking configuration using the
wizard or the editor? (wizard/editor/help) [wizard] editor

The following virtual networks have been defined:

. vmnet0 is bridged to eth0
. vmnet8 is a NAT network on private subnet 172.16.138.0.
```

I'm using win2000 pro as guest. When I'm running vmware win2000, that Ethernet0 doesn't blink (at bottom right vmware). Here is what comes when I run ipconfig on guest. [http://koti.mbnet.fi/bryzell/pics/vmware.png](http://koti.mbnet.fi/bryzell/pics/vmware.png)

Somebody please help me.
thanks![/QUOTE]

Well, i see that you have configured two nics, why?

 And also i can give you a tip, install vmtools, shot down the guest, and change the nic from amd to vmxnet. This one has less cpu overhead and is faster

---

### Post by an31146 on 2008-04-05
I found this post and was having a similar problem - the vmxnet module was loaded but it wasn't acquiring an IP address from the VMnet8 DHCP service.

But it was working just fine until I installed VMware Tools! :confused:

Anyway, this fix worked for me: insert the following line into your VM's .vmx config file:
ethernet0.virtualDev = "e1000"

---

### Post by Crennie on 2008-05-01
> **an31146 said:**
> I found this post and was having a similar problem - the vmxnet module was loaded but it wasn't acquiring an IP address from the VMnet8 DHCP service.

But it was working just fine until I installed VMware Tools! :confused:

Anyway, this fix worked for me: insert the following line into your VM's .vmx config file:
ethernet0.virtualDev = "e1000"

Thanks an31146, your trick did the trick for me!  It just seemed to suddenly refuse connecting to NIC and your one liner pasted in fixed it.

~cheers

---

### Post by brocruit on 2008-05-14
> **an31146 said:**
> I found this post and was having a similar problem - the vmxnet module was loaded but it wasn't acquiring an IP address from the VMnet8 DHCP service.

But it was working just fine until I installed VMware Tools! :confused:

Anyway, this fix worked for me: insert the following line into your VM's .vmx config file:
ethernet0.virtualDev = "e1000"

Yes, thank you very much

---

