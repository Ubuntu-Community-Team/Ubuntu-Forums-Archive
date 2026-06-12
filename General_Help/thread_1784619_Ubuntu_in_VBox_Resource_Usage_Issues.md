---
title: "Ubuntu in VBox Resource Usage Issues"
date: 2011-06-17
forum: General Help
---

### Post by TrotskyIcepick on 2011-06-17
I've been running Ubuntu in an Oracle VirtualBox for quite some time now as it is generally my favourite Linux distro.

Whilst Ubuntu always seems to have been a "bit" of a resource hog, since 10.04 it has been really bad, and now with 11.04 it is soooo bad I can't understand the new interface as everything runs so slowly I lose patience after 30 seconds or so whilst waiting.

My setup is as follows:

Windows Vista SP2 host with 3Gb RAM, 128Mb video, dual core processor.
For my Ubuntu guest I give it 1.5Gb RAM and the full 128Mb video with 3D acceleration enabled.
I can't remember the rest as I'm at work at the moment.

On the host, resource usage remains pretty minimal, so obviously I've not got my VM configured optimally. Just about all other Linux ditro's I've tried seem to run fine, just Ubuntu causes problems.

What I guess I want from you guys/gals is some suggestions as to how to optimally configure my VBox VM and Ubuntu itself to run with reasonable performance. I want to run with the new interface as using classic destroys all the work I put into my 10.04 interface and still runs slowly.

If necessary I could downgrade back to 10.04 or 10.10 but since performance is still an issue there I'd rather not.

Thanks in Advance
Andrew

---

### Post by jerrrys on 2011-06-18
unlike you, i have been running VB for a month.  right now i got two different configuratioins going on. 

#1  U10o4 host and X1110 guest

#2 X host and guest

and i find no difference in guest performance.  host is fast on both.

i also tried vmWare before VB and found guest performance equal to host.  but vmware will recognize more that one core out of the box and VB will not.  and from what i can tell, this is not an option on my box, too bad for me.  but performance is acceptable and Vb has the option of taking snapshots where Vm does not.

---

### Post by TrotskyIcepick on 2011-06-21
Oh well, guess I'll see what I can glean from the VirtualBox forums. If I was totally insane I'd just wipe Windoze out altogether just to see how Ubuntu behaves as the main OS......but I'm not....and that's not an option.

I'm almost sure it HAS to be something to do with how VB is configured for this machine....so off I go to check.

Thanks

---

### Post by bodhi.zazen on 2011-06-21
> **TrotskyIcepick said:**
> Oh well, guess I'll see what I can glean from the VirtualBox forums. If I was totally insane I'd just wipe Windoze out altogether just to see how Ubuntu behaves as the main OS......but I'm not....and that's not an option.

I'm almost sure it HAS to be something to do with how VB is configured for this machine....so off I go to check.

Thanks

So keep windows, install Ubuntu, and dual boot. Dual booting is what most people do as they transition from windows to linux.

---

### Post by TrotskyIcepick on 2011-06-22
Don't really want to go the dual boot route. I need Windoze for a lot of stuff also, and just don't want to take any of the attendant risks with installing Ubuntu in a dual boot scenario. Also, I'm having lots of issues with my theme settings partially reverting to something that looks like the old Ubuntu Humanity theme from v9.04, and many applications not picking up settings from my theme (ie. font sizes, toolbars etc).

Have pretty much resolved the reource usage problem (to a reasonable degree) by doing a clean install and setting the affinity of the VBox process to CPU 0 on the host.

Thanks for the suggestion though.

---

### Post by Horadranin on 2011-06-22
Man, right now I have both 11.04 and 11.10(alpha 1) running in Virtualbox 4.0.8 with no lag, even the alpha version. For both machines I set only 512 MB RAM and System Monitor shows me that memory usage is 175 MB (!) and 286 MB respectively. How much memory your is using? The system is constantly accessing disk? Are you using the latest version of Virtualbox and have you installed the latest Guest Additions?

---

