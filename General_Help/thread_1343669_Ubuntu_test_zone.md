---
title: "Ubuntu test zone"
date: 2009-12-02
forum: General Help
---

### Post by Elie-M on 2009-12-02
hello, I wanna I do some tests for airsnarf and IP-Over-DNS over ubuntu and that requires some software installs and editing some .conf files, which last time i screwed and then network stopped completely and i had to reformat ubuntu. I need something similar to a test zone or a mark point where I can test and then undo everything I did from that point if I screwed up. (much similar to the new kaspersky function -but that's windows so I'm sure few of u ever saw it-) anyone can help plz? and thx

---

### Post by memilanuk on 2009-12-02
Hmmm... perhaps try RemasterSys or Clonezilla to take a snapshot of where you are when you get ready to start, and then be able to reboot from the CD and restore that image when you're done testing (or when the testing crashes/locks the machine)?

---

### Post by ankspo71 on 2009-12-02
Hi, 
If I am in the mood for some major testing, I will install Ubuntu inside Virtualbox and get it set up how I like it, then I backup my virtualbox folder (that way I won't have to reinstall Ubuntu again), then start testing away. If I mess up I can delete the virtualised Ubuntu installation and replace it with the backed up one. Any tests performed this way will not hurt your regular Ubuntu install. 

Virtualbox can be found in Synaptic Package Manager and on the Internet.
Hope this helps.
James

---

### Post by Elie-M on 2009-12-02
thx both :)

The second reply did hit it the exact point I wanted to know and that helped! thx a lot man. I will try it today :)

---

### Post by memilanuk on 2009-12-02
Virtualbox was my first thought as well (I love that program!), but reading this:

> 
do some tests for airsnarf


was the reason I didn't recommend it.

Virtualbox does many wonderful things, but I'm not sure how well you'll be able to run things related to wifi from within a virtual machine.  IIRC the nics available are all ethernet... but you can do some interesting things with 'bridged' and 'host-only' adapters so maybe you can find something that will work for you.

---

### Post by Elie-M on 2009-12-03
dunno man... the thing is i wanna Try to work on DNS servers conf and DHCP to try to run the pc as a rogue AP to see how that works.. if virtualbox doesnt support that, that would be a problem :-/ I badly need to test that without ruining my OS

---

### Post by akakingess on 2009-12-03
I thought memilanuk's idea of using Clonezilla was perfect, just get your install right, Clone it, then test all you want and when/if it breaks, "reinstall" from the clone.

---

### Post by ankspo71 on 2009-12-03
Hi again,

I use clonezilla too (well I used to, I need to get another cd for Karmic), but cloning with clonezilla requires another hard drive, a usb drive (?), or maybe some drive space available on your home network(?). If you have a place to store the cloned ubuntu (or backup images) then using clonezilla would be a good choice. I wasn't aware that this type of network testing couldn't be performed in Virtualbox. Sorry if my advice ended up being not that great.

