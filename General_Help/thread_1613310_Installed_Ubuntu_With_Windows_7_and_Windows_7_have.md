---
title: "Installed Ubuntu With Windows 7 and Windows 7 have errors"
date: 2010-11-04
forum: General Help
---

### Post by udinnet on 2010-11-04
[B]Hi All,
I installed ubuntu 10.10 32bit on my HPDV6 laptop and I selected "[COLOR=Red]Install alongside other operating systems[/COLOR]" setting and Installation went fine. But after restart I got GRUB panel and selected [COLOR=Red]Windows 7(loader) dev/sda1[/COLOR] for boot. It comes with the widows 7 log on screen and after few seconds the scandisk and it says my c: (windows) drive need to be "[COLOR=Red]scan for consistency[/COLOR]". But scan is also not running and it [COLOR=Red]termi[/COLOR][/B][B][COLOR=Red]nates[/COLOR]. But after that [COLOR=Red]Windows 7 loading fine[/COLOR]. Every time I select windows 7 and this error is being occurred.

What should I do now for get rid of that scandisk problem? Is the problem with GRUB? please can anyone help.
Ps:- Ubuntu is running fine.

Thanks.[/B] 

OS Windows7 64bit
RAM 4GB DDR3
HDD 640Gb WD

---

### Post by oldfred on 2010-11-04
All grub does is pass the boot to windows. Once passed it is not a grub problem but a windows problem. You seem to have some issue running chkdsk. Did you resize the win7 partition to make it smaller with the windows MMC. It is better to use windows tools on windows and linux tools on linux. But sometimes you have to repair windows from linux.:)

I would first try running chkdsk from a windows CD.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Run chkdsk several times, until no more errors are detected.
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by udinnet on 2010-11-05
Thanks for the reply. I just solved it by my own.

Yes I re-sized the Windows partition which is sda1 and I understood it is a problem with windows start-up with bootmgr. So just you want to do is make a recovery disk (x64 or x86 according to your windows 7) and boot it @ system startup. Then select Stratup repair and it will do the trick.

Downland the recovery cd image files from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") and burn it to a cd.

This question is solved and please mark it a solved.

Thanks
:guitar:

---

### Post by Mark Phelps on 2010-11-05
> **udinnet said:**
> ..Downland the recovery cd image files from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") and burn it to a cd.

Actually, you don't have to go there to make a recovery disk.  Unlike with Vista, Win7 comes with its own recovery-disk-maker builtin.  Just invoke the Backup feature and select the option to create and burn a repair CD.  IF more folks would do that first off, they would have easier times recovery from these dual-boot problems.

---

