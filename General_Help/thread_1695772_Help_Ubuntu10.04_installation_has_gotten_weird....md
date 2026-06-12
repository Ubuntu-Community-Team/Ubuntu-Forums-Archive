---
title: "Help? Ubuntu10.04 installation has gotten weird..."
date: 2011-02-26
forum: General Help
---

### Post by tyler9 on 2011-02-26
My Ubuntu10.04 installation worked great until recently.

But now, this stuff happens:

--On the GNU GRUB ver 1.98-1ubuntu7 list, about half the time I can't move the highlight--no response to keyboard arrow keys, and no response to Enter key--have to wait 60-seconds for highlighted item to start.
--login box's appearance is different, like a different visual scheme/theme
--after login, the screen remains black for a long time before the desktop appears
--when desktop appears, the desktop program icons are gone
--when I launch an app, like the terminal window, it takes a long time for it to open, and after opening, it takes a long time for the prompt tyler9@tyler9-desktop to appear
--Nautilus file browser won't open. When I launch it, I get a button on panel on bottom of screen [like Windows Taskbar] that says "Starting File Browser" but the button disappears, and Nautilus doesn't open. If I enter "nautilus" in terminal window, I get "Bus error."
--Firefox is very slow; typically a delay when I click a tab, and very often, it "darkens"--takes on a darker color and won't respond to clicks. This "darkening" thing happens in other pgms and docs too
--often a long delay when I click anything--panel menu, in a doc, etc

Any ideas for troubleshooting, what the cause(s) might be? My subjective sense is that there's some process(es) running that is causing all this junk. Is there a way to "roll back" to when everything worked OK? Is there an error log or something that might specify why this is happening?

[Note: It's not a HW issue--machine is dual-boot Ubuntu/Mint9, and Mint9 works fine--none of the above problems.]

Sorry but my skill level is low--can follow directions though! Appreciate the hand-holding--Thx!

---

### Post by runeh76 on 2011-02-26
Hi

What have u done before that problem came up?
It sounds like ur graphic card could be broken or wrong driver.
Have u tryed install other desktop KDE/GNOME or similar?

---

### Post by knitmom on 2011-02-26
me too!!!!

The only thing I did before this other than the updates, was to get my ipod working with rhythmnbox and gtkpod ipod manager.

When I go to the system manager, evinced and nautilus were using most of the cpu resources.

---

### Post by tyler9 on 2011-02-26
> **runeh76 said:**
> 
What have u done before that problem came up?
It sounds like ur graphic card could be broken or wrong driver.
Have u tryed install other desktop KDE/GNOME or similar?

That's what puzzles me--I've downloaded only the usual updates, and my installation is as simple as possible. I'm a basic home user, with minimal needs [so far]--email, web, office productivity apps; don't listen to audio nor watch video, no ipod, etc. Mainly, I write 6-8 hrs/day.

I have onboard graphics [gigabyte motherboard], and as I mentioned, Mint9 works great on this machine. So somehow my Ubuntu install got weird.

knitmom: Hope you can benefit from this thread too!

---

### Post by runeh76 on 2011-02-26
Lets try kernel output

```
dmesg
```

---

### Post by knitmom on 2011-02-26
I hope so too!

Do you use dropbox?  When I was looking through my downloads, I noticed the dropbox app said nautilus-dropbox.  

When ever I try to save something, ie. a .pdf, it locks up.  If I try to go to any of my folders, it locks up.

Everything you described in your initial post happens to me too.

---

### Post by runeh76 on 2011-02-26
> **knitmom said:**
> I hope so too!

Do you use dropbox?  When I was looking through my downloads, I noticed the dropbox app said nautilus-dropbox.  

When ever I try to save something, ie. a .pdf, it locks up.  If I try to go to any of my folders, it locks up.

Everything you described in your initial post happens to me too.

I think its lock up, becouse dropbox is online backup program and its sync what ever u do with ur files...i recommended-->dont use it! There is REALLY good backup programs what u can use  ;)

---

### Post by tyler9 on 2011-02-26
> **runeh76 said:**
> Lets try kernel output
```
dmesg
```

