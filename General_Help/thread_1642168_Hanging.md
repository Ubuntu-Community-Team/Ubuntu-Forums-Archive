---
title: "Hanging"
date: 2010-12-10
forum: General Help
---

### Post by sandeepnaik on 2010-12-10
[SIZE=3]Hello all, I have just installed Ubuntu 10.10 and there is a problem whose reason I couldn't understand, so please help.

It hangs sometimes while I work, without any reason, mouse-keyboard go freeze and nothing happens untill I restart my system.

I did not make any mistake while installing it, then what is the problem, I couldn't understand it's reason! Can anyone tell me why it is happening and how should I fix this?
[/SIZE]

---

### Post by fatharraxman on 2010-12-10
could you answer these Qs please ?
-is it installed inside windows or from cd,or usb, is it installed alongside other os?
-what is your computer ? RAM? processor ? and so
-how much space did you installed on ? and how much free space  available ?

---

### Post by sikander3786 on 2010-12-10
Welcome to the forums :-)

In addition to questions in above post, we would also like to know that do you remember any specific application running at the time when it hangs? Or it is just random?

Which graphics card is there?

Applications > Accessories > Terminal

```
lspci | grep VGA
```

Did you install any proprietary drivers for that? Did you enable compiz?

---

### Post by sandeepnaik on 2010-12-10
could you answer these Qs please ?
-is it installed inside windows or from cd,or usb, is it installed alongside other os?
-what is your computer ? RAM? processor ? and so
-how much space did you installed on ? and how much free space  available ?

1. It has not been installed alongside other OS. I installed it from CD whose iso image I got from Ubuntu website.
2. My PC's RAM is 512 MB and Processor 1.6 Ghz Dual Core and total HDD is 160 GB.
3. How I installed:
3 (i) First I created (/boot) as Primary having Ext4 journalising file system of size 500 MB at begining location.
3 (ii) Then created (/) also as Primary having Ext4 journalising file system of size 20000 MB at begining location.
3 (iii) Then created (swap area) also as Primary having twice the size of my RAM i.e. 1024 MB at begining location.
3 (iv) Lastly I created (/home) as Logical having rest of the size of my HDD i.e. 138 GB approx. at begining location.

