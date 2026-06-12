---
title: "How to install network printer"
date: 2010-05-02
forum: General Help
---

### Post by dderolph on 2010-05-02
I'm using Ubuntu 9.10. I have limited experience with it.  I have a Brother MFC-790CW printer which is connected to my router and used by two other computers (Win XP desktop PC and a notebook PC [wireless]).  Ubuntu lists some Brother printers in its repository of printer drivers but my printer is not one of them.  

I visited Brother's website and found a Linux driver.  Actually, I had a choice of a .rpm file and a .deb file. First, I tried the .rpm file and discovered, if I understand this correctly, that it would have to converted to a .deb file using a tool called alien. So, I downloaded the .deb file from Brother and, per [http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm), installed it by simply double clicking on it.  Still, if I go to System | Administration | Printing, the printer does not appear there.  

So, apparently my attempt to the printer only applies to a local printer, not a network printer, and I need to go about this in a different way for a network printer. 

Do I need to install a "CUPS server"?  I'm referring to [Setting Up a Network Printer using CUPS]("http://www.linuxquestions.org/linux/answers/Networking/Setting_Up_a_Network_Printer_using_CUPS").

---

### Post by gordintoronto on 2010-05-02
Did you see the instructions on this page:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html)

It appears they have not updated the page for Ubuntu 9.10 or 10.04. I would do the things they suggest for 9.04.

With my Brother network laser, attached to my router, I had to set it to have a static IP address in order to use it in Ubuntu.  Brother provides a utility program which runs under Windows, which set that up. The default was DHCP. Mind you, that was a year ago, when I was running Ubuntu 7.10.

---

### Post by markackerman8@gmail.com on 2010-05-11
I am trying to install this printer as well.  It is attached to the network wirelessly.  I followed the brother site instructions for amd64 and force architecture node and the lpd option, and had a few errors.  Well I also tried the alien method after it didn't seem to work with the deb file install.  Well at this stage, Thr prinyer is seen with the friendly green checkmark, but still doesn't print.  It does however appear to print - no errors, nothing left in queue, hmmmm

should I try to install it attached by usb first, or is anyone having any success any way?

---

### Post by gordintoronto on 2010-05-11
Did you force the printer to have a static IP address?

---

### Post by markackerman8@gmail.com on 2010-05-12
Thank you for your response.

W.R.T. the static ip address, I have 2 questions.  But first a few of my limitations.  I am working on my brothers Ubuntu converted computer (and this is his last glitch, yahoooo a convert).  And I am building and administrating it from 3000km away by remote desktop, so I can't physically access the printer.  Sooo...

Is there a way I can find the ip address of the printer by scanning the network?; I can't find any leads from google other than suggestions that it is impossible, and you must print a test page.

And in answer to your question, I don't know if it is set as dynamic or static IP; where do I control that from? (the printers onboard menu?)

Thanks in advance.  :P

---

