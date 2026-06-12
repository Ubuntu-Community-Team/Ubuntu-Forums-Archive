---
title: "Ubuntu 10.10x64 Flash Problem"
date: 2010-12-02
forum: General Help
---

### Post by Calcipher on 2010-12-02
First of, let me apologize for this getting a bit technical. Several weeks ago, I found that while using NPR's media player (e.g. click on 'Listen to the Show' - this is what I've been using as a test) the stream would suddenly halt after a minute or three. I could not get the stream to restart without reloading the page. Now, I assumed this was an issue with NPR's player and Linux (or just a bug in their stuff in general) so I began to dig, the following is what I have tried to date (please note, the tldr; option is to skip to the latest thing as I think I know what is causing the problem).

Note: All testing has been done, for consistency purposes, on a clean install of Chromium with no pluggins running. My machine is Ubuntu 10.10x64.

   1. First thing I always try, I disabled all firewall stuff on the system (UFW, default deny all, allow ssh). No change, firewall back up for all additional tests unless otherwise noted. In any case, UFW is stateful, so connections it started on a non-specified on different ports will continue to work.
   2. I deleted my ~/.macromeda and ~/.adobe folders, restarted (just to be sure) and tried. Program still froze.
   3. I decided the problem might be with my install of flash, so I purged the version I had (and the home folders again). I installed the x64 version of flash from a PPA. This had no effect.
   4. I decided that the problem might be with the version of flash, so I purged the x64 version and installed the standard x32 version that comes with Ubuntu. No luck.
   5. Back to the x64 version for consistency, I decided to set up a 64-bit mini 'clone' of my system in VirtualBox. I was able to run the media player with no problem.
   6. I rsynced (in archive mode) my home directory from my real machine to the virtual machine (with bridged networking, so it was fully visible on the network). I also used a few tricks to install ALL of the same software (and repositories) from the real machine to the virtual machine. I was still able to listen to the player.
   7. I decided that the problem was with my install (after all, it had gone through two major version upgrades). As I have /home/ on a separate partition it was easy to reinstall and use the same trick from #6 to have my system up and running again within about an hour. I continue to have issues with the NPR Media Player.
   8. By this point the weekend had come. At work, I use a wired connection while at home I use a wireless connection. For some reason I forgot that I was having problems and used the NPR Media Player over the weekend. Low and behold it worked just fine at home on wireless (note: for various reasons, I could not test this on wired at home).
   9. Following from #6, I decided that the problem was either something with the network at work or still something with my account. As the latter was easier to test, I created a new account on my system and used that at work. The Media Player worked.
  10. At a loss, I decided to watch the traffic with tshark (the text based brother of wireshark) - X's to protect the innocent, I am the XXX.24.200.XXX:

    sudo tshark -i eth0 -p -t a -R "ip.addr == XXX.24.200.XXX && ip.addr == XXX.166.98.XXX"