Now after installation File System Drive shows 14.4 GB free space and Home Folder shows 113.8 GB free space (after saving my personal data, such as songs, videos, phtotos etc.

---

### Post by sandeepnaik on 2010-12-10
Firstly, when my brother was using he told that I hanged while he was scrolling through System>Preferences and mouse pointer got freeze then OS stopped working until he restarted the PC.
Secondly, when I was writing iso image of Xubuntu on CD it hanged at everything got freeze until I restarted the PC.

My Graphic Card is: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

---

### Post by sandeepnaik on 2010-12-10
Did you install any proprietary drivers for that? Did you enable compiz?

No, I did not enable compiz.
I have not yet installed any proprietary drivers, when I go through System>Administration>Additional Drivers it showed: No proprietary drivers are in use on this system.

---

### Post by 3rdalbum on 2010-12-10
It sounds like faulty memory. You're probably running into it quite frequently because you don't have a lot of RAM.

Try borrowing some different RAM and see if the problem occurs with that - or, if your computer has two memory sticks to make up the 512mb, try taking one out (if you still get the problem, put it back in and take the other one out and see if that fixes it).

Faulty memory is very common. Very.

---

### Post by 3rdalbum on 2010-12-10
It sounds like faulty memory. You're probably running into it quite frequently because you don't have a lot of RAM.

Try borrowing some different RAM and see if the problem occurs with that - or, if your computer has two memory sticks to make up the 512mb, try taking one out (if you still get the problem, put it back in and take the other one out and see if that fixes it).

Faulty memory is very common. Very.

---

### Post by fatharraxman on 2010-12-10
It is better to have 1gb memory or more to amuse Ubuntu but 512 mb ram is the least required, if you can not bring memory now for whatever reason I suppose you to install lubuntu or xubuntu > sudo apt-get lubuntu-desktopand you will see how fast it is until you get your memory

---

### Post by kanishkdudeja on 2010-12-10
post the output of ```
top
```

---

### Post by sandeepnaik on 2010-12-10
@ [3rdalbum]("http://ubuntuforums.org/member.php?u=61044")

Hey! Thanks.

I have 512 MB DDR2 RAM currently.
Now I am going to buy new RAM of 2 GB.

Please tell me that:
1. What is a SWAP Partition?
2. What it does?
3. Is it necessary to create it?
4. I read somewhere on internet that, SWAP Partition should be made of double size of your RAM, is it necessary to do so?
5. As currently I have 512 MB DDR2 RAM and SWAP Partition of 1024 MB then If I buy a new RAM of 2 GB then should I again create a new SWAP Partition of 4096 MB removing previous one of 1024 MB?

---

### Post by sandeepnaik on 2010-12-10
@ [fatharraxman]("http://ubuntuforums.org/member.php?u=1176779")

No Sir, I can buy a new 2 GB DDR2 RAM.
I liked Ubuntu very much therefore I will not go for any other OS.

Thanks!

---

### Post by sandeepnaik on 2010-12-10
@ kanishkdudeja


top - 10:18:18 up 25 min,  2 users,  load average: 0.15, 0.24, 0.19
Tasks: 150 total,   1 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.1%us,  1.5%sy,  0.0%ni, 96.9%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    499884k total,   460184k used,    39700k free,    21016k buffers
Swap:  1000444k total,        0k used,  1000444k free,   230044k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  936 root      20   0 33504  13m 6884 S    3  2.8   0:33.53 Xorg               
 1799 sandeepn  20   0 91040  13m  10m S    3  2.7   0:01.02 gnome-terminal     
 1603 sandeepn  20   0  296m  78m  27m S    1 16.1   1:12.39 firefox-bin        
 1822 sandeepn  20   0  2624 1132  840 R    0  0.2   0:00.20 top                
    1 root      20   0  2872 1708 1244 S    0  0.3   0:00.48 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.01 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.07 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns

---

### Post by kanishkdudeja on 2010-12-10
looks like memory is running out..i suggest upgrade ur ram to 1 or 2 gb.

---

### Post by sandeepnaik on 2010-12-11
@ kanishkdudeja

Ok Sir, Thanks!
Now I will buy a 2GB RAM.

---

### Post by kanishkdudeja on 2010-12-11
lol..dnt call me Sir please..feels awkward..

anyway id suggest first try to borrow a ram from some frnd and try it out..

if it does not hang only den replace it..

and check ur ram..if it is ddr1 or ddr2..

ur ram may be faulty or less for running ubuntu..

or even both..:P..

---

### Post by sandeepnaik on 2010-12-11
@ kanishkdudeja

Hey I got new 2 GB DDR2 RAM and inserted in my PC then again installed Ubuntu 10.10

but when after completing installation when the message that installation is complete and click to shutdown is displayed I saw the screen showed:

[2993.693601] end_request: I/O error, dev sr0, sector 537844

there were so many lines displayed like this then I pressed enter after removing installation CD the PC restarted after that PC ran normally but I couldn't understand what the error is?

Please tell me urgently!

---

### Post by kanishkdudeja on 2010-12-11
its a common error..u dont need to worry..btw does it hang now?

---

### Post by sandeepnaik on 2010-12-11
No, not hanged at all yet!!! 

But what was that error, can you tell me please?
Because I had no knowledge of installing Linux OSs therefore at even a single unusual thing I installed-reinstalled OSs with formatting my HDD completely. Now I am bored of doing this and want to just enjoy Ubuntu. Please tell me that what was that error and if it was not serious then can it be removed after installing OS?
Will it cause any problem in future using Ubuntu?

---

### Post by kanishkdudeja on 2010-12-11
im sorry. i dont know. i face the same error and many other people too. 

As far as i know it shudnt be a cause of worry..

but if want to fix it desperately..

post the problem in another thread. 

Mayb some other person could help.

---

### Post by choongii on 2010-12-11
Hello,

I've experienced the same problem after upgrading to 10.10 on my laptop. My system would completely freeze at random when I was e.g. browsing the web. Additionally, enabling wifi without the power adaptor plugged in would cause my system to freeze.

After some google-ing around, I circumvented the issue by doing

```
apt-get remove pm-utils
```

This will also uninstall the package acpi-support. I can't put my laptop into sleep mode anymore because of this, but I never did so anyway, so I don't care ;)

Give it a try. If it doesn't work, you can always re-install the packages. I'm curious if this solves the hanging for you.

EDIT: Oh and of course, restart your system after removing pm-utils.

EDIT2: Disregard that. My system just hung again.

---

### Post by HermanAB on 2010-12-11
OK, here are three things to check:
1. Change your video card driver to Vesa and see whether the trouble goes away.
2. Run ifconfig and see whether the ethernet card reports lots of errors.
3. Run dmesg and see whether there are any error messages reported.

---

