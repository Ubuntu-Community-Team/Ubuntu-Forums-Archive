---
title: "New RAM problems"
date: 2006-04-16
forum: General Help
---

### Post by Supertip on 2006-04-16
Up Graded RAM from 2 256mb ddr cards to 1 256 and 1 512 card, but now i can only get it to detect 512mb of RAM. 

my /proc/meminfo says....

MemTotal:       581672 kB
MemFree:         10948 kB
Buffers:         25636 kB
Cached:         331572 kB
SwapCached:          0 kB
Active:         331880 kB
Inactive:       197008 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       581672 kB
LowFree:         10948 kB
SwapTotal:     3903752 kB
SwapFree:      3903752 kB
Dirty:              24 kB
Writeback:           0 kB
Mapped:         220184 kB
Slab:            28548 kB
CommitLimit:   4194588 kB
Committed_AS:   320100 kB
PageTables:       1476 kB
VmallocTotal:   434168 kB
VmallocUsed:      9100 kB
VmallocChunk:   423004 kB

idk if that helps

---

### Post by uncleed on 2006-04-16
I know this shouldnt make a difference, but it has worked for me in the past, with the same problem. Try switching the cards in the slots. If that dont do it, try installing one, boot up and see if it detects it. If it does, shut down and install the other. Dont know why, but sometimes it works !!

---

### Post by Supertip on 2006-04-17
ok, i only installed the 512mb card and i get

MemTotal:       516004 kB
MemFree:        161872 kB
Buffers:         14544 kB
Cached:         199568 kB
SwapCached:          0 kB
Active:         205044 kB
Inactive:       114744 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       516004 kB
LowFree:        161872 kB
SwapTotal:     3903752 kB
SwapFree:      3903752 kB
Dirty:            6720 kB
Writeback:           0 kB
Mapped:         136800 kB
Slab:            22020 kB
CommitLimit:   4161752 kB
Committed_AS:   180236 kB
PageTables:       1460 kB
VmallocTotal:   507896 kB
VmallocUsed:      9184 kB
VmallocChunk:   496732 kB

so i am obviously getting about the 512mb of the card, but when i install both the cards i only get 581mb, why am i losing so much memory?

---