Here is a pretty good link about using clonezilla.
[http://www.makeuseof.com/tag/free-advanced-hard-drive-cloning-solution-from-clonezilla/](http://www.makeuseof.com/tag/free-advanced-hard-drive-cloning-solution-from-clonezilla/)

James

---

### Post by akakingess on 2009-12-03
> **ankspo71 said:**
> Hi again,

I use clonezilla too (well I used to, I need to get another cd for Karmic), but cloning with clonezilla requires another hard drive, a usb drive (?), or maybe some drive space available on your home network(?). If you have a place to store the cloned ubuntu (or backup images) then using clonezilla would be a good choice. I wasn't aware that this type of network testing couldn't be performed in Virtualbox. Sorry if my advice ended up being not that great.

Here is a pretty good link about using clonezilla.
[http://www.makeuseof.com/tag/free-advanced-hard-drive-cloning-solution-from-clonezilla/](http://www.makeuseof.com/tag/free-advanced-hard-drive-cloning-solution-from-clonezilla/)

James

I don't think that memilanuk meant he KNEW it couldn't be done, just thought that it might not be able to be done or be the best way to test it, I don't want to put words in his/her mouth or speak for him/her, but I think the idea was just that that was why clonezilla was his/her first choice as an option.

---

### Post by ankspo71 on 2009-12-03
Hi Akakingess,
Oops, my reply wasn't directed at your reply in any way. ;) I was only adding more to the topic and also letting the original poster know I might have given some advice that might or might not help. 
James

---

### Post by akakingess on 2009-12-03
> **ankspo71 said:**
> Hi Akakingess,
Oops, my reply wasn't directed at your reply in any way. ;) I was only adding more to the topic and also letting the original poster know I might have given some advice that might or might not help. 
James

James,
I didn't take it that way at all, I just didn't want the OP to dismiss the idea of VBox, because that would be a good way to go if we could determine that he/she would be able to do all the testing that they wanted to under virtualization.  I took no offense at all and I am actually the one butting in where I probably shouldn't :D

I love this community, we are all so polite to each other!!!

---

### Post by memilanuk on 2009-12-03
I'm definitely *not* saying it can't be done... just I don't readily see a way for it to work, if that makes sense.

I'm currently running Vbox 3.0.12 (unfortunately not in front of it at the moment) and IIRC there are four choices for network adapters when you set up any virtual machine - and those choices are there because they are solid, reliable, common and very well supported in nearly every operating system that supports networking.  They are also all ethernet.  

You can also use the NIC in the guest OS in one of four modes - internal network, where it is only 'wired' to a virtual switch when and if other virtual machines are present on the same internal network, 'host-only' which is very similar (internal virtual network, no outside access) but there are ways (so I hear) to point a packet sniffer to the interface in the host operating system and take a peek at the network traffic.  Then there is the default NAT mode where the guest OS picks up a private IP from a virtual DHCP server and is NAT'd behind the physical hosts NIC.  Finally, there is bridged mode where the physical NIC is essentially 'split' between the guest and the host, and the guest literally has its own IP address for its connection on the same network as the host.  For example, my host OS is Windows Vista, with an Atheros a/b/g/n wifi adapter and it gets a fixed IP via dhcp on my local WLAN of 192.168.11.2.  If I put a bridged NIC in a guest machine in Virtualbox and fire it up, it picks up an IP of 192.168.11.9 (next unassigned dynamic address) from the Buffalo Air Station's dhcp server.

With the connection being 'bridged' again I've read that you can point a packet sniffer or similar program on the *host* at that connection and see all the traffic going by.  You can do pretty much everything you want to with DNS, DHCP, etc. in Virtualbox inside a virtual LAN with nearly any kind of guest OS you want.  I'm doing something along those lines so I can tinker with different networking configurations that I might not want 'open' to the outside world; my 'gateway' machine has two virtual NICs - one bridged with my wifi connection to the real-world LAN (still shows up as 'eth0'), and one connected to the internal virtual LAN (shows up as 'eth1').  Very slick.

I will say that in some sense it *should* be possible to do something with the wifi connection from within Virtualbox... I seem to recall something about being able to run Backtrack4 in a virtual machine and access the physical wifi devices on an Intel Macbook - specifically the built-in Airport card wouldn't work, so they recommended a couple specific cards as being compatible with things like aircrack, etc.  Maybe they were just talking about booting Backtrack4 as a live cd, but for some reason I could swear I thought they mentioned doing it from within a virtual machine...

I have never used VMware or any other virtualization software so I have no idea what might be possible with other programs out there on the market.  I *would* be very interested in hearing what you come up with if you do go the route of trying to access a wifi link from within Virtualbox...

Monte

Added afterward...

[http://forums.virtualbox.org/viewtopic.php?f=6&t=20913&p=90351&#p90351](http://forums.virtualbox.org/viewtopic.php?f=6&t=20913&p=90351&#p90351)

---

### Post by memilanuk on 2009-12-04
Been thinking about this a bit as I have been searching on some other stuff.  Would you be able to do what you need from a LiveCD?  There are ways to get 'persistent' data with a usb thumb drive along with an immutable LiveCD image, so what ever you do or break should be very easily undone.  Also, it's possible to setup custom LiveCDs (or LiveUSB sticks) that are essentially bootable clones of your existing system.  And one of the options I mentioned originally, Remastersys, creates a bootable backup CD/DVD of your system.  

Hope you find something that works for you.

Monte

---