Here ya go:
[  204.573930] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  204.573933]          res 41/40:00:c4:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  204.573941] ata4.00: status: { DRDY ERR }
[  204.573946] ata4.00: error: { UNC }
[  204.576611] ata4.00: configured for UDMA/133
[  204.576638] ata4: EH complete
[  206.690754] ata4.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  206.690764] ata4.00: irq_stat 0x40000008
[  206.690772] ata4.00: failed command: READ FPDMA QUEUED
[  206.690788] ata4.00: cmd 60/08:08:c0:b3:04/00:00:00:00:00/40 tag 1 ncq 4096 in
[  206.690791]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  206.690798] ata4.00: status: { DRDY ERR }
[  206.690803] ata4.00: error: { UNC }
[  206.693642] ata4.00: configured for UDMA/133
[  206.693674] ata4: EH complete
[  208.682630] ata4.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  208.682640] ata4.00: irq_stat 0x40000008
[  208.682648] ata4.00: failed command: READ FPDMA QUEUED
[  208.682662] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  208.682665]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  208.682672] ata4.00: status: { DRDY ERR }
[  208.682677] ata4.00: error: { UNC }
[  208.685457] ata4.00: configured for UDMA/133
[  208.685484] sd 3:0:0:0: [sda] Unhandled sense code
[  208.685489] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.685498] sd 3:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  208.685509] Descriptor sense data with sense descriptors (in hex):
[  208.685514]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  208.685534]         00 04 b3 c6 
[  208.685543] sd 3:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  208.685553] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 00 04 b3 c0 00 00 08 00
[  208.685572] end_request: I/O error, dev sda, sector 308166
[  208.685613] ata4: EH complete
[  338.488128] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  338.488138] ata4.00: irq_stat 0x40000008
[  338.488147] ata4.00: failed command: READ FPDMA QUEUED
[  338.488163] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  338.488166]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  338.488174] ata4.00: status: { DRDY ERR }
[  338.488179] ata4.00: error: { UNC }
[  338.490754] ata4.00: configured for UDMA/133
[  338.490777] ata4: EH complete
[  340.921717] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  340.921726] ata4.00: irq_stat 0x40000008
[  340.921735] ata4.00: failed command: READ FPDMA QUEUED
[  340.921749] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  340.921752]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  340.921760] ata4.00: status: { DRDY ERR }
[  340.921765] ata4.00: error: { UNC }
[  340.952095] ata4.00: configured for UDMA/133
[  340.952119] ata4: EH complete
[  343.180393] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  343.180403] ata4.00: irq_stat 0x40000008
[  343.180412] ata4.00: failed command: READ FPDMA QUEUED
[  343.180426] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  343.180430]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  343.180437] ata4.00: status: { DRDY ERR }
[  343.180442] ata4.00: error: { UNC }
[  343.183052] ata4.00: configured for UDMA/133
[  343.183076] ata4: EH complete
[  345.163839] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  345.163848] ata4.00: irq_stat 0x40000008
[  345.163856] ata4.00: failed command: READ FPDMA QUEUED
[  345.163871] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  345.163874]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  345.163881] ata4.00: status: { DRDY ERR }
[  345.163886] ata4.00: error: { UNC }
[  345.166513] ata4.00: configured for UDMA/133
[  345.166537] ata4: EH complete
[  347.272395] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  347.272404] ata4.00: irq_stat 0x40000008
[  347.272412] ata4.00: failed command: READ FPDMA QUEUED
[  347.272426] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  347.272429]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  347.272436] ata4.00: status: { DRDY ERR }
[  347.272441] ata4.00: error: { UNC }
[  347.275011] ata4.00: configured for UDMA/133
[  347.275034] ata4: EH complete
[  349.255944] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  349.255953] ata4.00: irq_stat 0x40000008
[  349.255962] ata4.00: failed command: READ FPDMA QUEUED
[  349.255978] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  349.255981]          res 41/40:00:c4:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  349.255988] ata4.00: status: { DRDY ERR }
[  349.255993] ata4.00: error: { UNC }
[  349.258882] ata4.00: configured for UDMA/133
[  349.258908] sd 3:0:0:0: [sda] Unhandled sense code
[  349.258914] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  349.258923] sd 3:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  349.258934] Descriptor sense data with sense descriptors (in hex):
[  349.258940]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  349.258961]         00 04 b3 c4 
[  349.258969] sd 3:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  349.258980] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 00 04 b3 c0 00 00 08 00
[  349.259000] end_request: I/O error, dev sda, sector 308164
[  349.259040] ata4: EH complete
[  351.239524] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  351.239535] ata4.00: irq_stat 0x40000008
[  351.239544] ata4.00: failed command: READ FPDMA QUEUED
[  351.239560] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  351.239563]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  351.239571] ata4.00: status: { DRDY ERR }
[  351.239576] ata4.00: error: { UNC }
[  351.242237] ata4.00: configured for UDMA/133
[  351.242265] ata4: EH complete
[  353.348054] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  353.348063] ata4.00: irq_stat 0x40000008
[  353.348072] ata4.00: failed command: READ FPDMA QUEUED
[  353.348088] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  353.348091]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  353.348099] ata4.00: status: { DRDY ERR }
[  353.348104] ata4.00: error: { UNC }
[  353.350693] ata4.00: configured for UDMA/133
[  353.350717] ata4: EH complete
[  355.331641] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  355.331650] ata4.00: irq_stat 0x40000008
[  355.331658] ata4.00: failed command: READ FPDMA QUEUED
[  355.331673] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  355.331676]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  355.331683] ata4.00: status: { DRDY ERR }
[  355.331688] ata4.00: error: { UNC }
[  355.334436] ata4.00: configured for UDMA/133
[  355.334461] ata4: EH complete
[  357.315196] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  357.315205] ata4.00: irq_stat 0x40000008
[  357.315213] ata4.00: failed command: READ FPDMA QUEUED
[  357.315227] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  357.315231]          res 41/40:00:c3:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  357.315238] ata4.00: status: { DRDY ERR }
[  357.315243] ata4.00: error: { UNC }
[  357.317837] ata4.00: configured for UDMA/133
[  357.317861] ata4: EH complete
[  359.298743] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  359.298753] ata4.00: irq_stat 0x40000008
[  359.298761] ata4.00: failed command: READ FPDMA QUEUED
[  359.298776] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  359.298779]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  359.298787] ata4.00: status: { DRDY ERR }
[  359.298792] ata4.00: error: { UNC }
[  359.301439] ata4.00: configured for UDMA/133
[  359.301463] ata4: EH complete
[  361.282312] ata4.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  361.282322] ata4.00: irq_stat 0x40000001
[  361.282330] ata4.00: failed command: READ FPDMA QUEUED
[  361.282345] ata4.00: cmd 60/08:00:c0:b3:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  361.282348]          res 41/40:00:c6:b3:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  361.282356] ata4.00: status: { DRDY ERR }
[  361.282361] ata4.00: error: { UNC }
[  361.282367] ata4.00: failed command: READ FPDMA QUEUED
[  361.282380] ata4.00: cmd 60/08:08:f8:49:27/00:00:00:00:00/40 tag 1 ncq 4096 in
[  361.282383]          res 41/40:00:c7:b3:04/00:00:00:00:00/40 Emask 0x9 (media error)
[  361.282390] ata4.00: status: { DRDY ERR }
[  361.282395] ata4.00: error: { UNC }
[  361.285012] ata4.00: configured for UDMA/133
[  361.285038] sd 3:0:0:0: [sda] Unhandled sense code
[  361.285044] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  361.285052] sd 3:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  361.285063] Descriptor sense data with sense descriptors (in hex):
[  361.285068]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  361.285089]         00 04 b3 c6 
[  361.285098] sd 3:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  361.285109] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 00 04 b3 c0 00 00 08 00
[  361.285127] end_request: I/O error, dev sda, sector 308166
[  361.285170] ata4: EH complete
[  372.716794] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  372.716804] ata4.00: irq_stat 0x40000008
[  372.716813] ata4.00: failed command: READ FPDMA QUEUED
[  372.716828] ata4.00: cmd 60/08:00:f0:51:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  372.716832]          res 41/40:00:f0:51:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  372.716839] ata4.00: status: { DRDY ERR }
[  372.716845] ata4.00: error: { UNC }
[  372.719419] ata4.00: configured for UDMA/133
[  372.719443] ata4: EH complete
[  374.708665] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  374.708675] ata4.00: irq_stat 0x40000008
[  374.708683] ata4.00: failed command: READ FPDMA QUEUED
[  374.708697] ata4.00: cmd 60/08:00:f0:51:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  374.708700]          res 41/40:00:f0:51:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  374.708708] ata4.00: status: { DRDY ERR }
[  374.708713] ata4.00: error: { UNC }
[  374.711283] ata4.00: configured for UDMA/133
[  374.711306] ata4: EH complete
[  376.700491] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  376.700500] ata4.00: irq_stat 0x40000008
[  376.700509] ata4.00: failed command: READ FPDMA QUEUED
[  376.700523] ata4.00: cmd 60/08:00:f0:51:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  376.700526]          res 41/40:00:f0:51:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  376.700534] ata4.00: status: { DRDY ERR }
[  376.700539] ata4.00: error: { UNC }
[  376.703143] ata4.00: configured for UDMA/133
[  376.703166] ata4: EH complete
[  378.692435] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  378.692445] ata4.00: irq_stat 0x40000008
[  378.692454] ata4.00: failed command: READ FPDMA QUEUED
[  378.692469] ata4.00: cmd 60/08:00:f0:51:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  378.692473]          res 41/40:00:f0:51:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  378.692480] ata4.00: status: { DRDY ERR }
[  378.692486] ata4.00: error: { UNC }
[  378.695070] ata4.00: configured for UDMA/133
[  378.695094] ata4: EH complete
[  380.684302] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  380.684312] ata4.00: irq_stat 0x40000008
[  380.684321] ata4.00: failed command: READ FPDMA QUEUED
[  380.684336] ata4.00: cmd 60/08:00:f0:51:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  380.684340]          res 41/40:00:f0:51:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  380.684347] ata4.00: status: { DRDY ERR }
[  380.684353] ata4.00: error: { UNC }
[  380.686893] ata4.00: configured for UDMA/133
[  380.686917] ata4: EH complete
[  382.676191] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  382.676200] ata4.00: irq_stat 0x40000008
[  382.676209] ata4.00: failed command: READ FPDMA QUEUED
[  382.676223] ata4.00: cmd 60/08:00:f0:51:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  382.676227]          res 41/40:00:f0:51:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  382.676234] ata4.00: status: { DRDY ERR }
[  382.676239] ata4.00: error: { UNC }
[  382.678826] ata4.00: configured for UDMA/133
[  382.678851] sd 3:0:0:0: [sda] Unhandled sense code
[  382.678856] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  382.678865] sd 3:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  382.678876] Descriptor sense data with sense descriptors (in hex):
[  382.678881]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  382.678902]         00 04 51 f0 
[  382.678911] sd 3:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  382.678921] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 00 04 51 f0 00 00 08 00
[  382.678940] end_request: I/O error, dev sda, sector 283120
[  382.678978] ata4: EH complete
[  385.923481] PPP BSD Compression module registered
[  385.985965] PPP Deflate Compression module registered
[  491.362842] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  491.362852] ata4.00: irq_stat 0x40000008
[  491.362861] ata4.00: failed command: READ FPDMA QUEUED
[  491.362877] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  491.362881]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  491.362888] ata4.00: status: { DRDY ERR }
[  491.362894] ata4.00: error: { UNC }
[  491.365585] ata4.00: configured for UDMA/133
[  491.365613] ata4: EH complete
[  493.354702] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  493.354712] ata4.00: irq_stat 0x40000008
[  493.354721] ata4.00: failed command: READ FPDMA QUEUED
[  493.354736] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  493.354739]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  493.354747] ata4.00: status: { DRDY ERR }
[  493.354752] ata4.00: error: { UNC }
[  493.357371] ata4.00: configured for UDMA/133
[  493.357395] ata4: EH complete
[  495.346643] ata4.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[  495.346653] ata4.00: irq_stat 0x40000001
[  495.346661] ata4.00: failed command: READ FPDMA QUEUED
[  495.346676] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  495.346679]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  495.346687] ata4.00: status: { DRDY ERR }
[  495.346692] ata4.00: error: { UNC }
[  495.346698] ata4.00: failed command: WRITE FPDMA QUEUED
[  495.346712] ata4.00: cmd 61/08:08:98:29:d4/00:00:11:00:00/40 tag 1 ncq 4096 out
[  495.346715]          res 41/40:00:57:12:0d/00:00:00:00:00/40 Emask 0x9 (media error)
[  495.346721] ata4.00: status: { DRDY ERR }
[  495.346726] ata4.00: error: { UNC }
[  495.346732] ata4.00: failed command: WRITE FPDMA QUEUED
[  495.346745] ata4.00: cmd 61/08:10:80:44:d9/00:00:11:00:00/40 tag 2 ncq 4096 out
[  495.346748]          res 41/40:00:57:12:0d/00:00:00:00:00/40 Emask 0x9 (media error)
[  495.346755] ata4.00: status: { DRDY ERR }
[  495.346759] ata4.00: error: { UNC }
[  495.346765] ata4.00: failed command: WRITE FPDMA QUEUED
[  495.346778] ata4.00: cmd 61/08:18:c0:4c:11/00:00:00:00:00/40 tag 3 ncq 4096 out
[  495.346781]          res 41/40:00:57:12:0d/00:00:00:00:00/40 Emask 0x9 (media error)
[  495.346787] ata4.00: status: { DRDY ERR }
[  495.346792] ata4.00: error: { UNC }
[  495.349431] ata4.00: configured for UDMA/133
[  495.349462] ata4: EH complete
[  497.338519] ata4.00: exception Emask 0x0 SAct 0x8 SErr 0x0 action 0x0
[  497.338528] ata4.00: irq_stat 0x40000008
[  497.338537] ata4.00: failed command: READ FPDMA QUEUED
[  497.338551] ata4.00: cmd 60/08:18:50:12:0d/00:00:00:00:00/40 tag 3 ncq 4096 in
[  497.338554]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  497.338561] ata4.00: status: { DRDY ERR }
[  497.338566] ata4.00: error: { UNC }
[  497.341212] ata4.00: configured for UDMA/133
[  497.341236] ata4: EH complete
[  499.330403] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  499.330412] ata4.00: irq_stat 0x40000008
[  499.330420] ata4.00: failed command: READ FPDMA QUEUED
[  499.330434] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  499.330437]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  499.330444] ata4.00: status: { DRDY ERR }
[  499.330449] ata4.00: error: { UNC }
[  499.333130] ata4.00: configured for UDMA/133
[  499.333153] ata4: EH complete
[  501.322284] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  501.322293] ata4.00: irq_stat 0x40000008
[  501.322300] ata4.00: failed command: READ FPDMA QUEUED
[  501.322314] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  501.322317]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  501.322325] ata4.00: status: { DRDY ERR }
[  501.322330] ata4.00: error: { UNC }
[  501.324936] ata4.00: configured for UDMA/133
[  501.324961] sd 3:0:0:0: [sda] Unhandled sense code
[  501.324966] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  501.324974] sd 3:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  501.324985] Descriptor sense data with sense descriptors (in hex):
[  501.324990]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  501.325011]         00 0d 12 51 
[  501.325019] sd 3:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  501.325030] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 00 0d 12 50 00 00 08 00
[  501.325049] end_request: I/O error, dev sda, sector 856657
[  501.325083] ata4: EH complete
[  503.347501] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  503.347511] ata4.00: irq_stat 0x40000008
[  503.347520] ata4.00: failed command: READ FPDMA QUEUED
[  503.347535] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  503.347539]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  503.347546] ata4.00: status: { DRDY ERR }
[  503.347552] ata4.00: error: { UNC }
[  503.350162] ata4.00: configured for UDMA/133
[  503.350186] ata4: EH complete
[  505.339345] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  505.339355] ata4.00: irq_stat 0x40000008
[  505.339364] ata4.00: failed command: READ FPDMA QUEUED
[  505.339379] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  505.339382]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  505.339390] ata4.00: status: { DRDY ERR }
[  505.339395] ata4.00: error: { UNC }
[  505.341803] ata4.00: configured for UDMA/133
[  505.341825] ata4: EH complete
[  507.331211] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  507.331221] ata4.00: irq_stat 0x40000008
[  507.331230] ata4.00: failed command: READ FPDMA QUEUED
[  507.331245] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  507.331248]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  507.331256] ata4.00: status: { DRDY ERR }
[  507.331261] ata4.00: error: { UNC }
[  507.333655] ata4.00: configured for UDMA/133
[  507.333678] ata4: EH complete
[  509.323140] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  509.323150] ata4.00: irq_stat 0x40000008
[  509.323159] ata4.00: failed command: READ FPDMA QUEUED
[  509.323174] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  509.323178]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  509.323185] ata4.00: status: { DRDY ERR }
[  509.323191] ata4.00: error: { UNC }
[  509.325782] ata4.00: configured for UDMA/133
[  509.325806] ata4: EH complete
[  511.315020] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  511.315030] ata4.00: irq_stat 0x40000008
[  511.315039] ata4.00: failed command: READ FPDMA QUEUED
[  511.315054] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  511.315057]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  511.315065] ata4.00: status: { DRDY ERR }
[  511.315070] ata4.00: error: { UNC }
[  511.317767] ata4.00: configured for UDMA/133
[  511.317792] ata4: EH complete
[  513.306901] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  513.306911] ata4.00: irq_stat 0x40000008
[  513.306920] ata4.00: failed command: READ FPDMA QUEUED
[  513.306935] ata4.00: cmd 60/08:00:50:12:0d/00:00:00:00:00/40 tag 0 ncq 4096 in
[  513.306938]          res 41/40:00:51:12:0d/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  513.306946] ata4.00: status: { DRDY ERR }
[  513.306951] ata4.00: error: { UNC }
[  513.309740] ata4.00: configured for UDMA/133
[  513.309766] sd 3:0:0:0: [sda] Unhandled sense code
[  513.309771] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  513.309780] sd 3:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  513.309791] Descriptor sense data with sense descriptors (in hex):
[  513.309796]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  513.309818]         00 0d 12 51 
[  513.309826] sd 3:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  513.309837] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 00 0d 12 50 00 00 08 00
[  513.309856] end_request: I/O error, dev sda, sector 856657
[  513.309894] ata4: EH complete
[  551.727726] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  551.727736] ata4.00: irq_stat 0x40000008
[  551.727745] ata4.00: failed command: READ FPDMA QUEUED
[  551.727761] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  551.727764]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  551.727772] ata4.00: status: { DRDY ERR }
[  551.727777] ata4.00: error: { UNC }
[  551.731377] ata4.00: configured for UDMA/133
[  551.731402] ata4: EH complete
[  553.736223] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  553.736232] ata4.00: irq_stat 0x40000008
[  553.736241] ata4.00: failed command: READ FPDMA QUEUED
[  553.736256] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  553.736259]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  553.736266] ata4.00: status: { DRDY ERR }
[  553.736271] ata4.00: error: { UNC }
[  553.738883] ata4.00: configured for UDMA/133
[  553.738907] ata4: EH complete
[  555.744799] ata4.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[  555.744812] ata4.00: irq_stat 0x40000001
[  555.744821] ata4.00: failed command: READ FPDMA QUEUED
[  555.744835] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  555.744838]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  555.744846] ata4.00: status: { DRDY ERR }
[  555.744851] ata4.00: error: { UNC }
[  555.744857] ata4.00: failed command: WRITE FPDMA QUEUED
[  555.744870] ata4.00: cmd 61/08:08:a0:29:d4/00:00:11:00:00/40 tag 1 ncq 4096 out
[  555.744873]          res 41/40:00:07:18:e4/00:00:11:00:00/40 Emask 0x9 (media error)
[  555.744880] ata4.00: status: { DRDY ERR }
[  555.744885] ata4.00: error: { UNC }
[  555.744891] ata4.00: failed command: WRITE FPDMA QUEUED
[  555.744904] ata4.00: cmd 61/08:10:98:44:d9/00:00:11:00:00/40 tag 2 ncq 4096 out
[  555.744907]          res 41/40:00:07:18:e4/00:00:11:00:00/40 Emask 0x9 (media error)
[  555.744914] ata4.00: status: { DRDY ERR }
[  555.744918] ata4.00: error: { UNC }
[  555.744924] ata4.00: failed command: WRITE FPDMA QUEUED
[  555.744937] ata4.00: cmd 61/08:18:28:4e:11/00:00:00:00:00/40 tag 3 ncq 4096 out
[  555.744940]          res 41/40:00:07:18:e4/00:00:11:00:00/40 Emask 0x9 (media error)
[  555.744946] ata4.00: status: { DRDY ERR }
[  555.744951] ata4.00: error: { UNC }
[  555.747567] ata4.00: configured for UDMA/133
[  555.747598] ata4: EH complete
[  557.753323] ata4.00: exception Emask 0x0 SAct 0x8 SErr 0x0 action 0x0
[  557.753333] ata4.00: irq_stat 0x40000008
[  557.753340] ata4.00: failed command: READ FPDMA QUEUED
[  557.753354] ata4.00: cmd 60/08:18:00:18:e4/00:00:11:00:00/40 tag 3 ncq 4096 in
[  557.753357]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  557.753365] ata4.00: status: { DRDY ERR }
[  557.753369] ata4.00: error: { UNC }
[  557.756052] ata4.00: configured for UDMA/133
[  557.756079] ata4: EH complete
[  559.770200] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  559.770209] ata4.00: irq_stat 0x40000008
[  559.770217] ata4.00: failed command: READ FPDMA QUEUED
[  559.770231] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  559.770234]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  559.770242] ata4.00: status: { DRDY ERR }
[  559.770247] ata4.00: error: { UNC }
[  559.772841] ata4.00: configured for UDMA/133
[  559.772864] ata4: EH complete
[  561.778755] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  561.778764] ata4.00: irq_stat 0x40000008
[  561.778772] ata4.00: failed command: READ FPDMA QUEUED
[  561.778786] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  561.778789]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  561.778796] ata4.00: status: { DRDY ERR }
[  561.778801] ata4.00: error: { UNC }
[  561.781496] ata4.00: configured for UDMA/133
[  561.781521] sd 3:0:0:0: [sda] Unhandled sense code
[  561.781526] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  561.781535] sd 3:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  561.781546] Descriptor sense data with sense descriptors (in hex):
[  561.781551]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  561.781572]         11 e4 18 00 
[  561.781580] sd 3:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  561.781591] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 11 e4 18 00 00 00 08 00
[  561.781610] end_request: I/O error, dev sda, sector 300161024
[  561.781644] ata4: EH complete
[  563.795607] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  563.795617] ata4.00: irq_stat 0x40000008
[  563.795626] ata4.00: failed command: READ FPDMA QUEUED
[  563.795641] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  563.795644]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  563.795652] ata4.00: status: { DRDY ERR }
[  563.795658] ata4.00: error: { UNC }
[  563.798281] ata4.00: configured for UDMA/133
[  563.798305] ata4: EH complete
[  565.804186] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  565.804195] ata4.00: irq_stat 0x40000008
[  565.804203] ata4.00: failed command: READ FPDMA QUEUED
[  565.804218] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  565.804221]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  565.804228] ata4.00: status: { DRDY ERR }
[  565.804233] ata4.00: error: { UNC }
[  565.806839] ata4.00: configured for UDMA/133
[  565.806862] ata4: EH complete
[  567.812760] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  567.812769] ata4.00: irq_stat 0x40000008
[  567.812778] ata4.00: failed command: READ FPDMA QUEUED
[  567.812792] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  567.812795]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  567.812803] ata4.00: status: { DRDY ERR }
[  567.812808] ata4.00: error: { UNC }
[  567.815397] ata4.00: configured for UDMA/133
[  567.815421] ata4: EH complete
[  569.821278] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  569.821287] ata4.00: irq_stat 0x40000008
[  569.821296] ata4.00: failed command: READ FPDMA QUEUED
[  569.821311] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  569.821314]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  569.821322] ata4.00: status: { DRDY ERR }
[  569.821327] ata4.00: error: { UNC }
[  569.823922] ata4.00: configured for UDMA/133
[  569.823946] ata4: EH complete
[  571.829832] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  571.829841] ata4.00: irq_stat 0x40000008
[  571.829849] ata4.00: failed command: READ FPDMA QUEUED
[  571.829864] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  571.829867]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  571.829875] ata4.00: status: { DRDY ERR }
[  571.829880] ata4.00: error: { UNC }
[  571.832578] ata4.00: configured for UDMA/133
[  571.832603] ata4: EH complete
[  573.838408] ata4.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  573.838418] ata4.00: irq_stat 0x40000008
[  573.838426] ata4.00: failed command: READ FPDMA QUEUED
[  573.838441] ata4.00: cmd 60/08:00:00:18:e4/00:00:11:00:00/40 tag 0 ncq 4096 in
[  573.838444]          res 41/40:00:00:18:e4/00:00:11:00:00/40 Emask 0x409 (media error) <F>
[  573.838452] ata4.00: status: { DRDY ERR }
[  573.838457] ata4.00: error: { UNC }
[  573.841065] ata4.00: configured for UDMA/133
[  573.841091] sd 3:0:0:0: [sda] Unhandled sense code
[  573.841096] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  573.841105] sd 3:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  573.841116] Descriptor sense data with sense descriptors (in hex):
[  573.841122]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  573.841142]         11 e4 18 00 
[  573.841151] sd 3:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  573.841162] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 11 e4 18 00 00 00 08 00
[  573.841181] end_request: I/O error, dev sda, sector 300161024
[  573.841216] ata4: EH complete
tyler9@tyler9-desktop:~$ 

