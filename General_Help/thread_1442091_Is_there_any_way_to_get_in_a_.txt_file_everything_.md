---
title: "Is there any way to get in a .txt file everything that is shown while turning on?"
date: 2010-03-29
forum: General Help
---

### Post by hihihi100 on 2010-03-29
Ill try to make it clearer:

When I turn on my laptop, some messages appear, but the time to read those is too small and I cant recall what they say. I am interested in knowing the exact content of those messages, given that I have, somehow, be able to read "error" somewhere, but it would be of much help to know the exact wording of the message

Cheers

---

### Post by Jouke74 on 2010-03-29
Open a command line terminal and type "dmesg > fileyouwant.txt" without the quotes.

---

### Post by jobix on 2010-03-29
In addition to using "dmesg" as Jouke74 suggested, you can also look at the file /var/log/messages for more info. If you just want to search for "error" try:

> grep -i error /var/log/messages

---

### Post by nitstorm on 2010-03-29
Also you can try looking into System->Administration->Log File Viewer

---

### Post by hihihi100 on 2010-03-29
log file viewer: too many lines... and, how do I make it stop? every 30 seconds or so, it adds like 6 new lines and scrolls me down to the last line

But id like to draw ur attention to:
```
hihihi100@hihihi100-laptop:~$ grep -i error /var/log/messages 
Mar 28 18:05:20 hihihi100-laptop kernel: [ 1294.779772] synaptic[3350]: segfault at b9b6c280 ip 0037aab3 sp bf8deaa0 error 4 in libapt-pkg-libc6.10-6.so.4.8.1[30d000+bd000]
Mar 28 18:06:13 hihihi100-laptop kernel: [ 1347.465991] synaptic[6230]: segfault at b9c44280 ip 00b2dab3 sp bfe21f40 error 4 in libapt-pkg-libc6.10-6.so.4.8.1[ac0000+bd000]
Mar 28 18:32:50 hihihi100-laptop kernel: [ 2944.095463] scim-helper-lau[15859]: segfault at 8 ip 00a7bf63 sp bfba2ce0 error 4 in _scim.so[a70000+1d000]
Mar 29 21:30:12 hihihi100-laptop kernel: [ 5006.298437] nautilus[8614]: segfault at 4caead0 ip 04caead0 sp bfc6b12c error 4 in libgstreamer-0.10.so.0.22.0[52f2000+ba000]
hihihi100@hihihi100-laptop:~$ 


```How do I fix those?

I also executed, as suggested:

```
hihihi100@hihihi100-laptop:~$ dmesg > fileyouwant.txt
hihihi100@hihihi100-laptop:~$ 

```Nothing happened

---

### Post by rbc on 2010-03-29
```
dmesg > fileyouwant.txt
```

In this case, you are not going to see anything. You may have already found this, but what that did was run the dmesg command, create a file (in the current directory) called fileyouwant.txt, then redirect the output of dmesg to that file

---

### Post by hihihi100 on 2010-03-29
ok, I didnt know I could be this dumb....

Yes Just now I found it, thanks anyway

---

### Post by gordintoronto on 2010-03-29
If you have access to a phone which can record videos, or an actual video recorder, that is a better choice.  If you have VLC installed, it can slow down video playback so you can pause when something interesting appears.

---

### Post by hihihi100 on 2010-03-30
I was thinking about the video option, seems the most plausible now... I havent found the exact wording with the suggested commands

---

### Post by anaconda on 2010-03-30
I have used a normal camera for thet purpose...

---

