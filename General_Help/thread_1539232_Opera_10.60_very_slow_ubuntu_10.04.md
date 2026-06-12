---
title: "Opera 10.60 very slow ubuntu 10.04"
date: 2010-07-26
forum: General Help
---

### Post by Lost-Found on 2010-07-26
Hi,

I'm on ubuntu 10.04 32-bit desktop. Somehow Opera 10.60 is very slow to load.


I just switched from FF to Opera, and (I'm pretty sure, might be dreaming though) that the first few days it was lightning fast.. and now it takes like 10+ secs to load any page.

---

### Post by tdayal on 2010-07-26
Did you try reinstalling Opera?

---

### Post by Lost-Found on 2010-07-26
It's even though I did some fresh-installs of ubuntu itself. Happend before I did it, and keep on being a problem.

---

### Post by bilmas on 2010-07-26
i'm having this same problem.  the same version runs fine on my mac which is an older computer with less memory

opera starts up quickly enough but opening new tab and simply navigating websites is almost always plagued with lag and sometimes opera will fail to load a page simply because it is running so slowly.  chrome will load that same page almost instantly.  

does anybody know why this should be happening?

davidbilmas

---

### Post by Lost-Found on 2010-07-27
Try changeing DNS to googles. 8.8.8.8 + 8.8.4.4

Did something here :D

---

### Post by bilmas on 2010-07-27
for me it's the software itself, not just the loading of sites.  so long as the software is running properly the sites load the same

---

### Post by darolu on 2010-07-30
I had this problem and I managed to solve it.

The problem is not Opera configurations I think, the problem seems to be how Ubuntu handles IPv6 (and probably bad routers too), chances are good that Firefox is also slow in your system.

So the solution is to **disable IPv6**.

There are more than 1 method to do it, I did all of them (well the ones I know) to solve it, so I'm not sure which one actually did it so here they are.

1.) Blacklist ipv6: Open gedit with super user powers and edit/create a file named "blacklist" in your /etc/modprobe.d/ directory.
```
gksu gedit /etc/modprobe.d/blacklist
```
And add this lines:
```
# Disable ipv6
blacklist ipv6
```

2) Create aliases in your /etc/modprobe.d/: similar to the previous one, the difference is that the file you are going to edit/create is named "aliases":
```
gksu gedit /etc/modprobe.d/aliases
```
And you add these lines:
```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6
```

After saving the files you will need to reboot.

3) Stopping ipv6 from your Grub, again open gedit with super user powers and edit the /etc/default/grub file:
```
gksu gedit /etc/default/grub
```

There find the line that says **GRUB_CMDLINE_LINUX=""** and change it to:
```
GRUB_CMDLINE_LINUX="ipv6.disable=1"
```
Save the file and run:
```
sudo update-grub
```
Then reboot and Opera should be working as fast as usual.

To prove that ipv6 is indeed disabled you can run:
```
lsmod | grep ipv6
```
and
```
ip a | grep inet6
```
You should se nothing, if you see something means ipv6 is still up.

---

### Post by wiggie on 2010-07-30
Well I have the same problem, had it for some time now. I managed to find a workaround using teredo, however I forgot how to get it working. Now it just works.

Either way I wanted to disable ipv6 and followed darolu's instructions.

Steps 1 and 2 did nothing, and step 3 is not possible since I use grub legacy, not grub2, hence there is no /etc/default/grub file.

I also tried [_[COLOR="Blue"]this[/COLOR]_]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html") but it hasn't worked either. I do get the message that it is disabled, but Opera, thunderbird, firefox still take forever to open a page.

I'm stumped.

---

### Post by darolu on 2010-07-30
Step 3 should work for you too, the difference is you have to add the line in your menu.lst file, for example:
```
gksu gedit /boot/grub/menu.lst
```
And add the **bold text** part to your "kernel /boot" line:
```
kernel /boot/vmlinuz-2.6.31-16-generic root=UUID=bd85aeae-f8e2-4c6c-a759-af537e79da38 ro quiet splash **ipv6.disable=1**
```
Save the file and reboot. Hopefully it will work.

---

### Post by wiggie on 2010-08-11
thank you darolu, I have followed your instructions from your last post and it has worked!
:popcorn:

---

### Post by pterosky on 2010-09-22
I had the same problem with Opera 10.62, but after setting the Start page ("Home page") to nothing, it seems to open up a lot faster. If it stays like this after a reboot is another question.

EDIT: Slow again, after reboot. I will try the ip6 fix mentioned.

---

