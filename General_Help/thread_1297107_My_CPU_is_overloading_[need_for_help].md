---
title: "My CPU is overloading [need for help]"
date: 2009-10-21
forum: General Help
---

### Post by NawafLol on 2009-10-21
Hey Follow Ubuntu Users !

My ubuntu 9.04 use's to much CPU it goes nearly 90.1% on browsing and music playing  !

i'm also using compiz-fusion Desktop wall,and other plugins !
 
My spec are :

Intel Core 2 Duo T6400 (2.0 GHz,800 HMz,2 MB L2 cach)
nVidia G105 512 MB
3 GB DDR3
320 GB HDD

sometimes when i leave it for one hour it goes laggy not like startup ,had some apps crash !

is it my Xorg ? cause it shouldn't be like that !

anyhow comment ,help ,and thanks for reading !

Keep On ubuntuing !

P.S :Using 9.10 didn't fix the problem !

---

### Post by Niko Johnson on 2009-10-21
How much swap do you have?

---

### Post by P4man on 2009-10-21
what process is using those cpu cycles? Find out in system monitor (make sure you enable all process in the view menu) or running ```
top
``` from a terminal.

Also find out if its always a problem, or if things are normal right after a fresh boot and gradually get worse over time (which would indicate a memory leak)

> 
How much swap do you have?

Who cares? With 3GB ram he will probably never need any.

---

### Post by NawafLol on 2009-10-21
i have a 8.6 of swap !

and i tried the "top" command already but couldn't copy and paste it !

is there a hot key for coping !

---

### Post by DeMus on 2009-10-21
> **NawafLol said:**
> i have a 8.6 of swap !

and i tried the "top" command already but couldn't copy and paste it !

is there a hot key for coping !

Ctrl shift C for copying.

---

### Post by P4man on 2009-10-21
> **NawafLol said:**
> i have a 8.6 of swap !

and i tried the "top" command already but couldn't copy and paste it !

is there a hot key for coping !

Just post the name of the process eating up your cpu cycles and tell us how much ram its using.  Or make a screenshot. Or redirect the output to a file

```
top > topresult.txt
```

stop it with control +c

---

### Post by NawafLol on 2009-10-21
op - 19:56:37 up  6:01,  2 users,  load average: 1.70, 1.42, 1.14
asks: 167 total,   3 running, 162 sleeping,   0 stopped,   2 zombie
pu(s):  5.7%us, 59.1%sy,  0.0%ni, 27.6%id,  0.0%wa,  4.6%hi,  3.0%si,  0.0%st
em:   3092140k total,  1149252k used,  1942888k free,   127332k buffers
wap:  9060620k total,        0k used,  9060620k free,   591628k cached

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
4222 nawaflol  20   0  175m  39m  19m R   35  1.3  29:34.73 chromium-browse    
1825 root      20   0  567m  45m  14m R   31  1.5  90:11.61 Xorg               
3771 nawaflol  20   0 82276  32m  14m S   24  1.1  18:56.95 python             
4036 nawaflol  20   0  195m  54m  24m S    9  1.8   8:08.29 chromium-browse    
2561 nawaflol  20   0 82112  48m  14m S    9  1.6  21:46.61 compiz.real        
4604 nawaflol  20   0 42172  14m  10m S    8  0.5   0:11.21 gnome-terminal     
4530 nawaflol  20   0 98.4m  31m  17m S    8  1.0   0:04.64 rhythmbox          
2566 nawaflol  20   0  117m  37m  18m S    7  1.2   2:05.71 nautilus           
4274 nawaflol  20   0  117m  25m  11m S    4  0.8   2:05.90 chromium-browse    
   9 root      15  -5     0    0    0 S    1  0.0   1:13.44 events/0           
  63 root      15  -5     0    0    0 S    1  0.0   2:58.35 kondemand/1        
