---
title: "Ubuntu 10.04 freeze and lost connection with HDD"
date: 2010-11-26
forum: General Help
---

### Post by sham08 on 2010-11-26
Hello. So,I've been following several thread in this forum, related to PC froze and hung randomly issues. And unfortunately still without any solutions till this very moment. Log file viewer also can't provide much help. I'm also affected by this issue that has been gone on my PC for almost 2 months, now. I've been forced to re-install Ubuntu ( from 9.04 to 10.04 ) countless time. As other users mentioned in their thread, the problems occurred randomly. Sometimes right after start-up, sometimes after 10 min to an hour of PC usage and sometimes no freeze at all. But the symptoms seems similar though on different component of hardwares. Me, myself, my PC always started to display freezing symptoms after 2-3 days of any Ubuntu fresh installations. The only way to re-boot are through RSEIUB/O ( and luckily I've never failed to do so ). Its just maybe took countless time of Ctrl + Alt + Del, before I could enter Grub menu and after that Ubuntu. Seems like that BIOS doesn't recognize HDD ( where the Ubuntu situated ), but oddly it ( BIOS ) only rcognize the CD/DVD drive . Lately, to overcome this HDD problem, I tried to pull out the SATA cable connected to CD/DVD drive and left only the SATA cable to HDD. And guess what, I've never encounter this unrecognized HDD problem for the past 2 days. I suspected the cause off all this issues are maybe the AsRock G31M-VS2 mobo that I've just installed about 2 month ago. But certainly, this issue never back me off my love to Ubuntu. As long its Open Sources, I'm sure this problem will be solve.

---

### Post by sikander3786 on 2010-11-26
It would help the reader if you post properly in paragraphs please ;-)

Which graphics card is there? And which version of proprietary drivers (if any)?

Is compiz enabled?

And regarding the HDD problem, I can't understand what the problem is actually. Are you able to boot Ubuntu now?

---

### Post by tajiknomi on 2010-11-26
[SIZE=2][I]I didn't get your words properly,specially about the **HDD**............can you **explain** a little more........
[/I]


[/SIZE]

---

### Post by sham08 on 2010-11-27
Thanks for the replies and sorry for not explaining it properly. To tell the truth, after reading all the related thread of this freeze and hung problems I'm also in great confusions. Whether which of the threads and situations that similar to mine. Because seems to me, my PC had all the symptoms, that any other users mentioned about this issue. 
I use Nvidia GeForce 8400GS graphic card on my PC, and no proprietary driver and compiz enabled. As in the past, if I used the proprietary driver and enabled compiz, my PC will not survive even one day without froze. The problem is, every time if the PC froze, and after the RSEIUB restarted, I always had this 'Primary Master Hard Disk Error'. The BIOS won't recognized the HDD, but only recognized the CD/DVD drive. Ironically, both ( the HDD and CD/DVD drive )and the AsRock G31M-VS2 mobo were newly installed. So, to restart Ubuntu 10.04 normally, I had to pull out the CD/DVD drive SATA cable, so that BIOS forcefully recognized only HDD. It seems to me the Mobo is in the state of confusion. Hope this explain my situation and I'm ready to provide more information if not sufficient. Anyway, thanks again for the responses.

---

### Post by sikander3786 on 2010-11-27
Reading all that, I guess it is a hardware specific problem. First of all I would try to replace the HDD and CD/DVD Drive sata cables and also their ports.

---

### Post by sham08 on 2010-11-27
Thanks sikander 3786 for still being with me in this problem. I've tried replaced SATA cables on both drive recently, and I couldn't even entered the BIOS set-up pages. By mentioning 'port', what do you referring to? Really, I'm still new in PC world, but using Ubuntu had developed my knowledge a step further.
I also think, I should explain that 2 month earlier, my PC had undergone quite a big transformation. It started from a malfunctioned Power Supply Unit, and I had to change almost every hardwares. From the Power Supply Unit it selves, Graphic Card ( Nvidia GEForce 8400GS ), HDD ( Samsung 500GB ), CD/DVD drive ( Samsung ) and the AsRock G31M-VS2 motherboard. Oddly, in my old PC, I've never experienced this issue. In fact, I've even managed installed Ubuntu 10.04 without any single problems.
So, right in this moment, maybe I should satisfy myself with only the HDD functioning and the CPU cover detach ( for simplicity ). Because, every time if I re-connect the CD/DVD drive, then in 5 minutes or less I must restart the PC again and again. Thanks anyway, hope I'll see the light again and this issue will be solved.

---

### Post by tajiknomi on 2010-11-27
@ Sham08
> **sikander3786 said:**
> It would help the reader if you post properly in paragraphs please ;-)


[SIZE=2]<Not belongs to thread>i think you should think about the Sikandar's Post above> this will help the readers to understand your problem thoroughly, hope you understand Bro[/SIZE] :p <Close>

---

### Post by sikander3786 on 2010-11-27
> **sham08 said:**
> Thanks sikander 3786 for still being with me in this problem. I've tried replaced SATA cables on both drive recently, and I couldn't even entered the BIOS set-up pages. By mentioning 'port', what do you referring to? Really, I'm still new in PC world, but using Ubuntu had developed my knowledge a step further.
I also think, I should explain that 2 month earlier, my PC had undergone quite a big transformation. It started from a malfunctioned Power Supply Unit, and I had to change almost every hardwares. From the Power Supply Unit it selves, Graphic Card ( Nvidia GEForce 8400GS ), HDD ( Samsung 500GB ), CD/DVD drive ( Samsung ) and the AsRock G31M-VS2 motherboard. Oddly, in my old PC, I've never experienced this issue. In fact, I've even managed installed Ubuntu 10.04 without any single problems.
So, right in this moment, maybe I should satisfy myself with only the HDD functioning and the CPU cover detach ( for simplicity ). Because, every time if I re-connect the CD/DVD drive, then in 5 minutes or less I must restart the PC again and again. Thanks anyway, hope I'll see the light again and this issue will be solved.
Paragraphs buddy please paragraphs :-)

"Ports" mean the sata ports on your motherboard to which you connect the HDD and CD/DVD Drive cables. If more than two, you can change the ports for both the drives.

And if changing the cables and even ports doesn't sort out the problem, then it is definitely a motherboard problem.

I would first try to add a PCI Sata Card and see if that sorts out the problem.

If doesn't, replacing the board... Might be get it checked by a hardware professional or claim Warranty (if applicable).

Good Luck!

---

### Post by sham08 on 2010-12-03
[SIZE="2"]Hello. Sorry for this late reply. I've did as your recommended solution ( changed the SATA port ), and guess what? It worked perfectly. 
And what make me glad is I've surpassed 3 days without any froze or hung-up. I can't express how thankful I am to you sikander3786, as the problem that haunted me for the last 2 month had been solved, and hope it will be the last. Again, thanks a lot.[/SIZE]

---

### Post by sikander3786 on 2010-12-03
> **sham08 said:**
> [SIZE="2"]Hello. Sorry for this late reply. I've did as your recommended solution ( changed the SATA port ), and guess what? It worked perfectly. 
And what make me glad is I've surpassed 3 days without any froze or hung-up. I can't express how thankful I am to you sikander3786, as the problem that haunted me for the last 2 month had been solved, and hope it will be the last. Again, thanks a lot.[/SIZE]
You are most Welcome :-)

Glad to know it is sorted now.

You can mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

