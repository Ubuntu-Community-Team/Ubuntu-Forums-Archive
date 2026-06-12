---
title: "Help! EBCDIC format to ASCII"
date: 2011-08-26
forum: General Help
---

### Post by hrchl86 on 2011-08-26
Hi everyone,
 
I have a 70MB EBCDIC file, with record length 102, block size 32742 and IBM standard label.
 
I use 
"dd if=*input file* of=*outputfie *ibs=32742 cbs=102 conv=ascii"
 
but I still don't get a viewable file under ASCII.
 
Can anyone told me what's the problem?
 
Do I need more parameters about my file or I commanded wrong?
 
Thanks..

---

### Post by hrchl86 on 2011-08-27
no one has experience? I would be grateful to hear from you.

---

### Post by galvatron408 on 2011-08-27
EBCDIC, I can barely pronounce it.

---

### Post by jwbrase on 2011-08-27
> **hrchl86 said:**
> I use 
"dd if=*input file* of=*outputfie *ibs=32742 cbs=102 conv=ascii"
 
but I still don't get a viewable file under ASCII.


What program are you trying to view the resulting file with?

---

### Post by haqking on 2011-08-28
> **hrchl86 said:**
> Hi everyone,
 
I have a 70MB EBCDIC file, with record length 102, block size 32742 and IBM standard label.
 
I use 
"dd if=*input file* of=*outputfie *ibs=32742 cbs=102 conv=ascii"
 
but I still don't get a viewable file under ASCII.
 
Can anyone told me what's the problem?
 
Do I need more parameters about my file or I commanded wrong?
 
Thanks..


I am presuming this is from a AS400 or similar environment ?

How did you retrieve the file ?

The problem i suspect is the way you moved the file such as FTP etc.

There are preferred methods from moving files from a mainframe environment.

try ocopy to create the ASCII before transport.

also have a look here [http://support.sas.com/techsup/technote/ts642.html]]("http://support.sas.com/techsup/technote/ts642.html")

a little ways down you will see a section on moving files between platforms

---

### Post by hrchl86 on 2011-08-29
Hi [jwbrase]("http://ubuntuforums.org/member.php?u=766828"),

As long as the resulting file is readable, it can be .txt, .pdf or even .dbf file.

---

### Post by hrchl86 on 2011-08-29
You are right! I retrieved the file from ftp server. The  problem here is exactly how to view a file from mainframe server to Unix/windows environment. Thanks for your suggestion I will have a look at the link :)

---

### Post by haqking on 2011-08-29
> **hrchl86 said:**
> You are right! I retrieved the file from ftp server. The  problem here is exactly how to view a file from mainframe server to Unix/windows environment. Thanks for your suggestion I will have a look at the link :)

ok let us know how you get on, do you have the option to recopy it ? or to use ocopy before transport ?

---

### Post by hrchl86 on 2011-08-29
The tricky thing is someone else retrived the file and sent to me. I will have a try to see if I can retrieve the file myself.

---

### Post by haqking on 2011-08-29
> **hrchl86 said:**
> The tricky thing is someone else retrived the file and sent to me. I will have a try to see if I can retrieve the file myself.


ok well like i said Ocopy will change it to ascii before transfer

but i cant remember the syntax you will need to look it up

Edit:  infact see if the answer is here [http://ibmmainframes.com/about33861.html](http://ibmmainframes.com/about33861.html)

---

### Post by hrchl86 on 2011-08-29
thanks! I will update if I have any progress.

---

### Post by jwbrase on 2011-08-30
> **hrchl86 said:**
> Hi [jwbrase]("http://ubuntuforums.org/member.php?u=766828"),

As long as the resulting file is readable, it can be .txt, .pdf or even .dbf file.

I don't think you understood my question: You said "but I still don't get a viewable file under ASCII". Presumably you tried using some program to open it, and it failed to do so. What program did you use to try to open it?

---

### Post by hrchl86 on 2011-08-30
Thanks for clarify:)

Now I try to use OpenCobol..

any recommandations?

---

### Post by hrchl86 on 2011-08-30
Hi, I just found out the file in the server is a compressed .z file...

---

### Post by haqking on 2011-08-30
> **hrchl86 said:**
> Hi, I just found out the file in the server is a compressed .z file...

so unpack it then ;-)

[http://www.ncbi.nlm.nih.gov/Ftp/uncompress.html](http://www.ncbi.nlm.nih.gov/Ftp/uncompress.html)

---

### Post by hrchl86 on 2011-08-30
:) Thanks.

I thought you mean convert the file before i retrive from the server. Since the file is compressed, it cannot be converted before unpack, isn't it? :D


> **haqking said:**
> so unpack it then ;-)

[http://www.ncbi.nlm.nih.gov/Ftp/uncompress.html](http://www.ncbi.nlm.nih.gov/Ftp/uncompress.html)

---

### Post by zSeries on 2011-08-30
I am not aware of any program on Linux that can read EBCDIC files.
If you know that the file contains just EDCDIC text, ie equivalent to a plain ASCII text file you may be able to use NoteTab on windows, it is free and can convert EBCDIC text to ASCII. If the file contains binary data you can give up now as you will need to understand what the format of each by is, eg word, half word, packed decimal etc. You have as much chance of reading it as opening an MS Access mdb with gedit and expect to read it. Even if it is plain text YOU may well need to break up the internal lines (aka record, since you known the record length is fixed thats not impossible). EBCDIC dont have CR/LFs. It is further complicated by the fact you don't really know if it is compressed. In practice compression isn't used much on these systems anyway. Also there is no such thing as a file type on EBCDIC systems either.
You can pm me if you like. I have been working on EBCDIC systems, now known as zSeries for 30 years. You have also learnt where my userid comes from.
Tony.

---