4724 nawaflol  20   0  2468 1188  884 R    1  0.0   0:00.60 top                
   7 root      15  -5     0    0    0 S    0  0.0   0:08.59 ksoftirqd/1        
  47 root      15  -5     0    0    0 S    0  0.0   0:34.19 scsi_eh_1          
  62 root      15  -5     0    0    0 S    0  0.0   2:53.54 kondemand/0        
1553 root      20   0  3448 1144  972 S    0  0.0   0:28.92 hald-addon-stor    
2335 nawaflol  20   0  7788 4780 2168 S    0  0.2   0:29.51 gconfd-2           

i hope this helps i tried the hot copy key !

---

### Post by P4man on 2009-10-21
something wrong with xorg. seems to be using 500+Mb, thats a memory leak if i ever saw one. Could be caused by the videodrivers or xorg itself. I bet you dont have a problem right after a reboot?

Which videodrivers are you using?

---

### Post by NawafLol on 2009-10-21
nVdidia graphics driver 185 !

---

### Post by NawafLol on 2009-10-21
how can someone fix this ?

---

### Post by QIII on 2009-10-21
Do you have desktop sharing (vino) enabled?  It sometimes hammers your CPU without any indication in top.

Are you using xscreensaver or gnome-screensaver?  I have encountered high CPU usage when using Compiz while xscreensaver is installed.

---

### Post by Sylslay on 2009-10-21
And You have 2 zobie proces on yours machine.
( I know is just before Hallowin),,
but seems to 2 programs strarted and ended in neverland?,:confused:
best option for You:

upgrade Your system to latest.
How?
1)Go for Update manager in System/administatnion,
or 
2) Alt+F2 and run command update-manager
or 
3) In terminal/console 
command line:
sudo apt-get update 
sudo apt-get dist-upgrade,

PS. Make soure that Yours Softwere Source is point at Main Server insted local conutry (usualy delays on latest softwere) 

Last idea, switch off multithreding and boot, while see the grub on screen , press e, 
and edit boot option from grub:
delete splash and quite , and add "nosmp" for switch off 1 cpu, and/or cpumax=0

---

### Post by NawafLol on 2009-10-22
hmmm.... multithreading what is that ?

as for vino i never enabled Desktop shearing !

i tried sudo apt-get update before ,sudo apt-get dist-upgrade, didn't help much !

i will try the grub option ! I want it to remove that damn splashscreen !

And Sylslay what do you mean by ?

 and add "nosmp" for switch off 1 cpu, and/or cpumax=0

And thanks everyone for your help :D

---

### Post by P4man on 2009-10-22
I dont see how disabling a cpu core or "multithreading" (I guess he meant hyperthreading?) would help at all

I propose you do a bit further investigation in to when this problem occurs. Does it happen on a fresh boot? Does it happen after disabling compiz and all unneeded apps and panels and docks and what not?  Just open top in a terminal and keep it running and find out what triggers it.

---

### Post by Sylslay on 2009-10-22
I mean by switch off, 
When You are booting , edit grub line and add some parametrs
Just Prss Tab/ or e letter , than chanege booting line, delete other parametrs and add 3 parametrs

it's from my grub:
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=db96d726-e57f-44b8-af35-279408553c8b ro nosmp, cpumax=0

Ps.Just try, it, it switch symetric load on cpu,
so 1 core don't have to thing what is doing 2 core,

You got "weaker" cpu with better response from user,
but if hardwere - motherboard  is ok, so you see no diffrence , than

---

### Post by Sylslay on 2009-10-23
Had browsing one website with load off flash picture and info-bars,
used 100 proc of my cpu,

Sa I installed flashblock,
and use 22 proc of cpu on that www,,,

or try diffrent flashplugins

---

### Post by NawafLol on 2009-10-24
Hey back ... sorry for not responding  !

tried flashblock didn't help that much ! but better in browsing

so i open a terminal with the "top"command ,when i leave my mouse pointer in a empty space my Xorg uses 5-6 % of the CPU while when i move my mouse randomly it goes to a smacking 64% of CPU uses !

ya i think its The Windows Manger !

again sorry for been away that long time :D !

---

