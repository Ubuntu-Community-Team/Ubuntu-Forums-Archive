---
title: "Is there a hardware list for DVD burners that work in Ubuntu?"
date: 2006-02-20
forum: General Help
---

### Post by annsachd on 2006-02-20
Is there a hardware list for DVD burners that work in Ubuntu?

Thanks for the help.

---

### Post by el3ktro on 2006-02-20
Why should a DVD burner not work? They're all the same ATAPI interface and don't need any driver at all. The only thing that does not work yet is S-ATA DVD burners, but there's only one such thing on the market afaik, Pioneer or Panasonic.

Tom

---

### Post by taurus on 2006-02-20
Let's see.  I have NEC, Toshiba, Sony, and some crappy DVD that I can't even find who built it in my new Dell on my machines at work and home and every single one of them works just fine...

---

### Post by annsachd on 2006-02-20
Odd, I know I've read some threads where people had trouble getting their DVD writer recognized.

---

### Post by soulestream on 2006-02-20
> Odd, I know I've read some threads where people had trouble getting their DVD writer recognized.

i wouldnt go blaming that on the burner. ;) 

soule

---

### Post by annsachd on 2006-02-20
That's a very good point.

I'm looking at a Sony internal someone wants to sell me for cheap. Just don't want to get stuck with something that doesn't work in Ubuntu.

---

### Post by Genecks on 2007-11-27
> **el3ktro said:**
> Why should a DVD burner not work? They're all the same ATAPI interface and don't need any driver at all. The only thing that does not work yet is S-ATA DVD burners, but there's only one such thing on the market afaik, Pioneer or Panasonic.

Tom

Oh, excuse me, I thought it was because they were MMC compliant, as listed on the DVD-tools website. *dark, biting sarcasm*

No, but really folks, as I searched the web for "dvd burners that work with Linux" this page came up. I think if anyone else is going to research the topic, this thread might be of interest.

For one thing, not all CD/DVD drives were created equal.
Laptop drives are different than drives inside of boxes.

Also, there is the fact that many DVD-burners need firmware updates, which seem to be solely available for Windows. Is someone going to say that the coders who work in C and whatever language for the drivers have already thought about this?

And if so, prove it.
I need to see some actual sources.

I've been to the Linux kernel website, and I've seen pages say, "Fixed bug and created update to device."

Maybe the Linux kernel website is the only HCL list available? In other words, if you want to know if a device works, you have to sort through all the B.S. located inside of the Linux Kernel website?

---

### Post by jespdj on 2007-11-27
First of all, why are you replying to a thread that is 1 year and 9 months old?

Do you have a specific CD/DVD drive that does not work with Ubuntu and are you annoyed by it? If so, explain exactly what hardware you have and someone might be able to help you with the problem.

Almost all CD/DVD burners work with Linux, because they all use the same interface (PATA or SATA). Laptop drives use the same kind of interface internally, so there is not a big difference with desktop PCs.

About firmware updates: The firmware is the software inside the drive itself. It is not specifically for Windows or for any other operating system. It runs on the processor in the drive itself. Maybe the software you need to update the firmware is for Windows only, and if that's so you have to blame the manufacturer of the drive and/or the firmware. It's not something that Linux developers can fix for you.

---

