---
title: "Error: File too large"
date: 2009-12-30
forum: General Help
---

### Post by JNied on 2009-12-30
I am trying to copy a 4.7 GB file from my HDD to a MicroSD card. I've tried leaving the card in my phone and using a USB cable, Bluetooth and WiFi, as well as taking the card out and putting it directly into my computer's built-in card reader, and with all methods I get the same problem:
[font=courier new]cp: writing `/media/1142-D595/movie.mkv': File too large[/font]

I tried both through the GUI and terminal.
I've checked and double-checked and triple-checked that I have enough free space on my card to hold this new file.
I understand I can split it into several smaller compressed files, which will be fine for this one time, however I don't want to have to compress, copy and decompress a file every time I want to move it (especially because a file this large takes quite some time for each step).

Is there a way around this?  Am I doing something wrong?

I'd really appreciate any help or advice you happen to have.  Thanks in advance.

To whom it may concern:
[font=courier new]Linux Jason-Ubuntu 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux[/font]

---

### Post by Command_line_lover on 2009-12-30
What file system does the SD card have?

---

### Post by USB_NL on 2009-12-30
how big is the micro-sd-card and how many partitions?

---

### Post by USB_NL on 2009-12-30
> **Command_line_lover said:**
> What file system does the SD card have?
fat32 and maby a ubuntu liveCD presitently boot ???

---

### Post by Command_line_lover on 2009-12-30
> **USB_NL said:**
> fat32 and maby a ubuntu liveCD presitently boot ???

I didn't ask you.

---

### Post by Jackzor on 2009-12-30
I believe FAT32 can on;y move 3 or 4 gigbytes at a time... As a single file that is. You would have to have both storage areas in something with a larger limit.
 
I believe that you could move the file between two file systems that are ntfs/ext3/ext4

NOT fat or fat32

I hope I'm right....

---

### Post by Command_line_lover on 2009-12-30
Jackzor: I thought that was only FAT.

Either way, you should just back every thing up then format as ext3/4. Unless you need to remain compatible with PCs and Macs

---

### Post by oldfred on 2009-12-30
4GB is correct for FAT32 as the max file size. 


NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
max - 4GB minus 2 Bytes

---

### Post by Jackzor on 2009-12-30
> **oldfred said:**
> 4GB is correct for FAT32 as the max file size. 


NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
max - 4GB minus 2 Bytes

Thanks for verifying.

---

### Post by JNied on 2009-12-30
I'm actually not sure what the FS on the card is, nor how to check.  It is a 16 GB "Micro SD HC" with a single partition.  I have to assume it's FAT, since the 4 GB limit was mentioned and that's always where it stops.  I have no problem reformatting, but it still needs to be readable on my phone, and I usually connect my phone via USB to friends' computers and use it as a jump drive, so it would still need to play nice with Windows.

---

### Post by Jackzor on 2009-12-30
What phone are you useing?

---

### Post by Command_line_lover on 2009-12-30
I think you can check using disk utility under system>administration.

Oh, and you can always try to convince your friends to switch to linux...

---

### Post by JNied on 2009-12-31
> **Jackzor said:**
> What phone are you useing?HTC Touch Pro (Pocket PC w/ Windows Mobile)


> **Command_line_lover said:**
> I think you can check using disk utility under system>administration.FAT32


> **Command_line_lover said:**
> Oh, and you can always try to convince your friends to switch to linux...I'm constantly doing that anyway, but in the mean time I need Windows compatibility.

---

### Post by dcstar on 2009-12-31
> **JNied said:**
> HTC Touch Pro (Pocket PC w/ Windows Mobile)


FAT32


I'm constantly doing that anyway, but in the mean time I need Windows compatibility.

Then format it NTFS.

---

### Post by rnerwein on 2009-12-31
hey - you are running linux - that means -> if you can't fix it, fake it. use this
if u get a file eg. bla (5028970496 byte) execute:
split -b 2514485248 bla - the result will be the files: xaa (2514485248 byte) and xab (2514485248 byte)
that size fits. save this files. and back you use: cat xaa xab > bla and the will get back
bla (5028970496 byte). for more about split see the man pages.
hope it will help you. ciao

---

### Post by StuartN on 2009-12-31
> **JNied said:**
> I'm actually not sure what the FS on the card is, nor how to check.

The maximum file size on a FAT32 filesystem is 4 GB [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits) and you can not create a larger file. This is most likely the filesystem on the card. You would need to reformat the card (assuming there are no important files on it) to write a larger file, and NTFS is probably the only choice. Even so, it is possible that your other device is not compatible with even NTFS.

gparted will show you what filesystem is in use, or reformat a partition.

If NTFS is compatible and there is nothing important on the card, then insert the card and run gparted (or System -> Administration -> Partition Editor). Select the device from the list in the top right, then select the partition - be very careful not to overwrite the wrong partition. Unmount the partition. Select Format to ... NTFS. Click Apply.

---

### Post by JNied on 2009-12-31
> **rnerwein said:**
> hey - you are running linux - that means -> if you can't fix it, fake it. use this
if u get a file eg. bla (5028970496 byte) execute:
split -b 2514485248 bla - the result will be the files: xaa (2514485248 byte) and xab (2514485248 byte)
that size fits. save this files. and back you use: cat xaa xab > bla and the will get back
bla (5028970496 byte). for more about split see the man pages.
hope it will help you. ciaoI appreciate you showing me the split command; I'm trying to get more into Linux command line and scripting, and split definitely seems like a useful tool.  However, I still have the same problem: I have to wait for an almost 5 GB file to split, then I have to transfer 5 Gigs of data, then I have to wait for two 2.5 GB files to concatenate.  It's effectively tripling the amount of time taken to copy the file.
That being said, I again thank you because it does seem like a useful tool that I will indeed use in the future.


> **StuartN said:**
> The maximum file size on a FAT32 filesystem is 4 GB [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits) and you can not create a larger file...Thanks for the link, it's very informative.
Formatting is something I'm familiar with already, but nonetheless I appreciate the amount of detail with which you explained your suggestion.  One thing that bothers me is when someone is vague in their answers and it takes several posts just to figure out what they meant.  So again, thank you.



I am currently in the process of backing up the card so that I can reformat to NTFS and I'll let everyone know how it went.  Thanks for your help so far.

---

### Post by JNied on 2009-12-31
GParted will not allow me to format the card in NTFS.  My only options are ext*, FAT* and linux-swap.  Everything else is disabled in the list.

---

### Post by dcstar on 2009-12-31
> **JNied said:**
> GParted will not allow me to format the card in NTFS.  My only options are ext*, FAT* and linux-swap.  Everything else is disabled in the list.

Install the **ntfsprogs** package.

---

### Post by JNied on 2009-12-31
That did it.  However, as I suspected, my phone does not recognize NTFS (yes that's right, a Microsoft OS doesn't recognize a Microsoft file system :roll: ).

Thank you everyone for your help, I really do appreciate it.  However, it looks like I'm doomed to split any >4 GB files.  Oh well.

---

### Post by dcstar on 2010-01-01
> **JNied said:**
> That did it.  However, as I suspected, my phone does not recognize NTFS (yes that's right, a Microsoft OS doesn't recognize a Microsoft file system :roll: ).


Unfortunately most consumer devices only use FAT32 for its simplicity and compatibility with just about everything. Because of that we all have to live with its inherent limitations (and fragility).

---

### Post by doggywuff on 2010-01-07
Yeah I had the same problem 
i tried to copy a movie that was 6.6 gigs (one single file) and it kept stopping at 4.0 gigs
just to clarify there is absolutely no way to get by this? thanks in advance

---

