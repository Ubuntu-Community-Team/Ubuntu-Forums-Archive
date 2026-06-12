---
title: "Wanting to install Ubuntu with Vista. Few questions..."
date: 2010-03-07
forum: General Help
---

### Post by silverwolf22 on 2010-03-07
1. I'm wanting to use Wubi, But I'm still scarred out of my wits. Can I still get to Windows vista okay? Can I uninstall it and go back to using vista as I am now if I don't like it? Can I still get to my Dell/Windows recovery program thing (Press F8 on boot and hit repair windows ect) if my Windows ever screws up? Can I still reinstall windows with my Dell restore DVDs? And I CAN dualboot with vista using Wubi right?

2. What about games? I only usualy play Emulators (Up to PS1 and N64 and below) and TF2 and stuff. Can I use Wine to play Steam games? Are there any console emulators that run natively under Ubuntu? Can I run Steam using Ubuntu somehow (wine ect)?

3. I mainly only play the games described above, Watch anime, Use the internet and listen to music on my PC now, Will I like Ubuntu better? Will it run faster than Vista?

Sorry for all the dumb newbie questions, I just never installed another OS before, And I'm sick of M$'s crap. Thanks :D

EDIT: Also, How does HDD space work with Wubi and vista? Since it's not a seperate partition, If I say, Install a 1GB program on Ubuntu, How would that effect my total HDD space in Windows? Say I have 350GB left, I install a 1GB program in Ubuntu, Would that make it say 349GB in both Windows and Ubuntu?

---

### Post by Old_Grey_Wolf on 2010-03-07
> **silverwolf22 said:**
> 1. I'm wanting to use Wubi, But I'm still scarred out of my wits. Can I still get to Windows vista okay? Can I uninstall it and go back to using vista as I am now if I don't like it? Can I still get to my Dell/Windows recovery program thing (Press F8 on boot and hit repair windows ect) if my Windows ever screws up? Can I still reinstall windows with my Dell restore DVDs? And I CAN dualboot with vista using Wubi right? 

Before you do anything read my signature.

I'm not a fan of WUBI; however, you can use it to determine if you like Ubuntu. If you like it then I would suggest installing it as a dual boot or install it using Virtualization (hypervisor) like VMware or Virtualbox. 

To answer some of your questions, here is a link to WUBI FAQ - [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php).

The Dell provides a boot-loader that runs before Windows loads. That is what makes the F8 key work. WUBI should not affect the Dell boot-loader. 

Your Dell restore DVDs will overwrite everything you have on your disk and return your disk to the configuration it was in when you baught it.
 
>  2. What about games? I only usualy play Emulators (Up to PS1 and N64 and below) and TF2 and stuff. Can I use Wine to play Steam games? Are there any console emulators that run natively under Ubuntu? Can I run Steam using Ubuntu somehow (wine ect)? 
I'm not a gamer. I can't answer that question.

>  3. I mainly only play the games described above, Watch anime, Use the internet and listen to music on my PC now, Will I like Ubuntu better? Will it run faster than Vista?

You like some games and not others. With Linux distributions it is similar. You may like some and not others. You probably don't think of MAC OSX as a replacement for Microsoft Windows. Linux is not a replacement either, it is a totally different operating system.

Linux should run faster than Vista. If it doesn't then you need to install the correct video driver for your video card.

> Sorry for all the dumb newbie questions, I just never installed another OS before, And I'm sick of M$'s crap. Thanks :D
Don't need to say you are sorry. Most of us have been through the same feelings you are experiencing.

>  EDIT: Also, How does HDD space work with Wubi and vista? Since it's not a seperate partition, If I say, Install a 1GB program on Ubuntu, How would that effect my total HDD space in Windows? Say I have 350GB left, I install a 1GB program in Ubuntu, Would that make it say 349GB in both Windows and Ubuntu?
Disk space doesn't magically appear out of nowhere. WUBI uses disk space. If you need more, you can resize the WUBI disk space but you loose some for Windows. :D

---

### Post by meierfra. on 2010-03-07
> Say I have 350GB left, I install a 1GB program in Ubuntu, Would that make it say 349GB in both Windows and Ubuntu? 

Not quite.  You will have to choose how much to use for Wubi during installation.  Say you choose 50GB for Wubi. Then you will have 50GB available for   Wubi and 300GB for Windows. (It is possible to resize Wubi later, but it is not easy)

---

### Post by Old_Grey_Wolf on 2010-03-07
> **meierfra. said:**
> Not quite.  You will have to choose how much to use for Wubi during installation.  Say you choose 50GB for Wubi. Then you will have 50GB available for   Wubi and 300GB for Windows. (It is possible to resize Wubi later, but it is not easy)

Yeah, that is one reason I like Virtual Machines (VM). You can set up the VM to increase its disk space dynamically as needed.

---

