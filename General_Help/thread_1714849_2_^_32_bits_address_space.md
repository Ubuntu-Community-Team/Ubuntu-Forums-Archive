---
title: "2 ^ 32 bits address space"
date: 2011-03-25
forum: General Help
---

### Post by newbuntuxx on 2011-03-25
Hello all,

I spent the last few hours researching the issue of 32 bit CPU architecture and their support for RAM.

I discovered that a 32 bit CPU can support a maximum of 4 GB. This is because the size of the CPU register is only 32 bits. So, (2 ^ 32)/(1024*1024) = 4 GB. Therefore, the CPU can only process 32 bits of information at once. Since that is the case, any memory address larger than 32 bits is not visible to the 32 bit CPU because the 32 bit CPU can not possibly see anything larger than 32 bits. 

To get around that limitation, PAE (physical address extension) was introduced. This kernel option can take advantage of RAM greater than 4 GB even though the 32 bit CPU can not see it. This is done using virtual/logical addresses. Slightly similar to the way swap works. The translation from virtual/logical address to real physical addresses is done by the kernel. The processes/applications running can not see any address space larger than 32 bit. 

This was all fine and dandy until I thought twice about this calculation:
(2 ^ 32)/(1024*1024) = 4 GB

Obviously that can not be right!

It has to be: 4 Gigabits (Gb), not bytes. Because the original value is in bits and it was never converted to bytes:
2 ^ 32 bits = 4294967296 bits
4294967296 bits / 1024 = 4194304 Kilobits
4194304 Kilobits / 1024 = 4096 Megabits
4096 Megabits / 1024 = 4 Gigabits

This means that the 32 bit CPU can see a maximum of 512 Megabytes of RAM (4096 Megabits / 8)! 


Obviously I am missing something here. Where does that 8 multiplier come from? 

Please enlighten me.

Thanks,

---

### Post by asmoore82 on 2011-03-25
You are being *too* logical :P.

The purpose of addressing is to simplify data access and use a smaller object —
the address — to "point to" a much larger object — the actual data in RAM.
Each *bit* of the CPU represents a *byte* address in RAM.

There are 8 bits in a byte so there is your 8x multiplier!

Here's how a 2-bit CPU could address a full 4 bytes (32 bits) of RAM:
```
CPU   RAM    RAM in hex
---  ------   --------
 00 01111111     7f
 01 00011111     1f
 10 01101111     6f
 11 10001111     8f
```
^So the 2-bit Address 10 references the full byte of data 6f.

---

### Post by Bitrate on 2011-03-26
PAE utilizes 36-bit addressing which equates to a maximum of 64GB of addressable memory.

---

### Post by newbuntuxx on 2011-03-26
> Each bit of the CPU represents a byte address in RAM.


So the size of the smallest piece of data that a process can write to memory is 1 byte and not a bit less? 


I thought that the 8 came from the 8 registers that an x86 CPU. (8 registers each 32 bits big)

It would be great If you can elaborate further or perhaps direct me to some reading material about this topic.

---

### Post by dcstar on 2011-03-26
> **newbuntuxx said:**
> 
I thought that the 8 came from the 8 registers that an x86 CPU. (8 registers each 32 bits big)


A "Byte" originally referred to the data bus width of a particular computer architecture. Different architectures of computers used many different "Byte" definitions early on in the development of computers.

When the first microprocessors were introduced they had 8-bit data structures, so that is where the current commonly used definition of a "Byte" evolved from.

8-bit data was very convenient as a single ASCII character was also 8-bits, and as data bus widths expanded to 16, 32 and 64 bits then multiples of 8-bit "Bytes" would fit neatly into them with no wastage.

---

### Post by 3rdalbum on 2011-03-26
> **newbuntuxx said:**
> So the size of the smallest piece of data that a process can write to memory is 1 byte and not a bit less?

That wouldn't surprise me - after all, what program would really want to write bits directly? That's like writing a fraction of a character in a text file. The programs I've written have always written bytes, and I've never wanted to write individual bits.

---

### Post by mcduck on 2011-03-26
> **3rdalbum said:**
> That wouldn't surprise me - after all, what program would really want to write bits directly? That's like writing a fraction of a character in a text file. The programs I've written have always written bytes, and I've never wanted to write individual bits.

well, changing a single bit can serve many purposes. If you just need to store a yes/no answer, then a single bit is enough...  ;)

Check "flag bit" and "bit field", for example.

Of course the concept works just fine even when reading/writing full bytes instead of individual bits. You still get 1/8th of the memory usage compared to storing such values as numbers, for example, and you can fit 8 different flags in a single CPU register or memory address.

---

### Post by newbuntuxx on 2011-03-26
Thanks for the replies guys.

I take it then that any information written to memory in a 32 bit CPU has to be padded to either 8 bits or 16 bits or 32 bits, depending on the size of the data?

Also, do you guys have any recommended books/reading material that I can read to learn more about this stuff?

Thanks,

---

