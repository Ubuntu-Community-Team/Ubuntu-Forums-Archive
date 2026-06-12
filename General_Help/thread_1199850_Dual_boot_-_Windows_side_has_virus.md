---
title: "Dual boot - Windows side has virus"
date: 2009-06-29
forum: General Help
---

### Post by CheesyD on 2009-06-29
Not sure if this is the right place for this but here goes...

I have an Acer Travelmate 8100 laptop that is currently set up to dual boot between Windows XP Sp3 and Ubuntu Jaunty. I primarily use the Ubuntu side but keep the Windows side for my Zune and for my camera interface. 

I recently (somehow) got a trojan on the Windows side that I can't get rid of. McAfee won't clean it, and the trojan is somehow preventing me from even running Spybot or Malware or AVG anti-virus. McAfee identifies the trojan but when I tell it to clean the file, I get the blue screen of death.

So, I want to reformat the Windows side without affecting my Ubuntu side. My question to all of you experts out there is... how do I go about doing that without hurting Ubuntu? I get around pretty well in Windows but am pretty inexperienced with Linux. So please, be specific and gentle. Thanks!

---

### Post by kuja on 2009-06-29
Well, there are probably 3 good options here. 
a) Scan with an antivirus boot disk.
b) Identify the infected files and either quarantine or remove from within Linux
c) Reinstall Windows, after which you will have to reinstall the grub boot loader to the MBA.

---

### Post by jimv on 2009-06-29
Before you reinstall Windows, try booting into safe-mode (press F8 during bootup) and running a scan from your antivirus.  Often this helps.

You can also install Avast, ClamAV, etc in Ubuntu and scan your Windows partition from there.

---

### Post by hibliss on 2009-06-29
> **jimv said:**
> Before you reinstall Windows, try booting into safe-mode (press F8 during bootup) and running a scan from your antivirus.  Often this helps.


Do this. Try Malwarebytes. You may need to rename the executable before you attempt to install Malwarebytes because many viruses block the installation based on the name of the install package.

For free, it is hands down the best option.

---

### Post by mhgsys on 2009-06-29
You could also download a virusscanner on linux, such as clamav or avg free, and scan your windows disk.
\
edit: Jimv, just noticed you also said that, I agree.

---

### Post by philcamlin on 2009-06-29
> **mhgsys said:**
> You could also download a virusscanner on linux, such as clamav or avg free, and scan your windows disk.
\
edit: Jimv, just noticed you also said that, I agree.


that works ive used it to save my windows :):popcorn:

^^ with that too the virus wont spread

---

### Post by CheesyD on 2009-06-29
I just ended up doing a fresh install of Ubuntu and getting rid of Windows altogether. I can run my Zune off of my wife's PC.

Good riddance Windows!!

---

