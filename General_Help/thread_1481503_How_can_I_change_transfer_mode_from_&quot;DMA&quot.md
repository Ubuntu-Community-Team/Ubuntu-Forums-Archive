---
title: "How can I change transfer mode from &quot;DMA&quot; to &quot;PIO only&quot; ?"
date: 2010-05-12
forum: General Help
---

### Post by solorize on 2010-05-12
Hi,

Does anyone know if there is a way to change “DMA transfer mode” to “**PIO only**” under Xubuntu?

I was getting a problem when running Win OS ( with the same hard drive that I now have Xubuntu on),
which would not load and after reading up I found out that I had to rectify the problem by doing the following
(which corrected the loading problem under Win OS):

1.
Right-click My Computer, and then click Manage. 

2.
Double-click System Tools in the right pane, and then double-click Device Manager. 

3.
Double-click IDE ATA/ATAPI Controller in the right pane, and then double-click the appropriate controller. 

4.
On the Advanced Settings tab, click PIO Only in the Transfer Mode box. 


This was due to the fact that I was using DMA transfer mode with an ATA66 hard disk and the ATA66 DMA transfer mode
is not supported for the onboard IDE controller.

*Full article can be read here:*
[http://support.microsoft.com/kb/262448/en-us]("http://support.microsoft.com/kb/262448/en-us")



I have had a look at the HDPARM command and have run the following:
“**Hdparm –i /dev/dsa**”
and can see the following:

Model=WDC, FwRev=11.07D11, SerialNo=WD-WXE506002619 
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq } 
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50 
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=16 
 CurCHS=17475/15/63, CurSects=16513875, LBA=yes, LBAsects=156301488 
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120} 
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 ***udma5** 
 AdvancedPM=yes: unknown setting WriteCache=enabled 
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

Which I think is showing me that I am currently using UDMA5 transfer mode?


But now I am struggling to find how to change to “PIO only” transfer mode (under Xubuntu), as I am experiencing a
similar problem when booting and think this may also be down the using DMA transfer mode not being “PIO Only”

Any help would be greatly appriciated.

Thanks in advance,

Mark

---

### Post by solorize on 2010-05-13
I have had a look at the following site for 
the HDPARM command.

[http://manpages.ubuntu.com/manpages/jaunty/man8/hdparm.8.html]("http://manpages.ubuntu.com/manpages/jaunty/man8/hdparm.8.html")

But am unsure which flags etc. to use to get it into
PIO only transfer mode.

Does anyone know which flags I should use?

Mark

---

### Post by dandnsmith on 2010-05-13
>        -d     Disable/enable the "using_dma" flag for this drive.  This option now works with most combinations of drives  and  PCI  interfaces which  support DMA and which are known to the kernel IDE driver. It is also a good idea to  use  the  appropriate  -X  option  in combination  with  -d1  to  ensure  that  the  drive  itself  is programmed for the correct DMA mode, although most BIOSs  should do this for you at boot time.  Using DMA nearly always gives the best performance, with fast I/O throughput and  low  CPU  usage. But  there  are  at  least  a few configurations of chipsets and drives for which DMA does not make much of a difference, or  may even  slow  things  down  (on really messed up hardware!).  Your mileage may vary.


Looks like the **-d** is the one - I quoted the relevant bit from your page link.

---

### Post by solorize on 2010-05-13
Hi dandnsmith,

Thanks for the help.

Will I need to edit the **hdparm.conf **file
with the command + flags, or can I just type
it into Terminal and execute it from there?

If I execute from Terminal will it only use
the settings I select until I reboot and then
it will revert back to its original state?
Therefore being better to edit the .conf file?


I am thinking of using the following command:

*[COLOR="Red"]hdparm -d0 -X12 /dev/sda[/COLOR]*
( to disable "DMA" and enable "pio4" )
(( or should I be using "-d1" instead of "-d0" as I am not 100% sure
if I should keep it Enabled "-d1" and just change -X12 to enable "pio4" ))

Also, is it best for me to enable pio4 rather than 
pio1, pio2 or pio3?

Sorry for all the questions, I just dont want to mess
it up ;)

