---
title: "Hotmail reading hard drive"
date: 2010-10-19
forum: General Help
---

### Post by cyrex on 2010-10-19
This ONLY happen when i open my hotmail or any other hotmail website. Tried on Ubuntu 10.04 and 10.10. This is what happens:

1. Open Pidgin, Emesene, aMSN or Empathy.
2. Recieve the update that "You got mail"
3. Go to the hotmail website and log in
4. The hard drive will start reading/writing something.

The sound that comes from the hard drive (Am talking about new 1TB hard drives, less than 30 days of use) is like it is copying reading/writing something every 1 or 2 seconds.

This was tested with 2 laptops and 2 PCs. Different hard drives. In one PC i tested 3 differente hard drives with same result. 

In the moment you open the hotmail account it starts reading/writing something somewhere. It only happens with hotmail, tested with yahoo and gmail. Both did not make the PC slower. Only hotmail did. Now here comes to funny part. Tested same PCs and 1 laptop with Windows XP. Guess what, it did not make any sounds with the hard drive.

I then went and tested Debian, Linux Mint and last OpenSuse. Same result. In all tests, Hotmail made the hard drive start reading/writing something every 1 or 2 seconds.

With a big WTF i ask How can i check whatever is happening when i open the hotmail.

NOTE: 5 Hotmail accounts were used to test in all hardwares. So i think it was very well tested.

---

### Post by Barriehie on 2010-10-19
Is this happening with or without javascript enabled?

---

### Post by ean5533 on 2010-10-19
My only guess: Hotmail is writing and reading cookies. A lot of cookies. Unfortunately I don't know of a good way to verify that.

---

### Post by iponeverything on 2010-10-19
```
lsof -p <pid> |grep REG 
```

Where <pid> is the pid of your browser process.

This will show all file handles.

---

### Post by cyrex on 2010-10-21
I disabled javascript and the problem went away. After activating it again since without it hotmail does not work, the problem started. I also did the lsof line and it showed about 50 opened files related to firefox in this case. Tested again with gmail and yahoo. All is ok. It is hotmail that sucks the life out of the PC.

---

