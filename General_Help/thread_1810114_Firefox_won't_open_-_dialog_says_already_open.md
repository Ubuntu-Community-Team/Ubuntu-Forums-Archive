---
title: "Firefox won't open - dialog says already open"
date: 2011-07-22
forum: General Help
---

### Post by FredVanH on 2011-07-22
Hi.  I tried to invoke Firefox in Ubuntu 10.04.  I got a dialog box entitled “Close Firefox”, which said:
 “Firefox is already running, but is not responding.  To open a new window, you must first close the existing Firefox process, or restart your system.”.  I had not recently had Firefox running; so there was no instance of Firefox showing on the desktop display.
 

 I have had this problem from time to time in the past;  but just rebooted.  Seems like there should be a better way.  Any ideas as to:
 1.  How that unknown instance of Firefox got orphaned?, and
 2.  How to fix the problem without rebooting?
Thanks,
Fred

---

### Post by Quackers on 2011-07-22
You could try opening system monitor and under the processes tab see if there is an entry for firefox.bin running. If there is highlight it and click on "end process".
It may not appear at all in system monitor though.

---

### Post by altometer on 2011-07-22
CTRL+ALT+T type TOP and hit enter
If you see a process called "Firefox" press K and type the number in the process ID column. Then press enter.

---

### Post by ajgreeny on 2011-07-22
You can also try ```
killall firefox
``` in terminal or just reboot, but try to kill it first if you can, to save rebooting, which should not be necessary.

---

### Post by FredVanH on 2011-07-22
Thanks, Quackers & Altometer for your kind and timely responses.

Quackers, I tried yours first and the firefox binary was indeed listed in System Monitor.
It looked like all I had to do was highlight its entry and push the "End Process" button.  I postponed doing it because I also wanted to see the other solution.  Thanks!

Altometer, I then tried yours:
Ctrl-Alt-T got me into Terminal (nice - now I know 1 more thing),
"TOP" was rejected but "top" got me into the processes display and there indeed was the firefox binary listed on the first line.
Typing "K" brought up the Kill Process 1-line dialog.
I typed the Firefox binary's PDID number and hit Enter.
What looked like a failsafe message came up: "Kill PDID 3914 with signal [15]:"
I typed "Y" for Yes and hit enter.  The display changed a little but Firefox was still there.
I typed "15"          and hit enter.  The display changed a little but Firefox was still there.
I merely                     hit enter.  The display changed a little but Firefox was still there.
What did I miss?
Thanks,
Fred

---

### Post by The Cog on 2011-07-22
I haven't used system monitor to kill processes. I have sometimes seen tha tproblem where firefox-bin is running but has no visible window, making it impossible to launch a new firefox properly. I think this command has always worked for me:> killall firefox-bin but if that doesn't do it, this should:> killall -9 firefox-bin

---

### Post by Quackers on 2011-07-22
It looks like it won't respond.
Try the system monitor method and see if it does the same.
The only other thing I would try is to shutdown fully and try a cold boot.
It would be interesting to know where the instruction to start the bogus firefox is coming from though.

---

### Post by The Cog on 2011-07-22
> **Quackers said:**
> It would be interesting to know where the instruction to start the bogus firefox is coming from though.
I think it happens when a legitemate firefox fails to shut down properly - the window disappears but some part is left running. It seems to happen to me occasionally when firefox gets unresponsive on certain page contents and I close it with the intention of starting a new one. I haven't seen it happen so much recently though, so I guess FF is getting better.

---

### Post by Quackers on 2011-07-22
Ah, that makes sense. I wonder why it does that on occasions? Very naughty.
Thanks :-)

---

### Post by FredVanH on 2011-07-22
I hope Quackers, ajgreeny and The Cog are not offended by my postponement of trying your solutions.  They all seem straightforward and I WILL try them.  I only have one situation to test.  If you will bear with me, I'd like to see if altometer responds as to what my response to the failsafe on his solution should have been.  Many thanks to all of you!
Sincerely,
Fred

