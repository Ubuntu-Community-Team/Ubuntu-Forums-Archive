---
title: "so, Windows and linux, cross contamination"
date: 2011-06-24
forum: General Help
---

### Post by F.G. on 2011-06-24
hey folks,
i'm wondering if anyone knows about security regarding windows accessing a linux partition.  basically my brother borrowed my laptop and used the windows partition(by that i mean used windos, i dual boot).  I wonder if a program in Windows can access the bits of memory used by ubuntu. I know that programs in linux will give a seg-fault if they go out of their allocated space, though progs in windows (depending on the version) can go out of their allocated space.

does anyone know if using pointers, in c or c++, in a windows partition can go outside of the ntfs partition, into ext2,3,4...?? ie. can a process in Windows access your linux partition, and alter the contents.  as far as i'm aware, yes it can.
f.g.

---

### Post by haqking on 2011-06-24
> **F.G. said:**
> hey folks,
i'm wondering if anyone knows about security regarding windows accessing a linux partition.  basically my brother borrowed my laptop and used the windows partition(by that i mean used windos, i dual boot).  I wonder if a program in Windows can access the bits of memory used by ubuntu. I know that programs in linux will give a seg-fault if they go out of their allocated space, though progs in windows (depending on the version) can go out of their allocated space.

does anyone know if using pointers, in c or c++, in a windows partition can go outside of the ntfs partition, into ext2,3,4...?? ie. can a process in Windows access your linux partition, and alter the contents.  as far as i'm aware, yes it can.
f.g.

not accidentally

with intent yes.

explore2FS springs to mind amongst many others

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) one of many ways to access it

---

### Post by snowpine on 2011-06-24
Anyone with physical access to your computer has full access to all non-encrypted data. (i.e. "yes")

---

### Post by F.G. on 2011-06-24
presumably if it can be done by intent, then it can also be done by accident.  leaving a for loop, with a c style pointer, (or c++) incrementing is not so difficult.  however my concern is malicious programs.  if I run a windows, with a dual boot, with a super malicious virus...  this is my concern.  (what happens if you try to access non-existent memory in windows? as this is precisely the how this would occur, and because that is how this could be an issue).  ??
any thoughts?
f.g.

---

### Post by F.G. on 2011-06-24
> **snowpine said:**
> Anyone with physical access to your computer has full access to all non-encrypted data. (i.e. "yes")
yes, but my question is broader than that.  it relates to remote access, and all kinds of access. institutions that use unix to network their machines, though still run windows individually ect, etc...

basically are partitions safe, from alien programs, i just don't know?

---

### Post by snowpine on 2011-06-24
In theory, if your Windows is compromised, then so is any data in your Linux partition. In practice, I have not heard of any actual malware targeting dual boots (but I am not a security expert).

---

### Post by Thewhistlingwind on 2011-06-24
Considering that windows has no native ext4 functionality, it'd be quite the shot they'd be making to infect your Ubuntu partition from windows, but yes, I think it would be possible.

---

### Post by F.G. on 2011-06-24
i think it would be almost impossible target dual-boots effectively, though if a total wipe was the aim, then maybe.  I guess i'm just wondering if you can run a pointer from one partition to another, without some serious problems.  i know that you can do it throughout the main memory, but cross-partition seems kind of different, i know i can't 'see' my ubuntu partitions from windows without extra help.

---

### Post by haqking on 2011-06-24
> **F.G. said:**
> presumably if it can be done by intent, then it can also be done by accident.  leaving a for loop, with a c style pointer, (or c++) incrementing is not so difficult.  however my concern is malicious programs.  if I run a windows, with a dual boot, with a super malicious virus...  this is my concern.  (what happens if you try to access non-existent memory in windows? as this is precisely the how this would occur, and because that is how this could be an issue).  ??
any thoughts?
f.g.

yeah of course, i mean like by being logged in they couldnt just browse the data accidentally.

I was assuming you meant that they would be using it, logging into windows and maybe try to access his data...its late and im typing rubbush ;-)

I have just had coffee and re-read what you wrote in OP...sorry ;-)

---

### Post by tgm4883 on 2011-06-24
It seems you have a misunderstanding as to how exactly partitions work and what you exactly mean by access.

First lets correct some terms.