As you would expect, there were tons and tons of packets, but each and every time the player froze, this is what I got
```

08:42:20.679200 XXX.166.98.XXX -> XXX.24.200.XXX TCP macromedia-fcs > 56371 [PSH, ACK] Seq=817686 Ack=6 Win=65535 Len=1448 TSV=495713325 TSER=396467

08:42:20.718602 XXX.24.200.XXX -> XXX.166.98.XXX TCP [TCP ZeroWindow] 56371 > macromedia-fcs [ACK] Seq=6 Ack=819134 Win=0 Len=0 TSV=396475 TSER=495713325

08:42:21.050183 XXX.166.98.XXX -> XXX.24.200.XXX TCP [TCP ZeroWindowProbe] macromedia-fcs > 56371 [ACK] Seq=819134 Ack=6 Win=65535 Len=1 TSV=495713362 TSER=396475

08:42:21.050221 XXX.24.200.XXX -> XXX.166.98.XXX TCP [TCP ZeroWindowProbeAck] [TCP ZeroWindow] 56371 > macromedia-fcs [ACK] Seq=6 Ack=819134 Win=0 Len=0 TSV=396508 TSER=495713362

08:42:21.680548 XXX.166.98.XXX -> XXX.24.200.XXX TCP [TCP ZeroWindowProbe] macromedia-fcs > 56371 [ACK] Seq=819134 Ack=6 Win=65535 Len=1 TSV=495713425 TSER=396508

08:42:21.680605 XXX.24.200.XXX -> XXX.166.98.XXX TCP [TCP ZeroWindowProbeAck] [TCP ZeroWindow] 56371 > macromedia-fcs [ACK] Seq=6 Ack=819134 Win=0 Len=0 TSV=396571 TSER=495713425

08:42:22.910354 XXX.166.98.XXX -> XXX.24.200.XXX TCP [TCP ZeroWindowProbe] macromedia-fcs > 56371 [ACK] Seq=819134 Ack=6 Win=65535 Len=1 TSV=495713548 TSER=396571

08:42:22.910400 XXX.24.200.XXX -> XXX.166.98.XXX TCP [TCP ZeroWindowProbeAck] [TCP ZeroWindow] 56371 > macromedia-fcs [ACK] Seq=6 Ack=819134 Win=0 Len=0 TSV=396694 TSER=495713548

08:42:25.340458 XXX.166.98.XXX -> XXX.24.200.XXX TCP [TCP ZeroWindowProbe] macromedia-fcs > 56371 [ACK] Seq=819134 Ack=6 Win=65535 Len=1 TSV=495713791 TSER=396694

08:42:25.340517 XXX.24.200.XXX -> XXX.166.98.XXX TCP [TCP ZeroWindowProbeAck] [TCP ZeroWindow] 56371 > macromedia-fcs [ACK] Seq=6 Ack=819134 Win=0 Len=0 TSV=396937 TSER=495713791

08:42:30.170698 XXX.166.98.XXX -> XXX.24.200.XXX TCP [TCP ZeroWindowProbe] macromedia-fcs > 56371 [ACK] Seq=819134 Ack=6 Win=65535 Len=1 TSV=495714274 TSER=396937

08:42:30.170746 XXX.24.200.XXX -> XXX.166.98.XXX TCP [TCP ZeroWindowProbeAck] [TCP ZeroWindow] 56371 > macromedia-fcs [ACK] Seq=6 Ack=819134 Win=0 Len=0 TSV=397420 TSER=495714274

08:42:39.801738 XXX.166.98.XXX -> XXX.24.200.XXX TCP [TCP ZeroWindowProbe] macromedia-fcs > 56371 [ACK] Seq=819134 Ack=6 Win=65535 Len=1 TSV=495715237 TSER=397420

08:42:39.801784 XXX.24.200.XXX -> XXX.166.98.XXX TCP [TCP ZeroWindowProbeAck] [TCP ZeroWindow] 56371 > macromedia-fcs [ACK] Seq=6 Ack=819134 Win=0 Len=0 TSV=398383 TSER=495715237

08:42:59.032648 XXX.166.98.XXX -> XXX.24.200.XXX TCP [TCP ZeroWindowProbe] macromedia-fcs > 56371 [ACK] Seq=819134 Ack=6 Win=65535 Len=1 TSV=495717160 TSER=398383

08:42:59.032696 XXX.24.200.XXX -> XXX.166.98.XXX TCP [TCP ZeroWindowProbeAck] [TCP ZeroWindow] 56371 > macromedia-fcs [ACK] Seq=6 Ack=819134 Win=0 Len=0 TSV=400306 TSER=495717160

08:43:00.267721 XXX.24.200.XXX -> XXX.166.98.XXX TCP 56371 > macromedia-fcs [FIN, ACK] Seq=6 Ack=819134 Win=0 Len=0 TSV=400430 TSER=495717160

08:43:00.267827 XXX.24.200.XXX -> XXX.166.98.XXX TCP 56371 > macromedia-fcs [RST, ACK] Seq=7 Ack=819134 Win=65535 Len=0 TSV=400430 TSER=495717160

```
So, as you can see, my machine is sending out a ZeroWindow packet (which I think means some buffer or another filled up) which causes the Media Player to halt (unfortunately, terminally - no controls on it really do anything anymore). Any ideas, at all, what would cause this? Why only on eth0 under my main account?

