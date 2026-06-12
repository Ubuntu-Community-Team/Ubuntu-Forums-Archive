---
title: "BIOS update question - Error #M1004"
date: 2006-03-29
forum: General Help
---

### Post by aresgoddess on 2006-03-29
Ok, so, I installed Breezy on Sunday night, i think. Might have been Monday night. since then, my comp has shut down and displayed the error #M1004 when I start it back up. This error refers to a too high temperature in the computer. (Dell Inspiron 5150, btw.) I wrote an email to Dell and got an automated response that said I need to update BIOS, but when I try to download the update, no matter what OS i say that I use, I get a link to download an .exe file and if i remember correctly, .exe files can't be used in any linux system, right? 

So what do i do? Is it possible to use the .exe file or should i look for something else?

What is BIOS anyways? It affects the motherboard, right? Is that the same as the processor? 

I read somewhere, i don't know where, that it might be possible to change an .exe to an .iso and burn the image onto a cd-rw and install it that way. is that true? if it is, how can i do that?

---

### Post by play0r on 2006-03-29
here's a link to dell's linux projects:
[http://linux.dell.com/projects.shtml](http://linux.dell.com/projects.shtml)

check out the BIOSdisk section of dell's linux projects website, hopefully that will sort you out. :) 

good luck,
play0r

p.s.
if you're up for a quick read & want to gain a little tidbit of knowledge, read through the following link: [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
knowledge is the path to enlightenment.

---

### Post by dcstar on 2006-03-30
[QUOTE=aresgoddess]Ok, so, I installed Breezy on Sunday night, i think. Might have been Monday night. since then, my comp has shut down and displayed the error #M1004 when I start it back up. This error refers to a too high temperature in the computer. (Dell Inspiron 5150, btw.) I wrote an email to Dell and got an automated response that said I need to update BIOS, but when I try to download the update, no matter what OS i say that I use, I get a link to download an .exe file and if i remember correctly, .exe files can't be used in any linux system, right? 

So what do i do? Is it possible to use the .exe file or should i look for something else?

What is BIOS anyways? It affects the motherboard, right? Is that the same as the processor? 

I read somewhere, i don't know where, that it might be possible to change an .exe to an .iso and burn the image onto a cd-rw and install it that way. is that true? if it is, how can i do that?[/QUOTE]
You basically need a DOS boot disk (Floppy or CD) and then copy the .exe file to it - you should be able to download a boot image somewhere off the 'net to use for this purpose.

BIOS (**B**asic **I**nput **O**utput **S**ystem) is the portion of software the converts generic interface commands to the specific requirements of your motherboard hardware.

For instance, an OS (Windows, Linux whatever) will send a hardware independent command to the BIOS to do something specific on you disk, the BIOS will make sure that the command is sent to your specific hardware in a way that performs the operation correctly.

Because hardware changes constantly, the BIOS essentially hides the need to accommodate these changes from the OS and gives the OS a consistent interface to these resources.

Sometimes motherboard manufacturers find errors in their BIOS, or find better ways to achieve the same things that work already, or add in support for new features etc., that is why BIOS updates are made available.

Most BIOS functions date back to the original IBM PC, as you can imagine PC hardware has changed a lot since then, but an OS from that time will probably still work on state of the art hardware because the BIOS functions have remained consistent.

---

### Post by aresgoddess on 2006-03-30
Thanks for your help. ^_^ that page is a bit confusing though. i mean, where do i type in 

biosdisk install [-o option] [--name=] /path/to/{.exe | .img}
or 
biosdisk mkfloppy [-o option] [-d device] [-k baseimage] /path/to/.exe 

and do i need to put the .exe file name in the command? those are commands, right? =( what about the option, name or device or base image? ack. i'm making myself go crazy... x.X it doesn't really say what to do with those lines or what i'm supposed to do once i've clicked on the RPM, SRPM, and tarball link. 
***********************
Side Note:
oh, also, that email i sent and got the automated response to...i replied in order to talk to an actual human being, saying that I didn't know what to do and basically asking for assistance. This is what I got in return:

> I understand that you would like to install the BIOS file in a 
non-Windows operating system. Ms. Gomez I reviewed your system details for the 
Service Tag number: *******.

We being technicians with the Hardware Warranty Support do not have 
enough expertise in troubleshooting software (including 3rd party 
software) to its core. Hence, I request you to make use of our Dell On Call 
service. The technicians providing assistance at Dell On Call are experts 
in software issues, and would be in a better position to guide you 
further from here.

Dell&#8217;s Standard Support Services include technical support to ensure 
the functionality of your Dell hardware. This does not include software 
usage, "how-to" support or support on non-Dell hardware. 

In order to assist you in a resolution, I can refer you to the Dell On 
Call. Dell On Call is a fee-based service that provides assistance in 
software usage and can answer questions about non-Dell branded hardware. 
Dell On Call can be reached by calling 866-497-2661. This service is 
available 7 days a week, 24 hours a day, and 365 days a year. Dell On 
Call offers several plans, and I am sure that one of them will meet your 
technology needs.

You may alternatively refer to some other resources that are typically 
available at no charge. These may include:

The Dell Support One Stop Troubleshooting Tool:
 
[http://support.dell.com/support/topics/global.aspx/support/dsn/en/entry?c=us&cs=19&l=en&s=dhs](http://support.dell.com/support/topics/global.aspx/support/dsn/en/entry?c=us&cs=19&l=en&s=dhs)

The Dell Support web site [http://support.dell.com](http://support.dell.com)
The Dell Community Forum [http://forums.us.dell.com/](http://forums.us.dell.com/)
The Microsoft Support web site [http://support.microsoft.com/](http://support.microsoft.com/)

If you need assistance with troubleshooting your Dell hardware, please 
reply to this e-mail, and I will be happy to provide assistance.


*sighs* ah, i remember when I was able to get software help from Dell...I don't know if it was paid for or not, (my dad bought me the comp and therefore handled the bill for it), but i always believed it was part of my warranty. My dad being the cheap bastard that he is, probably wouldn't have sprung for the extra service.

---

### Post by BLTicklemonster on 2007-12-06
Yikes, I'm having the same problem with my C510. Any way to just put this on a bootable disk? I like the way I'm told I can make my computer boot to the file from grub, but the instructions are mind boggling. Anybody ever done this who can help here?


[http://linux.dell.com/projects.shtml#biosdisk](http://linux.dell.com/projects.shtml#biosdisk)

---

