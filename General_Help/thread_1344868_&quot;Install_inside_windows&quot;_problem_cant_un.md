---
title: "&quot;Install inside windows&quot; problem cant uninstall"
date: 2009-12-03
forum: General Help
---

### Post by earfer on 2009-12-03
- LOL Sorry got 2 of the same post DELETED this one so please do read the one BELOW. Thank you -

---

### Post by earfer on 2009-12-03
Hey guys, sorry if this is the millionth thread about this.
And also i was trying to find a move thread button, but guess there isnt...so theres one of the same thread inside "General Help"

Problem is is that i install ubuntu using "install inside windows" and now i cant uninstall it. Its taking up 30gb's in my D: and i just restored my C: (Vista). Now i cant boot in to ubuntu, nor can i uninstall it.

Summary:

- Installed Ubuntu using "Install in Windows"
- Installed on D: and toke up 30 GB'S
- Restored C: (Vista)
- Couldn't boot ubuntu.
- Formatted D: thinking it would uninstall ubuntu, and get 30 GB's back... i was wrong. (then found out bout menu.lst boot.)
- Tried installing Wubi again and uninstalling it...fail.
- Dont know what to do ...

(Ive been formatting my D: that 110gb that surppose to be 140gb but i cant get the 30gbs back so ekk.)

Thanks in Advance~!

---

### Post by lisati on 2009-12-03
Wubi (the tool that lets you install Ubuntu "in" Windows) doesn't usually set up new partitions, it uses a folder in the Windows partition. Therefore, if you used the "standard" way of of installing within Windows, your 30GB should be there.

Did you do a full restore of Windows or a non-destructive restore? 
Did you set up a separate /home partition manually?

Edit: Oh. Did you install "Within" Windows AND do a normal install as well? Please clarify.

---

### Post by darkod on 2009-12-03
Another soul lost to wubi. This is exactly why I don't like wubi. Unfortunately it seems to misguide plenty of people expecting a full side-by-side install with it.

At this moment it's best that you post a screenshot of your Disk Management in vista. Press windows button + R and type diskmgmt.msc hit Enter. Make a screenshot of the disk layout and attach it here so we can see the partitions you have at the moment.

Otherwise when you formatted D: that would destroy the wubi folder but it should not cut anything from it, definitely not 30GB.

---

### Post by earfer on 2009-12-03
> **lisati said:**
> Wubi (the tool that lets you install Ubuntu "in" Windows) doesn't usually set up new partitions, it uses a folder in the Windows partition. Therefore, if you used the "standard" way of of installing within Windows, your 30GB should be there.

Did you do a full restore of Windows or a non-destructive restore? 
Did you set up a separate /home partition manually?

Edit: Oh. Did you install "Within" Windows AND do a normal install as well? Please clarify.

Thank you for the quick reply,

Im not so sure if installed ubuntu the "standard" way...
I installed it normally using wubi "install inside windows"...

Full restore or Non - Destructive? I think i did a full restore on my C: (Vista) and i formatted my D: 
- well i did a factory default restore that..yes did delete everything inside the C: -

I really dont know.

P.s yeh i rly dont know why my 30gb's gone. its not a parition its as if...u can say... disappeared from the D:

---

### Post by cariboo on 2009-12-03
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by lisati on 2009-12-03
If you use Wubi to install within Windows, it normally uses part of your Windows drive, usually C:.
When you later do a restore of Windows, your Ubuntu installation will be wiped. I'm not sure if or why Wubi would touch D:.

---

### Post by earfer on 2009-12-03
> **cariboo907 said:**
> Please don't create multiple threads on the same subject. I have merged your two threads.

Thank you very much.

---

### Post by earfer on 2009-12-03
> **lisati said:**
> If you use Wubi to install within Windows, it normally uses part of your Windows drive, usually C:.
When you later do a restore of Windows, your Ubuntu installation will be wiped. I'm not sure if or why Wubi would touch D:.

Heres a picture of the problem...just a lil picture.

[IMG]http://i740.photobucket.com/albums/xx49/earfer/Partition.jpg[/IMG]

OH and also what happens if i delete my D: partition? disappear? or unallocated?

---

### Post by earfer on 2009-12-03
Hmm i got some ideas. imma see if i install wubi again then boot in ubuntu and i might hit the same ubuntu as before. or ill just reboot install the partition way~ and i might find the partition version of the ubuntu there.

More Info Edit:

So i installed Ubuntu "Install inside windows" and while installing it flashed by...
"Creating Partition" and said something "Creating Ext4? #1 Loop1 (Loop2)" something like that...

Hope you guys can help out :)

---

