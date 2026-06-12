---
title: "Lets give it a go! (But can i do it?)"
date: 2010-05-25
forum: General Help
---

### Post by ZnoteOT on 2010-05-25
Hello.

I am using Windows 7 Professional 64bit on my computer.

I wanna go dual boot and test out Ubuntu. 

I only got 4GB RAM, so when using Linux, 64bit should not be necessary? I should go 32bit. <--- I want to because I am afraid of compatibility issues. 

The big question:

Dual booting Windows 64bit with Ubuntu 32bit. Will that work? Ain't the loading (e.g grub loader) based on a bit like 32bit? Won't it mess the dual booting?

Is it even possible to dual boot two different bittrated OS?

I just noticed that there are thousons of different Ubuntu OS, any special I should go for? I have installed Linux once before, LinuxMint with ?Gnome? desktop? That looked a bit like Windows and stuff was easy. and I have been playing a little with command line like downloading and running a private server by following a guide and basically copy pasting everything he wrote. Not that I understod much, but it worked! :P

Well, hope you got a basic concept of my "level of experience" and can help me. :D

Greets/
Znote

---

### Post by babybean on 2010-05-25
I have 32 windows and 64 ubuntu, They both work. Windows has bother starting but I dont think it is related. Though I am sure the advice you will get is just to go for 64 bit ubuntu. With 4GB RAM it is worth it :)

---

### Post by James78 on 2010-05-25
The dual booting should work completely fine. All Grub does is set up a chain loader to the Windows loader, and it shouldn't matter whether it's 32-bit Grub handing it over to Windows or 64-bit Grub. I'm running 64-bit Ubuntu and 32-bit Windows 7, and everything works perfectly fine here.

Don't worry about compatibility issues. You're just as likely to break something by going 64-bit as you are by going 32-bit, so you might as well get 64-bit and take advantage of the extra computing power and RAM support.

If you want to go for a Windows-like interface, I suggest KDE. If you don't want to bother setting it up on your own (just install kubuntu-desktop if you do), then just get the Kubuntu variant.

---

### Post by Chris Musampa on 2010-05-25
I use 32bit as from my minimal experience with 64bit seemed like one huge problem (flash) and no tangible benefit.  Kubuntu 9.10 32bit seems to access all of my 4GB of RAM using PAE, I didn't have to do anything to enable it, I think the installer just gives you that kernel if applicable.

+1 for Kubuntu, as a windows user since for ever gnome seems... a little awkward (to be polite).

---

### Post by WorMzy on 2010-05-25
You might have a bit of trouble getting flash to work on 64-bit Ubuntu, the software repositories don't have a 64-bit version of flash by default, so you need to seek out the 64-bit version (it's floating around on these forums somewhere, or else try google) if you want to watch flash videos et al.

But yeah, with 4GB RAM, if you want to use it all, you're best off getting 64-bit Ubuntu. If you don't care about utilising all your RAM and don't want to mess about with flash, go for 32-bit.

---

### Post by ZnoteOT on 2010-05-26
Alright! I have apsolutely no intentions of ultilizing so much RAM, I will use it as a test server to see the performance difference on hosting websites windows vs linux for myself, and see if stuff works properly. And I will try to install a few games, try to make it an ordinary computer with writing apps, learn to use wine etc so I know it for later periods. I have a feeling the Linux industry is growing and it might be handy to know how to handle it.

---

