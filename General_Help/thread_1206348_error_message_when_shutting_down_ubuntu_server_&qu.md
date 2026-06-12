---
title: "error message when shutting down ubuntu server &quot;unable to iterate IDE devices: No su&quot;"
date: 2009-07-07
forum: General Help
---

### Post by simudream on 2009-07-07
[IMG]http://www.flickr.com/photos/26389252@N05/3696432329/[/IMG]

Above is a pic of the error message I get when I shutdown Ubuntu Jaunty Jackalope 9.04 server edition.

I'm running an Asus P2B-D mother board with dual pentium III, 1 gighz processors, bios version 1014 beta 003

Basically before shutting down It says:
 
Will now halt
halt:unable to iterate IDE devices: No such file or directory

Right after that the computer will shut off no problem.

I just don't like the fact I have to see this error message every time I shut down.

---

### Post by sam_delta on 2009-07-08
happening exactly the same to me

dell latitude d630

sam

---

### Post by agel1 on 2009-07-08
i solve this problem adding "apm power_off=1" to gksudo gedit /etc/modules

---

### Post by Soul-Sing on 2009-07-08
I'am afraid this is a nasty bug....

---

### Post by Wilvanduren on 2009-09-28
this is the first time that i'm in Ubuntu and have the same failure, how do I do this:
 
i solve this problem adding "apm power_off=1" to gksudo gedit /etc/modules
 
Thnx in advance,
 
Wil

---