Yow--alot of "error" and "failed command"--definitely beyond my skill level to interpret--what's it mean?

---

### Post by knitmom on 2011-02-26
I've been using dropbox with no problem up until a week ago.

All these issues started middle to end of last week.

Also, is nautilus the file browser program?

---

### Post by runeh76 on 2011-02-26
I did google that _error: { UNC }_
and here is result:
(UNC) Uncorrectable Data: An ECC error in the data field could not be corrected (a media error or read instability). 


It seems that ur HD have problems..

U could try to fix errors with fchk:

Change directory to root (/) directory:
# cd /

Create a file called forcefsck:
# sudo touch /forcefsck

Now reboot the system:
# reboot

---

### Post by tyler9 on 2011-02-26
> **knitmom said:**
> I've been using dropbox with no problem up until a week ago.
All these issues started middle to end of last week.
Also, is nautilus the file browser program?

...don't know anything about dropbox; nautilus is the gnome graphical file browser. If you use it, it should open when you type: 
nautilus
...in a terminal window. When I do that, I get "Bus error." And nautilus won't open via a menu command either, as I mention in original post above.

[http://live.gnome.org/Nautilus/Screenshots](http://live.gnome.org/Nautilus/Screenshots)

---

### Post by runeh76 on 2011-02-26
tyler9

Here is thread with same error messages, u could take a look:

[http://ubuntuforums.org/showthread.php?t=937872]("http://ubuntuforums.org/showthread.php?t=937872")

---

### Post by tyler9 on 2011-02-26
> **runeh76 said:**
> I did google that _error: { UNC }_
and here is result:
(UNC) Uncorrectable Data: An ECC error in the data field could not be corrected (a media error or read instability). 

It seems that ur HD have problems..

U could try to fix errors with fchk:

Change directory to root (/) directory:
# cd /

Create a file called forcefsck:
# sudo touch /forcefsck

Now reboot the system:
# reboot

By "HD problems" do you mean a physical problem with the drive, or with the drive's file system? 

Does using fchk pose any danger? I tried researching the command, but I simply don't understand:
[http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm](http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm)

I checked that other thread you mentioned, but it'd take me days to understand what they're talking about.

---

### Post by runeh76 on 2011-02-26
Im not sure what kind of problems ur HD have, but fchk doesnt harm ur HD its just try to fix problems if it finds them, just run those commands in terminal.

( last command  reboot  type--> sudo reboot )

---

### Post by VOT Productions on 2011-02-26
It shouldn't pose danger.
Your output is more than likely to be a faulty HD.

---

### Post by tyler9 on 2011-02-26
> **VOT Productions said:**
> It shouldn't pose danger.
Your output is more than likely to be a faulty HD.

By "faulty HD" do you mean the HD itself is defective? Or are you referring to a less-serious kind of problem?

It's a Western Digital bought last year; if it's defective or failing prematurely, I'll want a replacement. 

I assume there are varying degrees of severity of HD problems, so I need some understanding of how serious this might be.

Edited to add: 
knitmom, how does your output from  "dmesg" command compare to mine?

---

### Post by tyler9 on 2011-02-26
> **runeh76 said:**
> I did google that _error: { UNC }_
and here is result:
(UNC) Uncorrectable Data: An ECC error in the data field could not be corrected (a media error or read instability). 

It seems that ur HD have problems..

U could try to fix errors with fchk:

Change directory to root (/) directory:
# cd /

Create a file called forcefsck:
# sudo touch /forcefsck

Now reboot the system:
# reboot

OK--did that, got the "checking hard drive" msg on boot up. But got no output, no results of check, no msg to see file "xyz" for results, nothing. Ubuntu is running the same, with same problems. Is the output of this check written to a text file or something, so we can check? Is that what forcefsck is?

Thx!

---

### Post by knitmom on 2011-02-26
I ran dmesg also,  but didn't come up with the same error.

Here are my results:

[    0.420636]   alloc kstat_irqs on node -1
[    0.420657] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.421015] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.421323] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.421344] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701fca8), AE_ALREADY_EXISTS
[    0.421709] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.421732] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701fca8), AE_ALREADY_EXISTS
[    0.422087] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.422107] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701fca8), AE_ALREADY_EXISTS
[    0.422443] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.422463] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701fca8), AE_ALREADY_EXISTS
[    0.422900] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.422922] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701fca8), AE_ALREADY_EXISTS
[    0.423259] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.423279] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701fca8), AE_ALREADY_EXISTS
[    0.423637] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.423657] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701fca8), AE_ALREADY_EXISTS
[    0.424028] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.424047] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f701fca8), AE_ALREADY_EXISTS
[    0.424177] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.424532] intel_idle: MWAIT substates: 0x20220
[    0.424540] intel_idle: v0.4 model 0x1C
[    0.424547] intel_idle: lapic_timer_reliable_states 0x2
[    0.424569] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.424956] Switching to clocksource hpet
[    0.425686] ACPI: AC Adapter [ACAD] (on-line)
[    0.425977] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.425993] ACPI: Power Button [PWRB]
[    0.426144] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.426616] ACPI: Lid Switch [LID0]
[    0.426804] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.426819] ACPI: Sleep Button [SLPB]
[    0.427009] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.427022] ACPI: Power Button [PWRF]
[    0.427929] ACPI: acpi_idle yielding to intel_idle
[    0.437138] ERST: Table is not found!
[    0.438009] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.443043] brd: module loaded
[    0.444267] ACPI: Battery Slot [BAT1] (battery absent)
[    0.444308] isapnp: Scanning for PnP cards...
[    0.445161] loop: module loaded
[    0.445801] ata_piix 0000:00:1f.2: version 2.13
[    0.445839] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.445852] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.445939] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.446151] scsi0 : ata_piix
[    0.446425] scsi1 : ata_piix
[    0.449209] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x60a0 irq 14
[    0.449219] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x60a8 irq 15
[    0.450578] Fixed MDIO Bus: probed
[    0.450714] PPP generic driver version 2.4.2
[    0.450867] tun: Universal TUN/TAP device driver, 1.6
[    0.450874] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.451139] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.451191] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.451229] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.451239] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.451351] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.451403] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.451424] ehci_hcd 0000:00:1d.7: debug port 1
[    0.455318] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.455366] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58544400
[    0.473529] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.473946] hub 1-0:1.0: USB hub found
[    0.473962] hub 1-0:1.0: 8 ports detected
[    0.474186] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.474245] uhci_hcd: USB Universal Host Controller Interface driver
[    0.474335] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.474355] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.474364] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.474501] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.474557] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00006080
[    0.474948] hub 2-0:1.0: USB hub found
[    0.474963] hub 2-0:1.0: 2 ports detected
[    0.475126] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.475143] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.475152] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.475264] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.475335] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006060
[    0.475702] hub 3-0:1.0: USB hub found
[    0.475717] hub 3-0:1.0: 2 ports detected
[    0.475892] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.475910] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.475918] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.476025] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.476093] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    0.476477] hub 4-0:1.0: USB hub found
[    0.476491] hub 4-0:1.0: 2 ports detected
[    0.476651] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.476669] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.476677] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.476784] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.476850] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006020
[    0.477254] hub 5-0:1.0: USB hub found
[    0.477268] hub 5-0:1.0: 2 ports detected
[    0.477585] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    0.481574] i8042.c: Warning: Keylock active.
[    0.504521] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.517135] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.517162] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.517286] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.517369] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.517449] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.517838] mice: PS/2 mouse device common for all mice
[    0.518374] rtc_cmos 00:03: RTC can wake from S4
[    0.518496] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.518548] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.518922] device-mapper: uevent: version 1.0.3
[    0.538193] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.542729] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.557452] device-mapper: multipath: version 1.1.1 loaded
[    0.557464] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.557955] EISA: Probing bus 0 at eisa.0
[    0.557965] EISA: Cannot allocate resource for mainboard
[    0.557974] Cannot allocate resource for EISA slot 1
[    0.557982] Cannot allocate resource for EISA slot 2
[    0.557990] Cannot allocate resource for EISA slot 3
[    0.557997] Cannot allocate resource for EISA slot 4
[    0.558005] Cannot allocate resource for EISA slot 5
[    0.558013] Cannot allocate resource for EISA slot 6
[    0.558021] Cannot allocate resource for EISA slot 7
[    0.558029] Cannot allocate resource for EISA slot 8
[    0.558035] EISA: Detected 0 cards.
[    0.573705] cpuidle: using governor ladder
[    0.574114] cpuidle: using governor menu
[    0.574976] TCP cubic registered
[    0.575439] NET: Registered protocol family 10
[    0.576437] lo: Disabled Privacy Extensions
[    0.577104] NET: Registered protocol family 17
[    0.578452] Using IPI No-Shortcut mode
[    0.578751] PM: Resume from disk failed.
[    0.578786] registered taskstats version 1
[    0.579493]   Magic number: 15:618:654
[    0.579649] rtc_cmos 00:03: setting system clock to 2011-02-23 22:37:38 UTC (1298500658)
[    0.579659] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.579664] EDD information not available.
[    0.664600] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    0.664613] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.682891] ata1.00: configured for UDMA/133
[    0.785313] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    0.798672] isapnp: No Plug & Play device found
[    0.799057] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    0.799560] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.799882] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.800137] sd 0:0:0:0: [sda] Write Protect is off
[    0.800148] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.800244] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.800908]  sda: sda1 sda2 < sda5 sda6 >
[    0.822747] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.872940] Freeing initrd memory: 10512k freed
[    0.883737] Freeing unused kernel memory: 688k freed
[    0.884598] Write protecting the kernel text: 4936k
[    0.884679] Write protecting the kernel read-only data: 1976k
[    0.926207] udev[80]: starting version 163
[    1.370645] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.370713] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.370797] r8169 0000:02:00.0: setting latency timer to 64
[    1.370877]   alloc irq_desc for 44 on node -1
[    1.370887]   alloc kstat_irqs on node -1
[    1.370918] r8169 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.372574] r8169 0000:02:00.0: eth0: RTL8102e at 0xf804e000, 00:23:8b:69:bf:61, XID 04a00000 IRQ 44
[    1.396996] sdhci: Secure Digital Host Controller Interface driver
[    1.397054] sdhci: Copyright(c) Pierre Ossman
[    1.403038] sdhci-pci 0000:04:00.0: SDHCI controller found [197b:2382] (rev 0)
[    1.403092] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.403191] sdhci-pci 0000:04:00.0: setting latency timer to 64
[    1.403300] Registered led device: mmc0::
[    1.403429] mmc0: SDHCI controller on PCI [0000:04:00.0] using ADMA
[    1.403464] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 0)
[    1.403511] sdhci-pci 0000:04:00.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.403534] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
[    1.403553] sdhci-pci 0000:04:00.2: PCI INT A disabled
[    1.578841] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    8.257451] usb 1-5: USB disconnect, address 2
[    8.528063] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    8.596401] hub 1-0:1.0: unable to enumerate USB device on port 5
[    8.864098] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    9.012249] usb 4-1: not running at top speed; connect to a high speed hub
[   20.821967] Adding 1461876k swap on /dev/sda5.  Priority:-1 extents:1 across:1461876k 
[   20.918908] udev[364]: starting version 163
[   21.023894] lp: driver loaded but no devices found
[   21.329458] intel_rng: FWH not detected
[   21.352710] leds_ss4200: no LED devices found
[   21.470967] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   21.471132] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
[   21.695354] Linux agpgart interface v0.103
[   21.725943] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   21.725964] jmb38x_ms 0000:04:00.3: setting latency timer to 64
[   21.758327] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   21.883110] acerhdf: Acer Aspire One Fan driver, v.0.5.22
[   21.883130] acerhdf: Fan control off, to enable do:
[   21.883136] acerhdf: echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode
[   21.956780] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[   21.957588] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   21.960568] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[   21.978217] Linux video capture interface: v2.00
[   22.114794] type=1400 audit(1298518680.031:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=614 comm="apparmor_parser"
[   22.115666] type=1400 audit(1298518680.031:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=614 comm="apparmor_parser"
[   22.116282] type=1400 audit(1298518680.031:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=614 comm="apparmor_parser"
[   22.117621] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   22.136475] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input6
[   22.136707] usbcore: registered new interface driver uvcvideo
[   22.136716] USB Video Class driver (v0.1.0)
[   22.155731] cfg80211: Calling CRDA to update world regulatory domain
[   22.336853] cfg80211: World regulatory domain updated:
[   22.336864]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.336876]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.336886]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.336896]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.336906]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.336916]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.523378] [drm] Initialized drm 1.1.0 20060810
[   22.582825] ath5k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.582853] ath5k 0000:03:00.0: setting latency timer to 64
[   22.582977] ath5k 0000:03:00.0: registered as 'phy0'
[   22.937416] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000/0xa0000
[   23.018442] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   23.268169] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.268290]   alloc irq_desc for 45 on node -1
[   23.268298]   alloc kstat_irqs on node -1
[   23.268325] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   23.268388] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   23.335296] type=1400 audit(1298518681.251:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=846 comm="apparmor_parser"
[   23.336184] type=1400 audit(1298518681.251:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=846 comm="apparmor_parser"
[   23.336712] type=1400 audit(1298518681.251:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=846 comm="apparmor_parser"
[   23.347945] type=1400 audit(1298518681.263:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=845 comm="apparmor_parser"
[   23.409913] type=1400 audit(1298518681.327:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=856 comm="apparmor_parser"
[   23.411079] type=1400 audit(1298518681.327:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=856 comm="apparmor_parser"
[   23.424936] type=1400 audit(1298518681.339:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=853 comm="apparmor_parser"
[   23.488129] r8169 0000:02:00.0: eth0: link down
[   23.488840] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.512735] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.512751] i915 0000:00:02.0: setting latency timer to 64
[   23.628028] mtrr: no more MTRRs available
[   23.628040] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   23.671122] [drm] set up 7M of stolen space
[   23.743385] ath: EEPROM regdomain: 0x65
[   23.743394] ath: EEPROM indicates we should expect a direct regpair map
[   23.743404] ath: Country alpha2 being used: 00
[   23.743409] ath: Regpair used: 0x65
[   23.850669] phy0: Selected rate control algorithm 'minstrel'
[   23.852748] Registered led device: ath5k-phy0::rx
[   23.852835] Registered led device: ath5k-phy0::tx
[   23.852845] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   23.887031] apm: BIOS not found.
[   23.890456] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   23.891053] [drm] initialized overlay support
[   24.160052] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.217115] Skipping EDID probe due to cached edid
[   24.581401] Console: switching to colour frame buffer device 128x37
[   24.590772] fb0: inteldrmfb frame buffer device
[   24.590852] drm: registered panic notifier
[   24.591549] Slow work thread pool: Starting up
[   24.591736] Slow work thread pool: Ready
[   24.591768] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.739607] ppdev: user-space parallel port driver
[   24.756119] Skipping EDID probe due to cached edid
[   25.621319] Skipping EDID probe due to cached edid
[   25.652302] Skipping EDID probe due to cached edid
[   26.203435] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   26.303710] wlan0: authenticate with 00:1f:90:b0:d9:34 (try 1)
[   26.310853] wlan0: authenticated
[   26.310947] wlan0: associate with 00:1f:90:b0:d9:34 (try 1)
[   26.321093] wlan0: RX AssocResp from 00:1f:90:b0:d9:34 (capab=0x431 status=0 aid=5)
[   26.321104] wlan0: associated
[   26.322986] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.332187] cfg80211: Calling CRDA for country: US
[   26.353368] cfg80211: Regulatory domain changed to country: US
[   26.353379]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.353389]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   26.353398]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   26.353407]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.353416]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.353424]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.353433]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   27.101122] Skipping EDID probe due to cached edid
[   27.136190] Skipping EDID probe due to cached edid
[   27.188143] Skipping EDID probe due to cached edid
[   27.220144] Skipping EDID probe due to cached edid
[   31.149741] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   36.976089] wlan0: no IPv6 routers present
[   44.185157] Skipping EDID probe due to cached edid
[   44.224855] Skipping EDID probe due to cached edid
[   44.261150] Skipping EDID probe due to cached edid
[   50.536149] Skipping EDID probe due to cached edid
[  433.273116] usb 1-2: new high speed USB device using ehci_hcd and address 4
[  814.342155] usb 1-2: USB disconnect, address 4
[ 2799.844143] usb 4-1: USB disconnect, address 2
[ 2800.152103] usb 1-5: new high speed USB device using ehci_hcd and address 5
[ 2800.217906] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 2800.616109] usb 4-1: new full speed USB device using uhci_hcd and address 3
[ 2800.767557] usb 4-1: not running at top speed; connect to a high speed hub
[ 2800.840388] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[ 2800.862917] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input8
[ 2802.759120] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 2805.549195] wlan0: deauthenticating from 00:1f:90:b0:d9:34 by local choice (reason=3)
[ 2805.595614] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2805.595629] cfg80211: Restoring regulatory settings
[ 2805.595639] cfg80211: Calling CRDA to update world regulatory domain
[ 2805.763176] cfg80211: World regulatory domain updated:
[ 2805.763188]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2805.763199]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2805.763209]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2805.763218]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2805.763227]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2805.763236]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2806.623370] PM: Syncing filesystems ... done.
[ 2806.645400] PM: Preparing system for mem sleep
[ 2806.913346] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 2806.932202] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 2806.948190] PM: Entering mem sleep
[ 2806.948299] Suspending console(s) (use no_console_suspend to debug)
[ 2806.964364] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2806.964659] sd 0:0:0:0: [sda] Stopping disk
[ 2807.030246] jmb38x_ms 0000:04:00.3: PCI INT A disabled
[ 2807.030509] sdhci-pci 0000:04:00.0: PCI INT A disabled
[ 2807.030739] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 2807.030761] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[ 2807.030783] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 2807.030805] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 2807.030825] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 2807.031283] i915 0000:00:02.0: PCI INT A disabled
[ 2807.132162] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 2807.148081] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 117.137 msecs
[ 2807.283738] PM: suspend of drv:sd dev:0:0:0:0 complete after 319.396 msecs
[ 2807.283792] PM: suspend of drv:scsi dev:target0:0:0 complete after 319.320 msecs
[ 2807.283836] PM: suspend of drv:scsi dev:host0 complete after 254.391 msecs
[ 2807.284114] ata_piix 0000:00:1f.2: PCI INT B disabled
[ 2807.300087] PM: suspend of drv:ata_piix dev:0000:00:1f.2 complete after 269.452 msecs
[ 2807.300139] PM: suspend of drv: dev:pci0000:00 complete after 268.738 msecs
[ 2807.300178] PM: suspend of devices complete after 351.605 msecs
[ 2807.300193] PM: suspend devices took 0.352 seconds
[ 2807.316213] r8169 0000:02:00.0: PME# enabled
[ 2807.316256] pcieport 0000:00:1c.1: wake-up capability enabled by ACPI
[ 2807.348443] PM: late suspend of devices complete after 48.238 msecs
[ 2807.348497] ACPI: Preparing to enter system sleep state S3
[ 2807.349574] PM: Saving platform NVS memory
[ 2807.359293] Disabling non-boot CPUs ...
[ 2807.464073] CPU 1 is now offline
[ 2807.464080] SMP alternatives: switching to UP code
[ 2807.470499] Back to C!
[ 2807.470499] PM: Restoring platform NVS memory
[ 2807.470499] Enabling non-boot CPUs ...
[ 2807.470499] SMP alternatives: switching to SMP code
[ 2807.476529] Booting Node 0 Processor 1 APIC 0x1
[ 2807.469563] Initializing CPU#1
[ 2807.469563] Atom PSE erratum detected, BIOS microcode update recommended
[ 2807.593055] CPU1 is up
[ 2807.593554] ACPI: Waking up from system sleep state S3
[ 2807.718837] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 2807.718894] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20005050, writing 0x5050)
[ 2807.718912] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 2807.718974] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x2ff)
[ 2807.718992] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x52015101)
[ 2807.719002] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0x57205630)
[ 2807.719011] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x4030)
[ 2807.719021] pcieport 0000:00:1c.1: restoring config space at offset 0x6 (was 0x200, writing 0x20200)
[ 2807.719037] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 2807.719096] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x3ff)
[ 2807.719114] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0x53015211)
[ 2807.719123] pcieport 0000:00:1c.2: restoring config space at offset 0x8 (was 0x0, writing 0x56205520)
[ 2807.719133] pcieport 0000:00:1c.2: restoring config space at offset 0x7 (was 0x20000000, writing 0x2020)
[ 2807.719143] pcieport 0000:00:1c.2: restoring config space at offset 0x6 (was 0x300, writing 0x30300)
[ 2807.719158] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 2807.719239] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 2807.719309] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 2807.719353] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 2807.719396] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 2807.719438] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 2807.719490] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[ 2807.719524] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
[ 2807.719740] r8169 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[ 2807.719755] r8169 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfffe0000)
[ 2807.719772] r8169 0000:02:00.0: restoring config space at offset 0x8 (was 0xc, writing 0x5100000c)
[ 2807.719785] r8169 0000:02:00.0: restoring config space at offset 0x6 (was 0xc, writing 0x5101000c)
[ 2807.719798] r8169 0000:02:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x3001)
[ 2807.719809] r8169 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2807.719822] r8169 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 2807.719913] ath5k 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 2807.719946] ath5k 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x55200004)
[ 2807.719957] ath5k 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2807.719970] ath5k 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2807.720061] sdhci-pci 0000:04:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[ 2807.720077] sdhci-pci 0000:04:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff8000)
[ 2807.720105] sdhci-pci 0000:04:00.0: restoring config space at offset 0x4 (was 0x0, writing 0x54100300)
[ 2807.720122] sdhci-pci 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2807.720181] pci 0000:04:00.2: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[ 2807.720217] pci 0000:04:00.2: restoring config space at offset 0x4 (was 0x0, writing 0x54100200)
[ 2807.720233] pci 0000:04:00.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
[ 2807.720292] jmb38x_ms 0000:04:00.3: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[ 2807.720328] jmb38x_ms 0000:04:00.3: restoring config space at offset 0x4 (was 0x0, writing 0x54100100)
[ 2807.720344] jmb38x_ms 0000:04:00.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2807.720403] pci 0000:04:00.4: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[ 2807.720439] pci 0000:04:00.4: restoring config space at offset 0x4 (was 0x0, writing 0x54100000)
[ 2807.720455] pci 0000:04:00.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 2807.720953] PM: early resume of devices complete after 2.347 msecs
[ 2807.721657] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2807.721673] i915 0000:00:02.0: setting latency timer to 64
[ 2807.726254] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2807.726270] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 2807.726338] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[ 2807.726443] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2807.726451] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2807.726459] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2807.726464] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2807.726501] usb usb2: root hub lost power or was reset
[ 2807.726505] usb usb3: root hub lost power or was reset
[ 2807.726539] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 2807.726546] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[ 2807.726553] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2807.726558] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 2807.726591] usb usb4: root hub lost power or was reset
[ 2807.726601] usb usb5: root hub lost power or was reset
[ 2807.726632] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2807.726645] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 2807.726664] pci 0000:00:1e.0: setting latency timer to 64
[ 2807.726696] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2807.726741] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 2807.726752] pcieport 0000:00:1c.1: wake-up capability disabled by ACPI
[ 2807.726764] r8169 0000:02:00.0: PME# disabled
[ 2807.726808] sdhci-pci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2807.726831] sdhci-pci 0000:04:00.0: setting latency timer to 64
[ 2807.726880] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2807.726892] jmb38x_ms 0000:04:00.3: setting latency timer to 64
[ 2807.729337] sd 0:0:0:0: [sda] Starting disk
[ 2807.873132] PM: resume of drv:usb dev:usb3 complete after 143.850 msecs
[ 2807.873178] PM: resume of drv:hub dev:3-0:1.0 complete after 143.888 msecs
[ 2807.873274] PM: resume of drv:usb dev:usb2 complete after 144.021 msecs
[ 2807.873290] PM: resume of drv:usb dev:usb5 complete after 143.977 msecs
[ 2807.873336] PM: resume of drv:hub dev:5-0:1.0 complete after 144.010 msecs
[ 2807.873352] PM: resume of drv:hub dev:2-0:1.0 complete after 144.076 msecs
[ 2807.977100] PM: resume of drv:usb dev:usb4 complete after 247.803 msecs
[ 2807.977145] PM: resume of drv:hub dev:4-0:1.0 complete after 247.837 msecs
[ 2807.977161] PM: resume of drv:usb dev:usb1 complete after 250.207 msecs
[ 2807.977232] PM: resume of drv:usb dev:4-1 complete after 247.800 msecs
[ 2807.977248] PM: resume of drv:hub dev:1-0:1.0 complete after 247.998 msecs
[ 2807.977282] PM: resume of drv:uvcvideo dev:4-1:1.1 complete after 247.838 msecs
[ 2807.977298] PM: resume of drv:uvcvideo dev:4-1:1.0 complete after 247.845 msecs
[ 2807.977328] PM: resume of drv: dev:ep_81 complete after 240.259 msecs
[ 2810.245408] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 2810.245433] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[ 2810.273926] ata1.00: configured for UDMA/133
[ 2810.277766] PM: resume of drv:sd dev:0:0:0:0 complete after 2548.424 msecs
[ 2810.277826] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2289.061 msecs
[ 2810.277844] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2548.403 msecs
[ 2810.278218] PM: resume of devices complete after 2557.118 msecs
[ 2810.620495] PM: resume devices took 2.900 seconds
[ 2810.620571] PM: Finishing wakeup.
[ 2810.620575] Restarting tasks ... 
[ 2810.620678] usb 4-1: USB disconnect, address 3
[ 2810.621646] done.
[ 2810.621673] video LNXVIDEO:00: Restoring backlight state
[ 2810.634521] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 2810.693137] Skipping EDID probe due to cached edid
[ 2810.760385] usb 1-5: new high speed USB device using ehci_hcd and address 6
[ 2810.941641] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[ 2810.959481] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input9
[ 2811.220280] r8169 0000:02:00.0: eth0: link down
[ 2811.221231] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2811.257083] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2811.403068] usb 1-5: USB disconnect, address 6
[ 2811.664732] usb 1-5: new high speed USB device using ehci_hcd and address 7
[ 2811.840391] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[ 2811.857410] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input10
[ 2813.613591] wlan0: authenticate with 00:1f:90:b0:d9:34 (try 1)
[ 2813.616666] wlan0: authenticated
[ 2813.616729] wlan0: associate with 00:1f:90:b0:d9:34 (try 1)
[ 2813.619005] wlan0: RX AssocResp from 00:1f:90:b0:d9:34 (capab=0x431 status=0 aid=2)
[ 2813.619017] wlan0: associated
[ 2813.620780] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2813.973306] usb 1-5: USB disconnect, address 7
[ 2814.236095] usb 1-5: new high speed USB device using ehci_hcd and address 8
[ 2814.411498] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[ 2814.428972] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input11
[ 2815.163800] usb 1-5: USB disconnect, address 8
[ 2815.420224] usb 1-5: new high speed USB device using ehci_hcd and address 9
[ 2815.595510] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[ 2815.612370] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input12
[ 2816.244907] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[ 2824.111026] usb 1-5: USB disconnect, address 9
[ 2824.376299] usb 1-5: new high speed USB device using ehci_hcd and address 10
[ 2824.521032] wlan0: no IPv6 routers present
[ 2824.549479] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[ 2824.570333] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input13
[ 2836.929429] usb 1-5: USB disconnect, address 10
[ 2837.196449] usb 1-5: new high speed USB device using ehci_hcd and address 11
[ 2837.367399] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[ 2837.384412] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input14
[ 2885.877962] usb 1-5: USB disconnect, address 11
[ 2886.148102] usb 1-5: new high speed USB device using ehci_hcd and address 12
[ 2886.321566] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[ 2886.338531] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input15
[ 3040.152264] WARNING! power/level is deprecated; use power/control instead


