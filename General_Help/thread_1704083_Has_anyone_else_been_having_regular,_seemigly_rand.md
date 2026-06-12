---
title: "Has anyone else been having regular, seemigly random freezes in 10.10? Please post if"
date: 2011-03-10
forum: General Help
---

### Post by migel_wimtore on 2011-03-10
Hi. I am interested to know if, as i am, many people out there using Ubuntu 10.10 (or 10.4) have been experiencing seemingly random freezes. Whereby the system freezes and responds to absolutely no input.

If you have been having a similar issue perhaps you could post in this thread and we could try and establish some commonalities. 

Or maybe, you have some suggestions on how you have dealt with a similar issue.

Perhaps its hardware, software, drivers or some combination. 

I have a Dell Inspiron 1300, with a Pentium M 2.10ghz CPU.

I have experienced freezes with and without Compiz running and even in Openbox sessions.

So anybody?

---

### Post by mikewhatever on 2011-03-10
I've seen several threads on random freezes and even a mega-thread, but seemingly, nothing apparent connected them. Hardware, software, drivers, all can be the cause of freezing. Try running memtest to check the RAM, also, do you have a 8xx Intel GPU?

---

### Post by HermanAB on 2011-03-10
Yup, judging by the forum posts, Ubuntu 10.10 is one of the most unstable Linux distros in many a year.  It depends on your hardware.  If it crashes for you, then a good solution is to switch distros and try Fedora or OpenSuse.

---

### Post by prshah on 2011-03-10
> **migel_wimtore said:**
> have been experiencing seemingly random freezes. Whereby the system freezes and responds to absolutely no input.

Well, I'm using Ubuntu 10.04 and 10.10 on a mix of desktops and laptops, 32bit/64bit, and don't have a single problem. All 10.10s are upgraded from 10.04s.

The only time I was facing problems similar to what you describe was with 8.10, which I finally figured out to the fact that I had both Kubuntu and Ubuntu desktops installed in the same installation. Everything went back to normal after I removed most kde related stuff.

Basic steps to try:
a) When next your system freezes, check if HDD lights and/or optical drive lights are active.
b) Does the system recover by itself, or are you forced to reset?
c) Can you switch to a virtual terminal using Ctrl+Alt_F1..F6? 
d) Does using the [magic sysreq keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key") have any effect?
e) Force a diskcheck on the next reboot with the command```
sudo touch /forcefsck
```
f) Have you recently added any hardware such as a PCI wireless card, USB daughter card or Modem card?

If you install ssh-server you can check if the system is internally responsive when frozen by attempting to login in with another computer from the network.

Summary: I think it's an issue related to your machine, not Ubuntu in general.

---

### Post by migel_wimtore on 2011-03-10
Hi. Thanks for the feedback. 

In response to mike whatever, yes it is an 8xx series cpu. I have memtested the ram quite recently and it checked out. 

To HermanAB, i have also recently installed both arch and debian and they did not suffer the problem, but i came back to ubuntu, for reasons explained in this thread:

[http://ubuntuforums.org/showthread.php?t=1703976](http://ubuntuforums.org/showthread.php?t=1703976)

Where i also give more specifics regarding my case.

And to prshah, i currently have black electrical tape over all my flashing lights as they annoy me when watching video, but i will take it off next time i get a freeze to check. What exactly would active hd or optical drive lights indicate? 

And no, it most definitely does not recover by itself, and needs to be hard reset, neither does it respond to console change commands, ctrl alt backspace, or sysrq alt gr REISUB, is there anything else i should try?

Also, i am quite sure it is not the disk as it has been recently upgraded, the previous one having bad sectors, which i thought might be the cause. The new disk passes checks perfectly.

I would tentatively conclude that it is not my machine, per se (though perhaps something to do with my configuration) as i have tried other distros and they work fine. And, as HermanAB and mikewhatever mention, im am far from alone in reporting similar issues.

That being the case, perhaps il stick it out until 11.4 and see if that fixes the issue. Still, it would be great if anyone suffering a similar issue and who has any possible pointers, or just wants to ad their mark to the tally could do so.

Thanks all.

---

### Post by prshah on 2011-03-11
> **migel_wimtore said:**
> What exactly would active hd or optical drive lights indicate? 

definitely does not recover by itself, and needs to be hard reset, neither does it respond to console change commands,

Flashing HDD activity lights are normal. However, if you have a SOLID light (no or minimal flashing) for a minimal I/O operation, it may indicate a problem; eg, in the case of an HDD, possibly bad sectors; but from what you say, that is possibly not a cause.

I had a Samsung cheapo DVD drive in which, when a CD/DVD was inserted, the whole system froze until the DVD drive had finished recognizing whatever disk was installed. However it would recover fine and continue working properly once recognized; so I don't believe this is your problem.

Memtesting has eliminated memory problems.

So that leaves graphics or kernel problems.

A kernel freeze (panic) will be indicated by flashing caps lock and scroll lock lights on the keyboard. This can be caused by bad memory, hardware conflicts with legacy internal cards etc.

A graphics based problem should allow you to switch terminals and/or magic sysrq and/or ssh access, so I don't think this is possible either.

Have you considered a thermal issue? In intermittent, random hangs, this would probably be the first thing I would eliminate; are your case fans working properly?

---

### Post by Hedgehog1 on 2011-03-11
> **migel_wimtore said:**
> Hi. I am interested to know if, as i am, many people out there using Ubuntu 10.10 (or 10.4) have been experiencing seemingly random freezes. Whereby the system freezes and responds to absolutely no input.

_Perhaps its hardware, software, drivers or some combination._ 


migel_wimtore,

I have been working by Ubuntu 10.10 very hard.  I have never had as solid an OS as this before.  However, I am running more modern hardware and lots of RAM to support multiple Vbox images running at once.

The majority of the instabilities (outside of viruses) on our MS windows PCs are because of drivers, not the OS.  I expect you are suffering from driver based instabilities.

***The Hedge***

---

### Post by migel_wimtore on 2011-03-11
Hedghog1: Interesting. 

Any suggestions on how i might isolate the culprit? Perhaps by selectively using alternate drivers one by one to narrow it down?

I am not sure with video driver i am using, how can i find that out (amatuer i know)?

When i installed Arch i selected "xf86-video-intel", which seemed to be the only appropriate one in the list then provided (and was def. compatible, as i researched its applicability). 

Is it likely to be the same one in ubuntu, or would ubuntu install have given me a generic video driver, and could this be the problem?

Thanks for the feedback. And yes ubuntu used to be really stable for me to, when i used the powerpc edition, and yes, you are right, it is no doubt something to do with my setup, i just want to find out what.

My system isnt at all new, but it is (in my estimation) quite capable for my needs: Intel Pentium M Processor 740 (1.73GHz/2MB Cache/400MHz FSB), 2 Gig DDR2 RAM, Intel integrated Media Accelerator 900 graphics card. 

I just browse mainly, and she really does load dem pages quick, by gum.

---

### Post by Kramtoad on 2011-03-31
I started having a similar a few weeks ago. When it happened today I SSHed in from another machine. Found the load to be 1.00 and compiz sucking cpu time like crazy. Killed and restarted compiz. That fixed the current screen freeze.

Guess who has never been a fan of compiz?

-K

---

### Post by migel_wimtore on 2011-03-31
Hi thanks for replying. I had considered compiz might be the problem, so had disabled it when running GNOME, however this did not solve the issue. I hadnt expected it to, as most of the time i was running Openbox and the freeze problem was occurring.

Have moved to Debian now, so wont be able comment here about Ubuntu specifically.

I have been running Debian now for two weeks or so, and have experienced one freeze in that time.  I suppose this might suggest that the problem is my hardware, or perhaps the video driver (i am using the intel driver). Whatever the case, if this freeze is related, or caused by the same issue, Debian's famed stability seems to contain it more effectively.

Cheers.

---

### Post by newblueboy on 2011-03-31
I've had one freeze. 

I was watching CNET TV in Google Chrome and then I closed the browser. The audio kept playing, I couldn't stop it, and then by itself the audio quit and then I got a "Black Screen of Death". I did a cold reboot and it worked fine.

---

### Post by migel_wimtore on 2011-03-31
Newblueboy, the freezes i was experiencing seem to have been quite different. 

Though i might be doing (from what i could tell) quite different things before the freeze, the result was always the same: instant freeze, no mouse activity, and no ability to close applications, and no black screen, just a frozen screen. However, if i had an audioplayer open the last quarter second or so of the music would loop (which would not happen in a flash player, if one was playing at the time), until i hard rebooted.

Perhaps you freeze was flash related? If you are lucky you might be able to trace your freeze. Try searching "/var/log/messages" and "/var/log/syslog" to see if you can see anything that would indicate what happened at the time of your crash, then search around what you find there.
Also, you might check "var/log/kern.log", to see if you experienced a kernel panic. There is usually allot printed in these logs (which can also be accessed via the Log File Viewer application), so keep an eye on the time stamps printed on the left of each entry, to narrow down your search. Hope im not patronising.

Any other tips on diagnosing system freezes would be most welcome.

---

### Post by NadirPoint on 2011-03-31
This 10.10 install was fine until just recently, maybe less than a week ago.  Still running fine in background, router, servers, etc. just no mouse or keyboard response.  I'll look into the remote login/compiz issue next time.  Hard booted it three times now in the past 2 days.

Must be result of a recent update.

---

### Post by migel_wimtore on 2011-03-31
NadirPoint, thats very interesting. I had no way to tell about background processes (that i know of), as i am running an isolated desktop install, and with no access to mouse or keyboard...
However, when i did experience a freeze, judging from drive and fan activity, the system wasnt overloaded. So, conceivably all sorts of processes could have continued unimpeded. Perhaps, i was also just loosing mouse and keyboard input too.

Have you tried pressing alt gr + fn + r e i s u b? This key configuration is supposed to initiate various processes, ending in the safe power down of you computer, and a second or so should be allowed between presses of the letter keys. 
It never worked for me during a freeze though, what with no keyboard input.

---

### Post by NadirPoint on 2011-03-31
No, there's no input recognized, so...  Just happened twice in the past couple hours and remote login showed now unusual activity or lack thereof.  I have booted the previous kernel for now and will wait and see.  The problem diagnosing this machine is sometimes it may sit here running as my LAMP server for a day two at a time with nobody logging on locally to use it, so it could be in this condition for quite awhile before it was noticed.

---

### Post by migel_wimtore on 2011-03-31
Interesting. I could never find any pertinent readouts on scanning /var/log/messages,  /var/log/syslog or var/log/kern.log after any of the freezes i experienced. Often there were no readouts at all for the time of freeze. I would be interested to know if you narrow it down to the kernel, as i was not always experiencing this issue, so an update at some point might have caused it. Sometimes i would expereinece freezes as frequently as two in a couple of hours, more frequently one a day, sometimes even one per two/three or even four days, so it was very hard to pin down. As i mentioned above, Debian has been much more stable for me, though it has freezed once over the last two weeks. Yet, presumably both Ubuntu and Debian are running the latest kernel?

---

### Post by n213978745 on 2011-03-31
I used to have freeze problem with my old laptop, but it's not because of the OS' fault.  It's because that part of components of my laptop is broken, not the RAM, not the HDD.  It's my wireless part and something else... which I don't know LOL.  Also my BIOS has displayed some weird looking message telling me about some error code.

I further confirmed it by switching to other Linux distro, and it froze too.  So then I bought a new laptop, and freeze never happens again on my new laptop.

---

### Post by migel_wimtore on 2011-03-31
In my case you might be right. Swiched to Debian and have experienced a similar freeze. My laptop is quite old. However, once every two weeks i can handle, Debian, once a day was just bloody annoying, Ubuntu. That said my girlfriend had been running XP on this machine for a long time, before i bought it off her, and tells me she did not experience any regular freezing. So, ....

---

### Post by NadirPoint on 2011-04-01
This is a 4-year old HP Pavilion Slimline with the Nvidia 512mb graphics option on which .35-27 seems to run quite happily, as have all previous versions since installing 10.10 shortly after it became available.  .35-28, not so much.  Whatever the problem is, I believe the graphics/kernel interface may be at issue.  As I stated earlier, the system seems to run fine, just apparently no display.  Hard to tell if anything you are doing with the mouse or keyboard is getting in without the display.  Just a wild-assed guess.  :confused:

Looks like I am stuck waiting for the next kernel before being relived from invoking the Grub menu upon restarts.   :(

---

### Post by dhopley on 2011-04-01
Dear Forum , 
I've an old desktop with an Intel 85625 Integrated Graphics card under 10.10 and using mainly Metacity . On Metacity or Compiz I've experienced freezes which can be relieved only with ctl-alt-sysreq-K with the need to relogin and pick up where you left off , with Firefox usually presenting the 'Embarassed about this message' and asking for new session or restore . The problem seems to me to be a GPU lockup usually generated with >1 window in Firefox , with one window currently downloading a file and in another window attempting to scroll down the screen too quickly , especially if the scroll window contains a lot of flash video stuff . I just take more care now to see if the scroll screen is fully resolved before spinning the wheel . My guess it's problems in the generic driver as I don't bother with the specific Intel driver which I think is 'blacklisted' for my old machine anyhow ,    
Best Wishes

---

### Post by migel_wimtore on 2011-07-15
Hi. Just to update. I beleive i did narrow the cause of my freeze issue to flash player. I have since run FlashAid to resolve conflicting versions. I experimented with the various availbale versions offered within FlashAid, to get the best Flash player performance (make sure you test fullscreen when trying the different versions!).

It did seem as though i had conflicting versions installed on this machine, and since running and experimenting with FlashAid i have had no more freezes. Not one.

I was wary about posting that, lest i jinx myself. So, touch wood.

---

