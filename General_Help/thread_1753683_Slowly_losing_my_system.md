---
title: "Slowly losing my system"
date: 2011-05-09
forum: General Help
---

### Post by Habaken on 2011-05-09
Hello. I have been experiencing some major problems with Ubuntu for a while now.. Started with Lucid where my file system would go corrupt every week or so. Now I'm on Natty and it's 10x worse..

What happens:
Either full computer lockup; screen is froze but mouse still moves, can not click anything. Keyboard LED's are also frozen. I have to use SysRq+REISUB to reboot at this point.
OR: Screen graphics scramble, programs won't load their GUI's but are still functional.

File system sometimes becomes read only and corrupt too when this happens.
 
**Hardware:**
Computer Processor: 2x Intel(R) Pentium(R) Dual CPU E2180 @ 2.00GHz
Memory 3086MB: (443MB used)
VGA compatible controller:    Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])

**OS/Kernel**
Operating System: Ubuntu 11.04
Kernel: Linux 2.6.38-8-generic (i686)


**Syslog Sniplet**
> May 9 06:17:58 onnud-KJ385AA-ABA-a6433w kernel: [19809.880011] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 9 06:17:58 onnud-KJ385AA-ABA-a6433w kernel: [19809.880733] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 1073422 at 1073418, next 1073430)
May 9 06:17:58 onnud-KJ385AA-ABA-a6433w kernel: [19809.880881] [drm:i915_reset] *ERROR* Failed to reset chip.
May 9 06:18:39 onnud-KJ385AA-ABA-a6433w acpid: client 1035[0:0] has disconnected
May 9 06:18:39 onnud-KJ385AA-ABA-a6433w acpid: client connected from 1035[0:0]
May 9 06:18:39 onnud-KJ385AA-ABA-a6433w acpid: 1 client rule loaded
May 9 06:18:40 onnud-KJ385AA-ABA-a6433w kernel: [19851.735594] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
May 9 06:18:51 onnud-KJ385AA-ABA-a6433w kernel: Kernel logging (proc) stopped.
May 9 06:18:51 onnud-KJ385AA-ABA-a6433w rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="465" x-info="http://www.rsyslog.com"] exiting on signal 15.This is what was in the log at the time of the last crash. Full contents here:
Syslog: [http://pastebin.com/raw.php?i=nxDmzT79](http://pastebin.com/raw.php?i=nxDmzT79)
 Xorg.0.log: [http://pastebin.com/raw.php?i=6XKfHNW1](http://pastebin.com/raw.php?i=6XKfHNW1)

---

### Post by Habaken on 2011-05-12
**Update:**
The corrupted files seem to be mostly related to Python, Perl and some GTK stuff. Reinstalling packages related to those three lets me run apps that were once "corrupted" again.

What tipped me off was I ran the stuff that wouldn't launch correctly from the console to see their errors. What I'd find was either badly configured/corrupt stuff.

Stuff like:
*[I]debconf*: [I]Perl may be unconfigured
ImportError: No module named dbus
[/I]*Can't locate warnings/register.pm in @INC*[/I]

---

### Post by Habaken on 2011-05-31
Still having this happen to me FYI.

Am I not including enough info. to debug this? It's really getting old with me having to reinstall perl stuff or Ubuntu itself over and over.

---

### Post by jerrrys on 2011-05-31
don't know if it will help, but
have you tried to repair/check file system with either 'disk utility' or 'gparted'

---

### Post by Agent24 on 2011-05-31
To me this sounds like a hardware problem, most likely a faulty hard drive or RAM.

Have you tried running Memtest? What does Disk Utility say about your HDD's SMART status?

---

### Post by Habaken on 2011-06-02
Smart Status is non-existant I'm running Ubuntu off of a USB drive. 

And the file system was .. corrupt again, @ Jerry's. I'll just get a new HD and try my luck on that.

---

### Post by Agent24 on 2011-06-02
> **Habaken said:**
> Smart Status is non-existant I'm running Ubuntu off of a USB drive. 

And the file system was .. corrupt again, @ Jerry's. I'll just get a new HD and try my luck on that.

Maybe the fact you're running from USB is the problem. I find it's not always as reliable as IDE etc.

---

### Post by mattgyver83 on 2011-06-03
> **Agent24 said:**
> To me this sounds like a hardware problem, most likely a faulty hard drive or RAM.

Have you tried running Memtest? What does Disk Utility say about your HDD's SMART status?

Id have to agree, the symptoms that you explain sound very indicative of some hardware issue, especially because they are all across the board.  I once had some bad capacitors on a motherboard that continued to make a system of my reboot intermittently however only happened when I did certain actions on a web application that it was hosting.  Very odd but just to point out that sometimes hardware issues appear to be software issues.

---