Ubuntu can access the NTFS partition on your system because Ubuntu contains the code necessary to read and write to NTFS partitions. Your Windows machine is likely installed on an NTFS partition (or if it's super old it could be FAT32, but Ubuntu can read/write to that to).

Windows cannot read nor write to any partition that is not NTFS or FAT32 (and perhaps a very few others) as it does not contain the code necessary to do so (No code to read/write to EXT# partitions). There is code available through third party programs that can add that functionality to Windows, so that option is still available. 

That said, Windows would still be able to overwrite the partition so if destroying the data was the object it sure is possible.

Once we get past those issues, if the Linux partition is encrypted then he would need a password to decrypt it first.

As for Windows malware affecting a Linux partition in theory it is possible, in practice it is possible. In the wild I doubt it exists as a generic threat. If you do run across Windows malware that infected your Linux partition you better figure out who you pissed off as that would likely be a targeted attack.

---

### Post by F.G. on 2011-06-24
no worries haqking, yes, i didn't mean accidentally, but by some design (inteligent prgramming??, something like that).

---

### Post by tgm4883 on 2011-06-24
> **F.G. said:**
> i think it would be almost impossible target dual-boots effectively, though if a total wipe was the aim, then maybe.  I guess i'm just wondering if you can run a pointer from one partition to another, without some serious problems.  i know that you can do it throughout the main memory, but cross-partition seems kind of different, i know i can't 'see' my ubuntu partitions from windows without extra help.

I think you are confusing what pointers are. Pointers are referencing information loaded in memory (RAM), and when Windows is booted, Linux isn't in RAM. Everyone else here has been talking about logical partitions that reside on the physical hard disk.

---

### Post by F.G. on 2011-06-24
> **tgm4883 said:**
> It seems you have a misunderstanding as to how exactly partitions work and what you exactly mean by access.

First lets correct some terms.

Ubuntu can access the NTFS partition on your system because Ubuntu contains the code necessary to read and write to NTFS partitions. Your Windows machine is likely installed on an NTFS partition (or if it's super old it could be FAT32, but Ubuntu can read/write to that to).

Windows cannot read nor write to any partition that is not NTFS or FAT32 (and perhaps a very few others) as it does not contain the code necessary to do so (No code to read/write to EXT# partitions). There is code available through third party programs that can add that functionality to Windows, so that option is still available. 

That said, Windows would still be able to overwrite the partition so if destroying the data was the object it sure is possible.

Once we get past those issues, if the Linux partition is encrypted then he would need a password to decrypt it first.

As for Windows malware affecting a Linux partition in theory it is possible, in practice it is possible. In the wild I doubt it exists as a generic threat. If you do run across Windows malware that infected your Linux partition you better figure out who you pissed off as that would likely be a targeted attack.
yes, i know that windows can't read or write ext... partitions, what i'm basically worried about is that if you give a program a memory address in windows it tends to access it/or try to access it even if it is not a real memory address. so it seems possible that it could acccess/corrupt areas that are not ntfs, or fat as the file system format is essentially not relevant.  basically if i dereference the address 0xff.... with a * even if it is out of the bounds of the windows paritition it can still be accessed and modified.  in this context i don't think that the file system matters, in fact that is one of the roots of my question. 
i guess this issue is not so important.

---

### Post by Dangertux on 2011-06-24
> **tgm4883 said:**
> I think you are confusing what pointers are. Pointers are referencing information loaded in memory (RAM), and when Windows is booted, Linux isn't in RAM. Everyone else here has been talking about logical partitions that reside on the physical hard disk.

Exactly this, however in that vein of thinking  it IS very possible to cause a buffer overflow in a Windows guest system and "break out" of a VM into a Ubuntu host system. However that was not the question. So simply while Windows is running (assuming no VM) you can not reference something in Ubuntu that is not in memory already. 

As far as writing data to the partition this is possible with some forethought, although with lack of extensive planning of what happens once the data gets there the attack would likely fizzle for lack of a better word. What I mean by this is, even if Windows malware CAN see your Linux partition AND write to it, unless it's writing something that will effect the Linux world once that partition is mounted, it will be little more than copying Windows data to the partition and letting it sit there.

EDIT To address the post prior to this one : A pointer references a MEMORY address not a point on the hard drive. All available memory the system has would be running in Windows kernel space , since the swap partition isn't mounted by windows (this is the only conceivable physical memory a pointer could get to this way). A buffer overflow could not "break into" an EXT partition, partitions aren't even on the table.

More information on pointers [http://cslibrary.stanford.edu/106/](http://cslibrary.stanford.edu/106/)

---

### Post by tgm4883 on 2011-06-24
> **F.G. said:**
> yes, i know that windows can't read or write ext... partitions, what i'm basically worried about is that if you give a program a memory address in windows it tends to access it/or try to access it even if it is not a real memory address. so it seems possible that it could acccess/corrupt areas that are not ntfs, or fat as the file system format is essentially not relevant.  basically if i dereference the address 0xff.... with a * even if it is out of the bounds of the windows paritition it can still be accessed and modified.  in this context i don't think that the file system matters, in fact that is one of the roots of my question. 
i guess this issue is not so important.

Please see my above post on pointers

---

### Post by F.G. on 2011-06-24
> **tgm4883 said:**
> Please see my above post on pointers
ok, so i may be wrong about this though, my understanding of pointers is that they are a memory address stored in a register in the CPU which contains a number which corresponds via direct, indirect, or other addressing mechanisms to a space in main memory. and in various indirect addressing modes this can also refer to a thing on the hdd / external kinds of memory (you take an offset from an operand and add it to a base register in the cpu to get the actual address of the data).  if this is the case, could a modified address, in a general purpose register point at anything?? (even memory spaces that don't exist/aren't main memory?) or have i got this all backwards. 

sorry, hastily written, with all the mistakes.

---

### Post by F.G. on 2011-06-24
basically my query is not regarding logical, or physical partitions, just whether you can put any number into a program in windows and will it try to find that, even if it appears out of bounds. i know when i tried running an integer pointer up indefinitely in windows 7 it kept going till it ran off the end, though it should have been out of the programs allocated space.

---

### Post by tgm4883 on 2011-06-24
> **F.G. said:**
> ok, so i may be wrong about this though, my understanding of pointers is that they are a memory address stored in a register in the CPU which contains a number which corresponds via direct, indirect, or other addressing mechanisms to a space in main memory. and in various indirect addressing modes this can also refer to a thing on the hdd / external kinds of memory (you take an offset from an operand and add it to a base register in the cpu to get the actual address of the data).  if this is the case, could a modified address, in a general purpose register point at anything?? (even memory spaces that don't exist/aren't main memory?) or have i got this all backwards. 

sorry, hastily written, with all the mistakes.

If the goal is to read/write something from the disk, then what is the point of hacking pointers to do that? Buffer overflows are to gain access to portions of memory (RAM) that don't belong to that program. Hard drive bits don't belong to anything, so a buffer overflow is not necessary.

As I've stated before, there is nothing special needed to destroy a Linux partition from Windows (aside from Windows Administrator access which is easy enough to gain). 

In conclusion
1) If you want to read from/write to a Linux partition from Windows you will need to add the special drivers for Windows to be able to access it.

2) If you want to destroy the Linux partition from Windows you only need Windows Administrator access.

3) Hacking pointers to gain access to the Linux partition is pointless (no pun intended) as you will likely get a random bit of useless data, and it's unnecessary as nothing owned/protected those bits to begin with.

---

### Post by tgm4883 on 2011-06-24
> **F.G. said:**
> basically my query is not regarding logical, or physical partitions, just whether you can put any number into a program in windows and will it try to find that, even if it appears out of bounds. i know when i tried running an integer pointer up indefinitely in windows 7 it kept going till it ran off the end, though it should have been out of the programs allocated space.

So again, this is memory, not storage (big difference). I'd also ask could you actually access the information stored in those other memory locations?

---

### Post by F.G. on 2011-06-24
ah, so yes, apparently you can access that memory. if you print it out as chars then it reads something like, Windows copyright 199- written by x, etc, etc, repeatedly, up untill you max out the memory. if you go down (decrement the memory address) i found that you get the equivalent of a seg-fault, at just under a gigabyte. (this is with windows 7 btw).  
none-the-less storage is accessed and written to via main memory (excluding the use of a DMA, which could still be used int he same manner, i guess), so i remain unconvinced that that really makes a difference?

---

### Post by F.G. on 2011-06-24
> **tgm4883 said:**
> If the goal is to read/write something from the disk, then what is the point of hacking pointers to do that? Buffer overflows are to gain access to portions of memory (RAM) that don't belong to that program. Hard drive bits don't belong to anything, so a buffer overflow is not necessary.

As I've stated before, there is nothing special needed to destroy a Linux partition from Windows (aside from Windows Administrator access which is easy enough to gain). 

In conclusion
1) If you want to read from/write to a Linux partition from Windows you will need to add the special drivers for Windows to be able to access it.

2) If you want to destroy the Linux partition from Windows you only need Windows Administrator access.

