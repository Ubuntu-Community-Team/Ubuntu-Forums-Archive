---
title: "Ubuntu Breezy 5.10: Installation on Acer Aspire 1652 WLMi"
date: 2006-03-01
forum: General Help
---

### Post by xedxgex on 2006-03-01
[LIST=1]
[*]Insert cd and at prompt type: **linux noapic nolapic acpi=off pnpbios=off**
[*]Follow normal installation procedure and answer **Yes** on "Install Grub on MBR?" question
[*]Start the first boot normally. It should work well, except many modules couldn't not be loaded properly
[*]Open a terminal and type: **sudo gedit /boot/grub/menu.lst**
[*]Search for the section with title *Ubuntu, kernel 2.6.12-9-386* and comment the line starting with the word "kernel", typin a "#" before that word
[*]copy the same line under (and delete the charachter #). Remove parameters: **nolapic acpi=off pnpbios=off**
[*]Save... and reboot! Enjoy your fully functional Linux distro...
[/LIST]

---

### Post by Xavier_ on 2006-03-22
Hello,

I have this ACER 1652 model and I was very grateful to see how this instructions worked perfectly!!! The very first time I installed Ubuntu I turned mad seeking what was wrong with my NIC.

My new problem arises when, once all system is working perfectly, Ubuntu automatically ask me for installing updates. I agree of course, then reboot, and again I have problems with the wireless and ethernet connections... ](*,)  Ok, calm down, then, I re-install Ubuntu from the installation CD to recover the "working" version: All works fine in the installation, reboot, select the first GRUB menu, I re-do the steps of nolacpi, etc... reboot, select the first GRUB menu and....

[FONT="Courier New"]Booting Ubuntu, kernel 2.6.12-9-386

root (hd0,2)
Filesystem type is ext2fs, partition type 0x83
initrd /boot/initrd.img-2.6.12-9-386

Error 19: Linux kernel must be loaded before initrd

Press any key to continue[/FONT]

I press a key, and return to GRUB menu.. that leads me always to the same deadend.

Really dont know what to do. I just reinstalled Windows on the first partition, reinstalled and reinstalled Ubuntu and the same message arises always. Could you please give me a hint? :confused: 

Thanks,
Javier

---

### Post by Xavier_ on 2006-03-22
[COLOR="Red"]**_AUTOREPLY_**[/COLOR]: _Sorry _for my inconvenience. Ok, now, Javier, you kind of fool. I was using Vim to edit the file and... hell, I corrupted the menu.lst file using the wrong hay the **[B]dd**[/B] and **p **commands. Of course that initrd is executed before the kernel, as I confused the lines position.
I promise to learn more Vim :-#
 
Sorry again :-| 
Javier.

---

### Post by rabidphage on 2006-03-28
Hi
I did every thing as suggested and it did work. I've got sound and and most of the hotkeys are working now. I'm having a problem with the wireless connection. The network administration application shows that the connection is active and also detects the wireless ssid, dns servers etc. however ping fails. I'm not using wep. Please help...](*,)

---

### Post by dmizer on 2006-03-28
does ifconfig show that you're pulling an ip?  if so, what is it?  if not, is your router set for static or dhcp?  if you're not using wep, are you using mac filtering?

---

### Post by rabidphage on 2006-03-28
I'm under a university network. There is somesort of mac filtering but not at the level of the wireless router. I think so because the mac registering process involves connecting to the network and registering from a web page. And even before registering i'll be allowed to access the windows update site. Any way I've already registered the mac adress under windows Xp.
It is DHCP.I haven't tried the ifconfig command yet. Will let u know in the next post.

---

### Post by rabidphage on 2006-03-28
here's the ifconfig result....

darx@darx:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:CE:3C:CE:3C
          inet addr:172.25.26.188  Bcast:172.25.26.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe3c:ce3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:548 errors:0 dropped:5 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:64609 (63.0 KiB)  TX bytes:1020 (1020.0 b)
          Interrupt:11 Base address:0xa000 Memory:c820b000-c820bfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:86495 (84.4 KiB)  TX bytes:86495 (84.4 KiB)

I've attached a secreen shot of the hosts as well

Thank you

---

### Post by dmizer on 2006-03-28
have you gone to the registration site to register your mac?

ipv6 may also be causing you some problems.
directions here: [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28disable%29%7C%28ipv6%29](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28disable%29%7C%28ipv6%29)

---

### Post by rabidphage on 2006-03-28
yes i did register the mac. I'll try reading up on that.

---

### Post by rabidphage on 2006-03-28
:KS  yeehaw it worked like a charm.......
i'm posting from ubuntu.
cool
dmizer u rock.........

