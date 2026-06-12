---
title: "share internet between Ubuntu and VmWare Windows"
date: 2006-05-24
forum: General Help
---

### Post by seth0x2b on 2006-05-24
Hey guys.
Since I can't seem to get any answers to this thread [http://www.ubuntuforums.org/showthread.php?t=180624](http://www.ubuntuforums.org/showthread.php?t=180624)
I thought i'd ask it here too:
I installed VmWare Workstation evaluation on Ubuntu. I installed Windows as a guest operating system. I had trouble with sharing files between host and guest, but I got it working using Shared Folders in VmWare.
What I want now is to share my internet connection with the Ubuntu box.
I connect to the internet with DHCP. Simply enabling DHCP in the guest Windows machine doesn't work. What settings do I need for the network on the guest system(VM network setting and Windows internet settings) to get internet up and running?!
Since I have DHCP, I (think) I can't have both boxes on the net on the same time(as separate machines with different IP's). Could I setup VmWare with Host only network and make the Windows "get" it's internet connection from the host's?!And if so, what other settings would I need to set up?!

Sorry for double-posting but I really need internet on windows too ](*,)
Thanks ALOT for your interest. Any hint/advice is very welcomed!
Cheers

---

### Post by adie273 on 2006-05-24
[QUOTE=seth0x2b]Hey guys.
Since I can't seem to get any answers to this thread [http://www.ubuntuforums.org/showthread.php?t=180624](http://www.ubuntuforums.org/showthread.php?t=180624)
I thought i'd ask it here too:
I installed VmWare Workstation evaluation on Ubuntu. I installed Windows as a guest operating system. I had trouble with sharing files between host and guest, but I got it working using Shared Folders in VmWare.
What I want now is to share my internet connection with the Ubuntu box.
I connect to the internet with DHCP. Simply enabling DHCP in the guest Windows machine doesn't work. What settings do I need for the network on the guest system(VM network setting and Windows internet settings) to get internet up and running?!
Since I have DHCP, I (think) I can't have both boxes on the net on the same time(as separate machines with different IP's). Could I setup VmWare with Host only network and make the Windows "get" it's internet connection from the host's?!And if so, what other settings would I need to set up?![/QUOTE]

I use Vmware Workstation on my Ubuntu setup, but i use that 'NAT' setting under the Ethernet option in the virtual machine settings. That means that the guest operating system uses the same IP address etc as the host.

If you haven't tried that already, give it a go

---

### Post by seth0x2b on 2006-05-24
It works!.
I thought that using the same IP address would mean I can only use ONE machine at a time(Ubuntu or Windows) to connect to the internet. It seems I was mistaken :)
Thanks alot!
Cheers

---

