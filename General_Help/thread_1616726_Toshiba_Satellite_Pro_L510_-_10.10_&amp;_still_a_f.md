---
title: "Toshiba Satellite Pro L510 - 10.10 &amp; still a few issues"
date: 2010-11-08
forum: General Help
---

### Post by Bucky Ball on 2010-11-08
Hi all,

Brand new Tosh Satellite Pro L510 and freshly installed 10.10.

All is good (great actually) except for a few niggling problems which I haven't been able to fix. These machines are pretty new so there is not a lot of support around. 

----
1/ Wireless card flaky. It will be fine, 100% connection, then swing to 50% randomly. Sometimes it disconnects completely. This seems to be totally random. Wired works fine. Card:

Realtek RTL8191SEvB

----
2/ When I get to the boot list at startup (I have dual-boot with Windows 7) the keyboard is dead. I can't select any of the options. It boots into the first one on the list (10.10) as per normal when the countdown's up and all is good, everything works.

The odd thing is if I control/alt/del and restart, the keyboard is then working fine! It is only from a cold boot that the keyboard is dead. Once up and running, it's there on the restart.

----
3/ Can print a test page everytime, normal OOffice doc most times, and PDF files no times (well, it prints but takes about half an hour and the output is garbled rubbish). I suspect the PDF problem is a bug of some sort as I can find no fix and my wife's laptop has had this problem for ages. I could never find a fix.

* I moved some PDFs to my Xubuntu box, which prints them fine, and started printing. Noticed there were updates, installed, but cups. Now none of my boxes prints PDF so don't think this is confined to 10.10. I have it on 8.04 LTS also (on three machines!).

** Fixed this problem pretty simply; installed Acroread. Printed immediately. So not cups but Evince. Or ... something more sinister. If a PDF is supposed to be free, open-source file, why then do they not seem to print from anything but Acroread on all three of my open-source boxes? 

----
That is all I can think of right now but I just woke up! Sure there was something else but post that later when it comes to me or I come across it.

Hoping for some clues. This release and this laptop model are a bit of a new frontier so let's take it as a challenge and aid for future L510 users. :)

---

### Post by Bucky Ball on 2010-11-08
Looking at problem 1/ I see from iwconfig this:

```
wlan0     802.11bg  ESSID:"Slynn"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1B:11:84:AF:26   
          Bit Rate=11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-48 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```My card is actually the RTL8191SEvB (not the one in the nickname), b/g/n, and there is no channel assigned (or at least showing). 

And in /etc/hosts I see this:

```
192.168.0.106   tosher  # Added by NetworkManager
```I am running static IPs and this is the one for the cable connection, the wireless ends in .107 and there is no entry for that. I'm figuring there should be but not sure what. Any ideas?

UPDATE: Another anomoly:

```
binky@tosher:/$ dmesg | grep "8191"
[ 9432.819145] =====>rtl8192_set_chan()====ch:7
```When I try dmesg | grep "8192" I get a massive output of which these are the last three lines:

```
[  528.252831] =====>rtl8192_set_chan()====ch:6
[  528.263029] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  528.263036] rtl8192_update_cap(): WLAN_CAPABILITY_SHORT_PREAMBLE
```

---

### Post by Bucky Ball on 2010-11-08
And one more very strange thing. I seem to be getting 100% wireless and things are working fine. Right click the network icon, check wireless, and it give me the connection and says 'Used: Never', but I am actually online with it!

I'm stumped for the moment.

---

### Post by shibinj on 2010-11-21
Hi, 

I too using same configuration and same version of Ubuntu.  I too had same problem.  I have resolved it.

Here is the way, I resolved.

Go to [http://www.realtek.com](http://www.realtek.com) and download latest driver for RTL8191SE-VA2 ( it is dated as 25th October 2010 ).

Update this driver as instructed and reboot your notebook.

You can see those messages are stopped. I had monitored it for 1hr and found, no more bugging alerts.

Cheers

---

### Post by Bucky Ball on 2010-11-22
Thanks for that. I get an error trying the 'make install' command.

```
binky@tosher:~/Downloads/RealtekDriver/rtl8192se_linux_2.6.0018.1025.2010$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: Entering directory `/home/binky/Downloads/RealtekDriver/rtl8192se_linux_2.6.0018.1025.2010/HAL/rtl8192'
make -C /lib/modules/2.6.35-22-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/binky/Downloads/RealtekDriver/rtl8192se_linux_2.6.0018.1025.2010/HAL/rtl8192'
make: *** [install] Error 2
```

---

### Post by Bucky Ball on 2010-11-22
Shibinj, wondering if you could tell me exactly how you went about it?

I went to the appropriate directory and ran 'make', which went fine, then 'make install', which, as you can see, didn't.

Incidentally, I switched my machine on this morning and the wireless is working fine, sees the router fine, but won't connect or ping it! Despite the fact it sees it there. Last time I used the wireless was working fine (it is still unreliable but doesn't generally die completely).

---

### Post by shibinj on 2010-11-22
Have you run an update before trying to install?   I haven't faced any such error.  Not sure, what went wrong. 

Perhaps, you try to update generic headers first. Or else, try to re-install your "make".

---

### Post by Bucky Ball on 2010-11-23
Yep, run an update and just trying it again now. Just a point; I have navigated to the extracted folder:

/rtl8192se_linux_2.6.0018.1025.2010

In that folder there is another folder called /realtek. Should I be in that folder to run the 'make' command? I'll try a few things now and report back. 

Strange thing is: Switch on the machine this morning and wireless working fine. Go figure. Let's hope this gets things a little more consistent.

---

### Post by andydch on 2010-11-24
[FONT=Arial]I have no problem with my Toshiba Satellite L510 - S4017B. Everything goes fine with Ubuntu 10.10.

Try change some parameters in [B]/etc/default/grub
[/B][B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
[/B][B]GRUB_CMDLINE_LINUX="acpi=copy_dsdt"
save the file

then open terminal, type sudo update-grub
restart your laptop

:)
[/B][/FONT]

---

### Post by Bucky Ball on 2010-11-29
The only thing I was missing was 'acpi_osi=Linux'. Added that and no difference whatever. Don't think that is the issue here.

andydch: I am using 10.10 on a L510 PSLGXA-002002. A different model which is possibly why yours is running fine and mine's not. 

Two things I have thought of:

1/ Is it possible I need to uninstall the other driver before trying the make/ make install commands on the new one?
2/ Realtek say this driver is good up to 10.04. I'm using 10.10. I didn't think that would make much of a diff but maybe it does.

The full output after make install command with the problematic bits in bold:

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: Entering directory `/home/binky/Downloads/RealtekDriver/rtl8192se_linux_2.6.0018.1025.2010/HAL/rtl8192'
make -C /lib/modules/2.6.35-22-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
**make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.**
**make[2]: *** [prepare0] Error 2**
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
**make[1]: *** [modules] Error 2**
make[1]: Leaving directory `/home/binky/Downloads/RealtekDriver/rtl8192se_linux_2.6.0018.1025.2010/HAL/rtl8192'
**make: *** [install] Error 2**
```
I've been searching for clues but not finding ... yet. Obviously, **No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s' **is glaring at me, but no idea what it means ... yet.

---

