---
title: "WMWare question"
date: 2006-06-01
forum: General Help
---

### Post by Hoffmann on 2006-06-01
Hello:

First of all, how is your newest Dapper going? I am enjoying it a lot!!!

Does anyone here have experience with VMWare on Ubuntu? I realized that WMWare player is available for installing from synaptic. Well, I have a WindowsXP/Dapper dual boot system, and I would like to access my Windows partition from Ubuntu, or to build a virtual Windows for using from Ubuntu. I do use Ubuntu linux 90% of the time but, some times I need to use Windows. I am so in love with Ubuntu, that even during those 10 % of the time in Windows, I would like to "stay" on Ubuntu. :D 

Any hint for a start? 

Thanks a lot!

---

### Post by nix4me on 2006-06-01
Yes.  Vmware works fine.  I have vmware server (beta) running and I made a xp virtual no problem.

There was a post yesterday of someone who had .deb made for vmware server.  If you cant find it, just get it from vmware's website.

nix4me

---

### Post by nix4me on 2006-06-01
Here is the link.

[http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu](http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu)

nix4me

---

### Post by Rackerz on 2006-06-01
I've got VMWare workstation, is that ok to use?

---

### Post by Hoffmann on 2006-06-01
[QUOTE=nix4me]Here is the link.

[http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu](http://blog.wilf.me.uk/articles/2006/04/01/vmware-server-beta-on-ubuntu)

nix4me[/QUOTE]

Oops!!! I mistyped the name. Yes, I am talking about VMWare. 
Thanks a lot for  the link. I realized that the link is regarding installation of VMWare server. Could you let me know how did you implemented, how you are using WindowsXP on Ubuntu with VMWare?

---

### Post by mlind on 2006-06-01
There was a recent HOWTO about VMWare (was it player?) on Dapper forums.
You should search it and check it out, it was good stuff.

---

### Post by ubuntu_demon on 2006-06-01
I had troubles with vmware-player today see :
[http://www.ubuntuforums.org/showthread.php?p=1078764](http://www.ubuntuforums.org/showthread.php?p=1078764)

---

### Post by Hoffmann on 2006-06-01
[QUOTE=ubuntu_demon]I had troubles with vmware-player today see :
[http://www.ubuntuforums.org/showthread.php?p=1078764](http://www.ubuntuforums.org/showthread.php?p=1078764)[/QUOTE]
Wow!

After reading your comments on the other thread, I decide to forget to install VMWare for while, just in case. Dapper LTS is working so nice on my machine, and I can just boot to Windows, when needed....
Many thanks for your explanation!

---

### Post by siorai on 2006-06-01
VMWare Workstation (and previously Player) has been working perfectly for me. The only annoyance is that any time the kernel gets updated, I have to reinstall VMWare. It's really not a big deal though since I just need to accept all the default answers and it really only takes about 5 minutes at most.

Oh yeah, I didn't install through the repos. I installed with the installer from the VMWare website.

---

### Post by seth0x2b on 2006-06-02
Dapper with VMware workstation here. I run 2 virtual machines(Ubuntu Hoary and WindowsXP). Both work great! (no 3D acceleration, but I use it for Photoshop and Macromedia Flash so..no problem :) ).

Cheers

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Hoffmann]Wow!

After reading your comments on the other thread, I decide to forget to install VMWare for while, just in case. Dapper LTS is working so nice on my machine, and I can just boot to Windows, when needed....
Many thanks for your explanation![/QUOTE]
If you understand my instructions you'll probably be allright if it happens to you. I think it only happens in certain cases. It might be related to the motherboard or something else.

---

### Post by 5-HT on 2006-06-02
Possibly a stupid question (guess the answer is: try it and see), but please bear with me. I've searched the vmware website and this forum, but couldn't find the answer.

 I haven't used vmware yet but was wondering if I install Windows XP through vmware, will I have any problems activating windows as the hardware XP sees will be 'virtual' (I think, not sure) and not necessarily my computer's hardware?
 
I have used and activated XP on this computer before, so it's pretty much tied to the hardware. 

Thanks for any input.

(Sorry for the possible hijack, I thought the question fit somewhat in this thread)

---

### Post by seth0x2b on 2006-06-02
[http://www.vmware.com/support/guestnotes/doc/guestos_winxp.html](http://www.vmware.com/support/guestnotes/doc/guestos_winxp.html)
Check the "Product activation" area.


Cheers

---

### Post by Hoffmann on 2006-06-02
[QUOTE=seth0x2b][http://www.vmware.com/support/guestnotes/doc/guestos_winxp.html](http://www.vmware.com/support/guestnotes/doc/guestos_winxp.html)
Check the "Product activation" area.
Cheers[/QUOTE]
My dilema is: should I install VMWare player, and try to install the virtual Windows by using a free program for constructing the virtual machine or not? I realized that some people are using the non-free VMWare product. Well, I wouldn't like to spend money on that.
Any hint?

---

### Post by seth0x2b on 2006-06-02
This was good reading: [http://blogs.zdnet.com/BTL/?p=2631](http://blogs.zdnet.com/BTL/?p=2631)
Seems that some hardware aspects are not "virtualizable" (like the type of processor).So, probably windows does get(some) correct hardware information, not "virtual".
I think the worst thing that could happen is you'll have to activate your license again.
Here's the activation FAQ: [http://www.microsoft.com/piracy/activation_faq.mspx](http://www.microsoft.com/piracy/activation_faq.mspx)
> Product Activation discourages piracy by limiting the number of times a product key can be activated on different PCs (taken from the Microsoft product activation FAQ)
So..you can activate it on several architectures, but the number of "tries" is kinda' limited.

Cheers

---

### Post by Hoffmann on 2006-06-02
[QUOTE=seth0x2b]This was good reading: [http://blogs.zdnet.com/BTL/?p=2631](http://blogs.zdnet.com/BTL/?p=2631)
Seems that some hardware aspects are not "virtualizable" (like the type of processor).So, probably windows does get(some) correct hardware information, not "virtual".
I think the worst thing that could happen is you'll have to activate your license again.
Here's the activation FAQ: [http://www.microsoft.com/piracy/activation_faq.mspx](http://www.microsoft.com/piracy/activation_faq.mspx)

So..you can activate it on several architectures, but the number of "tries" is kinda' limited.

Cheers[/QUOTE]
Ok. I think my best option is not to install VMWare player. When I need to use Windows, I will boot to its partition. That seems to be safer and not time consuming. I have done that, since I started using linux.

---

### Post by seth0x2b on 2006-06-02
That is the best option(booting to Windows).On VmWare you can't install your video drivers, can't play games, you basicaly can use Windows only for "normal" software, and not at all for OpenGL games(it that's your thing).
But it's nice to know you have an alternative to rebooting.That's all :)
I personally don't have any problems with VmWare+WindowsXP.

Cheers

---

### Post by 5-HT on 2006-06-02
[quote=seth0x2b][http://www.vmware.com/support/guestnotes/doc/guestos_winxp.html]("http://www.vmware.com/support/guestnotes/doc/guestos_winxp.html")
Check the "Product activation" area.


Cheers[/quote] 
[quote=seth0x2b]This was good reading: [http://blogs.zdnet.com/BTL/?p=2631]("http://blogs.zdnet.com/BTL/?p=2631")
Seems that some hardware aspects are not "virtualizable" (like the type of processor).So, probably windows does get(some) correct hardware information, not "virtual".
I think the worst thing that could happen is you'll have to activate your license again.
Here's the activation FAQ: [http://www.microsoft.com/piracy/activation_faq.mspx]("http://www.microsoft.com/piracy/activation_faq.mspx")

So..you can activate it on several architectures, but the number of "tries" is kinda' limited.

Cheers [/quote]

Thanks a lot! Guess I didn't look hard enough.

---

### Post by leetcharmer on 2006-06-03
is it possible to get any 3D acceleration w/ vmware? I want to run HL2 faster than Cedega will let me :/.


nevermind -- answer was already posted.

---

