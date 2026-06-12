---
title: "I need help with GIMP"
date: 2010-01-16
forum: General Help
---

### Post by LazyPony on 2010-01-16
Hey everyone,
Before I continue with anything, I must tell you that I dont no ANYTHING about this stuff. Windows was easier. But, i wanted to try somthing new. When i had first gotten Ubuntu "Linux"?
Gimp worked fine, But i guess i must have messed somthing up and now barely anything works now :[ . Like when i try to launch Gimp, i hear my comptuer trying but nothing happens. I dont know whats wrong.... HELP!!!!!

---

### Post by michy99 on 2010-01-16
What happens if you open a terminal and enter this command?```
gimp-2.6
```If you get any errors, post them here.

---

### Post by drs305 on 2010-01-16
> **LazyPony said:**
> Hey everyone,
Before I continue with anything, I must tell you that I dont no ANYTHING about this stuff. Windows was easier. But, i wanted to try somthing new. When i had first gotten Ubuntu "Linux"?
Gimp worked fine, But i guess i must have messed somthing up and now barely anything works now :[ . Like when i try to launch Gimp, i hear my comptuer trying but nothing happens. I dont know whats wrong.... HELP!!!!!

You haven't given us much to go on. One way to determine what is happening in Linux is to try what you are doing in a terminal. The reason is that in terminal the user can see error messages which might tell you what is happening, what is wrong, and/or how to fix it.

Open a terminal (Applications, Accessories, Terminal) and then type "gimp" without the quotes and ENTER. Tell us what messages you get.

---

### Post by LazyPony on 2010-01-16
joe@agres-laptop:~$ gimp-2.6
Bus error
joe@agres-laptop:~$ gimp
Bus error
joe@agres-laptop:~$ 

Thx for the replies appreciate it. But this isnt the only program that has a bus error there are a few others. Not sure witch ones but yeh, And i had only installed Flash and wine

---

### Post by nerdy_kid on 2010-01-16
did you mess with ibus at all?
maybe create a new account and see if the same issues exist.

---

### Post by LazyPony on 2010-01-16
I have no idea what that is, but i did try the account thing and that didnt work :[

---

### Post by nerdy_kid on 2010-01-16
hmmm, ill try to help, but not sure i can.

can you post these files?

~/.xsession-errors
/var/log/syslog

---

### Post by LazyPony on 2010-01-16
haha i appreciate it but, i dont want you to get annoyed.. seeing as how i dont even know what that is or even how to find it

---

### Post by nerdy_kid on 2010-01-16
DONT DO THIS YET

also, open a terminal and do:
now, i heard that removing xulrunner might help, but this will take out most of your apps.  The below code will reinstall them after.  Just warning you.....
```

sudo apt-get purge xulrunner
sudo apt-get install ubuntu-desktop

```

---

### Post by junapp on 2010-01-16
to do that you could go to Applications -> Accessories -> Terminal

then type
```
cat ~/.xsession-errors /var/log/syslog > ~/postthis.txt
```then attach the postthis.txt file (might be a good idea to zip it first).

That's how to do it, I might suggest reviewing the files, and only including the parts around the time you try to run gimp (or other programs).

---

### Post by LazyPony on 2010-01-16
Im trusting you now... dont let me down

---

### Post by nerdy_kid on 2010-01-16
> **LazyPony said:**
> Im trusting you now... dont let me down
im not going anywhere :D

---

### Post by LazyPony on 2010-01-16
Junap... i dont know what im looking for but this is what came 

Jan 16 17:30:36 agres-laptop kernel: [18394.254618] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:30:36 agres-laptop kernel: [18394.254622]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:30:36 agres-laptop kernel: [18394.254633] ata1.00: status: { DRDY ERR }
Jan 16 17:30:36 agres-laptop kernel: [18394.254641] ata1.00: error: { UNC }
Jan 16 17:30:37 agres-laptop kernel: [18394.452157] ata1.00: configured for UDMA/133
Jan 16 17:30:37 agres-laptop kernel: [18394.452193] ata1: EH complete
Jan 16 17:30:39 agres-laptop kernel: [18396.741868] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:30:39 agres-laptop kernel: [18396.741888] ata1.00: BMDMA stat 0x4
Jan 16 17:30:39 agres-laptop kernel: [18396.741920] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:30:39 agres-laptop kernel: [18396.741926]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:30:39 agres-laptop kernel: [18396.741940] ata1.00: status: { DRDY ERR }
Jan 16 17:30:39 agres-laptop kernel: [18396.741951] ata1.00: error: { UNC }
Jan 16 17:30:39 agres-laptop kernel: [18396.937171] ata1.00: configured for UDMA/133
Jan 16 17:30:39 agres-laptop kernel: [18396.937226] sd 0:0:0:0: [sda] Unhandled sense code
Jan 16 17:30:39 agres-laptop kernel: [18396.937242] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 16 17:30:39 agres-laptop kernel: [18396.937263] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jan 16 17:30:39 agres-laptop kernel: [18396.937290] Descriptor sense data with sense descriptors (in hex):
Jan 16 17:30:39 agres-laptop kernel: [18396.937305]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 16 17:30:39 agres-laptop kernel: [18396.937364]         00 99 39 22 
Jan 16 17:30:39 agres-laptop kernel: [18396.937390] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jan 16 17:30:39 agres-laptop kernel: [18396.937419] end_request: I/O error, dev sda, sector 10041634
Jan 16 17:30:39 agres-laptop kernel: [18396.937506] ata1: EH complete
Jan 16 17:32:32 agres-laptop acpid: client 6051[0:0] has disconnected
Jan 16 17:32:32 agres-laptop acpid: client connected from 10068[0:0]
Jan 16 17:32:39 agres-laptop acpid: client 10068[0:0] has disconnected
Jan 16 17:32:39 agres-laptop acpid: client connected from 9751[0:0]
Jan 16 17:32:48 agres-laptop kernel: [18526.349637] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:32:48 agres-laptop kernel: [18526.349660] ata1.00: BMDMA stat 0x4
Jan 16 17:32:48 agres-laptop kernel: [18526.349703] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:32:48 agres-laptop kernel: [18526.349712]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:32:48 agres-laptop kernel: [18526.349732] ata1.00: status: { DRDY ERR }
Jan 16 17:32:48 agres-laptop kernel: [18526.349747] ata1.00: error: { UNC }
Jan 16 17:32:49 agres-laptop kernel: [18526.585179] ata1.00: configured for UDMA/133
Jan 16 17:32:49 agres-laptop kernel: [18526.585233] ata1: EH complete
Jan 16 17:32:51 agres-laptop kernel: [18528.892436] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:32:51 agres-laptop kernel: [18528.892460] ata1.00: BMDMA stat 0x4
Jan 16 17:32:51 agres-laptop kernel: [18528.892502] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:32:51 agres-laptop kernel: [18528.892512]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:32:51 agres-laptop kernel: [18528.892532] ata1.00: status: { DRDY ERR }
Jan 16 17:32:51 agres-laptop kernel: [18528.892546] ata1.00: error: { UNC }
Jan 16 17:32:51 agres-laptop kernel: [18529.087114] ata1.00: configured for UDMA/133
Jan 16 17:32:51 agres-laptop kernel: [18529.087167] ata1: EH complete
Jan 16 17:32:53 agres-laptop kernel: [18531.380831] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:32:53 agres-laptop kernel: [18531.380855] ata1.00: BMDMA stat 0x4
Jan 16 17:32:53 agres-laptop kernel: [18531.380899] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:32:53 agres-laptop kernel: [18531.380909]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:32:53 agres-laptop kernel: [18531.380929] ata1.00: status: { DRDY ERR }
Jan 16 17:32:53 agres-laptop kernel: [18531.380944] ata1.00: error: { UNC }
Jan 16 17:32:54 agres-laptop kernel: [18531.574135] ata1.00: configured for UDMA/133
Jan 16 17:32:54 agres-laptop kernel: [18531.574182] ata1: EH complete
Jan 16 17:32:56 agres-laptop kernel: [18533.892096] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:32:56 agres-laptop kernel: [18533.892114] ata1.00: BMDMA stat 0x4
Jan 16 17:32:56 agres-laptop kernel: [18533.892148] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:32:56 agres-laptop kernel: [18533.892154]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:32:56 agres-laptop kernel: [18533.892168] ata1.00: status: { DRDY ERR }
Jan 16 17:32:56 agres-laptop kernel: [18533.892179] ata1.00: error: { UNC }
Jan 16 17:32:56 agres-laptop kernel: [18534.085061] ata1.00: configured for UDMA/133
Jan 16 17:32:56 agres-laptop kernel: [18534.085105] ata1: EH complete
Jan 16 17:32:58 agres-laptop kernel: [18536.398552] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:32:58 agres-laptop kernel: [18536.398569] ata1.00: BMDMA stat 0x4
Jan 16 17:32:58 agres-laptop kernel: [18536.398602] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:32:58 agres-laptop kernel: [18536.398609]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:32:58 agres-laptop kernel: [18536.398623] ata1.00: status: { DRDY ERR }
Jan 16 17:32:58 agres-laptop kernel: [18536.398634] ata1.00: error: { UNC }
Jan 16 17:32:59 agres-laptop kernel: [18536.581123] ata1.00: configured for UDMA/133
Jan 16 17:32:59 agres-laptop kernel: [18536.581180] ata1: EH complete
Jan 16 17:33:01 agres-laptop kernel: [18538.874676] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:33:01 agres-laptop kernel: [18538.874700] ata1.00: BMDMA stat 0x4
Jan 16 17:33:01 agres-laptop kernel: [18538.874743] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:33:01 agres-laptop kernel: [18538.874753]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:33:01 agres-laptop kernel: [18538.874774] ata1.00: status: { DRDY ERR }
Jan 16 17:33:01 agres-laptop kernel: [18538.874788] ata1.00: error: { UNC }
Jan 16 17:33:01 agres-laptop kernel: [18539.068994] ata1.00: configured for UDMA/133
Jan 16 17:33:01 agres-laptop kernel: [18539.069049] sd 0:0:0:0: [sda] Unhandled sense code
Jan 16 17:33:01 agres-laptop kernel: [18539.069064] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 16 17:33:01 agres-laptop kernel: [18539.069085] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jan 16 17:33:01 agres-laptop kernel: [18539.069112] Descriptor sense data with sense descriptors (in hex):
Jan 16 17:33:01 agres-laptop kernel: [18539.069126]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 16 17:33:01 agres-laptop kernel: [18539.069184]         00 98 b1 89 
Jan 16 17:33:01 agres-laptop kernel: [18539.069211] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jan 16 17:33:01 agres-laptop kernel: [18539.069242] end_request: I/O error, dev sda, sector 10006921
Jan 16 17:33:01 agres-laptop kernel: [18539.069315] ata1: EH complete
Jan 16 17:33:03 agres-laptop kernel: [18541.384258] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:33:03 agres-laptop kernel: [18541.384276] ata1.00: BMDMA stat 0x4
Jan 16 17:33:03 agres-laptop kernel: [18541.384308] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:33:03 agres-laptop kernel: [18541.384314]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:33:03 agres-laptop kernel: [18541.384328] ata1.00: status: { DRDY ERR }
Jan 16 17:33:03 agres-laptop kernel: [18541.384339] ata1.00: error: { UNC }
Jan 16 17:33:04 agres-laptop kernel: [18541.582147] ata1.00: configured for UDMA/133
Jan 16 17:33:04 agres-laptop kernel: [18541.582203] ata1: EH complete
Jan 16 17:33:06 agres-laptop kernel: [18543.905089] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:33:06 agres-laptop kernel: [18543.905107] ata1.00: BMDMA stat 0x4
Jan 16 17:33:06 agres-laptop kernel: [18543.905140] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:33:06 agres-laptop kernel: [18543.905147]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:33:06 agres-laptop kernel: [18543.905161] ata1.00: status: { DRDY ERR }
Jan 16 17:33:06 agres-laptop kernel: [18543.905171] ata1.00: error: { UNC }
Jan 16 17:33:06 agres-laptop kernel: [18544.132731] ata1.00: configured for UDMA/133
Jan 16 17:33:06 agres-laptop kernel: [18544.132785] ata1: EH complete
Jan 16 17:33:09 agres-laptop kernel: [18546.440112] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:33:09 agres-laptop kernel: [18546.440132] ata1.00: BMDMA stat 0x4
Jan 16 17:33:09 agres-laptop kernel: [18546.440165] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:33:09 agres-laptop kernel: [18546.440171]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:33:09 agres-laptop kernel: [18546.440185] ata1.00: status: { DRDY ERR }
Jan 16 17:33:09 agres-laptop kernel: [18546.440196] ata1.00: error: { UNC }
Jan 16 17:33:09 agres-laptop kernel: [18546.629020] ata1.00: configured for UDMA/133
Jan 16 17:33:09 agres-laptop kernel: [18546.629064] ata1: EH complete
Jan 16 17:33:11 agres-laptop kernel: [18548.912662] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:33:11 agres-laptop kernel: [18548.912681] ata1.00: BMDMA stat 0x4
Jan 16 17:33:11 agres-laptop kernel: [18548.912713] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:33:11 agres-laptop kernel: [18548.912720]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:33:11 agres-laptop kernel: [18548.912734] ata1.00: status: { DRDY ERR }
Jan 16 17:33:11 agres-laptop kernel: [18548.912745] ata1.00: error: { UNC }
Jan 16 17:33:11 agres-laptop kernel: [18549.109007] ata1.00: configured for UDMA/133
Jan 16 17:33:11 agres-laptop kernel: [18549.109051] ata1: EH complete
Jan 16 17:33:14 agres-laptop kernel: [18551.444703] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:33:14 agres-laptop kernel: [18551.444721] ata1.00: BMDMA stat 0x4
Jan 16 17:33:14 agres-laptop kernel: [18551.444754] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:33:14 agres-laptop kernel: [18551.444760]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:33:14 agres-laptop kernel: [18551.444774] ata1.00: status: { DRDY ERR }
Jan 16 17:33:14 agres-laptop kernel: [18551.444785] ata1.00: error: { UNC }
Jan 16 17:33:14 agres-laptop kernel: [18551.649409] ata1.00: configured for UDMA/133
Jan 16 17:33:14 agres-laptop kernel: [18551.649454] ata1: EH complete
Jan 16 17:33:16 agres-laptop kernel: [18553.943018] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:33:16 agres-laptop kernel: [18553.943036] ata1.00: BMDMA stat 0x4
Jan 16 17:33:16 agres-laptop kernel: [18553.943069] ata1.00: cmd c8/00:08:87:b1:98/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:33:16 agres-laptop kernel: [18553.943075]          res 51/40:00:89:b1:98/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:33:16 agres-laptop kernel: [18553.943089] ata1.00: status: { DRDY ERR }
Jan 16 17:33:16 agres-laptop kernel: [18553.943100] ata1.00: error: { UNC }
Jan 16 17:33:16 agres-laptop kernel: [18554.129034] ata1.00: configured for UDMA/133
Jan 16 17:33:16 agres-laptop kernel: [18554.129088] sd 0:0:0:0: [sda] Unhandled sense code
Jan 16 17:33:16 agres-laptop kernel: [18554.129104] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 16 17:33:16 agres-laptop kernel: [18554.129123] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jan 16 17:33:16 agres-laptop kernel: [18554.129143] Descriptor sense data with sense descriptors (in hex):
Jan 16 17:33:16 agres-laptop kernel: [18554.129153]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 16 17:33:16 agres-laptop kernel: [18554.129193]         00 98 b1 89 
Jan 16 17:33:16 agres-laptop kernel: [18554.129211] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jan 16 17:33:16 agres-laptop kernel: [18554.129232] end_request: I/O error, dev sda, sector 10006921
Jan 16 17:33:16 agres-laptop kernel: [18554.129298] ata1: EH complete
Jan 16 17:38:04 agres-laptop acpid: client 9751[0:0] has disconnected
Jan 16 17:38:04 agres-laptop acpid: client connected from 10068[0:0]
Jan 16 17:38:10 agres-laptop acpid: client 10068[0:0] has disconnected
Jan 16 17:38:10 agres-laptop acpid: client connected from 6051[0:0]
Jan 16 17:43:23 agres-laptop kernel: [19161.083563] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:43:23 agres-laptop kernel: [19161.083574] ata1.00: BMDMA stat 0x4
Jan 16 17:43:23 agres-laptop kernel: [19161.083591] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:43:23 agres-laptop kernel: [19161.083594]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:43:23 agres-laptop kernel: [19161.083601] ata1.00: status: { DRDY ERR }
Jan 16 17:43:23 agres-laptop kernel: [19161.083606] ata1.00: error: { UNC }
Jan 16 17:43:23 agres-laptop kernel: [19161.298872] ata1.00: configured for UDMA/133
Jan 16 17:43:23 agres-laptop kernel: [19161.298911] ata1: EH complete
Jan 16 17:43:26 agres-laptop kernel: [19163.592857] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:43:26 agres-laptop kernel: [19163.592875] ata1.00: BMDMA stat 0x4
Jan 16 17:43:26 agres-laptop kernel: [19163.592907] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:43:26 agres-laptop kernel: [19163.592914]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:43:26 agres-laptop kernel: [19163.592928] ata1.00: status: { DRDY ERR }
Jan 16 17:43:26 agres-laptop kernel: [19163.592938] ata1.00: error: { UNC }
Jan 16 17:43:26 agres-laptop kernel: [19163.788031] ata1.00: configured for UDMA/133
Jan 16 17:43:26 agres-laptop kernel: [19163.788084] ata1: EH complete
Jan 16 17:43:28 agres-laptop kernel: [19166.091152] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:43:28 agres-laptop kernel: [19166.091165] ata1.00: BMDMA stat 0x4
Jan 16 17:43:28 agres-laptop kernel: [19166.091188] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:43:28 agres-laptop kernel: [19166.091192]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:43:28 agres-laptop kernel: [19166.091202] ata1.00: status: { DRDY ERR }
Jan 16 17:43:28 agres-laptop kernel: [19166.091210] ata1.00: error: { UNC }
Jan 16 17:43:28 agres-laptop kernel: [19166.321885] ata1.00: configured for UDMA/133
Jan 16 17:43:28 agres-laptop kernel: [19166.321942] ata1: EH complete
Jan 16 17:43:31 agres-laptop kernel: [19168.622919] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:43:31 agres-laptop kernel: [19168.622938] ata1.00: BMDMA stat 0x4
Jan 16 17:43:31 agres-laptop kernel: [19168.622971] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:43:31 agres-laptop kernel: [19168.622977]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:43:31 agres-laptop kernel: [19168.623003] ata1.00: status: { DRDY ERR }
Jan 16 17:43:31 agres-laptop kernel: [19168.623014] ata1.00: error: { UNC }
Jan 16 17:43:31 agres-laptop kernel: [19168.805067] ata1.00: configured for UDMA/133
Jan 16 17:43:31 agres-laptop kernel: [19168.805111] ata1: EH complete
Jan 16 17:43:33 agres-laptop kernel: [19171.099233] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:43:33 agres-laptop kernel: [19171.099256] ata1.00: BMDMA stat 0x4
Jan 16 17:43:33 agres-laptop kernel: [19171.099298] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:43:33 agres-laptop kernel: [19171.099307]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:43:33 agres-laptop kernel: [19171.099327] ata1.00: status: { DRDY ERR }
Jan 16 17:43:33 agres-laptop kernel: [19171.099341] ata1.00: error: { UNC }
Jan 16 17:43:33 agres-laptop kernel: [19171.293118] ata1.00: configured for UDMA/133
Jan 16 17:43:33 agres-laptop kernel: [19171.293172] ata1: EH complete
Jan 16 17:43:36 agres-laptop kernel: [19173.609214] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:43:36 agres-laptop kernel: [19173.609238] ata1.00: BMDMA stat 0x4
Jan 16 17:43:36 agres-laptop kernel: [19173.609283] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:43:36 agres-laptop kernel: [19173.609292]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:43:36 agres-laptop kernel: [19173.609312] ata1.00: status: { DRDY ERR }
Jan 16 17:43:36 agres-laptop kernel: [19173.609328] ata1.00: error: { UNC }
Jan 16 17:43:36 agres-laptop kernel: [19173.801124] ata1.00: configured for UDMA/133
Jan 16 17:43:36 agres-laptop kernel: [19173.801180] sd 0:0:0:0: [sda] Unhandled sense code
Jan 16 17:43:36 agres-laptop kernel: [19173.801194] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 16 17:43:36 agres-laptop kernel: [19173.801214] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jan 16 17:43:36 agres-laptop kernel: [19173.801240] Descriptor sense data with sense descriptors (in hex):
Jan 16 17:43:36 agres-laptop kernel: [19173.801254]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 16 17:43:36 agres-laptop kernel: [19173.801389]         00 99 39 22 
Jan 16 17:43:36 agres-laptop kernel: [19173.801415] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jan 16 17:43:36 agres-laptop kernel: [19173.801444] end_request: I/O error, dev sda, sector 10041634
Jan 16 17:43:36 agres-laptop kernel: [19173.801515] ata1: EH complete
Jan 16 17:45:58 agres-laptop kernel: [19315.597804] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:45:58 agres-laptop kernel: [19315.597823] ata1.00: BMDMA stat 0x4
Jan 16 17:45:58 agres-laptop kernel: [19315.597855] ata1.00: cmd c8/00:f8:9f:38:99/00:00:00:00:00/e0 tag 0 dma 126976 in
Jan 16 17:45:58 agres-laptop kernel: [19315.597862]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:45:58 agres-laptop kernel: [19315.597876] ata1.00: status: { DRDY ERR }
Jan 16 17:45:58 agres-laptop kernel: [19315.597887] ata1.00: error: { UNC }
Jan 16 17:45:58 agres-laptop kernel: [19315.805166] ata1.00: configured for UDMA/133
Jan 16 17:45:58 agres-laptop kernel: [19315.805222] ata1: EH complete
Jan 16 17:46:00 agres-laptop kernel: [19318.098824] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:00 agres-laptop kernel: [19318.098838] ata1.00: BMDMA stat 0x4
Jan 16 17:46:00 agres-laptop kernel: [19318.098861] ata1.00: cmd c8/00:f8:9f:38:99/00:00:00:00:00/e0 tag 0 dma 126976 in
Jan 16 17:46:00 agres-laptop kernel: [19318.098865]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:00 agres-laptop kernel: [19318.098875] ata1.00: status: { DRDY ERR }
Jan 16 17:46:00 agres-laptop kernel: [19318.098882] ata1.00: error: { UNC }
Jan 16 17:46:00 agres-laptop kernel: [19318.277001] ata1.00: configured for UDMA/133
Jan 16 17:46:00 agres-laptop kernel: [19318.277047] ata1: EH complete
Jan 16 17:46:03 agres-laptop kernel: [19320.594459] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:03 agres-laptop kernel: [19320.594477] ata1.00: BMDMA stat 0x4
Jan 16 17:46:03 agres-laptop kernel: [19320.594510] ata1.00: cmd c8/00:f8:9f:38:99/00:00:00:00:00/e0 tag 0 dma 126976 in
Jan 16 17:46:03 agres-laptop kernel: [19320.594516]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:03 agres-laptop kernel: [19320.594530] ata1.00: status: { DRDY ERR }
Jan 16 17:46:03 agres-laptop kernel: [19320.594541] ata1.00: error: { UNC }
Jan 16 17:46:03 agres-laptop kernel: [19320.789916] ata1.00: configured for UDMA/133
Jan 16 17:46:03 agres-laptop kernel: [19320.789972] ata1: EH complete
Jan 16 17:46:05 agres-laptop kernel: [19323.103985] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:05 agres-laptop kernel: [19323.103999] ata1.00: BMDMA stat 0x4
Jan 16 17:46:05 agres-laptop kernel: [19323.104071] ata1.00: cmd c8/00:f8:9f:38:99/00:00:00:00:00/e0 tag 0 dma 126976 in
Jan 16 17:46:05 agres-laptop kernel: [19323.104076]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:05 agres-laptop kernel: [19323.104087] ata1.00: status: { DRDY ERR }
Jan 16 17:46:05 agres-laptop kernel: [19323.104095] ata1.00: error: { UNC }
Jan 16 17:46:05 agres-laptop kernel: [19323.324990] ata1.00: configured for UDMA/133
Jan 16 17:46:05 agres-laptop kernel: [19323.325025] ata1: EH complete
Jan 16 17:46:08 agres-laptop kernel: [19325.624630] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:08 agres-laptop kernel: [19325.624648] ata1.00: BMDMA stat 0x4
Jan 16 17:46:08 agres-laptop kernel: [19325.624681] ata1.00: cmd c8/00:f8:9f:38:99/00:00:00:00:00/e0 tag 0 dma 126976 in
Jan 16 17:46:08 agres-laptop kernel: [19325.624688]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:08 agres-laptop kernel: [19325.624711] ata1.00: status: { DRDY ERR }
Jan 16 17:46:08 agres-laptop kernel: [19325.624726] ata1.00: error: { UNC }
Jan 16 17:46:08 agres-laptop kernel: [19325.848956] ata1.00: configured for UDMA/133
Jan 16 17:46:08 agres-laptop kernel: [19325.848999] ata1: EH complete
Jan 16 17:46:10 agres-laptop kernel: [19328.134164] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:10 agres-laptop kernel: [19328.134183] ata1.00: BMDMA stat 0x4
Jan 16 17:46:10 agres-laptop kernel: [19328.134216] ata1.00: cmd c8/00:f8:9f:38:99/00:00:00:00:00/e0 tag 0 dma 126976 in
Jan 16 17:46:10 agres-laptop kernel: [19328.134222]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:10 agres-laptop kernel: [19328.134236] ata1.00: status: { DRDY ERR }
Jan 16 17:46:10 agres-laptop kernel: [19328.134247] ata1.00: error: { UNC }
Jan 16 17:46:10 agres-laptop kernel: [19328.329086] ata1.00: configured for UDMA/133
Jan 16 17:46:10 agres-laptop kernel: [19328.329137] sd 0:0:0:0: [sda] Unhandled sense code
Jan 16 17:46:10 agres-laptop kernel: [19328.329149] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 16 17:46:10 agres-laptop kernel: [19328.329163] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jan 16 17:46:10 agres-laptop kernel: [19328.329183] Descriptor sense data with sense descriptors (in hex):
Jan 16 17:46:10 agres-laptop kernel: [19328.329193]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 16 17:46:10 agres-laptop kernel: [19328.329233]         00 99 39 22 
Jan 16 17:46:10 agres-laptop kernel: [19328.329251] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jan 16 17:46:10 agres-laptop kernel: [19328.329272] end_request: I/O error, dev sda, sector 10041634
Jan 16 17:46:10 agres-laptop kernel: [19328.329365] ata1: EH complete
Jan 16 17:46:13 agres-laptop kernel: [19330.665407] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:13 agres-laptop kernel: [19330.665426] ata1.00: BMDMA stat 0x4
Jan 16 17:46:13 agres-laptop kernel: [19330.665459] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:46:13 agres-laptop kernel: [19330.665465]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:13 agres-laptop kernel: [19330.665479] ata1.00: status: { DRDY ERR }
Jan 16 17:46:13 agres-laptop kernel: [19330.665490] ata1.00: error: { UNC }
Jan 16 17:46:13 agres-laptop kernel: [19331.024967] ata1.00: configured for UDMA/133
Jan 16 17:46:13 agres-laptop kernel: [19331.025019] ata1: EH complete
Jan 16 17:46:15 agres-laptop kernel: [19333.308175] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:15 agres-laptop kernel: [19333.308195] ata1.00: BMDMA stat 0x4
Jan 16 17:46:15 agres-laptop kernel: [19333.308228] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:46:15 agres-laptop kernel: [19333.308234]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:15 agres-laptop kernel: [19333.308248] ata1.00: status: { DRDY ERR }
Jan 16 17:46:15 agres-laptop kernel: [19333.308259] ata1.00: error: { UNC }
Jan 16 17:46:16 agres-laptop kernel: [19333.500985] ata1.00: configured for UDMA/133
Jan 16 17:46:16 agres-laptop kernel: [19333.501041] ata1: EH complete
Jan 16 17:46:18 agres-laptop kernel: [19335.795574] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:18 agres-laptop kernel: [19335.795592] ata1.00: BMDMA stat 0x4
Jan 16 17:46:18 agres-laptop kernel: [19335.795625] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:46:18 agres-laptop kernel: [19335.795632]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:18 agres-laptop kernel: [19335.795646] ata1.00: status: { DRDY ERR }
Jan 16 17:46:18 agres-laptop kernel: [19335.795657] ata1.00: error: { UNC }
Jan 16 17:46:18 agres-laptop kernel: [19335.976978] ata1.00: configured for UDMA/133
Jan 16 17:46:18 agres-laptop kernel: [19335.977031] ata1: EH complete
Jan 16 17:46:20 agres-laptop kernel: [19338.282839] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:20 agres-laptop kernel: [19338.282858] ata1.00: BMDMA stat 0x4
Jan 16 17:46:20 agres-laptop kernel: [19338.282891] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:46:20 agres-laptop kernel: [19338.282897]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:20 agres-laptop kernel: [19338.282911] ata1.00: status: { DRDY ERR }
Jan 16 17:46:20 agres-laptop kernel: [19338.282922] ata1.00: error: { UNC }
Jan 16 17:46:21 agres-laptop kernel: [19338.464967] ata1.00: configured for UDMA/133
Jan 16 17:46:21 agres-laptop kernel: [19338.465021] ata1: EH complete
Jan 16 17:46:23 agres-laptop kernel: [19340.792430] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:23 agres-laptop kernel: [19340.792449] ata1.00: BMDMA stat 0x4
Jan 16 17:46:23 agres-laptop kernel: [19340.792482] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:46:23 agres-laptop kernel: [19340.792489]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:23 agres-laptop kernel: [19340.792503] ata1.00: status: { DRDY ERR }
Jan 16 17:46:23 agres-laptop kernel: [19340.792513] ata1.00: error: { UNC }
Jan 16 17:46:23 agres-laptop kernel: [19340.984971] ata1.00: configured for UDMA/133
Jan 16 17:46:23 agres-laptop kernel: [19340.985024] ata1: EH complete
Jan 16 17:46:25 agres-laptop kernel: [19343.290855] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 16 17:46:25 agres-laptop kernel: [19343.290874] ata1.00: BMDMA stat 0x4
Jan 16 17:46:25 agres-laptop kernel: [19343.290907] ata1.00: cmd c8/00:08:1f:39:99/00:00:00:00:00/e0 tag 0 dma 4096 in
Jan 16 17:46:25 agres-laptop kernel: [19343.290914]          res 51/40:00:22:39:99/00:00:00:00:00/00 Emask 0x9 (media error)
Jan 16 17:46:25 agres-laptop kernel: [19343.290928] ata1.00: status: { DRDY ERR }
Jan 16 17:46:25 agres-laptop kernel: [19343.290938] ata1.00: error: { UNC }
Jan 16 17:46:26 agres-laptop kernel: [19343.472987] ata1.00: configured for UDMA/133
Jan 16 17:46:26 agres-laptop kernel: [19343.473046] sd 0:0:0:0: [sda] Unhandled sense code
Jan 16 17:46:26 agres-laptop kernel: [19343.473062] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 16 17:46:26 agres-laptop kernel: [19343.473083] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jan 16 17:46:26 agres-laptop kernel: [19343.473108] Descriptor sense data with sense descriptors (in hex):
Jan 16 17:46:26 agres-laptop kernel: [19343.473120]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 16 17:46:26 agres-laptop kernel: [19343.473160]         00 99 39 22 
Jan 16 17:46:26 agres-laptop kernel: [19343.473178] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jan 16 17:46:26 agres-laptop kernel: [19343.473199] end_request: I/O error, dev sda, sector 10041634
Jan 16 17:46:26 agres-laptop kernel: [19343.473276] ata1: EH complete
joe@agres-laptop:~$

---

### Post by LazyPony on 2010-01-16
*im not going anywhere*


joe@agres-laptop:~$ sudo apt-get purge xulrunner
[sudo] password for joe: 
Sorry, try again.
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xulrunner
joe@agres-laptop:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joe@agres-laptop:~$

---

### Post by nerdy_kid on 2010-01-16
sorry, on karmic its xulrunner-1.9.1
just type xulrunner then hit tab.  as i said, that will take out a bunch of stuff and might not work....

---

### Post by LazyPony on 2010-01-16
I have Karmic?

---

### Post by LazyPony on 2010-01-16
joe@agres-laptop:~$ xulrunner
Mozilla XULRunner 1.9.1.7

Usage: xulrunner [OPTIONS]
       xulrunner APP-FILE [APP-OPTIONS...]

OPTIONS
      --app                  specify APP-FILE (optional)
  -h, --help                 show this message
  -v, --version              show version
  --gre-version              print the GRE version string on stdout
  --register-global          register this GRE in the machine registry
  --register-user            register this GRE in the user registry
  --unregister-global        unregister this GRE formerly registered with
                             --register-global
  --unregister-user          unregister this GRE formely registered with
                             --register-user
  --find-gre <version>       Find a GRE with version <version> and print
                             the path on stdout
  --install-app <application> [<destination> [<directoryname>]]
                             Install a XUL application.

APP-FILE
  Application initialization file.

APP-OPTIONS
  Application specific options.
joe@agres-laptop:~$

---

### Post by junapp on 2010-01-16
I'm not qualified for this, but I'd say your harddrive may be having issues - bit of a guess there based on the repeating DRDY ERR status. Is it a newer machine?

[http://ubuntuforums.org/showthread.php?t=937872](http://ubuntuforums.org/showthread.php?t=937872)

---

### Post by LazyPony on 2010-01-16
Acer Aspire One
i dont really know if its new or not actualy, but Gimp was working fine not to long ago.

---

### Post by LazyPony on 2010-01-16
Along with that some of my downloads say somthing about dependency problems? well actualy almot all of them do.

---

### Post by nerdy_kid on 2010-01-16
```

sudo apt-get purge xulrunner-1.9.1
sudo apt-get install ubuntu-desktop

```you may want to consider a reinstall of ubuntu if you dont have any data on your machine.

@junapp
is there any way to test the possibility of a failing HD more?  I really have no clue how to....and itd be stupid to have her waste hours on an issue that cant be fixed....

---

### Post by LazyPony on 2010-01-16
ok um... fire fox is my main browser... is this safe?? :[

joe@agres-laptop:~$ sudo apt-get purge xulrunner-1.9.1
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  couchdb-bin* desktopcouch* evolution-couchdb* evolution-documentation-en*
  firefox* firefox-3.5* firefox-3.5-branding* firefox-3.5-gnome-support*
  firefox-gnome-support* gnome-user-guide* python-desktopcouch*
  python-desktopcouch-records* ubufox* ubuntu-desktop* ubuntu-docs*
  xulrunner-1.9.1* xulrunner-1.9.1-gnome-support* yelp*
0 upgraded, 0 newly installed, 18 to remove and 0 not upgraded.
After this operation, 298MB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by LazyPony on 2010-01-16
[I]and itd be stupid to have _[COLOR=Black]him[/COLOR]_ waste hours on an issue that cant be fixed...
[/I]happens to be a her

---

### Post by LazyPony on 2010-01-16
aaand....... i had sent my Note book out to get fixed up. and thats how i got ubuntu, but ive read around that i need a disk to reinstall?

---

### Post by nerdy_kid on 2010-01-16
> **LazyPony said:**
> [I]and itd be stupid to have _[COLOR=Black]him[/COLOR]_ waste hours on an issue that cant be fixed...
[/I]happens to be a her
ooooops
sorry :S
[edit] fixed my post :D
lol






the next command i gave u after removing xulrunner should reinstall all the apps that were deleted.

---

### Post by LazyPony on 2010-01-16
ok.......
im sooooooooooo counting on you

---

### Post by nerdy_kid on 2010-01-16
:rolleyes:> **LazyPony said:**
> ok.......
im sooooooooooo counting on you
lol i feel scared
be back tomorrow, gtg to get some sleep now.
if what i suggested still doesnt work, try googling "bus error karmic" or something like that and fish around a bit :rolleyes:

---

### Post by LazyPony on 2010-01-16
Rawr... Guess it worked :D
what does this mean?
The wicd daemon has shut down. The UI will not function properly until it is restarted.

---

### Post by nerdy_kid on 2010-01-16
where is that error comming from?
did you execute both commands?
might have 15min on IRC if you can...

---

### Post by LazyPony on 2010-01-16
IRC?

anyway it was a pop up after i did the second command. but about 2 months ago i had gotten wicd and now i have the other "default" one... gnome network manager.

---

### Post by nerdy_kid on 2010-01-16
Internet Relay Chat -- live forum :)

sooo is everything working now?

a restart should help that error also
i gtg get some sleep. be back tomorrow.

---

### Post by LazyPony on 2010-01-16
alright. thx for the help but gimp still isnt working >:[ maybe tomorrow if we talk agn  u can show me this IRC?

---

