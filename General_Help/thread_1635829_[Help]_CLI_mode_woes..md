---
title: "[Help] CLI mode woes."
date: 2010-12-02
forum: General Help
---

### Post by os[x on 2010-12-02
Hi guys,

I have a netbook that I mainly just use for programming and writing, and thus I have absolutely no need for a proper graphical GUI. I'd much rather just have a command line interface. 

So, anyway, I downloaded the Alternate Install CD, which provides just this feature. Cool.

..Only to find that it's stuck in 8 bit color mode. For the life of me I could not work out how to enable higher color modes. I was editing GRUB2, downloading all sorts of tools and so on. Eventually it would output that it was displaying 256 colors (using tput colors iirc), but if you tried to load a 256 color program it would just go crazy and turn all the characters into ÈÍÎÅØÎØÍÈÎÅÈÎØ type script or else just overlap the text to the point of unintelligability.

Is this something to do with the lack of framebuffer, or something? I don't really understand what's going on here -- but I do need to have at least 256 colors just for easiness on the eye, really. Can someone help me out? What do I have to do?

---

### Post by nothingspecial on 2010-12-02
Are you using screen?

I ask because, I`m pretty sure the screen package that comes bundled with Ubuntu is compiled without support for 256 colours. Annoying huh.

Just like you can`t watch a vid in the framebuffer within it.

That`s why we have multiple ttys I suppose.

You can compile screen with 256 colour support. If I find a link I`ll post back :D

---

### Post by QLee on 2010-12-02
[QUOTE='os[x]Hi guys,

I have a netbook that I mainly just use for programming and writing, and thus I have absolutely no need for a proper graphical GUI. I'd much rather just have a command line interface. 

So, anyway, I downloaded the Alternate Install CD, which provides just this feature. Cool.

..Only to find that it's stuck in 8 bit color mode. For the life of me I could not work out how to enable higher color modes. I was editing GRUB2, downloading all sorts of tools and so on. Eventually it would output that it was displaying 256 colors (using tput colors iirc), but if you tried to load a 256 color program it would just go crazy and turn all the characters into ÈÍÎÅØÎØÍÈÎÅÈÎØ type script or else just overlap the text to the point of unintelligability.

Is this something to do with the lack of framebuffer, or something? I don't really understand what's going on here -- but I do need to have at least 256 colors just for easiness on the eye, really. Can someone help me out? What do I have to do?[/QUOTE]

I'm not real sure I understand what you are asking for because first you say you want just a CLI. The command line doesn't have colours, unless you are using ANSI escape sequences, but then you say you want to load a program with 256 colours and you are stuck in 8 bit colour mode. Well, 8 bit colour is 256 colours and it's the default on my system. 

I'd guess you could try stopping the boot and going to a GRUB shell command line and run vbeinfo to see what your graphic card supports, followed by uncomenting and changing the line in /etc/default/grub, #GRUB_GFXMODE=640x480, followed by a update of GRUB. I don't know if that would work for what you want or not and you may have already tried that, you didn't specify what you have tried.

However, I might be totally misunderstanding your question.

Maybe mention the name of the program you're having trouble with.

---

### Post by os[x on 2010-12-02
> **QLee said:**
> I'm not real sure I understand what you are asking for because first you say you want just a CLI. The command line doesn't have colours, unless you are using ANSI escape sequences, but then you say you want to load a program with 256 colours and you are stuck in 8 bit colour mode. Well, 8 bit colour is 256 colours and it's the default on my system. 

I'd guess you could try stopping the boot and going to a GRUB shell command line and run vbeinfo to see what your graphic card supports, followed by uncomenting and changing the line in /etc/default/grub, #GRUB_GFXMODE=640x480, followed by a update of GRUB. I don't know if that would work for what you want or not and you may have already tried that, you didn't specify what you have tried.

However, I might be totally misunderstanding your question.

Maybe mention the name of the program you're having trouble with.
I am not talking about 8 bit colors, which is indeed 256 colors. I am talking about 8 colors -- Black, White, Green, Cyan, Purple, Yellow, Blue, and Red.

Any program that runs in 256 color mode does not work in 256 color mode. It's not just screen, either, although that doesn't work either -- if I try to run emacs, links2, mutt or vim in 256 color mode, I get clipping issues and errors all over the place.

Thanks for the suggestion with the comment in grub. I have uncommented that and have also tried adding vga and a vesa reso number to the boot line, but no joy.

I suspect it is a framebuffer issue, but I have no idea how to fix that.

---

### Post by nothingspecial on 2010-12-02
> **'os[x said:**
> I am not talking about 8 bit colors, which is indeed 256 colors. I am talking about 8 colors -- Black, White, Green, Cyan, Purple, Yellow, Blue, and Red.

Any program that runs in 256 color mode does not work in 256 color mode. It's not just screen, either, although that doesn't work either -- if I try to run emacs, links2, mutt or vim in 256 color mode, I get clipping issues and errors all over the place.

Thanks for the suggestion with the comment in grub. I have uncommented that and have also tried adding vga and a vesa reso number to the boot line, but no joy.

I suspect it is a framebuffer issue, but I have no idea how to fix that.

Try fbterm

---

### Post by nothingspecial on 2010-12-02
> **QLee said:**
> I'm not real sure I understand what you are asking for because first you say you want just a CLI. The command line doesn't have colours, 

I have colours in my console

[ATTACH]177210[/ATTACH]

---

### Post by os[x on 2010-12-02
> **nothingspecial said:**
> I have colours in my console

[ATTACH]177210[/ATTACH]
Yes, but that's only 8 colours. I'm talking about 256.

---

### Post by QLee on 2010-12-03
> **nothingspecial said:**
> I have colours in my console

Yes, I can too, the ones that can be programmed with ANSI escape sequences.

---

### Post by QLee on 2010-12-03
[QUOTE='os[x']...
Thanks for the suggestion with the comment in grub. I have uncommented that and have also tried adding vga and a vesa reso number to the boot line, but no joy.
...[/QUOTE]
Did you try dropping to a GRUB shell and running vbeinfo to obtain the information of what your graphics adaptor is capable of? The last line presented should be what the system is currently using. As well as uncommenting that line you could change it too, to a different resolution and colour depth from the list obtained with vbeinfo. However, I'm making an assumption, if you are using legacy GRUB you would want to use vbeprobe in the GRUB shell.

---

