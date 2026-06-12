---
title: "TurionPowerControl and Us"
date: 2011-02-26
forum: General Help
---

### Post by nico_mic on 2011-02-26
Well, i've been strugling to get this working since i woke up with no luck whatsoever...
I need to run TurionPowerControl on my Ubuntu 10.4.2 32-bit but I've not yet been able to run it. To make matters worse i'm an absolute newbie =)

System specs:
CPU: Phenom II x4 945BE (3.2ghz)
Motherboard: M2N-SLI Deluxe

As you can imagine i used to run Phenom MSR-Tweaker on Windows to get my cpu to run at proper speeds and found no way to go back to ubuntu untill i came across TPC. Now, down to business...

When i try to run TPC 0.30 i get this:
nicolas@NicoPC:~/tpc-0.30/bin/Fedora13-x86_64$ ./TurionPowerControl
bash: ./TurionPowerControl: cannot execute binary file

OR:
***@***:~/tpc-0.30/bin/Fedora13-x86_64$ sudo ./TurionPowerControl
[sudo] password for nicolas: 
./TurionPowerControl: 1: Syntax error: "(" unexpected

OR:
***@***:~/tpc-0.30/bin/Fedora13-x86_64$ sudo -s
root@***:~/tpc-0.30/bin/Fedora13-x86_64# sudo ./TurionPowerControl -l
./TurionPowerControl: 1: Syntax error: "(" unexpected
root@***:~/tpc-0.30/bin/Fedora13-x86_64#

Im hoping that this problem is very easily solved, but I'm pretty sure that greater problems lie ahead for me...

Thanks in advance ;)

---

### Post by acrazyplayer on 2011-02-26
do a "chmod +x" on the file and then try to run it. I have never heard of that program so I can't help you actually use it.

---

### Post by nico_mic on 2011-02-26
> **acrazyplayer said:**
> do a "chmod +x" on the file and then try to run it. I have never heard of that program so I can't help you actually use it.
Nope, still nothing. Same error. Thanks for replying, do you know of someone that might be able to help me out?

---

### Post by acrazyplayer on 2011-02-27
ok I'm trying it out now but i will not be able to actually tell you how to use this program as I do not have a amd processor but I will help you get it up and running.

first open a terminal and run "sudo apt-get install build-essential"

let it install

then navigate to where you downloaded and extracted the folder by doing in the terminal " cd /home/*username here*/Downloads/tpc-0.30/src/"

you want to go to the src folder like in the example because in there is 2 files that start with compile, now depending on what version of ubuntu you have you will want to execute that version of the compile file. so if you downloaded the 64 bit ubuntu then choose the x86_64 if not then choose the other, in the terminal, so I will assume you have the i386 (32 bit) ubuntu installed and will go from there.

so while you are still in the terminal in the src folder type in "./compile_i386.sh" and hit enter, hopefully it should work for you, it wont for me because I don't have what it needs (the processor I think) so give that a shot and report back what you find in case you still need some more help


also in the tpc folder is a "doc" which contains a readme.pdf and on page 23 it says all what I said in better detail and gives you more information.

for example after you compile the program you will find it in the bin folder of tpc and you run it how you did above in your first post as root.

---

### Post by nico_mic on 2011-02-27
Finally ill be using the program!!
Thank you =) I thought the program was already compiled in the bin folder, And if it hadn't been there i wouldn't have solved myself either since i don't know what compiling is yet ><

Thanks again acrazyplayer for your help =) Much appreciated!!!

---

### Post by nico_mic on 2011-02-27
Ran into another wall... things got messy!
To be continued here: [http://phoronix.com/forums/showthread.php?26065-New-tool-for-undervolt-overclock-AMD-K8L-and-K10-processors/page12](http://phoronix.com/forums/showthread.php?26065-New-tool-for-undervolt-overclock-AMD-K8L-and-K10-processors/page12)

---

