---
title: "swap or swap file on flash memory?"
date: 2010-08-16
forum: General Help
---

### Post by wayover13 on 2010-08-16
Hi. RAM for older machines like I use is fairly cheap these days. But flash memory is just as cheap or cheaper. So I'd like to ask about the feasibility of expanding my system's memory using flash memory. And about whether creating a partition for swap on the flash memory, or whether a swap file on the flash device, is the better way to go.

By flash memory I have in mind mainly USB sticks or what are sometimes called "pen drives." But I do also have CF and SD cards that, with the proper cheap adapter (one of which I already own for adapting CF) could be used to create extra swap space.

So, what is the current consensus on the feasibility/advisability of using flash memory for swap? I've read about the limited write cycles of flash being an argument against using it for swap. But recent reading indicates to me that the limited write cycles problem applies mostly to older, smaller-capacity flash memory. Some will come out and say that, for larger-capacity flash memory, the life of the device is likely to exceed the amount of time your current computer will be useful (I think I've seen estimates in the range of 3-4 years life--minimum--for newer, higher-capacity flash memory).

A more persuasive argument I've heard against using flash memory for swap is that access times for these devices can be much slower than SATA, and maybe even IDE, hard drives. That would certainly dictate against using flash memory for swap.

So, how about some input on this issue? Anyone using flash memory for swap? If so, what kind (e.g., usb stick or SD/CF)? Are you using a swap file or a swap partition? How's system performance?

Likewise, has anyone had flash-memory-used-as-swap die on them? The consequences would undoubtedly be dire. Also, has anyone measured flash memory access times to confirm or refute claims about slow access times? Are some types of flash memory better/worse than others in terms of access times?

Input will be appreciated.

Thanks,
James

---

### Post by wayover13 on 2010-08-16
deleted

---

### Post by kerry_s on 2010-08-16
yes, you can put your swap where ever you want.

i used a usb as swap for several years on a old laptop system, i made it all swap. the laptop was so old it was not worth getting a new drive for, the os was loaded from cd to ram, i used dsl linux back then.

ps: now a days i use dynamic swap, which is a swap file created when needed, deleted when no longer needed. i use "swapspace" in the repo, but there are several you can choose from.

---

