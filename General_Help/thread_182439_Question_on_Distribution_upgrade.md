---
title: "Question on Distribution upgrade"
date: 2006-05-26
forum: General Help
---

### Post by Cavalierski on 2006-05-26
Hi, ubuntu happy community.

I have a question on distribution upgrade (ex. breezy to Dapper
As far as I understand , the kernel is common among the distributions.(Fedora, Debian...)  Now I have the latest kernel comiled by vanila source based upon breezy which is 2.6.16.18.

Then the distribution is based upon the kernel with a lot of modified applications for one distribution. Therefore it seems that I don't have to dist upgrade to Dapper if I modify apt line from breezy to dapper and apt-update/upgrade will upgrade me to the up-to-date Dapper modified applications even with the newer kernel compare to Dapper.

Is my understanding right?

Thanks in advance for your support :D

---

### Post by Sef on 2006-05-26
> Is my understanding right?

No.  You have to dist-upgrade to get all the updates.

---

### Post by Jussi Kukkonen on 2006-05-26
The easiest way to stay on the same kernel is probably doing a normal dist-upgrade, and then editing /boot/grub/menu.lst to that your original kernel is the default -- the old kernels aren't removed on a dist-upgrade.

EDIT: Personally, I'd advice against doing this if you aren't aware of any problems with the newer kernels -- the amount of testing your planned setup has received is small, whereas the default Dapper kernel combined with Dapper software is tested extensively...

---

### Post by Cavalierski on 2006-05-26
Thank you for the prompt reply :) 
I still have 2 questions...

> **Jussi Kukkonen]The easiest way to stay on the same kernel is probably doing a normal dist-upgrade, and then editing /boot/grub/menu.lst to that your original kernel is the default -- the old kernels aren't removed on a dist-upgrade.[/QUOTE]

Q1)
This case, dis-upgrade will install the kernel & the (Dapper modified ) applications right? So if I still want to use the up-to-date kernel, steps are:
1) dist-upgrade
2) download vanila kernel & compile it using upgraded Dapper
3) Done  said:**
> EDIT: Personally, I'd advice against doing this if you aren't aware of any problems with the newer kernels -- the amount of testing your planned setup has received is small, whereas the  [COLOR="Red"]default Dapper kernel[/COLOR] combined with Dapper software is tested extensively...

Q2)
If you say [COLOR="Red"]"default Dapper kernel"[/COLOR], does this mean that the kernel itself is also modified for Dapper? My understanding is that the kernel is exactly same among the any distributions, only the difference is the applications on top of the kernel. (Every time the kernel is released at kernel.org , I compile it and test it with ubuntu and Debian. So far no problem on any ubuntu modified applications which I think proof that the kernel itself is the same.)

So I thought the dist-upgrade is not necessary to keep ubuntu applications up-to-date. Just changing apt-line from breezy to dapper solve the issue...

Will you teach me if I'm wrong and thanks for your time :)

---

### Post by Jussi Kukkonen on 2006-05-26
> Q1)
This case, dis-upgrade will install the kernel & the (Dapper modified ) applications right? So if I still want to use the up-to-date kernel, steps are:
1) dist-upgrade
2) download vanila kernel & compile it using upgraded Dapper
3) Done 
If you already have the kernel you want in Breezy there's no need for phase two, I believe -- you can keep using it.

> 
  If you say "default Dapper kernel", does this mean that the kernel itself is also modified for Dapper? My understanding is that the kernel is exactly same among the any distributions, only the difference is the applications on top of the kernel.
Well, I just meant the kernel that comes installed on Dapper -- but yes, distros do modify kernels. I'm not sure if Ubuntu does this (I'm guessing they do).

