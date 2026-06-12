---
title: "I Can Download Torrents, But I Can't Download anything else"
date: 2012-01-04
forum: General Help
---

### Post by Torbjorn S.D. on 2012-01-04
Hi!

Only one part of my Internet works: to download using Transmission. I can't use any browser and I can't use apt-get. I currently have Ubuntu 10.04, but I have had the same issues with Ubuntu 11.04, Lubuntu 11.04 and Ubuntu 10.10. I have used Ubuntu successfully for years and haven't had any difficulties until I recently had to format my computer and reinstall Ubuntu.

How should I go about to solve this? Is there any command I should type in Terminal that let's me know more about my connection and hardware? How should I get more information? Should I type dmesg or something and post the output here? Should I list my hardware in this forum?



Thanks in advance!

---

### Post by spacecheck on 2012-01-04
Have you checked the selected settings in Software Sources?

---

### Post by carranty on 2012-01-04
Firstly, are you behind a proxy?  If its a home computer probably not but if its a work PC you might be.

If not and you can use transmission but you can't browse the web my guess its a firewall issue, it could be blocking  all traffic except transmission.  To see if you've got the default firewall running type

```
sudo ufw status
```

in a terminal.

---

### Post by Torbjorn S.D. on 2012-01-05
> **carranty said:**
> Firstly, are you behind a proxy?  If its a home computer probably not but if its a work PC you might be.

If not and you can use transmission but you can't browse the web my guess its a firewall issue, it could be blocking  all traffic except transmission.  To see if you've got the default firewall running type

```
sudo ufw status
```

in a terminal.


I am a home computer user and I believe I am behind no proxy.



I have typed

```
 sudo ufw status
```

in the terminal. It replies

```
Inactive.
```


What should I do? Your answer, that it's probably, a firewall issue seems very likely to me. However, I don't know where to go from here. How should I continue to troubleshoot?

---

### Post by Torbjorn S.D. on 2012-01-05
@spacecheck
I have checked the selected settings in Software Sources. Everything looks normal.

---

### Post by Wayne_V on 2012-01-05
can you send the output of:

ifconfig -a
netstat -r
cat /etc/resolv.conf
nslookup ubuntuforums.org
sudo traceroute ubuntuforums.org

where do you get the torrent links to use if nothing else works?

---

### Post by imachavel on 2012-01-05
> **spacecheck said:**
> Have you checked the selected settings in Software Sources?

do mine look alright??

---

### Post by imachavel on 2012-01-05
> **Wayne_V said:**
> can you send the output of:

ifconfig -a
netstat -r
cat /etc/resolv.conf
nslookup ubuntuforums.org
sudo traceroute ubuntuforums.org

where do you get the torrent links to use if nothing else works?

everything works for me, healthy read out I suppose:

lsmod
Module                  Size  Used by
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
nls_utf8               12493  0 
isofs                  39571  0 
binfmt_misc            13213  1 
vesafb                 13449  1 
snd_hda_codec_hdmi     27535  1 
snd_intel8x0           33213  2 
snd_usb_audio          91410  1 
snd_hda_intel          24113  0 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_hda_codec          90901  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
snd_pcm                80042  6 snd_hda_codec_hdmi,snd_intel8x0,snd_hda_intel,snd_usb_audio,snd_ac97_codec,snd_hda_codec
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
fglrx                2434640  295 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
gspca_sonixj           32443  0 
gspca_main             27894  1 gspca_sonixj
psmouse                73312  0 
snd_timer              28659  2 snd_pcm,snd_seq
r8712u                281937  0 
dcdbas                 14054  0 
usblp                  17827  0 
joydev                 17322  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  1 gspca_main
parport_pc             32111  1 
serio_raw              12990  0 
snd                    55295  19 snd_hda_codec_hdmi,snd_intel8x0,snd_hda_intel,snd_usb_audio,snd_ac97_codec,snd_hda_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  3 snd_intel8x0,snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e100                   40108  0 
floppy                 60032  0 
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
danel@danel-Dimension-4700 ~ $ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:20:37:87:1b  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe37:871b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7072713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3697360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2005273432 (2.0 GB)  TX bytes:256943169 (256.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1920 (1.9 KB)  TX bytes:1920 (1.9 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:2f:39:be:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

danel@danel-Dimension-4700 ~ $ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
danel@danel-Dimension-4700 ~ $ cat /etc/resolv.conf
# Generated by NetworkManager
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.0.1
danel@danel-Dimension-4700 ~ $ nslookup ubuntuforums.org
Server:        192.168.0.1
Address:    192.168.0.1#53

Non-authoritative answer:
Name:    ubuntuforums.org
Address: 91.189.94.12

danel@danel-Dimension-4700 ~ $ sudo traceroute ubuntuforums.org
[sudo] password for danel: 
sudo: traceroute: command not found
danel@danel-Dimension-4700 ~ $ trace route
No command 'trace' found, did you mean:
 Command 'btrace' from package 'blktrace' (universe)
 Command 'itrace' from package 'irpas' (multiverse)
 Command 'ltrace' from package 'ltrace' (main)
 Command 'etrace' from package 'etrace' (universe)
 Command 'mtrace' from package 'libc-dev-bin' (main)
 Command 'tracer' from package 'pvm-dev' (universe)
 Command 'grace' from package 'grace' (universe)
 Command 'xtrace' from package 'xtrace' (universe)
 Command 'tracd' from package 'trac' (universe)
 Command 'strace' from package 'strace' (main)
 Command 'dtrace' from package 'systemtap-sdt-dev' (universe)
 Command 'rtrace' from package 'radiance-sse3' (universe)
 Command 'rtrace' from package 'radiance' (universe)
trace: command not found
danel@danel-Dimension-4700 ~ $ traceroute
The program 'traceroute' is currently not installed.  You can install it by typing:
sudo apt-get install traceroute
danel@danel-Dimension-4700 ~ $ sudo apt-get install traceroute
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  traceroute
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 49.6 kB of archives.
After this operation, 176 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/universe traceroute i386 1:2.0.15-1 [49.6 kB]
Fetched 49.6 kB in 1s (28.4 kB/s)                    
Selecting previously deselected package traceroute.
(Reading database ... 158692 files and directories currently installed.)
Unpacking traceroute (from .../traceroute_1%3a2.0.15-1_i386.deb) ...
Processing triggers for man-db ...
Setting up traceroute (1:2.0.15-1) ...
update-alternatives: using /usr/bin/traceroute.db to provide /usr/bin/traceroute (traceroute) in auto mode.
update-alternatives: using /usr/bin/lft.db to provide /usr/bin/lft (lft) in auto mode.
update-alternatives: using /usr/bin/traceproto.db to provide /usr/bin/traceproto (traceproto) in auto mode.
update-alternatives: using /usr/sbin/tcptraceroute.db to provide /usr/sbin/tcptraceroute (tcptraceroute) in auto mode.





















Anyway I'm not trying to Spam the thread. Looks kind of like a bad install. My curiosity is, would it hurt to reinstall? Or maybe, try this. reburn the ubuntu .iso from whichever pc you downloaded it to. Try burning the disk on the lowest speed possible. I don't have the answer to the question. I'll help in any way I can. That is all I can say. I don't want to give false answers and get banned, but I'd do a fresh install. Then again, I'm used to windows. What are the sudo commands for popping in the disk and running a repository repair. Did I say that right?

---

### Post by Torbjorn S.D. on 2012-01-05
@Wayne_V

where do you get the torrent links to use if nothing else works?

short answer: from a usb flash drive.

long answer: when i decided to reinstall and format my hard drive i wanted to save some media files but i thought they were to big to save cheaply and because i have a fast internet connection (100 mb/s) i thought it would be easier to just save the torrent files on a usb flash drive and download the media files once more.



torbjorn@torbjorn-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:8a:a4:41  
          inet addr:84.55.83.77  Bcast:84.55.83.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe8a:a441/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1267423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2896367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88040757 (88.0 MB)  TX bytes:4259461295 (4.2 GB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52990 (52.9 KB)  TX bytes:52990 (52.9 KB)





torbjorn@torbjorn-desktop:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
84.55.83.0      *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0






torbjorn@torbjorn-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
search 82.246.88.20
nameserver 82.246.88.10



torbjorn@torbjorn-desktop:~$ nslookup ubuntuforums.org
;; connection timed out; no servers could be reached






torbjorn@torbjorn-desktop:~$ sudo traceroute ubuntuforums.org
[sudo] password for torbjorn: 
sudo: traceroute: command not found

---

### Post by imachavel on 2012-01-05
if the torrent files are from a usb drive, they are uploaded. downloaded would mean you get the torrent files from a server off the inter net through your browser by connecting to the i.p. of the domain of the server that you torrent the files from. Well, let's not get complicated.

Downloading off the internet means that whatever you download is accessed through a port. for example:


[LIST]
[*]*20 & 21*: [File Transfer Protocol]("http://en.wikipedia.org/wiki/File_Transfer_Protocol") (FTP)
[*]*22*: [Secure Shell]("http://en.wikipedia.org/wiki/Secure_Shell") (SSH)
[*]*23*: [Telnet]("http://en.wikipedia.org/wiki/Telnet") remote login service
[*]*25*: [Simple Mail Transfer Protocol]("http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol") (SMTP)
[*]*53*: [Domain Name System]("http://en.wikipedia.org/wiki/Domain_Name_System") (DNS) service
[*]*80*: [Hypertext Transfer Protocol]("http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol") (HTTP) used in the [World Wide Web]("http://en.wikipedia.org/wiki/World_Wide_Web")
[*]*110*: [Post Office Protocol]("http://en.wikipedia.org/wiki/Post_Office_Protocol") (POP3)
[*]*119*: [Network News Transfer Protocol]("http://en.wikipedia.org/wiki/Network_News_Transfer_Protocol") (NNTP)
[*]*143*: [Internet Message Access Protocol]("http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol") (IMAP)
[*]*161*: [Simple Network Management Protocol]("http://en.wikipedia.org/wiki/Simple_Network_Management_Protocol") (SNMP)
[*]*443*: [HTTP Secure]("http://en.wikipedia.org/wiki/HTTP_Secure") (HTTPS)
[/LIST]
 
so your ports are open for http and html. Now with windows when you can access the internet and look at html pages, but can't download a file, then the problem is probably that a port is not working or configured for your downloads. This of course is rare, usually the .net framework, or the connection all together will fail, and from there you can't really get anywhere. I wouldn't know with linux the configuration or necessary root files that provide you with the frame work to access the internet, meaning your network interface adapter and the server the domain of the web site hosted you are accessing is on, are constantly pinging each other.

It's obvious you can use the internet. With windows there are sometimes problems with scripts, I'm sure linux has the same issues. With your read out, maybe another member can help you, but just know those torrent files on your usb drive are from previous downloads, you are accessing the drive from your desktop, as the usb interface recognizes it, and allows you to access files. So there you go. If anyone else can diagnose this, it'd be great. Sorry I'm not a linux person, but I am now, I got tired of winblows. But windows sure gets familiar, and often times figuring out a problem in windows isn't being a rocket scientist but simply having seen the solution a million times and knowing the solution to fix it.

---

### Post by Wayne_V on 2012-01-06
> torbjorn@torbjorn-desktop:~$ netstat -r
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
84.55.83.0 * 255.255.255.0 U 0 0 0 eth0
link-local * 255.255.0.0 U 0 0 0 eth0

I don't see a default route there.  You should see something like:

> $ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         home.gateway    0.0.0.0         UG        0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0


Are you using a static IP or is it set via DHCP?  (if static, you'll need to add the route statically as well.  if dhcp, your dhcp server should be setting it).

---

### Post by Wayne_V on 2012-01-06
to test if the missing default is your entire problem, find out what your default router IP is (from you ISP) and then run:

$ sudo route add default gw <default route IP>

if everything works then you can go into your network config gui and add it permanently (assuming you are using a static IP)

---

### Post by Torbjorn S.D. on 2012-01-07
@All

Thank you very much for all your help. I have managed to make my Internet connection work again. The problem was that I had typed in an incorrect DNS address. I called my ISP and he pointed it out for me.

Thank you all once again for your help.

---

### Post by imachavel on 2012-01-07
mine says this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

I don't know if comparing will help any, but you resolved the issue? Glad to know it :D

what does your IP routing table look like now?

---

### Post by imachavel on 2012-01-07
> **Torbjorn S.D. said:**
> @All

Thank you very much for all your help. I have managed to make my Internet connection work again. The problem was that I had typed in an incorrect DNS address. I called my ISP and he pointed it out for me.

Thank you all once again for your help.

that's always good, it's nice when they can set that for you.

---

### Post by imachavel on 2012-01-07
> **Wayne_V said:**
> to test if the missing default is your entire problem, find out what your default router IP is (from you ISP) and then run:

$ sudo route add default gw <default route IP>

if everything works then you can go into your network config gui and add it permanently (assuming you are using a static IP)

Mine says this:

sudo route add default gw 192.168.0.1
[sudo] password for *****: 
*****@*****-Dimension-4700 ~ $ 

well there we are. It didn't give a return syntax, but didn't disconnect me either. Here is my routing table i.p. information if it helps in the future, it doesn't oh well:

Interface: Ethernet (etho0)
Hardware Address: 00:13:20:37:87:1B
Driver: e100
Speed: 100 Mb/s
Security: None

IPv4
Ip Address: 192.168.0.102
Broadcast Address: 192.168.0.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.0.1
Primary DNS: 192.168.0.1


tah tah :popcorn:

---

