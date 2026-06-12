---
title: "64 bit or 32 bit?"
date: 2010-08-14
forum: General Help
---

### Post by talhaguy on 2010-08-14
Hey everyone,

I have a desktop with a AMD phenom II x6 processor. I was wondering whether I should install the 32-bit or 64-bit version of Ubuntu 10.04. Also, does anyone know it's performance on this processor?

I also have ATI Radeon HD 5850 graphics card. Do you guys think the graphics will be supported in Ubuntu 10.04?

I have been using Ubuntu on my laptop for a while but haven't installed it on this desktop for fear of any incompatibility.

---

### Post by uRock on 2010-08-14
64bit will work great. The only problem with it is that 64bit flash is not that great. As for the GPU, I'd recommend running the LiveCD and seeing how it acts.

---

### Post by Nick_Jinn on 2010-08-14
If you have less than 1.5gb of ram, I wouldnt use 64 bit. You dont really need 64bit to get the most out of your ram until you get above 3.2gb. 

Despite what I was told when I asked this same question, there are a number of compatibility issues with 64bit still. Some apps wont work in 64. Gaming in some instances takes some more doing. I always use 32 unless I have 4gb of ram, like I do in my desktop and laptop.

---

### Post by uRock on 2010-08-14
> **Nick_Jinn said:**
> If you have less than 1.5gb of ram, I wouldnt use 64 bit. You dont really need 64bit to get the most out of your ram until you get above 3.2gb. 

Despite what I was told when I asked this same question, there are a number of compatibility issues with 64bit still. Some apps wont work in 64. Gaming in some instances takes some more doing. I always use 32 unless I have 4gb of ram, like I do in my desktop and laptop.
The 32bit PAE kernel can support up to 64GB RAM.

---

### Post by Nick_Jinn on 2010-08-14
Then why does my system only recognise 3.2gb?

---

### Post by uRock on 2010-08-14
> **Nick_Jinn said:**
> Then why does my system only recognise 3.2gb?
Because you aren't using the PAE kernel properly.

---

### Post by Nick_Jinn on 2010-08-14
Thats an entirely believable explanation. 

How would I go about using it properly?

---

### Post by uRock on 2010-08-14
> **Nick_Jinn said:**
> Thats an entirely believable explanation. 

How would I go about using it properly?
You should start a thread if you need help using the PAE kernel to its full potential, instead hijacking this one.

---

### Post by talhaguy on 2010-08-15
Thanks for the info guys. I'll probably end try the Live CD and see how it goes. I'll post what I can tell here.

Also, somebody above mentioned some programs may not work. Are these rare programs or commonly used ones?

---

### Post by uRock on 2010-08-15
> **talhaguy said:**
> Thanks for the info guys. I'll probably end try the Live CD and see how it goes. I'll post what I can tell here.

Also, somebody above mentioned some programs may not work. Are these rare programs or commonly used ones?
64bit Flash is the only real problem for 64bit. There are many fixes listed on the net for flash. The only 32bit program I have not been able to install was Cisco PacketTracer.

---

### Post by Ginsu543 on 2010-08-15
64-bit or 32-bit also depends on how you intend to use your computer, not just on how much ram you have. If you intend to do cpu-intensive work, such as converting video, a 64-bit OS will give you better performance and save you time, since it will give that much more bandwidth to the cpu to access the ram.

As mentioned above, the only *possible* drawback I can see for 64-bit at this time is the Flash issue. For these reasons, I always install 64-bit for my machines.

---

### Post by Nick_Jinn on 2010-08-16
I have found that certain apps just wont work, like the accuweather widget only loads in a 32bit system currently. 

Gyachi doesnt use flash....I dont think anyway, and while its the best messenger for yahoo having voice and webcam support that Pidgen is still lacking for Yahoo specifically, those functions work in 32 and not 64.


These are just a few examples. There are more examples of things that still dont work in 64 besides flash.

And it uses more ram.

---

### Post by pania on 2010-08-16
My opinion is 64-bit machine, 64-bit operating system, the reason is performance. Flash works for me.

[http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

