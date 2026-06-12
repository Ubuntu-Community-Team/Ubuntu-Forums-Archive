---
title: "Newbie needs virtualbox help"
date: 2011-08-25
forum: General Help
---

### Post by coachdport on 2011-08-25
I have been using Ubuntu 11.04 for about 5 days now.  I am dual booting it and windows 7 because i need some windows programs for work.  I used vmware's program and made a virtual machine from my windows 7 hard drive partition.  I can run the virtual machine in ubuntu and everything works great except for the internet.  It can't connect and says in the device manager that it can't get the driver for the intel ethernet pro/1000 desktop.  Can anyone give me some help? The application I have to have for work is a website for football video that uses silverlight.  I have installed moonlight but the website still doesn't work right.  Thanks for the help.

---

### Post by coachdport on 2011-08-26
Can anyone point me in the right direction?

---

### Post by Bachstelze on 2011-08-26
Are you using vmware or virtualbox?

---

### Post by jerrrys on 2011-08-26
sounds more like a driver problem than a virtual problem.  in which case, i am of little help.  but i can a least give you a couple of links to investigate

 [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=intel+pro%2F1000+drivers&sa=Search&cof=FORID:9#806](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=intel+pro%2F1000+drivers&sa=Search&cof=FORID:9#806)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=intel+ethernet+pro%2F1000&sa=Search&cof=FORID:9#866](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=intel+ethernet+pro%2F1000&sa=Search&cof=FORID:9#866)

good luck

---

### Post by e79 on 2011-08-26
If you are using VirtualBox, did you installed the package called ['VirtualBox Extension Pack']("http://download.virtualbox.org/virtualbox/4.1.2/Oracle_VM_VirtualBox_Extension_Pack-4.1.2-73507.vbox-extpack") on your Ubuntu host, and then installed the VirtualBox Guest Addition in your Windows guest ?

---

### Post by haqking on 2011-08-26
Do you have your virtual machine set to NAT or Bridged networking ?

If it is bridged and you have assigned it a Static IP is it valid for your network ?

---

### Post by e79 on 2011-08-26
> **haqking said:**
> If it is bridged have you assigned it a valid Static IP ?

Sorry to correct you, but whether its bridged or NATed, the default setting is always DHCP since it is the Windows installation that controls it and not the virtualization program.

---

### Post by haqking on 2011-08-26
> **e79 said:**
> Sorry to correct you, but whether its bridged or NATed, the default setting is always DHCP since it is the Windows installation that controls it and not the virtualization program.

You are not correcting me, as i said nothing incorrect.

I was asking a question, if he has assigned it a static IP then i was asking to make sure it is valid for the network if using bridged. hence the question mark on the end of the sentence ;-)

---

### Post by e79 on 2011-08-26
> **haqking said:**
> You are not correcting me, as i said nothing incorrect.

I was asking a question, if he has assigned it a static IP then i was asking to make sure it is valid for the network if using bridged. hence the question mark on the end of the sentence ;-)

I misunderstood then, ma bad :D

---

### Post by haqking on 2011-08-26
> **e79 said:**
> I misunderstood then, ma bad :D
 

no worries, probably the way it reads.

peace

---

### Post by bodhi.zazen on 2011-08-26
> **coachdport said:**
> I have been using Ubuntu 11.04 for about 5 days now.  I am dual booting it and windows 7 because i need some windows programs for work.  I used vmware's program and made a virtual machine from my windows 7 hard drive partition.  I can run the virtual machine in ubuntu and everything works great except for the internet.  It can't connect and says in the device manager that it can't get the driver for the intel ethernet pro/1000 desktop.  Can anyone give me some help? The application I have to have for work is a website for football video that uses silverlight.  I have installed moonlight but the website still doesn't work right.  Thanks for the help.

Trying to get back on track ...

First shut down windows

In your virtualization software, vbox or vmware, select a different internet driver, then try windows again.

