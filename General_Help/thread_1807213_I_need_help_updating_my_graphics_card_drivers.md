---
title: "I need help updating my graphics card drivers"
date: 2011-07-18
forum: General Help
---

### Post by mattv111 on 2011-07-18
I someone please tell me how I update my graphics card drivers. I've been googling all day long, and everything I find is just confusing!! Any help will be greatly appreciated!

mattv111@matt-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Let me know if you need anymore info. Thank you.

---

### Post by wildmanne39 on 2011-07-18
Hi, as far as I know you dont the driver you have is installed by the kernel it should just work. What problems are you having?

---

### Post by mattv111 on 2011-07-18
I installed WOW using wine everything went fine. Then when I try and run it my screen changes resolution and goes back to normal, and I get this error message "Your 3D accelerator card is not supported by World of Warcraft. Pleas install a 3D accelerator card with dual- TMU support." I read some where that 99% of the time that is fixed by updating the drivers. Also when I windows on this computer WOW ran fine, so I think it is the drivers. I just don't know how to update them or even which ones I need

---

### Post by wildmanne39 on 2011-07-18
> **mattv111 said:**
> I installed WOW using wine everything went fine. Then when I try and run it my screen changes resolution and goes back to normal, and I get this error message "Your 3D accelerator card is not supported by World of Warcraft. Pleas install a 3D accelerator card with dual- TMU support." I read some where that 99% of the time that is fixed by updating the drivers. Also when I windows on this computer WOW ran fine, so I think it is the drivers. I just don't know how to update them or even which ones I needHi, I will do some research and see if I can find a way. I am sure if you upgraded the kernel itself it would upgrade the driver but I do not know if that would be the right thing to do.

What version of ubuntu are you using?

---

### Post by akand074 on 2011-07-19
Have you installed the proprietary drivers using the additional drivers application? I'm not very familiar with the Intel graphics though.

---

### Post by Mark Phelps on 2011-07-19
> **akand074 said:**
> Have you installed the proprietary drivers using the additional drivers application? .

Unless they've COMPLETELY redone the implementation, THAT option only applies to AMD/ATI and Nvidia cards/chips.  Intel drivers are installed automatically.

Driver updates have to be obtained from Intel and manually installed.

---

### Post by mattv111 on 2011-07-19
Hey thanks for the replies. I'm on 10.04. I dont' know which drivers to get I was looking all around the intel site

---

### Post by wildmanne39 on 2011-07-19
> **mattv111 said:**
> Hey thanks for the replies. I'm on 10.04. I dont' know which drivers to get I was looking all around the intel siteHi, this is your card Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) if you need more help post the link for the driver and we will see if we can help you figure it out.

---

### Post by mattv111 on 2011-07-20
Found this [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=2301&lang=eng&OSVersion=Linux*&DownloadType=Drivers](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=2301&lang=eng&OSVersion=Linux*&DownloadType=Drivers)

Takes me to this [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

---

### Post by mattv111 on 2011-07-20
My kernel is 2.6.32-33-generic

---

### Post by mattv111 on 2011-07-20
Also I've notice that it only happens when I use opengl. When I delete the 'SET gxApi "OpenGL"' from the config.wtf file and launch using "wine WoW.exe" it launches but the graphics are all messed up

Edit: I also just noticed this in the terminal window "do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter."

---

### Post by wildmanne39 on 2011-07-20
Hi, this is one is out of my range of experience, I suggest that you open synaptic and see if there is a kernel upgrade that you can do for your kernel and see if that fixes your problem.

---

### Post by mattv111 on 2011-07-21
so I updated to 10.10 and now it opens and I get sound and the cursor for the game but the screen is all black. Thanks for helping. I'll look around now to see if I can find a solution to this problem

---