It seems that the errors are ACPI related. Would fdsk work in my case too?

---

### Post by knitmom on 2011-02-26
Not sure if this is the right way to forward to another thread, but I found this [http://ubuntuforums.org/showthread.php?t=1592245]("http://ubuntuforums.org/showthread.php?t=1592245")  The title of this thread is "10.10 runs slow and jerky" in case the link doesn't work right.  

It seems that others are having the same issues with this too. I haven't read it all yet, there are 27 pages to this thread!

I really think it has to do with one of the updates I downloaded last week.  It worked great great before.

Thanks for all the help so far!

PS:  I have found if I wait.... it will finally let me save the file.  But that is not normal.  The reason I love Ubuntu is that it is faster than windows!!!

BTW, I'm running
10.10 Maverick
Kernel Linux 2.6.35-25 generic
Gnome 2.32.0
Memory 989.2 MiB
Dual Core Intel Atom CPU N270 @ 1.6 GHz
Acer Aspire One

---

### Post by knitmom on 2011-02-27
Okay, after agonizing over this today, I thought I would try something different.  I logged into another user on my computer and found out everything worked fine.  So I created a new administrative user for myself. Everything is working fantastic including dropbox and my ipod.  So I've come to the conclusion that something in my original user files must have been corrupted.  I do know for a fact that Nautilus is the problem with my original admin user acct.

Here's to hoping this is the fix for my issue.  You might want to try this and see how it works for you.

---

### Post by runeh76 on 2011-02-27
**tyler9**

I dont know, why forcefsck dont create log files. Log should be in /var/log/fsck/checkfs

Founded this for 10.10, but try it:
[http://linuxhub.net/2010/09/scan-your-hard-disk-with-gsmartcontrol-on-ubuntu-10-10/]("http://linuxhub.net/2010/09/scan-your-hard-disk-with-gsmartcontrol-on-ubuntu-10-10/")


Check ur HD "name"--->**Disk Utility**  System => Administration => (Disk Utility also shows SMART drive information and u can check errors also.)
Try this too (its fix for ubuntu9.10, but u could try, u dont lose nothing):


Boot from the Ubuntu LiveCD and then open a terminal and type:
Code:
sudo fsck -pcfv /dev/sda
_Where "sda" = the disk in question._ 

This command will force automatic bad block checking and it will automatically mark all known bad sectors as bad so that they wont "interfere" in the future. After you boot back into the OS, I would make sure that smartmontools is installed:

Code:
sudo apt-get install smartmontools
You will need to make sure that "SMART' capability is enabled in your BIOS. After you get it installed, then you can run an extended offline test (this will run in the background while the computer is on and you wont even know it is running). To do that:

Code:
sudo smartctl --test=long /dev/sda
And then to see the overall health of the system, you can type:

Code:
sudo smartctl -a /dev/sda
Also, please read the manpages for these programs if you want a more detailed explanation:

Code:
man fsck
man smartmontools

---

### Post by runeh76 on 2011-02-27
**knitmom**

That acpi error, its just bug. No need to do anything.
If ur system is working now, with new user, the problem ur "old" account can be anything..maybe some updates went wrong. Allways when system starts update something "bigger"--> kernel,graphic card etc.--> Make a backup!

Dont use ur Ubuntu just with one account! U should use different account than that what came after Ubuntu installation.

---

### Post by knitmom on 2011-02-27
runeh76

Thanks!  It's been awhile since I've played with commands in terminal - 5 or 6 years, so I'm glad you are available to help on the forums. That is one thing I love about the ubuntu forums - all the other users who are so knowledgeable!  I really need to refresh my memory when it comes to this. I use to work on unix based programs years (20+) ago, so some of this should come back!  Every distro is a new experience, but when it works, I love it!!! 

tyler9

I hope everything works out for you.

Have a great day!!!

---

### Post by runeh76 on 2011-02-27
Thank you **knitmom** :)


**tyler9** Lets see ur partitions info, i did read again ur first post, u did say that u have mint9 also. I was thinking.. Is it in same HD with Ubuntu?

Boot info script:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by tyler9 on 2011-02-27
runeh76, thanks for your persistence. [knitmom: congrats!]

I haven't yet done all the Terminal commands you specify in above posts; wanted to do this first:
System>Administration>Disk Utility>Check Filesystem [near bottom of Disk Utility box], and I get:

"An error occurred while performing an operation on "250 GB Filesystem" (partition 1 of [hd number): The device is busy"

I clicked the "Details" button and get:
"Device is mounted and no online capability in fsck tool for file system"

Re my disk: Yep, only one disk, partitioned for Ubuntu10.04, and Mint9. Mint9 works fine; problem is, as I mention in original post, half the time I can't move the highlighter on the GRUB screen down to select Mint9.

Another Q: in the Disk Utility box, in the "Drive" section, it says: Device:  /dev/sda
In the "Volumes" section, it says:  Device: /dev/sda1

Does this mean the entire drive is /sda, and the Ubuntu partition is /sda1?

Wanted to get your comments on this, before I try the terminal commands you suggest.

---

### Post by runeh76 on 2011-02-27
"An error occurred while performing an operation on "250 GB Filesystem" (partition 1 of [hd number): The device is busy"

I clicked the "Details" button and get:
"Device is mounted and no online capability in fsck tool for file system"

Thats normal. U just needed to check ur HD name and if u have SMART-support, u can see if its ok-->green


"Does this mean the entire drive is /sda, and the Ubuntu partition is /sda1?"

Yes correct! Choose sda to that code.


uumm..Which one was first, mint or ubuntu? pls post that boot info.

---

### Post by runeh76 on 2011-02-27
omg..i found a thread, where guy couldnt choose other OS in GRUB. And the solution was, that he had plugged keyboard to mouse port. So double check this pls  :)

---

### Post by tyler9 on 2011-02-28
> **runeh76 said:**
> omg..i found a thread, where guy couldnt choose other OS in GRUB. And the solution was, that he had plugged keyboard to mouse port. So double check this pls  :)

Lol! Nope, that's not the problem [at least not this time...]

I ran a diagnostic from HD manufacturer. Looks like the HD is failing. So I'm starting the RMA process today--bought this drive last year. First time I've had a HD fail.

I greatly appreciate your help. All the above info is very good to know.

[Let's see, back to the diagnostic: it says "press any key to continue"...I'm still looking...where's that "any" key?...] ;)

---

### Post by runeh76 on 2011-02-28
Okey, good to know that problem was HD! I wish good luck to u  :)

(pls mark thread solved)

---

### Post by tyler9 on 2011-03-01
runeh76:
Okey, good to know that problem was HD! I wish good luck to u :smile:
(pls mark thread solved) 
 
Good reminder--done. Thx again; I'll probably be back here bugging you with more Qs after I install Ubuntu on replacement HD!

---