Note: Cross posted from [Stack Exchange](http://askubuntu.com/questions/15718/help-me-solve-my-problem-with-npr-media-player)

---

### Post by drdos2006 on 2010-12-02
I had the same problem with Flash and Ubuntu 10.10 64bit. Windows 7 64bit, bridged network address and virtualbox worked fine but not Ubuntu. Installed Ubuntu 10.4 64 bit, same problem, Flash not loading fully. Tried Windows 7 64bit, bridged network address and virtualbox again, worked perfectly. Modem was a D-Link DSL-2642B. Downloaded Flash-Aid for Firefox, still Flash was dropping out after a few moments under Ubuntu. I was blaming Ubuntu however other things have come to light this week which has made me change my ISP. Due to my ISP upgrading their network, the D-Link no longer is able to connect and authenicate reliably. Checking with other forum members on the ISP forum I discovered a significant number of people were unable to connect as well, after the s upgrade. Obviously the chipset in the D-Link modem is not communicating with the authentication server any more. Changed the modem to an old Netgear modem and Flash runs reliably, no more dropouts or disconnects to my ISP connection. Try a different modem.

[http://forums.whirlpool.net.au/forum-replies.cfm?t=1586118&p=2](http://forums.whirlpool.net.au/forum-replies.cfm?t=1586118&p=2)


regards

---

### Post by Calcipher on 2010-12-07
Thanks for the reply, apparently I forgot to turn on email notifications so I thought no one had gotten to me.  I suppose it is possible that the routers (all Cisco - corporate network) might be causing the problem, but it is hard to say.  I'm going to do a few tests and see if it happens on other hardware.  In the meantime if anyone has other ideas please let me know.

---

### Post by TBABill on 2010-12-07
Unless I misread part of your post, you are troubleshooting flash and Chromium due to issues with NPR's stream. The problem is flash is built into Chromium (and Opera). Firefox relies on you to install Flash for it to work with flash applications, but Chromium and Opera do not. But since they contain flash I am not sure what you can do as far as troubleshooting goes other than to setup the daily build via PPA to see if another version may be better. Or try a different browser altogether. 
 
I do have instances where one browser may fail and another may succeed so I always install Chromium, Opera and have Firefox by default. You may also try Google Chrome to see if it performs differently than the version of Chromium you have installed.

---

### Post by Calcipher on 2010-12-07
> **TBABill said:**
> Unless I misread part of your post, you are troubleshooting flash and Chromium due to issues with NPR's stream. The problem is flash is built into Chromium (and Opera).Actually, Flash is built into Chrome, Chromium (the open source branch of Chrome) utilizes the system's copy of Flash.  I have tested in 4 other browsers to ensure that it is a problem with Flash and not the browser itself and I am using Chromium simply to remove a variable from the equation.

---

### Post by TBABill on 2010-12-07
I stand corrected. I Googled it just to be positive and I mis-read the info previously. Thanks for clarifying.

---

### Post by dcstar on 2010-12-08
> **Calcipher said:**
> First of, let me apologize for this getting a bit technical. Several weeks ago, I found that while using NPR's media player (e.g. click on 'Listen to the Show' - this is what I've been using as a test) the stream would suddenly halt after a minute or three.
.........

Site works fine on my 10.04 64-bit system in Firefox using the Adobe Beta 64-bit Flash plugin: 10.2 d161

---

### Post by Calcipher on 2010-12-08
Thank you for confirming that it works fine for you.  I'm almost positive that there is something wrong with my account.  The weird parts are that it only happens on wired connections and if I copy my home directory over to another account, I don't get the problem on the other account.

---