[http://www.virtualbox.org/manual/ch06.html#nichardware](http://www.virtualbox.org/manual/ch06.html#nichardware)

---

### Post by coachdport on 2011-08-26
I used vmware vcenter converter standalone client to make a virtual machine from my windows partition.  I couldn't get vmware player 3.1.4 installed on ubuntu so I have been running the virtual machine I created in virtualbox, which I could get installed.  I have the network set up as NAT and the adapter is Intel PRO/1000 MT Desktop (NAT).  Everything works great except for the internet, which I can't get.  I have installed the add ons from the first page of this post and the virtual machine add ons.  Anything else you guys need to know to help me figure this out, just let me know.

---

### Post by coachdport on 2011-08-26
Like I said I am new to Linux.  So how would I go about installing drivers for this problem.  Would I install them in the windows 7 guest os or the Ubuntu 11.04 host os? And how would I install drivers in Linux?

---

### Post by searchfgold6789 on 2011-08-26
You would have to install them in the virtual machine, that I can answer. It's as simple as obtaining the driver from the Intel home page, downloading it to one of your shared folders or a CD, and running it from the virtual machine.

---

### Post by e79 on 2011-08-26
> **coachdport said:**
> I used vmware vcenter converter standalone client to make a virtual machine from my windows partition. I couldn't get vmware player 3.1.4 installed on ubuntu so I have been running the virtual machine I created in virtualbox, which I could get installed.  I have the network set up as NAT and the adapter is Intel PRO/1000 MT Desktop (NAT).  Everything works great except for the internet, which I can't get.  I have installed the add ons from the first page of this post and the virtual machine add ons.  Anything else you guys need to know to help me figure this out, just let me know.

Could you paste the result in Windows of :

```
ipconfig /all
```

Could you also try to set your host adapter to 'bridged' instead of 'NAT' ? It should simply be able to obtain an IP address from your DHCP server if everyting goes well.

I personnaly only use NAT when I cannot get a second address on the network for my virtual machine or if I'm on a laptop so it can benefit the WiFi.

---

### Post by coachdport on 2011-08-26
I have tried to find the drivers for the intel pro/1000 mt desktop network card, but intel's sight said you could not download those drivers. Not really sure why.  Trying to find other drivers now, but its not looking good.  I can't believe I can't find drivers for any of those options.  Anyone know where I might find one?

---

### Post by searchfgold6789 on 2011-08-26
[http://downloadcenter.intel.com/detail_desc.aspx?agr=Y&DwnldID=18713](http://downloadcenter.intel.com/detail_desc.aspx?agr=Y&DwnldID=18713)

---

### Post by wildmanne39 on 2011-08-27
Hi, you do not need to install drivers, here is what mine looks like it should be very simple as long as your wired internet is working in ubuntu.

---

### Post by wildmanne39 on 2011-08-27
Hi, if I understand you correctly you did not create the vm in virtualbox if that is the case that may be a problem since you are using it in virtualbox now, I am not sure if that is an issue though.

---

### Post by coachdport on 2011-08-27
Okay this might be the problem.  I am not using wired internet at all.  I am trying to get wifi to work.  Is that possible in virutalbox?  Also i also thought that creating the virtual machine in vmware might be the problem.

---

### Post by wildmanne39 on 2011-08-27
Hi, as far as I know you need a wired connection.

Yes it could be a problem that the vm was created in another vm program.

Do you not have access to a wired connection?

---

### Post by wildmanne39 on 2011-08-27
Hi, here is a link for all possible settings for networking in virtualbox.
[http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

---

### Post by bodhi.zazen on 2011-08-27
> **wildmanne39 said:**
> Hi, if I understand you correctly you did not create the vm in virtualbox if that is the case that may be a problem since you are using it in virtualbox now, I am not sure if that is an issue though.

This is probably the problem. It is not so trivial to export a vmware guest to virtualbox.

I suggest you simply install a virtualbox guest.

---

### Post by coachdport on 2011-08-27
I could use wired connections if I absolutely had to, but I would rather just boot back into my windows partition instead of doing that.  The reason I used vmware to make the virtual machine is because I don't have a copy of windows 7.  It came with this laptop and didn't have an install disk with it.  Could I use virualbox on my windows partition to make a virtual machine?

---

### Post by wildmanne39 on 2011-08-27
Hi, yes you can make a virtual machine out of windows 7 with virtualbox, I have not done it and it takes a little setting up but I think it is easier then it used to be.

Read over all the documentation from this link.
[http://www.virtualbox.org/](http://www.virtualbox.org/) 
You can also use there forum if you need to but it is not a friendly as this one.

Also make your recovery disks before you try to make windows partition into your virtual machine, just in case you need to reinstall windows if the process fails.

---