**EDIT: (I'm too fast again)**
> 
So I thought the dist-upgrade is not necessary to keep ubuntu applications up-to-date. Just changing apt-line from breezy to dapper solve the issue...
I'd expect a lot of problems there... *dist-upgrade* is more than *upgrade*: e.g. upgrade won't remove anything (even if another package would be better) and it won't install new software. Even if it worked you'd be working with a setup no-one else has tested.

---

### Post by az on 2006-05-26
[QUOTE=Cavalierski]
As far as I understand , the kernel is common among the distributions.(Fedora, Debian...)  Now I have the latest kernel comiled by vanila source based upon breezy which is 2.6.16.18.[/QUOTE]

Well, they are the same in that they are linux.  But they are confiigured and patched differently.

And there is much much more to your system than the kernel.  The kernel is just the interface between the hardware and the rest of the software.  There is an ocean of software that makes up the Ubuntu desktop that is continually evolving.  A stable release is a snapshot of that development, made to work together.

---

### Post by Cavalierski on 2006-05-26
First of all, Jussi Kukkonen / azz , thanks for your time.

I'm almost there. But still some questions...

[QUOTE=Jussi Kukkonen]If you already have the kernel you want in Breezy there's no need for phase two, I believe -- you can keep using it.[/QUOTE]

I'm bit hesitate to do dist-upgrade as I just finish customizing ubuntu for my wife at home :) 
But my guess is that if I do dist-upgrade , it probably do ubuntu (Dapper) kernel installation as well as s/w upgrade. The reason why I think so is that if it just upgrade of the application s/w, we can do it by apt-upgrade, right?

[QUOTE=Jussi Kukkonen]upgrade won't remove anything (even if another package would be better) and it won't install new software.[/QUOTE]

I thought that apt-upgrade does remove old version and install new version, does it?

[QUOTE=azz]Well, they are the same in that they are linux. But they are confiigured and patched differently.
And there is much much more to your system than the kernel. The kernel is just the interface between the hardware and the rest of the software. There is an ocean of software that makes up the Ubuntu desktop that is continually evolving. A stable release is a snapshot of that development, made to work together.[/QUOTE]

Ok, let me write my understanding so far. The interfaces are the same. Some patches are added on vanila kernel (depending on distributions) That's why I can use vanila kernel on ubuntu without any problem. 

If so, I still think that I have latest kernel and I don't need to dist-upgrade but apt-upgrade application s/w is enought...

There might be the s/w layer such as below, so that I could understand dist-upgrade is really important even the kernel version is up to date as well as keeping the kernel version after the dist-upgrade as this dist-upgrade update ubuntu platform...

------s/w layer------
|Application s/w   |
|Ubuntu Platform| <= (My guess :this depens on Breezy or Dapper)
|Kernel                 |
|Device                |

hmm. Still too many to know [-(   it's fun though :)

---

### Post by Cavalierski on 2006-05-26
OK , here we go.

I looked into web and found the following at [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)

[I]New Kernel

The latest and greatest Linux kernel, version 2.6.15, is now the new default kernel which adds to the stability of Ubuntu. In order to further improve the speed of Ubuntu, there are now two distinct groups of kernel configurations. One configuration is tuned for desktop use and the other is tuned for server use.
Desktop Kernel

The desktop kernel provides a smoother and more pleasant user experience by turning on preemptive multitasking and other features meant to allow user processes (your running applications like Firefox and Rhythmbox) to run without ever skipping a beat.
Server Kernel

The server kernels are tuned differently from the desktop kernels providing better performance for server applications. The server kernel is generic, and should work on the same equipment that the desktop kernel runs on. The big iron server kernel is geared towards systems with greater than 8 CPUs (ES7000/Summit/BIGSMP). [/I]

Yep, there is a kernel customization on Distribution and much more as azz and Jussi Kukkonen pointed out. Especially the following , I somehow get it.

[QUOTE=azz]
And there is much much more to your system than the kernel. The kernel is just the interface between the hardware and the rest of the software. There is an ocean of software that makes up the Ubuntu desktop that is continually evolving. A stable release is a snapshot of that development, made to work together.[/QUOTE]

Now I'm upgrading the dist without the consent of my wife:-D  Now it's mission critical 8) 

OK, after dist-upgrade is done , I'll update how the current latest kernel will be treated.. Good luck on me;)

---

### Post by Cavalierski on 2006-05-27
Here I am again to give a feedback on my try.

 Last night I did dist-upgrade, everything excellent:) 
 (except aMSN which I installed by following this forums "How-to" didn't work because of the segmentation error.
[http://ubuntuforums.org/showthread.php?t=87001&highlight=amsn+dapper](http://ubuntuforums.org/showthread.php?t=87001&highlight=amsn+dapper)

This is how to fix, remove the following library & symbolic link.
(1)step1: deb package to remove
sudo apt-get remove tcl8.5_8.5.0-1~neto3_i386.deb
sudo apt-get remove tk8.5_8.5.0-1~neto3_i386.deb
sudo apt-get remove amsn_0.95-1~neto1_i386.deb
(2)step2:symlink to remove
sudo rm /usr/lib/libtk8.5.so.0 libtk8.5.so
sudo rm /usr/lib/libtcl8.5.so.0 libtcl8.5.so

Then follow the above instraction again to install it. (you might need to remove tk8.4 and tcl8.5 package if it is installed.)

 Then after the dist-upgrade, I also got the kernel installed.(2.6.15-23-386) And the previous kernel made from vanila kernel(2.6.18) installed on the box is also available & stable to use on Dapper. I also recompile the same kernel source with the same config to see the difference on Breezy and Dapper. I didn't check detail but just MD5sum gave me the different binary (this might depends on the gcc version rather than distribution..:-k 

 Anyway what I learned from the comunity about distribution upgrade are:
1) The kernel source on each distribution may differ from the vanila kernel ( Modified to work faster/stable : however applying ck kernel patch works better though)
2) Dist-upgrade will provide the  kernel itself as well as heaps of other application upgrade.
3) Even after the dist-upgrade, the kernel compiled with the previous version ( Breezy) works fine. ( Because the interfaces of the kernel kept same )
4) Ubuntu community is very happy and sweet. :KS 

Thank you all!

# By the way recently I changed servers at work from WIndow$ $erver to Debian. I faced some problems on Dell PowerEdge 1850 h/w (PERC raid controller etc) finally I figured out and all the servers at my lab turned into Debian. However what I did was not so sophisticated, probably I could do it by making customized live cd which kernel supports megaraid (which is maybe supported after 2.6.11 )diriver etc.  Only if the Dapper is released bit earlier I could use ubuntu for it. Never mind. I'll probably give a try later.;)

---

