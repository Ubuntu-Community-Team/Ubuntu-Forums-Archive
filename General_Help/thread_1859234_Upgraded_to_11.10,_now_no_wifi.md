---
title: "Upgraded to 11.10, now no wifi"
date: 2011-10-13
forum: General Help
---

### Post by ernestj on 2011-10-13
I was using Ubuntu 11.04. My wifi worked great. Today, I upgraded to 11.10 and now I can not access the Internet. Wifi is can locate hotspot, but is not connecting.

---

### Post by Kai Summers on 2011-10-13
Try wired connection hopefully that still works now quickly perform update, if still no wifi then have a look in System -> Administration -> Additional Drivers and see if there are any third party drivers that can be installed.

---

### Post by collisionystm on 2011-10-13
Try this...

Open terminal

type

sudo rfkill unblock all

put in your password

reboot the computer

---

### Post by gefthebest on 2011-10-14
I have the same issue.. that didn't fix it.
[http://fnaard.blogspot.com/2011/09/restoring-wifi-on-vaio-updated-to.html](http://fnaard.blogspot.com/2011/09/restoring-wifi-on-vaio-updated-to.html)
didn't either because nowhere was rt2xxx blacklisted...

Thank for your help

PS: I have Intel Wifi 5100 on laptop

---

### Post by ernestj on 2011-10-14
Did you try the trick in the blog? What is the fix?

---

### Post by garvinrick4 on 2011-10-14
It is a kernel driver I do believe "iwlagn"
```
lspci -nnk | grep -iA2 net
```If says iwlagn driver which it should.
Have you tried a new or different kernel?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Take a newer kernel and click on it. Lets say 3.0.4
Now take:
all.deb and download
Now take:
headers in your 32 or 64 bit whichever your system is download it.
Now take:
Image in your 32 or 64 bit whichever your system is download it.
Now you have 3 .deb packages downloaded click on them one at a time just order downloaded and will install through Ubuntu software center. Once all 3 done installing.
Reboot into new kernel 3.0.4 and see if Wifi works. Just to see if it is a kernel driver thing. "iwlagn" has been stable for me in 3.0 and up in oneiric. I choose 3.0.4 just at
random because it is newer than one you are using.
[COLOR=Red]Read below if do not know if 32 or 64 bit.[/COLOR]
```
uname -a
```Tells you if you have 64 bit such as below if does not say this you have 32 bit.
x86_64 x86_64

## If does not do it then can boot from previous kernel and remove in synaptic if you want to remove.
```
sudo apt-get install synaptic
```type 3.0.4 in search window and remove kernel image.
[COLOR=Red]
#I know you all are new so if this seems a bit scary just ignore.[/COLOR]

---

### Post by gefthebest on 2011-10-14
> **ernestj said:**
> Did you try the trick in the blog? What is the fix?

Yes I did try the fix, it was to remove any blacklisted adaptors from  the files in /etc/modprobe.d.... but I don't even have an ath adaptor so  that can't work...


> **garvinrick4 said:**
> try new or different kernels
Thanks, I will try later today

---