Now i need some help configuring the touch pad.
I can't double click and drag..
I could do that in windows.
Anyway now that half the battle is over, i'm relaxed..
Thanks mate........

---

### Post by dmizer on 2006-03-28
glad to know i helped.  don't know what to tell you about double click and drag.  can't get mine to do that either.  doesn't really kill me though.

---

### Post by rabidphage on 2006-03-28
i'm used to it. its double tap and drag by the way. i'm used to it and it's almost second nature. now i'm fumbling with the touch pad. Fedora core 5 did have it though. so i guess it must be a fairly simple configuration or something. 
thanks again.

---

### Post by rabidphage on 2006-03-28
I've updated the installation and got a new kernel and ran into connection troubles again(wireless). I checked the
/boot/grub/menu.lst file and all the kernel parameters have been reset. I edited it leaving just the noapic option as before and rebooted. 
Guess what still no wifi.
So by intuition i edited /etc/modprobe.d/aliases
to turn ipv6 back on.
reeboot and viola its working and ipv6 is supported.
Ubuntu is the best.......
For those of you who are tuning in late read the full thread. Aspire 1652 works with linux after all!!! hurrayy............:KS

---

### Post by rabidphage on 2006-03-28
After i've enables ipv6 the laptop sometimes does not connect to the wireless network after a reboot.

as for double tap and drag try this command
```
sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"
```
and reboot
i've copied the code from another thread. hoping to keep all issues related with acer aspire 1652 in one thread. look around and please try to update here as well.
thanks

---

### Post by mbgcam on 2006-04-01
Hi!

I just registered on this forum because I have the Acer 1652 WLMi and wanted to install ubuntu on the laptop... but I can't.

I downloaded the iso (ubuntu-5.10-install-i386.iso) burned it on a CD using Nero and ready to install it. I booted from CD, it appears the ubuntu logo and at prompt I type what you said (linux noapic nolapic acpi=off pnpbios=off). The I press enter and start the setup. Umpacking Linux, Loading modules, tons of command lines on the screen and then, suddenly (5-10 seconds after I pressed enter to start the installation) the screen goes black and nothing loads (CD, HDD, nothing).

I don't know what happens. I have tried the install several times, even adding new parameters (nopcmcia, etc), and nothing happens. It allways get frozen with the black screen...

Anyone know what happens? :confused: :confused: 

PS: Sorry for the English, I'm from Spain ;)

---

### Post by rabidphage on 2006-04-02
That seems unique, I have the very same laptop and it worked fine. Hope someone helps u out.

---

### Post by mbgcam on 2006-04-02
I'm installing it! I used the parameter: **vga=771** and all worked fine.

Now it's installing packages, I hope I won't have new problems:D

---

### Post by rabidphage on 2006-04-02
Acpi support is shoddy for example battery status doesn't work. Remember to post all your fixes here. and wifi will give you troubles as well.
I've installed the ati propreitary driver and it works fine. There are posts elsewhere in the forum regarding this.

---

### Post by mbgcam on 2006-04-02
Ubuntu works fine!!:KS :KS :KS 

The Wifi connection doesn't work but it isn't a real problem for me since I can use wired LAN connections on the Univerisity and at home.

Thank you all for this thread, it's absolutely useful for 1652 owners that wants a  solid Linux system - I tried SUSE and it couldn't even detect Ethernet LAN!!-

---

