---
title: "Various System Applications crash upon start"
date: 2012-03-31
forum: General Help
---

### Post by ludi567 on 2012-03-31
Hi All,

I have several problems:
Ubuntu Software Centre, Update Manager and Synaptic Package Manager all crash a few seconds after starting each of them.

Does anyone have any idea where this could originate from? All the fixes I tried require at least one of them to work so I am really stuck. Not sure what else doesn't work.

I am running 10.04.

Thanks a lot in advance.

---

### Post by dino99 on 2012-03-31
Proposing some cleanings: into a terminal, run each command one by one (copy/paste it to avoid error)
note: close all the opened apps first 

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo rm -rf .local

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

sudo reboot

---

### Post by ludi567 on 2012-03-31
I tried that, it crashes every time at the line:
Building dependency tree... 0%

Which then changes to:
Bus errordependency tree... 0%

The same thing happens also when I try to install programs (e.g. Wine) without using the Software Centre.

---

### Post by 2F4U on 2012-03-31
Can you provide the error messages?

---

### Post by ludi567 on 2012-03-31
Sure. Do you mind telling me though where I find the error message? Thanks.

---

### Post by ludi567 on 2012-04-03
This is what comes up in the System Log Viewer if that is what you meant (if not please tell me where I find the appropriate error messages). Would really appreciate it if someone could help me with this. Have reached a bit of a dead end. Thanks a lot in advance.

Apr  3 14:03:18 ludwig-desktop kernel: [  954.060369] ata3: EH complete
Apr  3 14:03:20 ludwig-desktop kernel: [  955.964860] ata3.00: configured for UDMA/133
Apr  3 14:03:20 ludwig-desktop kernel: [  955.964870] ata3: EH complete
Apr  3 14:03:21 ludwig-desktop kernel: [  957.872855] ata3.00: configured for UDMA/133
Apr  3 14:03:21 ludwig-desktop kernel: [  957.872867] ata3: EH complete
Apr  3 14:03:23 ludwig-desktop kernel: [  959.728361] ata3.00: configured for UDMA/133
Apr  3 14:03:23 ludwig-desktop kernel: [  959.728371] ata3: EH complete
Apr  3 14:03:25 ludwig-desktop kernel: [  961.588358] ata3.00: configured for UDMA/133
Apr  3 14:03:25 ludwig-desktop kernel: [  961.588370] ata3: EH complete
Apr  3 14:03:27 ludwig-desktop kernel: [  963.496848] ata3.00: configured for UDMA/133
Apr  3 14:03:27 ludwig-desktop kernel: [  963.496863] sd 2:0:0:0: [sdb] Unhandled sense code
Apr  3 14:03:27 ludwig-desktop kernel: [  963.496866] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr  3 14:03:27 ludwig-desktop kernel: [  963.496871] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Apr  3 14:03:27 ludwig-desktop kernel: [  963.496877] Descriptor sense data with sense descriptors (in hex):
Apr  3 14:03:27 ludwig-desktop kernel: [  963.496880]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Apr  3 14:03:27 ludwig-desktop kernel: [  963.496894]         0c eb 41 b7 
Apr  3 14:03:27 ludwig-desktop kernel: [  963.496900] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Apr  3 14:03:27 ludwig-desktop kernel: [  963.496908] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 0c eb 41 b0 00 00 08 00
Apr  3 14:03:27 ludwig-desktop kernel: [  963.496945] ata3: EH complete

---

### Post by ludi567 on 2012-04-03
Seems like a simple sudo apt-get update solved this problem. Went through the list of commands above as well afterwards and all seems well so far.

See also: [http://ubuntuforums.org/showthread.php?t=1578992](http://ubuntuforums.org/showthread.php?t=1578992)

---