Mark

---

### Post by dandnsmith on 2010-05-14
Hi again,
after further reading the page and your queries, I think that you want:
-d0 to switch off dma
-X13 to use PIO mode 4 (as that is the fastest available)

I do doubt that the latter is needed - I'd expect the interface to use the highest available speed.

I would also use the terminal input method rather than editing hdparm.conf, but I could be wrong on this.

I don't think you'll do any damage by trying it - but, of course, it's your data which is at risk.

HTH

---

### Post by cascade9 on 2010-05-14
> **solorize said:**
> Does anyone know if there is a way to change “DMA transfer mode” to “**PIO only**” under Xubuntu?

This was due to the fact that I was using DMA transfer mode with an ATA66 hard disk and the ATA66 DMA transfer mode
is not supported for the onboard IDE controller.


Odd....I've used ATA66/100 HDDs on ATA33 controllers and never got the problem. I would guess it would have to be a controller/Win2000 issue, and assuming that linux has problems with the same flaw, it could be causing some problems. I wopuld guess that linux doesnt have the same issue- the kernels used now are a lot newer than WinXP, and according to that microsoft link, its a Win2000 problem.

Before I started looking for a software (OS) solution, I'd try the BIOS. You might be able to drop the controller to ATA33, and then your shouldnt have any problems. (this is just a guess, as I've never had this issue)

> **solorize said:**
> 
I have had a look at the HDPARM command and have run the following:
“**Hdparm –i /dev/dsa**”
and can see the following:

Model=WDC, FwRev=11.07D11, SerialNo=WD-WXE506002619 
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq } 
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50 
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=16 
 CurCHS=17475/15/63, CurSects=16513875, LBA=yes, LBAsects=156301488 
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120} 
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 ***udma5** 
 AdvancedPM=yes: unknown setting WriteCache=enabled 
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

Which I think is showing me that I am currently using UDMA5 transfer mode?


But now I am struggling to find how to change to “PIO only” transfer mode (under Xubuntu), as I am experiencing a
similar problem when booting and think this may also be down the using DMA transfer mode not being “PIO Only”


Yes, that is in UDMA5 (ATA100) mode. 

I'd hate to use PIO4 (or any other PIO level) these days...its really slow, very old,a nd has none of the improvments of the later standards. 

Sorry if this hasnt really been that helpful ;)

---

### Post by solorize on 2010-05-14
Thanks for both of your replies.


Dandnsmith /

I have just re-read the setting on the HDRPARM page and I
think I will need to use –X12 to use PIO mode 4, as it 
said that you need to add 8 to the mode number which was
PIO4 therefore it would be 8 + 4 = 12.

Cascade /

I had the problem with Windows XP on my HP NC6000 laptop, I looked in the “event viewer” and 
it was giving me the error codes displayed on the above mentioned website. So I did the fix
it stated and all the errors in the “event viewer” went and my laptop worked fine with no hanging.

Therefore I thought that It could be a similar problem, now I have Xubuntu running on this Laptop now.

I will have a look in the BIOS, but last time I looked I don’t think there was an option to change
the controller to ATA33.

I am not too fussed if PIO is slower, as I would rather have a slower machine that boots up 100%
every time and not hangs. Plus I don’t want to go back to Win OS if I can avoid it ;-)

---

### Post by dandnsmith on 2010-05-14
You're right about it being -X12 (I'm really not with it, I conclude)

Good luck with setting PIO mode. My only similar experience was with a CD drive which suddenly turned up as only able to use PIO modes - I couldn't enable it (under Windows) for DMA, and some writing software was erroring. The experience was being mirrored under linux. I replaced the drive in the end, and then tracked the problem as being really a cable problem - fixable by replacing the cable.

---

