---
title: "what does it mean for a processor to be a n-bit, n = {4, 8, 16, 32, 64}"
date: 2010-04-05
forum: General Help
---

### Post by cybo on 2010-04-05
i have really never thought of this question before up until i was asked by my friend what does it mean for a processor to be 64 bit as opposed to 32 bit? how is it better? sadly for me i wasn't able to answer it. i did a little of googling (i must admit i didn't have much time) and wasn't able to find an answer. can anyone explain what does it mean for a processor to be n-bit, where n = {4, 8, 16, 32, 64}. aside from knowing that i can operate on larger data values on a 64 bit processor rather than on a 32 bit one, i know nothing more.

any help is appreciated.

---

### Post by quadproc on 2010-04-05
> **cybo said:**
> i have really never thought of this question before up until i was asked by my friend what does it mean for a processor to be 64 bit as opposed to 32 bit? how is it better?
Your question would justify a book or a doctoral dissertation, but I'll just suggest a few things about the bus size issue.  I will avoid discussing some of the subtleties of some computer architectures in the interest of simplicity.

Computers have been built with many different bus widths (number of bits).  I personally have used ones that were 8, 12, 16, 18, 24, 32, 48, and 64 bits.  The first microprocessor was the Intel 4004 which was 4 bits wide; it was originally intended for desk calculator applications.  Today's general purpose microprocessors are usually 64 bits wide.

There is also a very large market for small microprocessors such as those used in appliances, industrial controllers, burglar alarms, and other dedicated applications.  These are mostly 8 bit processors.

Data is usually addressed in chunks of 8 bits called bytes.  The processor combines together several bytes to make a word, and the word size is the bus width.  Thus, a 32 bit processor uses groups of 4 bytes to make words while a 64 bit processor uses groups of 8 bytes. 

Processors contain instructions which operate on words or bytes, and sometimes on other subdivisions of the word size.  Also, some processors are able to operate on arbitrary portions of words, even as little as 1 bit at a time.  But generally, data is moved around and operated on in units of words.  Therefore, a word which is twice as wide will cause twice as much to be done in a single unit of time.

Another consideration relates to accuracy, precision, or resolution.  Floating point numbers such as 17.14 generally cannot be expressed exactly inside of a computer; instead, they are very closely approximated.  A 32 bit word can hold about 6 meaningful digits of a decimal number; a 64 bit word holds lots more depending on how much of the word is allocated for the exponent.  Often a floating point number is represented by a 10 byte long value; note that this does not fit into either 32 or 64 bit words so multiple words have to be used to store such a value.  The 10 byte long value had its roots in Intel's separate floating point processors such as the 387.

Computers do not necessarily use the same bus width for data and addresses.  For example, the 8080 used 8 bit data and had a 16 bit address width.  Today's 64 bit processors are designed around 64 bit data and address sizes although some of the address pins are omitted from most designs because 40 bits is enough to address about a terabyte and nobody is running that much RAM these days.  But notice that today's hard disks are now available in sizes bigger than 1 terabyte so you need more than 40 bits to specify a particular byte on a disk; that number cannot fit into a 32 bit word so the 64 bit system has a substantial advantage in the case of large disks.

I do know of one drawback to 64 bit data bus widths: pointers.  A pointer needs to be able to point to anyplace in the address space so it must be 64 bits wide in a 64 bit system.  That 64 bits requires 8 bytes to store in memory, while a 32 bit system only requires 4 bytes of storage for one pointer.  I do not think that this is a big issue because it doesn't much increase the amount of memory needed by most programs.

So, in a very few words, the 64 bit system runs faster, provides greater precision, and allows the use of more than 4 gigabytes of RAM.

quadproc

---

### Post by Penguin Guy on 2010-04-05
I've used both 32-bit and 64-bit, I can see no difference whatsoever.

---

### Post by cybo on 2010-04-05
thank you everyone, espcially quadproc. it was a very in-depth answer. i really appreciate it.

---

### Post by x C0MMAND0 x on 2010-04-05
The non-technical answer that affects most users is that 32bit OS can only use 3.2gb of Ram whereas a 64bit OS can use much more (not sure the limits).  In terms of speed and program use, I have never personally noticed a difference although 64bit has much more potential.

---

### Post by dcstar on 2010-04-06
> **x C0MMAND0 x said:**
> The non-technical answer that affects most users is that 32bit OS can only use 3.2gb of Ram whereas a 64bit OS can use much more (not sure the limits).  In terms of speed and program use, I have never personally noticed a difference although 64bit has much more potential.

32-bit OSs **can** use more than 4GB RAM using PAE mode, but the maximum a 32-bit process can address (use) is still 4GB. PAE means that different 32-bit processes can use different 32-bit "chunks" of available RAM - but it becomes inefficient as the total RAM size increases.

For most users there is little tangible difference in using 32-bit or 64-bit, but as more and more systems use more than 4GB of RAM the difference in performance will be greater.

---

### Post by ubun2warrior on 2010-04-06
I have a 64 bit amd athlon and i have tried ubuntu 32-bit and 64-bit on my pc. but i noticed no difference infact the 64-bit ubuntu was not a good experience at all. the cursor would freeze very often in the 64-bit. i expected that the operation speed would get very enhanced and the user experience would also be enhanced in the 64-bit ubuntu but on the contrary it was the other way  around. 
Looking forward for some intelligent explanation from all..
A special mention for Quadproc for giving us such detailed answer.

---

### Post by cybo on 2010-04-07
@everyone thanks everybody. it did help. now i can "look smart" and say "smart" things when asked about 32-bit vs 64-bit.

---

### Post by Directive 4 on 2010-04-07
64bit is maybe 30% faster for some tasks,

ie' video transcoding

---

