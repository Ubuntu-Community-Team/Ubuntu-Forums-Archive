---
title: "go terminal from ubuntu boot cd"
date: 2011-05-23
forum: General Help
---

### Post by pua06 on 2011-05-23
salmo allikm warhmat allah wabrkato 
 
please 
my ubuntu wasn't boot cause unclean shut down 
when i boot that i get
>  
 
[COLOR=navy]**mount: mounting /dev on /root/dev failed: No such file or directory**[/COLOR]
**[COLOR=navy]mount: mounting /sys on /root/sys failed: No such file or directory[/COLOR]**
**[COLOR=navy]mount: mounting /proc on /root/proc failed: No such file or directory[/COLOR]**
**[COLOR=navy]Target System doesn't have requested /sbin/init[/COLOR]**

 
so i boot from ubuntu live CD follow this steps 
like this but in it it boot from usb
[http://ubuntuforums.org/showthread.php?t=1632231](http://ubuntuforums.org/showthread.php?t=1632231)
 
in step 2 open terminal
i don't know how to open terminal
there are four options
check disk......
install ubuntu ......
test memory .......
 
 
thanks

---

### Post by linuxinstalledfromhdd on 2011-05-23
Did you install 10.10 from a disc or USB?

---

### Post by pua06 on 2011-05-23
> **linuxinstalledfromhdd said:**
> Did you install 10.10 from a disc or USB?
 
i installed already ubuntu but now  have problem on it so can't open
i boot from live cd ubuntu  to solve problem but i want to run terminal and write commends 
this the problem

---

### Post by linuxinstalledfromhdd on 2011-05-23
I can't really help you very much because of communication issues.  Maybe someone else here can "guess" at a solution.

For now, if you aren't willing to wait for another user to help you, your best solution for now would be to simply reinstall Ubuntu. 

Try following step-by-step instructions from a nice helpful walkthrough, and you should be OK.

Here is a really nice guide:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by pua06 on 2011-05-23
> **linuxinstalledfromhdd said:**
> I can't really help you very much because of communication issues. Maybe someone else here can "guess" at a solution.
 
For now, if you aren't willing to wait for another user to help you, your best solution for now would be to simply reinstall Ubuntu. 
 
Try following step-by-step instructions from a nice helpful walkthrough, and you should be OK.
 
Here is a really nice guide:
 
[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)
 
 
 
really thanks
may be i was not clear 
so i edit my post and write in details

---

### Post by Hedgehog1 on 2011-05-23
This might solve the language issue: Let the PC explain its situation:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> This might solve the language issue: Let the PC explain its situation:
 
Please boot off the LiveCD/LiveUSB, select 'TRY', and then:
 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.
 
Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.
 
[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]
 
 
***The Hedge***
 
:KS
 
that i understand that  troubleshooting booting problems
it 's good 
but that i asked 
 
Open a terminal (Applications -> Accessories -> Terminal in Gnome) and type :
 
i can't boot to ubuntu to do this previous step that i ask from my thread how open terminal
i am trying to solve with ubuntu cd live but search how open terminal

---

### Post by Hedgehog1 on 2011-05-24
Once you have booted from the LiveCD/LiveUSB:

1) Select the 'TRY' option

2) Menu to** Applications -> Accessories -> Terminal**  from the menu of the LiveCD/LiveUSB.

The LiveCD/LiveUSB is a complete Ubuntu install.

If you still cannot find the 'terminal', then do this to see it:

**<ctrl> + <alt> + t**

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> Once you have booted from the LiveCD/LiveUSB:
 
1) Select the 'TRY' option
 
2) Menu to** Applications -> Accessories -> Terminal** from the menu of the LiveCD/LiveUSB.
 
The LiveCD/LiveUSB is a complete Ubuntu install.
 
If you still cannot find the 'terminal', then do this to see it:
 
**<ctrl> + <alt> + t**
 
 
thanks but when select try ubuntu
 
that i get 
unclean shutown ....................
panic occurred, switching back to text console

---

### Post by Hedgehog1 on 2011-05-24
If you are seeing:

[B]unclean shutown ....................
panic occurred, switching back to text console[/B]