### Post by rabidphage on 2006-04-04
Wifi works if u r on an open wireless network. I don't know about WEP coz i haven't tried it yet. I'm now posting via an open wireless network. It takes some  poking around to get it working though. You can update the ATI drivers as well.
[http://www.ubuntuforums.org/showthread.php?t=24557]("http://www.ubuntuforums.org/showthread.php?t=24557")

---

### Post by AnyOne on 2006-04-14
Guys i cant get my network to Work...

Ive disabled IPV6 but i cant get an ip :(

any ideas?

---

### Post by rabidphage on 2006-04-18
r u on wireless?
post your ifconfig and iwconfig outputs

---

### Post by rabidphage on 2006-04-20
if you are dual booting with windows, networking maynot work sometimes in ubuntu coz the dhcp lease won't be released by windows during a reboot. Relese the lease before shutting down windows by using
```
ipconfig /release
```
in the command prompt.

---

### Post by dmizer on 2006-04-21
> Guys i cant get my network to Work...

Ive disabled IPV6 but i cant get an ip

any ideas?
you might also consider trying to use a static ip instead.  just because it's a DHCP server doesn't mean that you can't plug in a static ip.

---

### Post by flntobi on 2006-04-25
Hi
I also have the acer aspire 1652. I installed as instructed on the first post. Wlan worked.

I updated everything via synaptics.

now neither wlan nor ethernet works.

"iwconfig"  says:
 ...
eth0      unassosiated  essid:"RZUW"
           Mode:managed  channel=0   Acces Point: 00:00:00:00:00:00
           Bit Rate=0 kb/s    Tx-Power=20dBm
           ...
seems ok so far except for the Acces Point

"iwlist eth0 scan" says:
eth0    No scan results

I also tried to turn of ipv6 via [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28disable%29%7C%28ipv6%29](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28disable%29%7C%28ipv6%29)

Under windows it works.

Anybody Ideas?

---

### Post by flntobi on 2006-04-25
Just wanted to tell everybody that I got the acpi to work. I just followed the instructions on [http://wiki.ubuntuusers.de/acpi-fix](http://wiki.ubuntuusers.de/acpi-fix)

Its german, so I summarise here:

take the DSDT.aml from the attachement
sudo cp DSDT.aml /etc/mkinitramfs/DSDT.aml
cd /boot
sudo cp vmlinuz-$(uname -r) vmlinuz-$(uname -r).orig
sudo cp initrd.img-$(uname -r) initrd.img-$(uname -r).orig
sudo dpkg-reconfigure linux-image-$(uname -r)

restart

Worked for me. Please write if it worked for you

---

### Post by Circleback on 2006-05-06
anyone managed to get the hotkeys working (Kubuntu) on your Acer. I different model of Acer (5502) but I think the hotkey layout is about the same. Some work out of he box like the screen brightness, screen black, touchpad off, volume, and mute but, but i cant figure out how to get the mail, internet, e-manager, and P, buttons to work at all. Also another very annoying thing is the Fn+F5 crt switch doesnt work.

---

### Post by gm__ on 2006-06-05
Hi !
I'm very glad having found that thread 'cause i was having trouble too making my Acer aspire 1652 working with linux.
Unfortunately i made the same mistake as Xavier on the first page:

"AUTOREPLY: Sorry for my inconvenience. Ok, now, Javier, you kind of fool. I was using Vim to edit the file and... hell, I corrupted the menu.lst file using the wrong way the dd and p commands. Of course that initrd is executed before the kernel, as I confused the lines position.
I promise to learn more Vim"

So how do you save it without corrupting the file?

That's the way i have edited it:
---------------------------------------------------------
#kernel   /boot/vmlinuz-2.6.12-9-686 root=/dev/hda2 ro noapic nolapic acpi=off pnpbios=off quiet splash
kernel   /boot/vmlinuz-2.6.12-9-686 root=/dev/hda2 ro noapic quiet splash
----------------------------------------------------------
Do i need to keep both lines, could somebody help me with it?

Thanks in advance!

---

### Post by flntobi on 2006-06-05
Hi
The "#" means the line is a comment, so it is ignored completly. Its just a way of saving it in case something goes wrong. So the way you edited it is correct.

Have Fun 
Tobi

---

### Post by gm__ on 2006-06-05
Thanks a lot Tobi everything works just fine , even my ethernet card , without installing any driver. 
So its supported natively apparently.
I will try the wifi card later ...

I'm so happy that i found this thread and i can stick with Ubuntu. :)
I was so desperate...

Long live Ubuntu and Xedxgex, for this thread! :)

---

### Post by phax on 2006-08-22
Hi,

I want to buy this Acer too (I am poor student and this notebook is very cheap I think:))

But I have questions:

1) wifi card - it's intel, and it should work flawless... is it true? What about the signal strengh? I also want to use kismet...

2) ACPI, suspend to disk, ram - somebody has written that all is OK, so the powersaving thinks are working on 100%? 

I also wonder how long you can work on batter - I have read 4 hours, is it true?

3) Would you recommend this notebook for Linux user?:)

Thanks very much!

sorry my english

---

### Post by flntobi on 2006-08-23
Hi

1. the intel wifi Card ist flawless supported by Dapper

2. Acpi like batterystatus works, see earlier posts. Suspend to disk or ram doesn't work out of the box ( I haven't tried otherwise)

3. Yes i would recommend it, like any other centrino notebook

have fun tobi

---

### Post by phax on 2006-08-24
Thanks very much for answer!

I admit that I thinked that working ACPI means working suspending... so battery status and so on works, but with suspending to RAM and HDD it is unsure? Is there any way how to find out if it will work? 

I tried to find out any "list of working devices", but I didn't manage :(

Have a nice day

---

