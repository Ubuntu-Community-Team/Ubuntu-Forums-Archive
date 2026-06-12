---
title: "Use raid volume from windows and ubuntu"
date: 2010-04-25
forum: General Help
---

### Post by niiklas on 2010-04-25
I currently have a raid setup of 2 1tb hdd's that i can use from my windows install, but in ubuntu i cannot find it.

Is it possible to reach a raid volume from both os?

---

### Post by P4man on 2010-04-25
When you say raid, do you mean a bios (fake) raid? Or a hardware raid (with a real raid controller card) or a software raid (one you set up in windows) ?

---

### Post by niiklas on 2010-04-25
> **P4man said:**
> When you say raid, do you mean a bios (fake) raid? Or a hardware raid (with a real raid controller card) or a software raid (one you set up in windows) ?


That would be a bios fake then, set it up in my bios..

---

### Post by P4man on 2010-04-25
No you cant see it or use it linux. Bios fake raid is not much more than a windows driver in bios; its  a workaround to allow windows to boot from a (non-hardware) raid, since windows itself can not do that.

Linux doesnt use it, doesnt need it, because unlike windows, it can boot itself from a software raid using dm-raid. Im not aware of a way to mount a windows (software) raid in linux, but I could be wrong.

---

### Post by jack_hmr on 2010-04-25
Ubuntu can sometimes use fakeraid [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")
More info can be found by searching the forums for fakeraid howto and Google for Ubuntu fakeraid howto.

As far as I know fakeraid or hardware raid is the only way to dual boot Windows and share raid.

However keep in mind that if your motherboard goes out (with fakeraid) you basically have to get an exact replacement in order to recover your data. So in the long term I recommend finding another solution unless you are using raid 0 and don't care about losing the data.

---

### Post by niiklas on 2010-04-25
is it possible to mount a LINUX software raid from windows? or vice versa

---

### Post by P4man on 2010-04-25
I dont know the answer to that. Mounting a linux raid in windows I think is out of the question, even regular Ext3/4 is problematic. The other way around.. it might be possible to mount windows dynamic disk soft raid, but I dont know for sure, let alone how.

However, regardless of windows/linux interoperability, I would strongly encourage you to think twice before using a bios fakeraid. BIOS raid is primarily a marketing gimmick. It offers no speed improvements over windows own soft raid, quite often its the exact opposite with the bios raid being considerably slower; in some cases even slower than no raid at all.

The very best case is intel matrix raid where the southbridge  chipset has some functionality to offload cpu load, and there is no additional latency to an offchip sata raid controller, and even it that case there is no gain over windows dynamic disks:
[http://kmwoley.com/blog/?p=429](http://kmwoley.com/blog/?p=429)

So its not faster, its usually slower and on top of that its definitely less secure and much less flexible. You add a point of failure (the bios and the driver). Windows' dynamic disks have been thoroughly tested and Im sure are fairly bug free. Would you bet money on the same stability and reliability from a no name motherboard vendor? If your motherboard dies, you can not rebuild a bios raid on a different board, it is tied to it. Even s small revision of the motherboard or its bios will break the raid and render it utterly unreadable. Even if you flash your bios, you risk losing the raid. 

I could go on.

The bottom line is this; in the vast majority of cases for windows, you are better off installing windows on a small, non raided partition and set up a software raid (using dynamic disks) for your documents, programs and swap.

---

### Post by niiklas on 2010-04-25
Thanks for your answers.

---

