---
title: "Adobe Reader"
date: 2012-05-31
forum: General Help
---

### Post by borgward on 2012-05-31
Ubuntu 10.04
I went to Applications -> Ubuntu Software Center -> Get Software -> Canonical Partners -> Adobe Reader 9 -> Install -> Authentication ..... entered password -> Install 

Download begins, but then "Failed to download ..." appears. Details reveals message: "Check your internet connection" (I do indeed have connection) ;Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.4.6-0lucid1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.4.6-0lucid1_i386.deb) 404  Not Found [IP: 91.189.92.191 80];

I need Adobe reader because Document reader will not read some PDF's

I am wondering if Adobe Reader 9 is still available at Ubuntu Software Center. If not where can I get it?

 ping  91.189.92.191 80
PING 80 (0.0.0.80) 56(124) bytes of data.
^C
--- 80 ping statistics ---
18 packets transmitted, 0 received, 100% packet loss, time 17017ms

 ping  91.189.92.191
PING 91.189.92.191 (91.189.92.191) 56(84) bytes of data.
64 bytes from 91.189.92.191: icmp_seq=1 ttl=48 time=189 ms
.............
64 bytes from 91.189.92.191: icmp_seq=7 ttl=48 time=188 ms
^C
--- 91.189.92.191 ping statistics ---
8 packets transmitted, 7 received, 12% packet loss, time 7007ms
rtt min/avg/max/mdev = 171.734/180.966/189.220/6.572 ms

---

### Post by scouser73 on 2012-05-31
Hi,

1 Go to [[COLOR="Red"]**Adobe Reader**[/COLOR]]("http://get.adobe.com/uk/reader/otherversions/")

2 The 1st drop-down menu find and select Linux

3 The 2nd drop-down menu find and select your language of choice

4 The 3rd drop-down menu find and select Reader 9.5.1 (.deb)

5 Click on Download Now, once downloaded simply install.

---

### Post by raja.genupula on 2012-05-31
> **scouser73 said:**
> Hi,

1 Go to [[COLOR=Red]**Adobe Reader**[/COLOR]]("http://get.adobe.com/uk/reader/otherversions/")

2 The 1st drop-down menu find and select Linux

3 The 2nd drop-down menu find and select your language of choice

4 The 3rd drop-down menu find and select Reader 9.5.1 (.deb)

5 Click on Download Now, once downloaded simply install.

+1 &  to install a .DEB file 
-- Open it with** Software center **
( or )
 -- **sudo dpkg -i <pathtofilename.deb>**

---

### Post by raja.genupula on 2012-05-31
> **borgward said:**
> Ubuntu 10.04
I went to Applications -> Ubuntu Software Center -> Get Software -> Canonical Partners -> Adobe Reader 9 -> Install -> Authentication ..... entered password -> Install 

Download begins, but then "Failed to download ..." appears. Details reveals message: "Check your internet connection" (I do indeed have connection) ;Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.4.6-0lucid1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.4.6-0lucid1_i386.deb) 404  Not Found [IP: 91.189.92.191 80];

I need Adobe reader because Document reader will not read some PDF's

I am wondering if Adobe Reader 9 is still available at Ubuntu Software Center. If not where can I get it?

 ping  91.189.92.191 80
PING 80 (0.0.0.80) 56(124) bytes of data.
^C
--- 80 ping statistics ---
18 packets transmitted, 0 received, 100% packet loss, time 17017ms

 ping  91.189.92.191
PING 91.189.92.191 (91.189.92.191) 56(84) bytes of data.
64 bytes from 91.189.92.191: icmp_seq=1 ttl=48 time=189 ms
.............
64 bytes from 91.189.92.191: icmp_seq=7 ttl=48 time=188 ms
^C
--- 91.189.92.191 ping statistics ---
8 packets transmitted, 7 received, 12% packet loss, time 7007ms
rtt min/avg/max/mdev = 171.734/180.966/189.220/6.572 ms

one possibility might be server down .
Have you tried changing the server from settings of update manager ?

If not open update manager-> settings -> in the 1st TAB -> at Download from change it to main server or best server then try again with what you are doing .

All the best :)

---

### Post by Primefalcon on 2012-05-31
To be honest you'd be better looking at Okular than Reader, simply because adobe has killed off Linux support for air, flash and I wonder if they will continue support for reader even... seems like it's the last left as of now.

---

### Post by borgward on 2012-06-01
> **raja.genupula said:**
> +1 &  to install a .DEB file 
-- Open it with** Software center **
( or )
 -- **sudo dpkg -i <pathtofilename.deb>**
I downloaded the reader from Adobe

Adobe Reader is a .bin file.

Here is what I did:


1:26:15 XYZ@1520: ~$ sudo dpkg -i /home/XYZ/Desktop/AdbeRdr9.5.1-1_i486linux_enu.bin
dpkg-deb: `/home/XYZ/Desktop/AdbeRdr9.5.1-1_i486linux_enu.bin' is not a debian format archive
dpkg: error processing /home/XYZ/Desktop/AdbeRdr9.5.1-1_i486linux_enu.bin (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /home/XYZ/Desktop/AdbeRdr9.5.1-1_i486linux_enu.bin

How to make .bin work?, or where to get .deb from?

---

### Post by rewyllys on 2012-06-01
> **borgward said:**
> . . . . or where to get .deb from?
Go to [http://get.adobe.com/reader/otherversions/]("http://get.adobe.com/reader/otherversions/")

Work your way though Steps 1 and 2.  Then Step 3 will offer you four different download versions, one of which is a ".deb" file.

Enjoy.

---

### Post by raja.genupula on 2012-06-01
> **borgward said:**
> I downloaded the reader from Adobe

Adobe Reader is a .bin file.

Here is what I did:


1:26:15 XYZ@1520: ~$ sudo dpkg -i /home/XYZ/Desktop/AdbeRdr9.5.1-1_i486linux_enu.bin
dpkg-deb: `/home/XYZ/Desktop/AdbeRdr9.5.1-1_i486linux_enu.bin' is not a debian format archive
dpkg: error processing /home/XYZ/Desktop/AdbeRdr9.5.1-1_i486linux_enu.bin (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /home/XYZ/Desktop/AdbeRdr9.5.1-1_i486linux_enu.bin

How to make .bin work?, or where to get .deb from?

if its a bin file then first we have to give perissions to execute it so the command for it is
```
chmod +x AdbeRdr9.5.1-1_i486linux_enu.bin
```

then we have to run it like
```
./AdbeRdr9.5.1-1_i486linux_enu.bin
```

---