Then you are **not** booting from the LiveCD/LiveUSB. You are still booting from the hard drive (which does not work right now).

You need to boot from the LiveCD or LiveUSB you used to install Ubuntu with.  You may need to change a bios setting to get your computer to boot from the CD first.

---

### Post by Hedgehog1 on 2011-05-24
Wait a minute - I bet you are using the 'Alternate CD' instead of a 'LiveCD'.

When you boot from the CD - do you see these screens:

[IMG]http://img858.imageshack.us/img858/9995/small06tryubuntu.png[/IMG]

and this:

[IMG]http://img202.imageshack.us/img202/5771/small07trygui.png[/IMG]

Are these the screens you are seeing? These are from a LiveCD/LiveUSB.

---

### Post by pua06 on 2011-05-24
thanks
when boot it write boot from cd
i think that i understand wrong
 
i download ubuntu from site then burn it 
follow step on windows 7 in this link
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
then boot from it but it give me four options try install check test memory
 
not like your screen shot
 
can tell me the what i did wrong
thanks so much

---

### Post by Hedgehog1 on 2011-05-24
OK - the CD you have made is the 'Alternate CD' (we use them for installing servers mostly)

The LiveCD is located here:

[http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download")

You will need to choose the 32 bit or 64 bit install - try to choose the same one you are using now.

Once you make a CD of that, you can boot from it (and even visit the Ubuntu forums from it) on your PC that is not booting off the hard drive.

***The Hedge***

:KS

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> OK - the CD you have made is the 'Alternate CD' (we use them for installing servers mostly)
 
The LiveCD is located here:
 
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
 
You will need to choose the 32 bit or 64 bit install - try to choose the same one you are using now.
 
Once you make a CD of that, you can boot from it (and even visit the Ubuntu forums from it) on your PC that is not booting off the hard drive.
 
***The Hedge***
 
:KS
 
*ok thanks sooooooooo much i don't know the differance with alternate and live*
*can i copy file within try ubuntu?*

---

### Post by Hedgehog1 on 2011-05-24
I think you are using 10.10 - right?

If so, you may need to download from here:

[http://releases.ubuntu.com/10.10/]("http://releases.ubuntu.com/10.10/")

Select the **ubuntu-10.10-desktop-amd64.iso** for 64 bit.

Select the **ubuntu-10.10-desktop-i386.iso** for 32 bit.

:P

---

### Post by Hedgehog1 on 2011-05-24
> **pua06 said:**
> ok thanks sooooooooo much i don't know the differance with alternate and live
can i copy file within try ubuntu?

**EDIT:** Please download the ISO on your Windows 7 PC, and burn a new CD from that system

You made a good CD last time this way, you just had the wrong ISO.

:KS :KS :KS

**EDIT:** If you are asking can you copy files from you Ubuntu disk to an external drive or USB stick using the LiveCD - yes you can but AFTER we fix your disk.

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> I think you are using 10.10 - right?
 
If so, you may need to download from here:
 
[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)
 
Select the **ubuntu-10.10-desktop-amd64.iso** for 64 bit.
 
Select the **ubuntu-10.10-desktop-i386.iso** for 32 bit.
 
:P
 
 
ok that i understand from link that  **live cd support only ubuntu-10.10-desktop-i386.iso**
**that support right?**

---

### Post by Hedgehog1 on 2011-05-24
Once you have booted from your new LiveCD & selected 'TRY':

Please run Gparted from the live CD.

Select your hard drive, and then on every Ubuntu partition do a 'check':

[IMG]http://imageshack.us/m/810/3612/chrckparion01.png[/IMG]

This does a check and repair on these partitions.

There is a good chance this will get you running again.

If it does not, then please do this from the LiveCD:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-24
> **pua06 said:**
> ok that i understand from link that  **live cd support only ubuntu-10.10-desktop-i386.iso**
**that support right?**

Yes - that will give you a 32 bit Ubuntu 10.10 Live CD. :D

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> I think you are using 10.10 - right?
 
If so, you may need to download from here:
 
[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)
 
Select the **ubuntu-10.10-desktop-amd64.iso** for 64 bit.
 
Select the **ubuntu-10.10-desktop-i386.iso** for 32 bit.
 
:P
 
 
thanks
ok i am downloading ubuntu [SIZE=3]10.10 netbook[/SIZE] -i386.iso 
 
not **ubuntu-10.10-desktop-amd64.iso** for 32 bit. right?
 
i wrote it wrong in previous post
for this [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
 
it download alternative cd 
right?
cause i downloaded ubuntu 10.10 iso from it in last time

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> Once you have booted from your new LiveCD & selected 'TRY':
 
Please run Gparted from the live CD.
 
Select your hard drive, and then on every Ubuntu partition do a 'check':
 
[IMG]http://imageshack.us/m/810/3612/chrckparion01.png[/IMG]
 
This does a check and repair on these partitions.
 
There is a good chance this will get you running again.
 
If it does not, then please do this from the LiveCD:
 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.
 
Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.
 
[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]
 
 
***The Hedge***
 
:KS
 
 
ok i will follow this
can file from hard send by email or must do check first?

---

### Post by Hedgehog1 on 2011-05-24
Please do the 'check' first.  That may repair the partitions and you may be able to boot normally right after that. :D

If the 'check' does not fix it, then please post the script so we can figure our the next step to fix your PC.



***The Hedge***

:KS

---

### Post by pua06 on 2011-05-24
>  
Please do the 'check' first. That may repair the partitions and you may be able to boot normally right after that. :grin:

If the 'check' does not fix it, then please post the script so we can figure our the next step to fix your PC.





 
 
thanks
 
ok i will check first hope fix my partition

---

### Post by pua06 on 2011-05-24
> **pua06 said:**
> thanks
[COLOR=navy]**ok i am downloading ubuntu [SIZE=3]10.10 netbook[/SIZE] -i386.iso **[/COLOR]
[COLOR=navy][/COLOR]
[COLOR=navy]**not ubuntu-10.10-desktop-amd64.iso for 32 bit. right?**[/COLOR]
[COLOR=navy][/COLOR]
[COLOR=navy]**i wrote it wrong in previous post**[/COLOR]
[COLOR=navy]**for this **[/COLOR][[COLOR=navy]**http://www.ubuntu.com/download/ubuntu/download**[/COLOR]]("http://www.ubuntu.com/download/ubuntu/download")
[COLOR=navy][/COLOR]
[COLOR=navy]**it download desktop cd **[/COLOR]
[COLOR=navy]**right?**[/COLOR]
[COLOR=navy]**cause i downloaded ubuntu 10.10 iso from it in last time**[/COLOR]
 
 
what i said before right ?
i am downloading ubuntu [SIZE=3]10.10 netbook[/SIZE] -i386.iso 
thanks

---

### Post by Hedgehog1 on 2011-05-24
I'm sorry. I am not following your question.

If you are asking about where to get the 10.10 release, it is a different web page:

[http://releases.ubuntu.com/10.10/]("http://releases.ubuntu.com/10.10/")

Select the **ubuntu-10.10-desktop-amd64.iso** for 64 bit LiveCD.

Select the **ubuntu-10.10-desktop-i386.iso** for 32 bit LiveCD.

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> I'm sorry. I am not following your question.
 
If you are asking about where to get the 10.10 release, it is a different web page:
 
[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)
 
Select the **ubuntu-10.10-desktop-amd64.iso** for 64 bit LiveCD.
 
Select the **ubuntu-10.10-desktop-i386.iso** for 32 bit LiveCD.
 
 
the previous is desktop like i downloaded  before and make wrong iso
 
i selected ubuntu [SIZE=3]10.10 netbook[/SIZE] -i386.iso !!!!!!!
 
what i said right or wrong ??

---

### Post by Hedgehog1 on 2011-05-24
If you are running the netbook version of Ubuntu now on your PC, then downloading the netbook 10.10 is fine.

I don't normally use the netbook ISO, so I can only guess as to the tools that are on it.

This web page has the 10.10 **desktop** Live CDs: [http://releases.ubuntu.com/10.10/]("http://releases.ubuntu.com/10.10/")

*The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use.* 

**PC (Intel x86) desktop CD**

**64-bit PC (AMD64) desktop CD**

**PC (Intel x86) netbook live CD**

any of these three should be fine.

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> If you are running the netbook version of Ubuntu now on your PC, then downloading the netbook 10.10 is fine.
 
I don't normally use the netbook ISO, so I can only guess as to the tools that are on it.
 
This web page has the 10.10 **desktop** Live CDs: [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)
 
*The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use.* 
 
**PC (Intel x86) desktop CD**
 
**64-bit PC (AMD64) desktop CD**
 
**PC (Intel x86) netbook live CD**
 
any of these three should be fine.
 
 
 
ok in first time  i download "desktop" from ubuntu site
and burned  it and i get when booting 4 options and you told me that alternate 
really i don't know what do install desktop again ?
may something i understand wrong 
can tell me

---

### Post by linuxinstalledfromhdd on 2011-05-24
You need to research how to install Ubuntu.  Maybe a translated web page in your native language.  You can try posting it in your native language as a new request.

---

### Post by Hedgehog1 on 2011-05-24
Here is the listing from page [http://releases.ubuntu.com/10.10/]("http://releases.ubuntu.com/10.10/").  You can use any of the ones in **BOLD**:

 ubuntu-10.10-alternate-amd64.iso         07-Oct-2010 15:47  694M  Alternate install CD for 64-bit PC (AMD64) computers (standard download)
 ubuntu-10.10-alternate-amd64.iso.torrent 10-Oct-2010 09:22   27K  Alternate install CD for 64-bit PC (AMD64) computers (BitTorrent download)
 ubuntu-10.10-alternate-amd64.iso.zsync   10-Oct-2010 09:21  1.4M  Alternate install CD for 64-bit PC (AMD64) computers (zsync metafile)
 ubuntu-10.10-alternate-amd64.jigdo       10-Oct-2010 09:21  141K  Alternate install CD for 64-bit PC (AMD64) computers (jigdo download)
 ubuntu-10.10-alternate-amd64.list        07-Oct-2010 15:47  101K  Alternate install CD for 64-bit PC (AMD64) computers (file listing)
 ubuntu-10.10-alternate-amd64.metalink    10-Oct-2010 09:25  9.0K  Ubuntu 10.10 (Maverick Meerkat)
 ubuntu-10.10-alternate-amd64.template    07-Oct-2010 15:47   12M  Alternate install CD for 64-bit PC (AMD64) computers (jigdo template)
 ubuntu-10.10-alternate-i386.iso          07-Oct-2010 15:49  693M  Alternate install CD for PC (Intel x86) computers (standard download)
 ubuntu-10.10-alternate-i386.iso.torrent  10-Oct-2010 09:22   27K  Alternate install CD for PC (Intel x86) computers (BitTorrent download)
 ubuntu-10.10-alternate-i386.iso.zsync    10-Oct-2010 09:22  1.4M  Alternate install CD for PC (Intel x86) computers (zsync metafile)
 ubuntu-10.10-alternate-i386.jigdo        10-Oct-2010 09:21  145K  Alternate install CD for PC (Intel x86) computers (jigdo download)
 ubuntu-10.10-alternate-i386.list         07-Oct-2010 15:49  103K  Alternate install CD for PC (Intel x86) computers (file listing)
 ubuntu-10.10-alternate-i386.metalink     10-Oct-2010 09:25  9.0K  Ubuntu 10.10 (Maverick Meerkat)
 ubuntu-10.10-alternate-i386.template     07-Oct-2010 15:49  2.8M  Alternate install CD for PC (Intel x86) computers (jigdo template)
 **ubuntu-10.10-desktop-amd64.iso**           07-Oct-2010 16:24  695M  Desktop CD for 64-bit PC (AMD64) computers (standard download)
 ubuntu-10.10-desktop-amd64.iso.torrent   10-Oct-2010 09:25   27K  Desktop CD for 64-bit PC (AMD64) computers (BitTorrent download)
 ubuntu-10.10-desktop-amd64.iso.zsync     10-Oct-2010 09:24  1.4M  Desktop CD for 64-bit PC (AMD64) computers (zsync metafile)
 ubuntu-10.10-desktop-amd64.list          07-Oct-2010 16:24  4.5K  Desktop CD for 64-bit PC (AMD64) computers (file listing)
 ubuntu-10.10-desktop-amd64.manifest      07-Oct-2010 16:20   37K  Desktop CD for 64-bit PC (AMD64) computers (contents of live filesystem)
 ubuntu-10.10-desktop-amd64.metalink      10-Oct-2010 09:25  8.9K  Ubuntu 10.10 (Maverick Meerkat)
 **ubuntu-10.10-desktop-i386.iso**            07-Oct-2010 16:25  693M  Desktop CD for PC (Intel x86) computers (standard download)
 ubuntu-10.10-desktop-i386.iso.torrent    10-Oct-2010 09:25   27K  Desktop CD for PC (Intel x86) computers (BitTorrent download)
 ubuntu-10.10-desktop-i386.iso.zsync      10-Oct-2010 09:25  1.4M  Desktop CD for PC (Intel x86) computers (zsync metafile)
 ubuntu-10.10-desktop-i386.list           07-Oct-2010 16:25  4.2K  Desktop CD for PC (Intel x86) computers (file listing)
 ubuntu-10.10-desktop-i386.manifest       07-Oct-2010 16:19   38K  Desktop CD for PC (Intel x86) computers (contents of live filesystem)
 ubuntu-10.10-desktop-i386.metalink       10-Oct-2010 09:25  8.9K  Ubuntu 10.10 (Maverick Meerkat)
 **ubuntu-10.10-netbook-i386.iso**            07-Oct-2010 17:50  696M  Netbook live CD for PC (Intel x86) computers (standard download)
 ubuntu-10.10-netbook-i386.iso.torrent    10-Oct-2010 09:23   28K  Netbook live CD for PC (Intel x86) computers (BitTorrent download)
 ubuntu-10.10-netbook-i386.iso.zsync      10-Oct-2010 09:23  1.4M  Netbook live CD for PC (Intel x86) computers (zsync metafile)
 ubuntu-10.10-netbook-i386.list           07-Oct-2010 17:50  4.8K  Netbook live CD for PC (Intel x86) computers (file listing)
 ubuntu-10.10-netbook-i386.manifest       07-Oct-2010 17:44   37K  Netbook live CD for PC (Intel x86) computers (contents of live filesystem)
 ubuntu-10.10-netbook-i386.metalink       10-Oct-2010 09:25  8.9K  Ubuntu 10.10 (Maverick Meerkat)
 ubuntu-10.10-server-amd64.iso            07-Oct-2010 16:18  642M  Server install CD for 64-bit PC (AMD64) computers (standard download)
 ubuntu-10.10-server-amd64.iso.torrent    10-Oct-2010 09:23   25K  Server install CD for 64-bit PC (AMD64) computers (BitTorrent download)
 ubuntu-10.10-server-amd64.iso.zsync      10-Oct-2010 09:23  1.3M  Server install CD for 64-bit PC (AMD64) computers (zsync metafile)
 ubuntu-10.10-server-amd64.jigdo          10-Oct-2010 09:23  109K  Server install CD for 64-bit PC (AMD64) computers (jigdo download)
 ubuntu-10.10-server-amd64.list           07-Oct-2010 16:18   78K  Server install CD for 64-bit PC (AMD64) computers (file listing)
 ubuntu-10.10-server-amd64.metalink       10-Oct-2010 09:25  8.9K  Ubuntu 10.10 (Maverick Meerkat)
 ubuntu-10.10-server-amd64.template       07-Oct-2010 16:18   12M  Server install CD for 64-bit PC (AMD64) computers (jigdo template)
 ubuntu-10.10-server-i386.iso             07-Oct-2010 16:20  627M  Server install CD for PC (Intel x86) computers (standard download)
 ubuntu-10.10-server-i386.iso.torrent     10-Oct-2010 09:24   25K  Server install CD for PC (Intel x86) computers (BitTorrent download)
 ubuntu-10.10-server-i386.iso.zsync       10-Oct-2010 09:23  1.2M  Server install CD for PC (Intel x86) computers (zsync metafile)
 ubuntu-10.10-server-i386.jigdo           10-Oct-2010 09:23  112K  Server install CD for PC (Intel x86) computers (jigdo download)
 ubuntu-10.10-server-i386.list            07-Oct-2010 16:20   79K  Server install CD for PC (Intel x86) computers (file listing)
 ubuntu-10.10-server-i386.metalink        10-Oct-2010 09:25  8.8K  Ubuntu 10.10 (Maverick Meerkat)
 ubuntu-10.10-server-i386.template        07-Oct-2010 16:20  2.6M  Server install CD for PC (Intel x86) computers (jigdo template)


If you are currently downloading **ubuntu-10.10-netbook-i386.iso**, that will work fine.

---

### Post by Hedgehog1 on 2011-05-24
> **linuxinstalledfromhdd said:**
> You need to research how to install Ubuntu.  Maybe a translated web page in your native language.  You can try posting it in your native language as a new request.

Now where is your sense of adventure?  :D

---

### Post by linuxinstalledfromhdd on 2011-05-24
I feel sorry for the poor user too. The user is struggling with this issue, and it obvious at this point that he needs either a translator or needs to post this in his native language. It's probably something very simple, but with the lack of communication here it makes it almost impossible.  Even if they posted it in their native language I would be able to run a translator program and understand more of what they are attempting to say.  Isn't there Ubuntu guides in multiple languages that we can refer?

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> Here is the listing from page [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/). You can use any of the ones in **BOLD**:
 
ubuntu-10.10-alternate-amd64.iso 07-Oct-2010 15:47 694M Alternate install CD for 64-bit PC (AMD64) computers (standard download)
ubuntu-10.10-alternate-amd64.iso.torrent 10-Oct-2010 09:22 27K Alternate install CD for 64-bit PC (AMD64) computers (BitTorrent download)
ubuntu-10.10-alternate-amd64.iso.zsync 10-Oct-2010 09:21 1.4M Alternate install CD for 64-bit PC (AMD64) computers (zsync metafile)
ubuntu-10.10-alternate-amd64.jigdo 10-Oct-2010 09:21 141K Alternate install CD for 64-bit PC (AMD64) computers (jigdo download)
ubuntu-10.10-alternate-amd64.list 07-Oct-2010 15:47 101K Alternate install CD for 64-bit PC (AMD64) computers (file listing)
ubuntu-10.10-alternate-amd64.metalink 10-Oct-2010 09:25 9.0K Ubuntu 10.10 (Maverick Meerkat)
ubuntu-10.10-alternate-amd64.template 07-Oct-2010 15:47 12M Alternate install CD for 64-bit PC (AMD64) computers (jigdo template)
ubuntu-10.10-alternate-i386.iso 07-Oct-2010 15:49 693M Alternate install CD for PC (Intel x86) computers (standard download)
ubuntu-10.10-alternate-i386.iso.torrent 10-Oct-2010 09:22 27K Alternate install CD for PC (Intel x86) computers (BitTorrent download)
ubuntu-10.10-alternate-i386.iso.zsync 10-Oct-2010 09:22 1.4M Alternate install CD for PC (Intel x86) computers (zsync metafile)
ubuntu-10.10-alternate-i386.jigdo 10-Oct-2010 09:21 145K Alternate install CD for PC (Intel x86) computers (jigdo download)
ubuntu-10.10-alternate-i386.list 07-Oct-2010 15:49 103K Alternate install CD for PC (Intel x86) computers (file listing)
ubuntu-10.10-alternate-i386.metalink 10-Oct-2010 09:25 9.0K Ubuntu 10.10 (Maverick Meerkat)
ubuntu-10.10-alternate-i386.template 07-Oct-2010 15:49 2.8M Alternate install CD for PC (Intel x86) computers (jigdo template)
**ubuntu-10.10-desktop-amd64.iso** 07-Oct-2010 16:24 695M Desktop CD for 64-bit PC (AMD64) computers (standard download)
ubuntu-10.10-desktop-amd64.iso.torrent 10-Oct-2010 09:25 27K Desktop CD for 64-bit PC (AMD64) computers (BitTorrent download)
ubuntu-10.10-desktop-amd64.iso.zsync 10-Oct-2010 09:24 1.4M Desktop CD for 64-bit PC (AMD64) computers (zsync metafile)
ubuntu-10.10-desktop-amd64.list 07-Oct-2010 16:24 4.5K Desktop CD for 64-bit PC (AMD64) computers (file listing)
ubuntu-10.10-desktop-amd64.manifest 07-Oct-2010 16:20 37K Desktop CD for 64-bit PC (AMD64) computers (contents of live filesystem)
ubuntu-10.10-desktop-amd64.metalink 10-Oct-2010 09:25 8.9K Ubuntu 10.10 (Maverick Meerkat)
**ubuntu-10.10-desktop-i386.iso** 07-Oct-2010 16:25 693M Desktop CD for PC (Intel x86) computers (standard download)
ubuntu-10.10-desktop-i386.iso.torrent 10-Oct-2010 09:25 27K Desktop CD for PC (Intel x86) computers (BitTorrent download)
ubuntu-10.10-desktop-i386.iso.zsync 10-Oct-2010 09:25 1.4M Desktop CD for PC (Intel x86) computers (zsync metafile)
ubuntu-10.10-desktop-i386.list 07-Oct-2010 16:25 4.2K Desktop CD for PC (Intel x86) computers (file listing)
ubuntu-10.10-desktop-i386.manifest 07-Oct-2010 16:19 38K Desktop CD for PC (Intel x86) computers (contents of live filesystem)
ubuntu-10.10-desktop-i386.metalink 10-Oct-2010 09:25 8.9K Ubuntu 10.10 (Maverick Meerkat)
**ubuntu-10.10-netbook-i386.iso** 07-Oct-2010 17:50 696M Netbook live CD for PC (Intel x86) computers (standard download)
ubuntu-10.10-netbook-i386.iso.torrent 10-Oct-2010 09:23 28K Netbook live CD for PC (Intel x86) computers (BitTorrent download)
ubuntu-10.10-netbook-i386.iso.zsync 10-Oct-2010 09:23 1.4M Netbook live CD for PC (Intel x86) computers (zsync metafile)
ubuntu-10.10-netbook-i386.list 07-Oct-2010 17:50 4.8K Netbook live CD for PC (Intel x86) computers (file listing)
ubuntu-10.10-netbook-i386.manifest 07-Oct-2010 17:44 37K Netbook live CD for PC (Intel x86) computers (contents of live filesystem)
ubuntu-10.10-netbook-i386.metalink 10-Oct-2010 09:25 8.9K Ubuntu 10.10 (Maverick Meerkat)
ubuntu-10.10-server-amd64.iso 07-Oct-2010 16:18 642M Server install CD for 64-bit PC (AMD64) computers (standard download)
ubuntu-10.10-server-amd64.iso.torrent 10-Oct-2010 09:23 25K Server install CD for 64-bit PC (AMD64) computers (BitTorrent download)
ubuntu-10.10-server-amd64.iso.zsync 10-Oct-2010 09:23 1.3M Server install CD for 64-bit PC (AMD64) computers (zsync metafile)
ubuntu-10.10-server-amd64.jigdo 10-Oct-2010 09:23 109K Server install CD for 64-bit PC (AMD64) computers (jigdo download)
ubuntu-10.10-server-amd64.list 07-Oct-2010 16:18 78K Server install CD for 64-bit PC (AMD64) computers (file listing)
ubuntu-10.10-server-amd64.metalink 10-Oct-2010 09:25 8.9K Ubuntu 10.10 (Maverick Meerkat)
ubuntu-10.10-server-amd64.template 07-Oct-2010 16:18 12M Server install CD for 64-bit PC (AMD64) computers (jigdo template)
ubuntu-10.10-server-i386.iso 07-Oct-2010 16:20 627M Server install CD for PC (Intel x86) computers (standard download)
ubuntu-10.10-server-i386.iso.torrent 10-Oct-2010 09:24 25K Server install CD for PC (Intel x86) computers (BitTorrent download)
ubuntu-10.10-server-i386.iso.zsync 10-Oct-2010 09:23 1.2M Server install CD for PC (Intel x86) computers (zsync metafile)
ubuntu-10.10-server-i386.jigdo 10-Oct-2010 09:23 112K Server install CD for PC (Intel x86) computers (jigdo download)
ubuntu-10.10-server-i386.list 07-Oct-2010 16:20 79K Server install CD for PC (Intel x86) computers (file listing)
ubuntu-10.10-server-i386.metalink 10-Oct-2010 09:25 8.8K Ubuntu 10.10 (Maverick Meerkat)
ubuntu-10.10-server-i386.template 07-Oct-2010 16:20 2.6M Server install CD for PC (Intel x86) computers (jigdo template)
 
 
If you are currently downloading **ubuntu-10.10-netbook-i386.iso**, that will work fine.
 
 
ok thanks but that not i mean
**ubuntu-10.10-desktop-i386.iso** 
 
i installed it before from ubuntu site  and burned on cd and  i know from threads  that not live cd 
**if ubuntu-10.10-desktop-i386.iso**  correct and that required and give me only two options try and install not 4 options (booting from hard)why not give me this when boot from it 
do i need to download again or continous with netbook
that my question
 
thanks again

---

### Post by Hedgehog1 on 2011-05-24
Please continue with the netbook download.

We will use that.

---

### Post by pua06 on 2011-05-24
> **linuxinstalledfromhdd said:**
> You need to research how to install Ubuntu. Maybe a translated web page in your native language. You can try posting it in your native language as a new request.
 
i am sorry to say that you completly understand me wrong 
i know how install and good in translating
but this not my question i explained it in previous thread
really if i wrote with my native language it will not be easy to translate 
because google not translate well "statement"
really thanks so much for help

---

### Post by linuxinstalledfromhdd on 2011-05-24
I see you struggling with it. I hope you can get it working. :P

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> Now where is your sense of adventure? :D
 
yes i have also better sense of adventure to write with language not my native

---

### Post by Hedgehog1 on 2011-05-24
It is 12:30 p.m. (30 minutes past midnight) here in Oregon (west coast of the United States).

I will be going to bed very soon.

Hopefully, the 'check' of the partitions using Gparted will get your PC going again.

I will not be online until late tomorrow.

If you have more issues, please post them and others will try to help.

Bye-For-Now!

***The Hedge***

:KS

---

### Post by pua06 on 2011-05-24
> **linuxinstalledfromhdd said:**
> I feel sorry for the poor user too. The user is struggling with this issue, and it obvious at this point that he needs either a translator or needs to post this in his native language. It's probably something very simple, but with the lack of communication here it makes it almost impossible. Even if they posted it in their native language I would be able to run a translator program and understand more of what they are attempting to say. Isn't there Ubuntu guides in multiple languages that we can refer?
 
 
I appreciate your sympathy but i think that **Hedgehog1**
almost understand what i say and i think that i write right but i may neglect details 
 
i amtrying to interact better than avoid facing
 
thanks again 
thanks for help

---

### Post by pua06 on 2011-05-24
> **Hedgehog1 said:**
> It is 12:30 p.m. (30 minutes past midnight) here in Oregon (west coast of the United States).
 
I will be going to bed very soon.
 
Hopefully, the 'check' of the partitions using Gparted will get your PC going again.
 
I will not be online until late tomorrow.
 
If you have more issues, please post them and others will try to help.
 
Bye-For-Now!
 
***The Hedge***
 
:KS
 
thanks so much for help
happy dreams

---

### Post by pua06 on 2011-05-24
this my last news 
i download desktop .iso live cd and that the same CD that telling me alternate
and this options that get [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
 
4 options but i have problem to access 
**Try Ubuntu without any change to your computer**

i wrote the new problem  in new thread to be clear and this 
[http://ubuntuforums.org/showthread.php?p=10856319#post10856319](http://ubuntuforums.org/showthread.php?p=10856319#post10856319)
hope telling me what i did  wrong and what problem that not booting?
really thanks sooooo much for help

---