3) Hacking pointers to gain access to the Linux partition is pointless (no pun intended) as you will likely get a random bit of useless data, and it's unnecessary as nothing owned/protected those bits to begin with.

sorry, only just read this. i think it probably confirms what i've been wondering.

---

### Post by F.G. on 2011-06-24
so, here's my random cpp program for anyone interested:
> #include <iostream>
using namespace std;
int main()
{char x[10];
int y[5];
signed z[3];
x[6] = 'o';
x[5] = 'c';
x[7] = 'u';
x[8] = 'c';
x[9] = 'h';
x[10] = '!!';

x[11] = 'O';
x[12] = 'U';
x[13] = 'C';
x[14] = 'H';
x[15] = '!';

//for(int i = 0; i >= -1000; i--)
for (int i = 0; i <= 30000; i++)
cout << "-> " << &x[i] << " = " << x[i]  << " -> " << &y[i] << " = " << y[i] <<" -> " << &z[i] << " = " << z[i] << endl;
//cout << "-> " << &x[-4000] << " = " << x[-4000] << endl;
}

it should probably really use INT_MAX and climits, still quite fun though.

---

### Post by tgm4883 on 2011-06-24
> **F.G. said:**
> so, here's my random cpp program for anyone interested:

it should probably really use INT_MAX and climits, still quite fun though.

