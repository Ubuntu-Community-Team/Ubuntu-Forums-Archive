---
title: "Help with the CD Command"
date: 2010-08-29
forum: General Help
---

### Post by Neil B. on 2010-08-29
I am familiar with the cd command. I have used in in windows, and am now trying to learn how to use it in Ubuntu.

However, I cannot seem to get it to work. 

I type the following:

cd /home/neil (press enter)

it changes the directory to neil. this of course is where my pics,vids,downloads, and documents folders are loacted. 

however if I type this command while i am in the home/neil directory:

cd /documents

it says it is an incorrect file path

i have also tried the following commands to no avail:
cd ./documents
cd ../documents
cd .documents
cd ..documents
cd /home/neil/documents

I have even tried the above commands with different directories, such as, pictures and downloads. 

What the hell am I doing wrong?

---

### Post by albandy on 2010-08-29
Linux is case sensitive.
Your documents folder start with "D" so:

cd /home/neil/Documents

I recomend you to read some bash manuals.

try this one:

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

---

### Post by lisati on 2010-08-29
If you're already in /home/neil, you can also type **cd Documents** to go to /home/neil/Documents

---

### Post by Neil B. on 2010-08-29
Thanks for the swift reply. 

I am actually reading this guide: [http://gd.tuwien.ac.at/linuxcommand.org/lts0020.php](http://gd.tuwien.ac.at/linuxcommand.org/lts0020.php)

It has been very helpful, but obviously did not mention that commands are case sensitive. 

Thank you very much. Is it possible to deactivate case sensitive commands? Without diving into the kernal :P

---

### Post by NovaAesa on 2010-08-29
It's not the commands that are case-sensitive, it's the paths. As far as I know, they cannot be "deactivated".

---

### Post by Neil B. on 2010-08-29
I see. 

Thanks to all who replied. I can now continue my studies. :D

---

### Post by andrew.46 on 2010-08-29
Hi Neil,

> **Neil B. said:**
> Thanks to all who replied. I can now continue my studies. :D

You do not always have to type the full path in, try typing in the first few letters and then press the tab key and the rest of the path will be filled in for you if it is unique. If there are multiple matches pressing tab twice will reveal these...

Andrew

---

