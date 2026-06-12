---
title: "possibly not the silliest question ever posted"
date: 2011-06-14
forum: General Help
---

### Post by westie457 on 2011-06-14
Hello to all

            Not sure if this is the right place to post this question.

Is it possible or wise to use a program like 'testdisk' running on an Ubuntu 32-bit system to rewrite the MBR of a Windows 64-bit system hard drive?

I am only asking because I am cleaning someone's HDD  after they got infected with a Trojan called "Dos/Alureon.A. 

They were worried that they might have to do a re-partition and clean install.

All advice will looked at.

Thanks in advance for your time

---

### Post by blueridgedog on 2011-06-14
I do not know of any reason that the 32 vs 64 issue of the OS would change the way a MBR is written.  Others may chime in.

---

### Post by westie457 on 2011-06-14
> **blueridgedog said:**
> I do not know of any reason that the 32 vs 64 issue of the OS would change the way a MBR is written.  Others may chime in.

Thanks for the quick response

I think I will wait for some more answers mainly because even if it is successful there is no way for me to check that it has worked. My dual-boot box is 32-bit and won't look at anything that is 64-bit.

---

### Post by Habitual on 2011-06-14
[Alureon Recovery]("http://www.microsoft.com/security/portal/Threat/Encyclopedia/Entry.aspx?Name=Trojan:DOS/Alureon.A#recovery_link")
says:

"This virus may cause damage to the Master Boot Record (MBR) and Boot Configuration Data (BCD). You will need to run the following commands using the "bootrec.exe" tool to ensure a complete repair of your computer:
 
bootrec /fixmbr
bootrec /fixboot
bootrec /rebuildbcd"

using a linux diagnostic disk on a MS-enabled system would have 'unknown' results.

Specific recovery options are at [http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

I'd stick to those.

Good Luck.

---

### Post by westie457 on 2011-06-16
Marked as solved even though this was a question for some advice. It has been answered.

Thanks guys.

---