I'm not a C programmer ( I know python ), but it doesn't look like you are actually referencing memory locations that don't belong to you. I'll do a bit more research, but it seems you are just increasing your own space.

---

### Post by tgm4883 on 2011-06-24
Yea so it doesn't seem you are using pointers at all, but I'm only going on this

[http://www.cplusplus.com/doc/tutorial/dynamic/](http://www.cplusplus.com/doc/tutorial/dynamic/)

Which seems to indicate there is dynamic memory allocation in C++, which means you aren't referencing things outside of your memory.

---

### Post by F.G. on 2011-06-24
so, I should have tidied this program up a bit. its c++, not c.  basically that array is incremented out of bound.  if the array x is only of size 10, or 15 (its defined as 10 then other bits are assigned). you shouldn't be able to print out x[1000]?? i think.  though i've also assigned stuff out side of its defined size, so i'm not sure how that works.

i think python does memory management more automatically.

---

### Post by F.G. on 2011-06-24
your right though it looks like the memory space is expanded.

---

### Post by tgm4883 on 2011-06-24
> **F.G. said:**
> your right though it looks like the memory space is expanded.

Yea the page I referenced is for C++, and it talks about dynamic memory management (something C doesn't have). It shows needing to do that by initializing it a special way, which is different than you did. Looking at another page it looks like it should be fixed, which means it should not do what it looks like it is doing.

That said, I'm a Python guy, so there might be some special C++ magic that is happening :)

---

### Post by F.G. on 2011-06-24
with regards to pointers, using an array in c or c++ is the same as actually using a pointer to the beginning of that array.  so, your right that there arn't explicit pointers, but, i,ve been led to believe that an array variable still acts as a pointer without its subscript.  i think that this is accurate, though this is a prog I wrote a while ago and maybe I should have a go again, with explicit pointers. i will post if i do that.

ps. on the subject of python, ive recently been doing pythonchallenges and loving them (i know no python).

---

### Post by F.G. on 2011-06-24
i just ran that my little program  on ubuntu. and it definitely doesn't go out of bounds (no seg-faults). so I guess it does expand the memory allocation of the program each iteration. 
ill have another go, more precisely and come back to this.
sorry for not figuring it out prior to posting.

---

### Post by Dangertux on 2011-06-25
I'm going to give a hint on this, but it's not going to be very detailed, you can do the rest of the research on your own.

You want to look for functions that don't boundary check when appending data to a string. Think strcat()

If you think logically you should be able to get the rest in time.

Why is it you want to write a buffer overflow anyway?

---

### Post by F.G. on 2011-06-25
curiosity, nothing but curiosity.

---

### Post by Duncan Williams on 2011-06-25
as you can see here:
[http://www.google.com/search?q=read%20linux%20partitions%20in%20windows](http://www.google.com/search?q=read%20linux%20partitions%20in%20windows)

there are lots of ways to access/delete/format linux partitions from windows.

One would think that if some hacker was determined enough they could use windows as a host to harm linux on dual boot.

---

### Post by walt.smith1960 on 2011-06-25
Disclaimer: I am not a programmer.

I use a boot manager to boot different partitions, it seems to be easier and more capable than just GRUB. One thing I like about it is that I can control which partitions are seen by each operating system. If I want Windows to only see its own partition I can do that.  If I want Windows to see its own partition plus a data storage partition, I can do that.  If I want Ubuntu to see its own partition plus the data storage partition I can do that. The downside is that I typically install Ubuntu twice in the same partition in order for it to boot properly.  There may be a way around that but it's easier for me to simply install twice; start the install and go do something else for 20 minutes and repeat.  Oh, and make sure GRUB installs in the partition, not in the MBR.  Here's the program-I have no connection beyond being a user: (BootIt Bare Metal - link removed)

Edit: Commercial link removed by mod.

---

