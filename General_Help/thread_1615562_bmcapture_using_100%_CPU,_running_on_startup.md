---
title: "bmcapture using 100% CPU, running on startup"
date: 2010-11-07
forum: General Help
---

### Post by Meshaal on 2010-11-07
Earlier tonight, I noticed my computer seemed to be running excessively noisily, and upon checking into System Monitor, I noticed that my CPU was being held constantly at 100%.  None of the processes listed on the process tab seemed t be responsible, but I found [this thread]("http://ubuntuforums.org/showthread.php?t=1533179") which gave me the 'top' command.

Running it, I found a process running as root called 'bmcapture' that was responsible for the CPU use.  Trying to 'kill' it failed; using 'sudo kill' gave me no error messages, but the process continued to run.  This carried on through a restart.

I then proceeded to shut the computer down and leave it off for a minute.  When I booted up again, the CPU was still running at full, and using 'top' I determined the same process was responsible; however, 'sudo kill' successfully killed it this time, with apparently no adverse effects.

My question is if anyone has any information about what 'bmcapture' is, whether its harmful (aside from the obvious issue of it using full CPU) or malicious, and if there's any way to stop it running on startup, because as it is I'm having to manually 'sudo kill' it every time I turn my computer on to stop it eating my CPU alive.

Thanks for any and all help.

---

### Post by PhoHammer on 2010-11-08
Do you have BitMeter OS installed? ([http://codebox.org.uk/pages/bitmeterOs](http://codebox.org.uk/pages/bitmeterOs)). 
I did on my mac and found this thread: [http://discussions.info.apple.com/thread.jspa?threadID=2586192&tstart=15](http://discussions.info.apple.com/thread.jspa?threadID=2586192&tstart=15) .

Just uninstall it and everything will go back to normal. On mac, I just ran "/Library/Application\ Support/BitMeter/bmremove.sh " in Terminal.

"sudo /etc/init.d/bitmeterweb stop" (without quotes) will stop it in a LInux terminal.
He doesn't appear to give uninstallation directions for Linux...

---

### Post by Meshaal on 2010-11-08
I apologize for leaving this thread unattended.  Shortly after I posted it, I determined it was BitMeter that was causing the issue.  After contacting the developer, he's been very helpful in solving the issue, which may, it seems, have been caused by the daylight saving time switch.

---

### Post by r0bd on 2010-11-09
Hi,
I'm the author of BitMeter OS - firstly my apologies for this, there was a nasty bug in the code that only appears if the app was running during the switch from Daylight Savings Time. I've got a fix and will be releasing a new version in the next few days, after testing. Details of the issue can be found here:
[https://sourceforge.net/tracker/?func=detail&aid=3105437&group_id=200024&atid=971845](https://sourceforge.net/tracker/?func=detail&aid=3105437&group_id=200024&atid=971845)
regards
Rob D

---

