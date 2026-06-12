---
title: "VMware - pros &amp; cons of various ways of running Ubuntu &amp; XP using VMware products"
date: 2006-03-06
forum: General Help
---

### Post by Vim on 2006-03-06
On my ThinkPad G41 I intend to install Ubuntu and make it so that I have both XP and Ubuntu simultaneously in memory in such a way that I can quickly switch back and forth between these 2 OS's. These are three ways which have come to mind:
[LIST=1]
[*]install VMware's [Ubuntu Virtual Appliance]("http://www.vmware.com/vmtn/appliances/ubuntu.html") (free)
[*]install [the VWware Player]("http://www.vmware.com/products/player/") (also free), then install Ubuntu on it
[*]purchase & install [VMware Workstation]("http://www.vmware.com/request_processor?nextPage=/vmwarestore/newstore/category.jsp&action=CATALOG.GETGROUPS&application=store&ProductGroupCodes=EXT-STORE-WKST-WIN,EXT-STORE-WKST-LX") ($ 189), create a virtual machine with it, and install Ubuntu on that machine
[/LIST]
I may have read somewhere that the Ubuntu Virtual Appliance does not have all the components of a complete Ubuntu installation.  And I wonder if most users of the Player after a short period find that they really need the Workstation, in which case I might as well buy it right away.  I have searched for, but not found, discussions on the pros and cons of these and similar ways of combining the use of these and similar products.  If such discussions exist online, I'd appreciate a link towards the best one for an XP end-user and Linux novice who is willing to pay $189 but, of course, rather doesn't.  Otherwise I'd love to see a discussion on this topic started here.

---

### Post by kingsidy on 2006-03-06
the best way to go in your situation is vmware workstation. It is easy and quite fast if you have the ram. 189 dollars, WOW. One word for you: Bittorrent, that is all i am going to say

---

### Post by Vim on 2006-03-06
What are disadvantages I am likely to encounter with VMware's [ Ubuntu Virtual Appliance]("http://www.vmware.com/vmtn/appliances/ubuntu.html") and/or their [Player]("http://www.vmware.com/products/player/")?

---

### Post by adie273 on 2006-03-06
With Vmware Workstation you can create virtual computer images, where as with Vmware Player by itself you can't.

