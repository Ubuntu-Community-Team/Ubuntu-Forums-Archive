---
title: "VirtualBox headless"
date: 2011-10-26
forum: General Help
---

### Post by Bradburts on 2011-10-26
I am setting up a headless server running a number of virtual machines using latest OSE.
How do I view the console of the VM when running an install so that I can enter installation choices?
 
Not knowing how to interact with the VM I tried to create a VM from command line & imported a VDI. VirtualBox accepted all the commands & on starting the VM I get the message:-
 
"Remote session has been successfully opened."
 
I tried to connect to the VM using:-
C:\Windows\System32\mstsc.exe with Computer: 192.168.2.100:3389 (VM host) & also 192.168.2.101:3389 (VM guest)
These connections fail.
ping 192.168.2.101 returns "Reply from 192.168.2.2: Destination host unreachable." where 192.168.2.2 is my Windows PC
 
I have run VB using a GUI and have found that when I clone a machine using NAT I have to remove the eth0 definition in /etc/udev/rules.d/70-persistent-net.rules. Otherwise the VM will not create the eth0 interface.
So it may be that my VM is working except for a failed ethernet, but I have no console to correct this!
 
I am not sure if running a VM headless on a headless server using OSE is going to work.
I have also not figured out which tools would help me diagnose and/or speak to the VM.
 
Anyone make this work before?
 
Heres how I created a VM & imported a vdi:-
```
 
[FONT=Courier New, monospace]VBoxManage createvm -name "Ubuntu 10.04 Server Base" -register[/FONT]
 
[FONT=Courier New, monospace]VBoxManage modifyvm "Ubuntu 10.04 Server Base" --memory "512" --acpi on --boot1 disk --nic1 nat –-ostype Ubuntu [/FONT]
 
[FONT=Courier New, monospace]VBoxManage storagectl "Ubuntu 10.04 Server Base" --name "IDE Controller" --add ide[/FONT]
[FONT=Courier New, monospace]VBoxManage storageattach "Ubuntu 10.04 Server Base" --storagectl "IDE Controller" --port 0 --device 0 --type hdd --medium “Ubuntu 10.04 Server Base.vdi”[/FONT]
[FONT=Courier New]# Where the base vdi is a working image copies from my PC[/FONT]
[FONT=Courier New]VBoxManage startvm "Ubuntu 10.04 Server Base" --type headless[/FONT]

```

---

