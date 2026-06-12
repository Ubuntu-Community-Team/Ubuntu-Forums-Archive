---
title: "Error with dd if=/dev/cdrom of=image.iso"
date: 2009-09-07
forum: General Help
---

### Post by jamesje on 2009-09-07
Hey fellow (k)ubuntu users,

I am pretty new to the Kubuntu 9.04 community and I have run into a little problem after scanning google and forums i found out i could rip CD's and could save as .iso, when i tried all possible ways i found that this had the best reputation. But i couldn't find i way to get this to work.. loads of people have said "Yay it works THANKYOU" yet i cant say that right now. When i do the line it only copies 1.7 mb and it is a 700MB disc. 

If anyone knows anything that might be the slightest of help. Please help me.

Thank you in advance, James

p.s this is what i get

james@Anonymous:~$ dd if=/dev/cdrom of=image.iso 
dd: reading `/dev/cdrom': Input/output error
810+0 records in
810+0 records out
1658880 bytes (1.7 MB) copied, 26.1928 s, 63.3 kB/s

---

### Post by tiagosales on 2009-09-07
Please, paste here the output from:
```
sudo lshw -c disk
```
```
ls -lha /dev/cd* /dev/dvd*
```
```
df -h
```

Sales, Tiago.

---

### Post by jamesje on 2009-09-07
In that order.


  *-disk                            
       description: ATA Disk        
       product: WDC WD6400AACS-0    
       vendor: Western Digital      
       physical id: 0               
       bus info: scsi@0:0.0.0       
       logical name: /dev/sda       
       version: 05.0                
       serial: WD-WCAUF2551218      
       size: 596GiB (640GB)         
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=2bab359d
  *-cdrom                                             
       description: DVD-RAM writer                    
       product: DVDRAM GH22NS40                       
       vendor: HL-DT-ST                               
       physical id: 1                                 
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: NL00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc



james@Anonymous:~$ ls -lha /dev/cd* /dev/dvd*
lrwxrwxrwx 1 root root 3 2009-09-07 13:22 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2009-09-07 13:22 /dev/cdrw -> sr0
lrwxrwxrwx 1 root root 3 2009-09-07 13:22 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2009-09-07 13:22 /dev/dvdrw -> sr0



james@Anonymous:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             578G  6.9G  542G   2% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G  212K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  140K  1.6G   1% /dev
tmpfs                 1.6G   12K  1.6G   1% /dev/shm
lrm                   1.6G  2.4M  1.6G   1% /lib/modules/2.6.28-11-generic/volatile


Thanks so much in advance ^^

---

### Post by tiagosales on 2009-09-07
Apparently, all is ok.
Do you get burn images to cd or copy cds and dvds?
Did you try generate a iso in some app(Brasero or gnomebaker)??

---

### Post by jamesje on 2009-09-07
I have not tried any applications i just read on google somewhere that you just type that and it works.. i take it it was wrong?

maybe some usefull info:

installed kubuntu 9.04 yesterday and i dont know all the programs i need to make it run perfectly.

---

### Post by fbianconi on 2009-09-07
Looks like a scratch on the cd, otherwise it wouldn't even start.
If you decide that is your problem gddrescue may be handy.
Can you try in some other drive or another PC?

---

### Post by tiagosales on 2009-09-07
Check this link:

[http://stikiflem.wordpress.com/2008/08/29/make-iso-file-in-ubuntu/](http://stikiflem.wordpress.com/2008/08/29/make-iso-file-in-ubuntu/)

Show how generate iso in the graphic way.

---

### Post by jamesje on 2009-09-07
> **fbianconi said:**
> Looks like a scratch on the cd, otherwise it wouldn't even start.
If you decide that is your problem gddrescue may be handy.
Can you try in some other drive or another PC?


Well i have tried more than one disc but cant use any other pc i have the only one in the house i can use.


> **tiagosales said:**
> Check this link:

[http://stikiflem.wordpress.com/2008/08/29/make-iso-file-in-ubuntu/](http://stikiflem.wordpress.com/2008/08/29/make-iso-file-in-ubuntu/)

Show how generate iso in the graphic way.

I am running Kubuntu and K3b doesnt even recognise my cd drive i dont think.. its a dvdrw but still K3b says "please insert a complete or appendable medium"

---

### Post by tiagosales on 2009-09-07
Do you have other OS?
Did you test the DVD drive in Windows?
I'm suspecting that your DVD drive is bad.

---

### Post by mc4man on 2009-09-07
You didn't mention what type of cd your trying to copy.

Overall dd is not that well suited to removable (optical) media. with the command your using even 1 read error will halt dd.

You'd have to add a conv=noerror option to get around that, again not really what you'd want to do

If it's an audio cd then dd is no good for that at all (from what I see

The suggestion in post 7 is good 
 
If it's a data cd with some possible hard or unreadable to read sectors then try dvddisaster
Leave the  read tries at the default of one for the first pass (if there are unreadable sectors it may take awhile

If there were unreadable sectors then up the read tries to 5 and run again. dvddisater only attempts to read sectors missed from previous read.

If there is success on recovering sectors but some remaining then up the try's to 10 and re run.

If your drive is at fault then this may be a waste of time (or take a very long time
Sometimes some canned air can help a drive, otherwise a new one is best option

---

### Post by jamesje on 2009-09-08
> **tiagosales said:**
> Do you have other OS?
Did you test the DVD drive in Windows?
I'm suspecting that your DVD drive is bad.


I have tried it on windows the reason i went over to Kubuntu is cause my windows failed on me with some bluescreens but my drive worked perfectly on there.

> **mc4man said:**
> You didn't mention what type of cd your trying to copy.

Overall dd is not that well suited to removable (optical) media. with the command your using even 1 read error will halt dd.

You'd have to add a conv=noerror option to get around that, again not really what you'd want to do

If it's an audio cd then dd is no good for that at all (from what I see

The suggestion in post 7 is good .......


I am trying to rip a few games off disc so i can put them on my friends EEE laptop cause it has no cd/dvd drive. I have tried more than 5 different discs but i can play the games but can't rip them. maybe there is some kind of protection seeing as they are all DVD roms?

---

### Post by jamesje on 2009-09-08
> **tiagosales said:**
> Apparently, all is ok.
Do you get burn images to cd or copy cds and dvds?
Did you try generate a iso in some app(Brasero or gnomebaker)??

I just tried to burn an iso to disc that also is not possible. I don't understand cause i can install games or copy data off disc's yet i cant make or burn iso's.

---

### Post by jamesje on 2009-09-09
Okay I have just reinstalled my pc this time no kubuntu but ubuntu 9.04 and problem = fixed thanks for those who tried to help ^^

---

