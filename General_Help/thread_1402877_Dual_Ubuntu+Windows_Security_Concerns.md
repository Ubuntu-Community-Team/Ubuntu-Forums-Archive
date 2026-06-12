---
title: "Dual Ubuntu+Windows: Security Concerns"
date: 2010-02-09
forum: General Help
---

### Post by jackthechemist on 2010-02-09
Greetings all,

Normally I would do some more research and figure this out on my own, but I'm in a hurry and haven't found my answer, so I'm throwing this out into the aether hoping someone will know...

I finally decided to get rid of Windows and install Ubuntu blah blah I'm sure everyone's heard this before :P but I'll be partitioning my drive and putting on after linux for programs WINE can't run. (XP, Vista or 7, not sure yet) I am wondering...

1) If I boot OS#1, can the inherent flaws of OS#2 (on a separate partition) be exploited?

2) If I boot OS#1, is it susceptible to any spyware/malware/viruses/Trojans that might have infected OS#2? (I know this question is a bit general)

3) Would it be wiser to buy a separate HD and put Windows on that? Consider questions 1) and 2) with regard to separate HDs.

4) Can anyone think of something I haven't yet considered?

Thank you all in advance for your input. Forgive me if the answers are obvious, normally I would do more research but am in a hurry.

Jackthechemist

---

### Post by zvacet on 2010-02-10
I think you are safe. I don't think any maleware will go to the your windows partition during Ubuntu running.I can be wrong and if I'm let somebody correct me.Read [this.]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by OrangeCrate on 2010-02-10
The Truth About Linux and Viruses

> Conventional wisdom says that a virus scanner is one of three protections necessary these days for computers connected to the Internet. (The other two being a spyware scanner or two, and a trainable spam filter.) The same wisdom also says that the only reason Linux and Macintosh computers don't see the same level of virus attacks as Windows PCs is because Windows PCs are so much more prevalent.

While this may be partly true, it's not the whole reason. According to various virus lists, there are less than 100 known viruses for Linux, none of which spread the way a Windows virus does. Meanwhile, there are thousands and thousands of Windows viruses. With the so-called discovery of a Linux/Windows virus, more light is being shined on the subject of Linux security.

<snip>

1. If you run Linux and only Linux, you do not need antivirus software. In its efforts to make Windows easier to use, Microsoft simplified the process of running executables under its operating system many years ago. Not only can a user launch a program by clicking an e-mail attachment, but it's possible for an executable to launch automatically just by hitting the preview pane of some email packages, including older versions of Outlook and Outlook Express. Scot's Newsletter Forums member Nathan Williams has provided an excellent FAQ for the All Things Linux forum explaining why Linux when used alone does not need antivirus protection.

Under Linux the steps for launching an executable from an e-mail are separate, discrete steps. A user would have to read the email, save the attachment, give the attachment executable permissions, and then run the executable. And to be truly damaging, the latter two would have to be done as root — not something informed users would allow. (For more information see Ch- Ch- Changing File Permissions.)

2. If you dual boot Linux and Windows and get a virus-infected mail in Linux, it can NOT jump to your Windows partition. Nor can it spread over the local network to other systems. You can even store the attachment in your /home directory and open the zip or click the file, and it will be dead in the water. Windows executables won't run under Linux. Linux files need to be granted permission to become executable. And even then, it can't spread beyond the home folder. (This is also why Linux AV programs do not have a "live guard" module in them — the virus does not execute or move.) You could even leave a virus executable there as long as you wanted to without risk. Windows will not get infected, unless you deliberately copy the virus to your Windows partition.

3. If you dual boot, however, you better get a good antivirus program for Windows. Microsoft's operating system and its bundled applications, Outlook and Internet Explorer, offer users powerful functionality in their attempts to be easy to use and easy to update. As a result, it's all too easy for virus writers to exploit the same functionality in a malicious way. Don't leave them an opening. Install an antivirus program and keep it updated.

4. The only time you'll need a Linux antivirus program is if you're running a mail server. And that's just good social behavior. It's not to protect your Linux server or client computer so much as to make sure you don't pass a virus on to a Windows system.

Think about it this way: If you have two warehouses, and you use the first one to store cheese, are you going to place mouse-traps in the second one where you only store stainless steel? I mean, be reasonable, mice do not eat stainless steel! So don't let antivirus vendors make you unnecessarily paranoid.


[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

### Post by 3rdalbum on 2010-02-10
I'm not being rude, but:

No, no, no! ;-)

1. An exploit exists in code that is running on your computer. If you boot OS #1, it is the only operating system running. OS #2 is not running on your computer, and none of its code can run without you rebooting (at which point, OS #1 is no longer running).

2. If you're talking about Windows and Linux, there is no malware that can run on both platforms. It's theoretically possible, but it certainly hasn't been created yet.

3. A partition is, according to the computer, a seperate hard disk anyway. With respect to #2, it's not necessary to put a different operating system onto a different physical disk for these sorts of security reasons. And in fact, it just makes the installation process more complex, because you have to make sure that the Ubuntu bootloader (GRUB) gets installed to the internal disk, not the external.

4. Monkeys have 99% the same DNA as humans, but are not genetically compatible with us. But seriously, just remember that if you download a file on Linux that has Windows malware in it, and then transfer it to Windows, the malware will still be intact. And also remember that there are no Linux viruses, and no malware if you are careful with what ports you open to the world.

---

### Post by Nunu on 2010-02-10
Never had a problem with this type of setup.

---

