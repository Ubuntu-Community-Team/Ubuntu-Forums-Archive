---
title: "iTunes on VM ( Ubuntu )"
date: 2012-04-05
forum: General Help
---

### Post by susja on 2012-04-05
Hello,
Not sure if it's the right forum for this question but I'll try :)
I recently bought iPad3 and need iTunes. I run Ubuntu 11.10 and iTunes doesn't support Linux. Well I installed Virtualbox on my Ubuntu and it's WinXP. Then I installed iTunes on windows. Now the problems started. My VM is seen on my home networks and my iPad also could recognize it and browse files/folder from iPad using iPad application FileExplorer. That tells me that they could talk to each other. Now when I start iTunes I want to sync it with my iPad wirelessly but it failed to find iPad. When I connect it with a  cable it locates it but not wirelessly.
Any idea how could I make VM running on Ubuntu to sync with iPad using WiFi?
Thanks.

---

### Post by Paddy Landau on 2012-04-06
Have you set your VM to use the same or a different IP from the host machine? If it's the same IP, your iPad is probably trying to access your Ubuntu OS.

(BTW, I presume you are using a router to connect your devices to the Internet. If not, it becomes more complicated.)

To set the VM to use a different IP address:

[LIST=1]
[*]Select your VM in Virtual Box (do not start it yet).
[*]Settings > Network > Adapter 1
[*]Enable Network Adapter (should already be ticked).
[*]Attached to > Bridged Adapter.
[*]If necessary, press Advanced and change any settings there, though the defaults should work.
[/LIST]
Now start your VM and iTunes, and see whether or not you can synchronise.

---

### Post by susja on 2012-04-06
hello,
thanks for reply,
I set my VM to use different IP than the host machine. I could wirelessly access my VM (I use app FileExplorer for that) file system from iPad hence they could talk. And I'm using router at home so all my home system are using the same LAN. And I'm using Bridged Adapter for VM.
Well I'll try it again ... but still confused .. it looks something related  particularly to iTunes and iPad sync. BTW I noticed that documentation states that iPad should be powered when try sync over WiFi.
Thanks again.

---

### Post by susja on 2012-04-07
well ... I realized that when I have to connect any device to my VM I have to enable USB connection. After that I could access external device.
I suggest that in my case the issue is not with iTunes but Virtualbox fails to establish connection to devise over WiFi.
I think I'll open another thread with more specific information.
Thanks.

---

### Post by susja on 2012-04-07
Hello,
In order to use my iPad with iTunes I installed Virtualbox on my Ubuntu 11.10. I installed WinXp on Virtualbox. When I connect device to my computer and start VM I have to enable USB connection to that device. After that I have no problem.
My problem is that I want to establish connection to iTunes over WiFi but it failed to recognize my iPad. Do you know if it's possible? Maybe it also need some tweak to enable WiFi on VM or etc?
Thanks in advance.

---

### Post by mikewhatever on 2012-04-07
Hm..., last time I checked, VirtualBox didn't implement a wifi interface, but a wired interface it provides should work just as well.

---

### Post by lisati on 2012-04-07
Threads merged: having two active threads for the same problem (or related issues) can dilute the communty's efforts.

---

### Post by susja on 2012-04-07
Well ... not sure what happened and was wrong before :)
Now as soon as I start my iPad it get connected to VM and they could recognize each other.
I'm 'resolving' this thread.

---

### Post by Paddy Landau on 2012-04-08
> **mikewhatever said:**
> Hm..., last time I checked, VirtualBox didn't implement a wifi interface, but a wired interface it provides should work just as well.
I have just tested Virtual Box by disconnecting my Ethernet and specifying that the bridged connection use wireless (wlan2). That works. But the guest machine thinks it is connecting via a wired connection.

In other words, you are correct.

However, it should not affect access by iTunes and the iPad.

---