---

### Post by FredVanH on 2011-07-23
Ok, guys/gals.  I tried 'em all and none of 'em worked:
The Quackers one - System Monitor, finding, highlighting and "end process" - no change.
Altometer's:  I've summarized it previously - no change.
ajgreeny's:  killall firefox:  I got "firefox: no process found". - no change.
The Cog's:  killall firefox-bin and killall -9 firefox-bin:  No reply - no change.

I am convinced that each one of your solutions was a good one and would have worked under "normal" circumstances.  To me, this was a glaring exception, as follows:

I finally cold booted and got firefox to come up;  but when I had invoked it from its icon, I first had to choose between a cold restart of firefox and a restore of a screwed-up session with my credit union's site from the night before.  I had forgotten about that (blush, blush).  In the middle of a secure session with them making an online deposit, I must have hit a wrong key combo and what I then got I can't even remember.  I later verified that my deposit had "taken" and even later received a normal confirmation email.  So, it appears to me that that's how that hunk of firefox remained, like Quackers and The Cog suggested.  I just invoked a new firefox session and dumped the old one.

So, sorry for all the confusion and thanks to each of you many times over for the solutions.  I learned a lot about how to kill processes, which I have many times wished I knew; so at least for me it wasn't a waste of time.

Thanks again,
Fred

---

### Post by FredVanH on 2011-07-23
Hi, Guys/gals.  I tried 'em all but none worked - for me.  I'm convinced that they're all good under normal circumstances;  but that this was just too notable an exception:

I finally cold booted.  When I then invoked firefox via its icon, I got a choice of invoking a new instance of firefox or restoring the screwed-up instance left over from last night, about which I had forgotten (blush).  Last night, in a secure session with my credit union, I was about to submit a new deposit when "something" happened (maybe a bad key-press).  I ended up logged off.  When I got back on, the deposit was registered a-ok.  I then logged off, closed firefox and forgot about it.

So, that was probably the warped instance of firefox about which Quackers and The Cog were speaking.

Sorry about the confusion.  I, for one, don't consider this to have been a waste of time because I learned 3 things I didn't know before but wished I had about how to kill a process.  I thank each of you very much for jumping to the rescue when I needed it.
Sincerely,
Fred

---

### Post by FredVanH on 2011-07-23
Sorry about the duplicate final message.  After submitting the second to last one, I failed to notice that it had gone to page 2 and thought it had gotten lost.

---

### Post by cdtech on 2011-07-23
Glad you got it Fred! I'm a command line kinda guy myself. Learn the ps (process status) command and it's options. The good thing about the ps command is that it is installed on your Linux system by default so if your running a headless system, server or loging in remotely, you won't have to worry about installing it. 

Good luck

---

### Post by FredVanH on 2011-07-23
Thanks fpr the encouragement and advice, CDTech.  I'll surely look into that.
Regards,
Fred

---

### Post by zlot on 2012-11-24
I quickly reviewed this thread because I have the same problem. But if my quick review has missed something, I apologize in advance.
It's interesting that the first post was 2009, and here it is almost 2013, and I'm having the same problem.
Although little more than a newbie(I've been using Ubuntu for a couple of years or so), I do know about system monitor and have it in the launch bar just to address the topic of this thread!
BUT!!!!...............
Let's attempt to deal with the real issue!
Here it is more than three years later and the same problem exists!
Why?
Why?
Why?
Why should we have to kill the Firefox process at all?
Is there something that can be done on the user level to keep this from happening?
If so, I wish someone would share that. 
I think what sometimes happens in my case is that Firefox isn't coming up very fast and I wind up clicking again and when it attempts to launch two versions more-or-less simultaneously, it chokes and neither launches.
But even granting my spasticness, it should be able to handle that. So maybe it's just a fault of the program that the developers refuse to contend with - I don't know, but wish I did!
Thanks in advance for any comments or suggestions.....

---