Vmware workstation also gives you the option to setup shared folders for you to  access files between your host computer and the virtual computer your running. Vmware Player doesn't do that. However from what i'm told, you can setup Samba yourself manually and create your own shared folders that Vmware Player can access. (But this takes more effort on your behalf and I haven't tried it personally myself)

Hopes this helps some,

Adie

---

### Post by ComplexNumber on 2006-03-06
instead of vmware, you could try xen instead because its a lot newer and better. you can find out about it here:
[http://www.cl.cam.ac.uk/Research/SRG/netos/xen/]("http://www.cl.cam.ac.uk/Research/SRG/netos/xen/")

---

### Post by Vim on 2006-03-06
[QUOTE=ComplexNumber]instead of vmware, you could try xen instead because its a lot newer and better. you can find out about it here:
[http://www.cl.cam.ac.uk/Research/SRG/netos/xen/]("http://www.cl.cam.ac.uk/Research/SRG/netos/xen/")[/QUOTE]

From that web page I quote: "A port of Windows XP was developed for an earlier version of Xen, but is not available for release due to licence restrictions."

I interpreted that as: one cannot use Xen to get XP and Ubuntu in memory at the same time, and switch quickly between them.

---

### Post by patrickfromspain on 2006-03-06
why do you want to run ubuntu as a guest for win xp?? I don't see the point, sorry.

---

### Post by Vim on 2006-03-06
[QUOTE=patrickfromspain]why do you want to run ubuntu as a guest for win xp?? I don't see the point, sorry.[/QUOTE]

I have a number of XP programs which run only under Windows.  I want to be able to use them without having to reboot my ThinkPad.  I intend to try to make Ubuntu my primary OS.

---

### Post by Vim on 2006-03-06
What are disadvantages I am likely to encounter with VMware's  Ubuntu Virtual Appliance and/or their Player?

---

### Post by Vim on 2006-03-06
[QUOTE=adie273]With Vmware Workstation you can create virtual computer images, where as with Vmware Player by itself you can't.

Vmware workstation also gives you the option to setup shared folders
   ... [snip] ...

Adie[/QUOTE]

Thanks for the info relative to shared folders.

If I install the Player or the Ubuntu Virtual Machine I will get to use a "virtual computer image", which was created for me.  I wonder if afterwards I will then ever feel the need to create a "virtual computer image" myself.  Did you ever create one?  If yes, then what did you do it for?

---

### Post by Zwack on 2006-03-06
We use vmware at the place I work...

Based on our experience you're better off using Linux as the main OS and running WinXP in the VM.

Mostly this is done with RedHat here though.

Z.

---

### Post by ComplexNumber on 2006-03-06
[quote=Vim]From that web page I quote: "A port of Windows XP was developed for an earlier version of Xen, but is not available for release due to licence restrictions."

I interpreted that as: one cannot use Xen to get XP and Ubuntu in memory at the same time, and switch quickly between them.[/quote] you can find out about it here with a comparison with vmware and other systems:
[http://en.wikipedia.org/wiki/Xen]("http://en.wikipedia.org/wiki/Xen")


i found this to be an interesting read about MS, linux, and xen:
[http://garage.docsearls.com/node/594]("http://garage.docsearls.com/node/594")

---

### Post by Vim on 2006-03-06
[QUOTE=ComplexNumber]you can find out about it here with a comparison with vmware and other systems:
[http://en.wikipedia.org/wiki/Xen]("http://en.wikipedia.org/wiki/Xen")

i found this to be an interesting read about MS, linux, and xen:
[http://garage.docsearls.com/node/594]("http://garage.docsearls.com/node/594")[/QUOTE]

Thanks for the references.  I'm quoting from your Wikipedia reference: "A Windows XP port was carried out during the initial development of Xen, but Microsoft's licensing prevents its public release."

---

### Post by Vim on 2006-03-06
I intend to continue using the XP IBM software designed specifically to be used under XP for the ThinkPad G41.  I'm assuming that this means that I should use XP as the host OS.

---

### Post by btarlinian on 2006-03-06
After all this Xen talk, I though I'd put in my own few words.

Both AMD and Intel are coming out with new processors soon (as in a few months) (I think Intel already has them) with something called virtualization technology. It basically allows you to run an unaltered Windows (and possibly Linux) on Xen thanks to special hardware instructions.

If you're interested, search for Pacifica AMD Xen on google, (can't remember the intel code name at the moment, sorry.)

---

### Post by Vim on 2006-03-07
[QUOTE=btarlinian]... [snip] ...   search for Pacifica AMD Xen on google   ...[snip]...[/QUOTE]

I did such a search, and found this [article on AMD Virtualization Technology]("http://www.devx.com/amd/Article/30186").  It'll probably be several years before I buy my next computer.  At that time I may well look for one with a CPU which has such technology built-in.

---

### Post by alamba on 2006-03-07
[QUOTE=Vim]These are three ways which have come to mind:
[/QUOTE]

Have you considered a 4th option - dual booting? Personally I've been a user of both vmware workstation and vmware player. After about 15 minutes I threw both of those out and just clean installed my laptop with ubuntu.

A

---

### Post by Vim on 2006-03-07
This [web page about the Ubuntu Virtual Appliance]("http://www.vmware.com/vmtn/appliances/ubuntu.html") is the only place where I have been able to find info about it.  That info is minimal.  Has anybody tried it?

---

### Post by Vim on 2006-03-07
Yes, I have considered that.  But I still hope that I will receive replies from other forum members who have found VMware's [Ubuntu Virtual Appliance]("http://www.vmware.com/vmtn/appliances/ubuntu.html"), [Player]("http://www.vmware.com/products/player/") and/or  [Workstation]("http://www.vmware.com/request_processor?nextPage=/vmwarestore/newstore/category.jsp&action=CATALOG.GETGROUPS&application=store&ProductGroupCodes=EXT-STORE-WKST-WIN,EXT-STORE-WKST-LX") useful.

Thanks for your reply.

---

### Post by pras2k on 2006-03-07
yes! you can have VMware install it on your primary OS as Ubuntu and have XP as your virtual machine. 

VMware also give a free VMware server product, curently in beta.
[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

---

### Post by RaptorRaider on 2006-03-07
Does anyone have a few links for "how do I **use** Xen"-based questions?


I can find tons of guides telling you how to install Xen on their favorite distribution, but not telling you how to use it - where can I find these specially altered images?
How do I install them?
Should my CPU have hardware support for virtualization (they're out already), how would I run whatever OS I want in Xen?
Doesn't every other computerpart (like the videocard) need it's own hardware virtualization support?

---

### Post by justleen on 2006-03-07
I've been running VMware workstion on XP, and Ubuntu on the VM machine.. this worked great..  i user samba to share files, though the shared folder works fine to (just practicing smb..)

To be honest, i never thought about any other options, really.. so not much of a help, really.. just thought i should mention thats the VMworkstation option is very good (as said before: bittorrent)

---

### Post by Vim on 2006-03-07
Thanks justleen.  Good to hear from somebody who is happy about [VMware Workstation]("http://www.vmware.com/request_processor?nextPage=/vmwarestore/newstore/category.jsp&action=CATALOG.GETGROUPS&application=store&ProductGroupCodes=EXT-STORE-WKST-WIN,EXT-STORE-WKST-LX").  Now, I hope to hear from forum users who have some experience with, and/or knowledge about VMware's [Ubuntu Virtual Appliance]("http://www.vmware.com/vmtn/appliances/ubuntu.html") and/or [Player]("http://www.vmware.com/products/player/").

(By the way: I grew up in the Netherlands, where you apparently live.)

---

### Post by vavoem on 2006-07-11
Why would you want to mess around with vmware workstation and pay $189 if you can download vmware server for free?

---

### Post by Peturrr on 2006-07-13
> **vavoem said:**
> Why would you want to mess around with vmware workstation and pay $189 if you can download vmware server for free?
Indeed. With the free VMWare Server you can create Vm Machines yourself and connect to them from remote machines if you would like that.
For a tutorial see => [HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://www.ubuntuforums.org/showthread.php?t=183209")

---

### Post by yetanothersteve on 2006-07-15
I have used VMWare Workstation, I had a license for the 4.x version from the company for which I work back when they did not check too closely as to what software developers were requesting. So, back then I ran Suse 9.2 and then Ubuntu 5.04 as my primary OS and then Win2K in VMWare.

Then with Ubuntu 5.10 I downloaded the trial VMWare Workstation 5.x, created a Win2K virtual machine and a PCBSD virtual machine and then only used the player after that.

With Ubuntu Dapper I have only used the VMWare player with the VMWare Win2K and PCBSD virtual machines I had previously created. 

You can also, last I checked, use Qemu to create a VMWare virtual machine. 
[http://www.ubuntuforums.org/showthread.php?t=84275](http://www.ubuntuforums.org/showthread.php?t=84275)  And then use VMWare Player to play your Qemu created virtual machine.
Or just use Qemu / KQemu as your emulator and not VMWare although they are not as fast.

I use VMWare because the VMWare bridged networking works without a lot of configuration hassle. I need bridged and not NAT for the MS Windows only remote access software to my workplace.  Qemu was difficult to configure for bridged networking.

If I ever need another VMWare virtual machine I will probably go the VMWare Server route if the licensing remains unrestrictive.

---

### Post by slider on 2006-07-15
I ran VMWare workstation on my XP box with a few linux distros as clients. It was an older version of Workstation though (4.x). I had trouble with any usb or firewire devices. Anything that required it's own driver wasn't accessible and others were somewhat flakey. I now run Ubuntu as my host OS with VMWare Server and XP as client. USB support seems a lot better although I imagine weirder devices will still not work (haven't tried). I can't see any shortcoming of VMWare server compared to Workstation 4.x. I'd try the free one before shelling out $190.

---

### Post by lightningguitar on 2006-08-02
> **Vim said:**
> Thanks justleen.  Good to hear from somebody who is happy about [VMware Workstation]("http://www.vmware.com/request_processor?nextPage=/vmwarestore/newstore/category.jsp&action=CATALOG.GETGROUPS&application=store&ProductGroupCodes=EXT-STORE-WKST-WIN,EXT-STORE-WKST-LX").  Now, I hope to hear from forum users who have some experience with, and/or knowledge about VMware's [Ubuntu Virtual Appliance]("http://www.vmware.com/vmtn/appliances/ubuntu.html") and/or [Player]("http://www.vmware.com/products/player/").

(By the way: I grew up in the Netherlands, where you apparently live.)

Hi Vim,
I have downloaded other OS's from the [VMTM]("http://www.vmware.com/vmtn/appliances/") page and used them in VMware Player running on Ubuntu 6.06.  I've also created my own virtual machines with VMware Workstation using XP.  I'm going to test the Workstation in Ubuntu 6.06 next.

From my experience, you can edit/run any updates you wish, and install any programs that you'd like inside the Virtual Machine of choice.  I haven't had any problems.

I'm almost certain that you could download the [Ubuntu 6.06 from the appliances page]("http://www.vmware.com/vmtn/appliances/ubuntu.html"), run it inside of VMware player and then customize it to whatever you'd like.

Just a thought.  Good Luck!

---