### Post by efflandt on 2010-05-13
Install nmap.  Commands I used here were:
[FONT=monospace]
[/FONT]nmap -sP 172.16.0.0/24 (scan your IP range for active IP's)
nmap -p T:515,631,9100 172.16.0.69 (check common printing ports on a likely IP)

```

efflandt@efflandt-lucid64:~$ nmap -sP 172.16.0.0/24

Starting Nmap 5.00 ( http://nmap.org ) at 2010-05-12 23:27 CDT
Host mainpc (172.16.0.1) is up (0.0082s latency).
Host 172.16.0.3 is up (0.0033s latency).
Host 172.16.0.4 is up (0.0032s latency).
Host ET0021B7009DA6 (172.16.0.69) is up (0.010s latency).
Host home (172.16.0.254) is up (0.0063s latency).
Nmap done: 256 IP addresses (5 hosts up) scanned in 3.00 seconds
efflandt@efflandt-lucid64:~$ nmap -p T:515,631,9100 172.16.0.69

Starting Nmap 5.00 ( http://nmap.org ) at 2010-05-12 23:28 CDT
Interesting ports on ET0021B7009DA6 (172.16.0.69):
PORT     STATE SERVICE
515/tcp  open  printer
631/tcp  open  ipp
9100/tcp open  jetdirect

Nmap done: 1 IP address (1 host up) scanned in 0.12 seconds
```PS: This was for a Lexmark C543dn.  I know someone with a MFC-790CW, but they are 1700 miles away, and I did not try it with Linux when I was there.

---

### Post by markackerman8@gmail.com on 2010-05-13
Well Great NEWS,  :P

My brothers MFC-790CW is working from the wireless network from Ubuntu.  I would like to mention that Brother technical support talked to me for 90 minutes  (though to no avail) but the online support gave me an answer within a few hours (linux experts!) and gave me 6 steps to get it working.  Cool LINUX SUPPORT!!!!!! and it did work.  The difference I am quite sure was that I installed the CUPS driver as well as the other, even though the brother website didn't show it inits list of Cups-functional printers.  And after that when i added the printer it actually found the driver on its own, and bammmm it was up and running.  Here is the 5 steps they gave me which is more thorough than there online guide.


from their linux support team!....
Yes. Brother printer drivers are created and optimized for 32 bit
version of Linux,
but those can be used for 64 bit Linux also. Some additional steps are
required.

For rpm users:
1. Install the standard C library for 32bit applications (e.g.
glibc.i686(Fedora), libstdc++ for 32bit(openSUSE)

2. Create some folders if it is required
2-1. Create /usr/lib/cups/filter if it does not exist.
Command1: mkdir /usr/lib/cups
Command2: mkdir /usr/lib/cups/filter
2-2. Create /usr/share/cups/model if it does not exist
Command: mkdir /usr/share/cups/model

3. Install the drivers.

4. Copy brlpdwrapperXXX files under /usr/lib/cups/filter/ to
/usr/lib64/cups/filter/
Command: cp /usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter

For dpkg users:
1. Install the standard c library for 32bit applications (e.g.
lib32stdc++6(Debian) or ia32-libs(Ubuntu))

2. Create some folders if it is required
2-1. Create /usr/lib/cups/filter if it does not exist.
Command1: mkdir /usr/lib/cups
Command2: mkdir /usr/lib/cups/filter
2-2. Create /usr/share/cups/model if it does not exist
Command: mkdir /usr/share/cups/model

3. Install the drivers using "--force-architecture" or
"--force-all"option.

4. Copy brlpdwrapperXXX files under /usr/lib/cups/filter/ to
/usr/lib64/cups/filter/
Command: cp /usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter

5. Copy libbrXXXX files under /usr/lib/ to /usr/lib32/ if /usr/lib32
exists.

---

### Post by tjn1987 on 2010-06-08
Hi,
I am using Super OS 9.10 32bit which is based on Ubuntu 9.10 32bit. Here is what I did to install network printer and network scanner drivers for Brother MFC-790CW. I have not tried 64bit drivers, but I think it also works, just download the associated 64bit drivers and install them.



For network printer:

  	 	 	 	 	   	 	 	 	 	 	  
[LIST=1]
[*][SIZE=3]Download 	LPR driver.deb and cupswrapper driver.deb off Brother printer 	website to  Desktop [/SIZE] 	
 	[SIZE=3][http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-790CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-790CW)[/SIZE]
[*][SIZE=3]Double 	click on mfc790cwlpr-1.1.2-2.i386.deb to install it.[/SIZE]
[*][SIZE=3]Double 	click on mfc790cwcupswrapper-1.1.2-2.i386.deb to install it.[/SIZE]
[*][SIZE=3]Go 	to System > Administration > Printing > right click on 	MFC790CW icon  > click Set As Default  > click OK[/SIZE]
[*][SIZE=3]Double 	click on MFC790CW icon  > click change button after Device URI > 	Network Printer > Brother MFC-790CW (Brother MFC-790CW) then wait 	awhile > Apply[/SIZE]
 	 	[COLOR=#ff0000][SIZE=3]**Note: 	**[/SIZE][/COLOR] 	
 	[COLOR=#ff420e][SIZE=3]Be 	sure “Device URI” shows 	“dnssd://Brother%20MFC-790CW._pdl-datastream_tpc.local/”[/SIZE][/COLOR]
[/LIST]


For network scanner:
  	 	 	 	 	 	  
[LIST=1]
[*][SIZE=3]Download 	brscan3 32bit.deb and scan-key-tool 32bit.deb off Brother website to 	Desktop 	[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)[/SIZE]
[*][SIZE=3]Double 	click brscan3-0.2.11-2.i386.deb to install it.[/SIZE]
[*][SIZE=3]Double 	click brscan-skey-0.2.1.3.i386.deb to install it.[/SIZE]
[*][SIZE=3]Open 	Terminal > Type sudo su > enter password of root > cd 	Desktop[/SIZE]
[*][SIZE=3]Type 	brsaneconfig3 -a name=any_name model=MFC-790CW ip=xxx.xxx.x.xxx[/SIZE]
[*][SIZE=3]Confirm 	network scanner entry by typing:[/SIZE]
 	[SIZE=3]brsaneconfig3 	-q | grep any_name
[/SIZE]
 	[SIZE=3]If 	the terminal screen shows:[/SIZE]
 	[COLOR=#ff0000][SIZE=3]0 any_name          “MFC-790CW”       I:xxx.xxx.x.xxx[/SIZE][/COLOR]
 	[SIZE=3]then 	scanner driver has just been installed and is ready for use.[/SIZE]
[*]T[SIZE=3]o 	use the scanner, go to Applications  >  Graphics  > Xsane 	Image Scanner[/SIZE]
[/LIST]
Cheers,

---

### Post by aribindi on 2010-12-26
1.  Looks like I installed the brother printer in networking setup, when I clicked on "print this page (test), looks like it is sending the data, but printer is not printing.
 
2. Scanner:   followed your instructions for  installing the MFC790CW scanner, but no luck.
  brsaneconfig3 -q | grep 790
 49 "MFC-790CW"   
**it did not show the IP address.**

3. In Applications menu[SIZE=3][/SIZE] I did not see Xsane Image Scanner, but it showed simple scan, when I clicked on it, it says scanner is not connected.

---

### Post by efflandt on 2011-01-04
I finally had a chance to try one of these printers at a friend's home (1700 miles away) in 64-bit Lucid running from a USB hard drive.  After downloading both lpr and cups printer drivers (lpr driver needs to be installed first) and doing:
```
sudo dpkg -i --force-all mfc790cwlpr-1.1.2-2.i386.deb
sudo dpkg -i --force-all mfc790cwcupswrapper-1.1.2-2.i386.deb
```It ends up configured as a USB printer. So assuming it is on your wireless network, you need to switch properties for that printer to a network printer (click [Change...] button for Device URI).

I have not configured scanning, but the Brother MFC-790CW prints great.

---

