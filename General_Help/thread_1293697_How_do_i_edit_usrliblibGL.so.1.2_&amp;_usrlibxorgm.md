---
title: "How do i edit /usr/lib/libGL.so.1.2 &amp; /usr/lib/xorg/modules/extensions/libglx.so"
date: 2009-10-17
forum: General Help
---

### Post by Cytomax on 2009-10-17
My flash doesnt work and i read here 

BASIC QUESTION
How do i edit 
/usr/lib/libGL.so.1.2
/usr/lib/xorg/modules/extensions/libglx.so

I gives me an error when i type in 
gedit /usr/lib/libGL.so.1.2
gedit /usr/lib/xorg/modules/extensions/libglx.so

I think my problem is either
These are symlinks 
or
These are bin files and i need something else to edit them with

HISTORY OF MY QUESTION.... no important

I seem to have the same problem everyone else has with FLASH
according to this post on adobe
[http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)
Flash cant be played in Fullscreen.

The work around is 

Hey everyone.

I managed to solve this issue on my machine. I have Intel 915GM graphics.

This adobe blog is really the key:

[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

The flash player does the unbelievably brain dead thing of checking the glxinfo vendor strings to make sure they do *not* contain the string "SGI". Flash hardware acceleration will only be enabled if the vendor strings do not contain the string "SGI". Incredible, huh?

The advice given in one of the comments actually worked for me. Specifically, use a hex editor (such as 'ghex') to alter these two binaries:

/usr/lib/libGL.so.1.2
/usr/lib/xorg/modules/extensions/libglx.so

(or the actual binaries these files link to, if they are symbolc links. They were links on my system.)

They each contain one instance of "<null>SGI<null>" (plenty of the string "SGI" in other contexts, but ignore these). Change the single instance in each file to "<null>ATI<null>". Restart X, and you may just have hardware accellerated flash. It worked for me.

 :D

---

### Post by StuartN on 2009-10-17
> **Cytomax said:**
> I think my problem is either
These are symlinks 
or
These are bin files and i need something else to edit them with

Specifically, **_use a hex editor (such as 'ghex')_** to alter these two binaries:

Your question and your answer, all in one.

---

### Post by Cytomax on 2009-10-17
Well i feel silly...
I installed ghex..
i typed in ghex2 /usr/lib/libGL.so.1.2
Then ghex opens up the document and that is where i get lost......
One panel of the progam looks like 10000 mac address 00 00 00 08 07 06 etc..
The other panel looks like 10000 periods..  ELF.....HU...hu....x....x....x...

anyways my problem is cant find the thing im supposed to find which is
<null>SGI<null> and change it to <null>ATI<null>

BTW does null stand for something generic or is it actually going to say <null>SGI<null>

Thanks again in Advance
Eddie

---

### Post by StuartN on 2009-10-17
> **Cytomax said:**
> Well i feel silly...

Sorry, I was being cheeky. It is so easy to miss things that a fresh pair of eyes spot straight off, especially when it is at a tangent and you are struggling with a problem.

> **Cytomax said:**
> I installed ghex..
i typed in ghex2 /usr/lib/libGL.so.1.2
Then ghex opens up the document and that is where i get lost......
One panel of the progam looks like 10000 mac address 00 00 00 08 07 06 etc..
The other panel looks like 10000 periods..  ELF.....HU...hu....x....x....x...

A hex editor normally displays an address, perhaps 8 hexadecimal digits, in the first column. Then there will be 8 or 16 two-digit hexadecimal numbers separated by spaces and finally the ASCII character representations of those same 8 or 16 numbers. If a character has no ASCII representation then a "." is displayed instead. This is a hexdump of a file containing the text "This is some text":

```
00000000  54 68 69 73 20 69 73 20  73 6f 6d 65 20 74 65 78  |This is some tex|
```

You are looking for a hexadecimal 00 followed by the hexadeciaml for S, G, and I, then another 00. The left-hand hexadecimal display will contain 00 53 47 49 00 and the right-hand ASCII display will contain .SGI. (the zeroes on the left have no ASCII representation, so they are displayed as ".").

You need to replace the three characters SGI with the three characters ATI.

NB: I have no idea what this is intended to achieve, but it looks like replacing the name of one graphics device with another inside a binary graphics driver library. I could not vouch for that being safe to do.

**Edit: *WAIT! Have you installed flashplugin-nonfree and tried all the usual solutions for getting flash to work before doing surgery on binary files?***

---

### Post by Cytomax on 2009-10-17
Thank you for your reply again.. it was most helpful...
I was able to successfully edit the file with the following command

sudo ghex2 /usr/lib/libGL.so.1.2

I then pressed ctrl+f
entered SGI on the right panel
added two 0's on the left panel before and after the SGI so it looked like this 00 53 47 49 00
I then altered it so it read ATI
Saved it

Then i repeated the process for 
sudo ghex2 /usr/lib/xorg/modules/extensions/libglx.so
Saved it and restarted...

This did not help my fullscreen youtube so looks like im just gonna keep waiting....

BTW to answer your question i used this to setup my ubuntu 9.04 laptop
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Youtube works fine as long as it isnt in fullscreen mode....


The known bug with flash can be found here [http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692) this was a possible workaround it seemed to help some but it didnt help me...

Thanks again for the response
Eddie

---

