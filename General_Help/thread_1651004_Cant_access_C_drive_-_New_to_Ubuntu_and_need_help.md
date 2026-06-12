---
title: "Cant access C drive - New to Ubuntu and need help"
date: 2010-12-22
forum: General Help
---

### Post by jgjr on 2010-12-22
[SIZE=4]Just installed Ubuntu and I think I am really going to like it. When I installed it, I had an external hard drive connected to the back of my laptop and now when I open Documents, Music etc... they are all empty. Is Ubuntu suppose to access my C drive and all its info? Im wondering if I messed it up by having the external connected when I installed the software. I tried to find an option to access C drive with no luck. Do I have to re install Ubuntu?
Thanks for any help.[/SIZE]

---

### Post by iosuna86 on 2010-12-22
When you say "C", you mean the C: partition from Windows?

I don't think Ubuntu can access Windows partitions. I think it has to do with the type of partitions. Whereas Windows uses NTFS, Ubuntu has ext3/ext4 partitions. 

I am pretty new to Ubuntu too, so there may be some way to access Windows from Ubuntu. I haven't heard of any though.

---

### Post by Verbeck on 2010-12-22
if you installed from wubi (the installer which appears in windows) then go to places>computer>file system>host

if its a partitioned dualboot, it should appear under the places menu (would be referred by its size rather than c: if you haven't labelled it)

---

### Post by jgjr on 2010-12-22
Thank you Verbeck, They are exactly where you said and I can view everything I have in my Windows files.
Can I make a shortcut in Ubuntu or do I have to go thru the same process each time to access them.
Thanks again..

---

### Post by Verbeck on 2010-12-22
middle-click and drag the host folder to your desktop and choose 'link here' 
or if you dont have a mouse-wheel,
from a terminal (applications>accessories), run 
ln -s /host ~/Desktop/Windows

---

