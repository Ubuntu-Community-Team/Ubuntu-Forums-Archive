---
title: "My Ubuntu is starting to slow down again (worse than before) My Windows 7 works fine."
date: 2011-01-23
forum: General Help
---

### Post by colobix on 2011-01-23
Hello guys. I am sorry that this is my 2nd thread on this.
I have been posting a lot on this forum ever since I installed version 10.04 on my PC.
My Windows 7 is just as fast as always but Ubuntu is slow as if I had my Windows PC on for like a week doing CPU killing processes all the time.
Like literally. It takes forever to open up a program. some times it comes up after I count to 5 but not faster than that.
Processes such as compressing files and things like that takes forever and slows down my pc a lot. Still lagging while I type things. And flash is a nightmare now. I can't chat on blogtv anymore because it takes forever and everything hangs a lot. This time I want a solution, a real fix.
**Do not suggest that I reinstall. Been there, done that 50 times.**

THings that I hope will fix some of these problems are
1) the upcoming flash version 10.2. They say it uses way less cpu.
2) the new upcoming kernel which is also pretty fast.
3) the new gnome thing for 11.04 I have heard good things about.
So I will give 11.04 a try before I decide rather or not I should move back to use windows only, but I REALLY don't wanna go there.
I know you might wanna ask. "Why don't you just wait for 11.04 to come out instead of trying to fix all this now?". Simple. I don't wanna do a reinstall. I want to do a normal upgrade so I don't have to reinstall all my stuff all over again. That thing is a nightmare.
Sorry again, and I know this is a long post for you to read since I've been rambling a lot, so yea. Again, thanks in advance. If you want to help me out, that would be nice. Thanks in advance.

---

### Post by ubudog on 2011-01-23
Hi!  Maybe I can help.

1. What type of computer do you have?
2. Maybe try upgrading to 10.10 via Update Manager?  Don't know if that will work, but I guess it's worth a try.  Back stuff up!

3. Open the System Monitor, or type 'top' in a terminal, and try to find a cpu killing process.  Killing it may help.  (Just make sure it's not necessary.)

---

### Post by tigerstripedcat on 2011-01-23
I'm not sure I've had an ubuntu machine slow down on me--it's just not windows-like design.

1) Get a live cd and boot with it, and run a benchmarking program (superpi? there's probably something better)
2) Compare it to what you have when you boot up without the live cd
3) Run "top".  What is taking up the cpu, what is taking up the memory. If you can kill those processes and see if it speeds up.
4) Try a boot analyzer to see what starts when you start the computer, maybe you have a lot of extra processes running.

It sounds like to me that you are having mostely browser/flash related problems. What browser are you using?  Have you tried chrome?  If so, have you tried firefox?  Make sure BOTH RUNNING IN SAFE MODE (that is without addons) when you test them out.  Go in and disable any unnecessary plugins too.  When flash is running try 'top' again and see how much cpu it's using.  Try the same with a live cd and see how different it is.

---

### Post by ubudog on 2011-01-23
For example, I have heard of cases where Pidgin (the chat client), was bugging out and taking up all the resources.  This made people's computers super slow.  This may be the same problem you're having.  You just have to find that process.

---

### Post by ubudog on 2011-01-23
You said you reinstall a lot, and each time it is slow.  So is there a program you install after each reinstall?  For example, Pidgin?

---

### Post by colobix on 2011-01-23
Thanks for your replies. 
I use an Acer PC, can't tell you what model but it's a 3 months old pc.
I don't use pidgin, I use Emesene. My problem isn't just the web and flash (Firefox 3.6), I don't like Chrome because FF has all the good plugins I need.
Graphics card: Nvidia, Kernel: 2.6.32.27.
But as I said, filebrowsing is also slow sometimes (depending on how many files etc).
But when I turn on the computer, everything works smooth until I start doing things that for some reason takes a lot CPU.
Things like flash (videos), music (I use rhythmbox), and things like that.
You know, things that doesn't take much cpu in windows.
So that is kinda odd. Because this means that there is (probably) nothing wrong with the PC.
Btw I took the memory test from the grub menu but it didn't find any errors.
Other facts:
Processor 0: Intel Atom CPU 230 @ 1,60GHz
Processor 1: Intel Atom CPU 230 @ 1,60GHz
Memory: 3GB (Actually 4 gb but can only read 3 of them for some reason).
Also, I always use the top command but the only things that takes a lot of cpu are things I need to have open (firefox, the flash plugin for firefox etc).
And I have already cleaned out the startup programs list.

---

### Post by tigerstripedcat on 2011-01-23
Look, you're going to have to start ELIMINATING things that can be causing the problem from the equation, not just trying tests for what you think it might be.

1) Boot with a live cd. Is it slow?  It better not be, or it might be a hardware problem.
2) Use chrome or another browser.  Not permanently, but just for diagnostic purposes. If it doesn't become slow, then you know it may be Firefox.
3) Reboot the computer and don't even use any browser at all, for an hour or so.  Try listening to some music or something else.  Does it slow down still?
4) You seem to think it's cpu related.  Well reboot and run a cpu burn in program and using the computer as normal, BUT DON'T OPEN A BROWSER.

Do this:
1) Reboot
2) Open a terminal and run
sudo apt-get install cpuburn
burnP6
3) Run it for an hour

Does it overheat, does it lockup, does it restart.

Then while it is running use the computer but don't open a browser.  Is it still slow?  It may be kinda slow because you are using 100% of cpu with this burnin program, but you should still be able to browse files and play music.  BUT DON'T OPEN A BROWSER.  See if it works ok without Firefox.

Based on everything you've told me, there's no reason to think it is not something with Firefox.  If a few flash tabs or bad plugins are going crazy then you can slow the entire system down. You really have to do the above, and do them EXTENSIVELY or else the worse problem arises: "Oh it can't be Firefox" and it really is, and you spend days looking elsewhere just because you made an assumption and didn't really investigate it.


I'm not saying that it has to be Firefox. But it is the buggiest and memory/cpu things you have on your computer, and everything you said is still consistent with it, which is why you have to be sure.

---

### Post by ubudog on 2011-01-23
It could very well just be a bad Firefox plugin.  This has happened to me before, even on my powerful lappy.

Also, if you can, try booting into another kernel on startup.  It may be an update issue...

---

### Post by colobix on 2011-01-23
Thanks guys
As I said in my first post, I have heard great things about the upcoming kernel, but I only have the one I use now since I am always too fast on removing things I don't need or use.
I also kinda think that his might have something to do with the flash plugin, but this is the only plugin that will play videos flawlessly on hulu which I use a lot.
A few questions about the google browser.
Are there alternatives for the UltraSurf / Wj proxy plugin, adblock plus, mediaplayerconnectivity and Video DownloadHelper?
These are the plugins I use in FireFox.
And I can't seem to find any google chrome plugins in synaptic.
How is flash in Chrome?
In firefox I use a plugin called Flash Aid. This plugin helps me find the best and most recommended flash plugin for my system.
That is also the plugin that works best and is less lagy than Adobe flash.

ALso, in synaptic I found 3 different versions of Chrome. 7.0 (stable), 8.0 (beta) and 9.0 (unstable).
Seems like they are experimenting a lot with different versions. which one should I choose?

---

### Post by ubudog on 2011-01-23
I'd say choose unstable, ironically, it supports more things.

---

### Post by skypuppy on 2011-01-23
I have the same problem as the OP.  I think it is something in Firefox with certain web pages.  Could be that java or some other plugin in certain web pages just grabs cpu and just won't let go.  And the problem seems to feed on itself, as if some java code is being extremely recursive (or grabbing memory) and won't let go of what it has.

---

### Post by colobix on 2011-01-23
Thanks. Don't worry about the plugins. I found what I Needed.
Also, in firefox, I like that you can shut it down and open it wit the same site history and tabs.
Is this possible to do with Chrome somehow?

---

### Post by mexicanseaf00d on 2011-01-23
the UbuntuOne firefox plugin had my cpu clogged up for no reason, everything was slowed down. But that was quite a while ago (not long after 10.04 came out)

---

### Post by Brad55 on 2011-01-23
Well one of the first things I do is goto startup apps and turn off the things I don't use so they don't load.

---

### Post by bucks on 2011-01-23
This is only my second post on these forums, but I had a similar problem the other day. My  problem was that i tried to update my grub, and it bogged my cpu right down . It used 100 percent of my cpu to open gedit. It was not really any one program slowing me down. Luckily i also installed ubuntu dual boot with windows 7. All i did was went into my Ubuntu folder in windows and saved my disk image to desktop. The i uninstalled Ubuntu. After that i reinstalled it and replaced the "blank" or new disk image with the one on my desktop.  Restarted the system and "BOOM" everything was running like a clean install for me. And i got to keep all of my files, programs and settings. My grub went back to an earlier version, and i didn't try upgrading that again. I mean this could help you out, if you had the same problem as me.

---

### Post by tigerstripedcat on 2011-01-23
Not sure about the tab save, but I'm it probably has it, might take a bit of googling.  Does it work better with chrome or are you just trying it out?

---

### Post by colobix on 2011-01-24
I got the tab thing to work. ANd thanks a lot guys for told me about GoogleChrome :) It is so much faster and better on so many levels.
My only problem now is the proxy swichy plugin which is great, but I can't set the proxy username and password anywhere. So I just have to use proxy on the whole browser now, but that's ok though. no big deal.
ANother thing that doesn't work which is not a big deal either, is Moonlight (silverlight).
BUt I guess I can live without these two things since the browser is just KING! So again, thanks:)

Now, nautilus can still be very slow in some folders such as my music folder, /usr/bin, etc. Sometimes it comes up only after 2 sec but sometimes I Have to wait for freaking ever. And yes, this is without having firefox open.
And rhythmbox is still very slow when I scroll, change song, etc...
And idea?

---

### Post by TBABill on 2011-01-24
> **colobix said:**
> Hello guys. I am sorry that this is my 2nd thread on this.
I have been posting a lot on this forum ever since I installed version 10.04 on my PC.
My Windows 7 is just as fast as always but Ubuntu is slow as if I had my Windows PC on for like a week doing CPU killing processes all the time.
Like literally. It takes forever to open up a program. some times it comes up after I count to 5 but not faster than that.
Processes such as compressing files and things like that takes forever and slows down my pc a lot. Still lagging while I type things. And flash is a nightmare now. I can't chat on blogtv anymore because it takes forever and everything hangs a lot. This time I want a solution, a real fix.
**Do not suggest that I reinstall. Been there, done that 50 times.**
 
THings that I hope will fix some of these problems are
1) the upcoming flash version 10.2. They say it uses way less cpu.
2) the new upcoming kernel which is also pretty fast.
3) the new gnome thing for 11.04 I have heard good things about.
So I will give 11.04 a try before I decide rather or not I should move back to use windows only, but I REALLY don't wanna go there.
I know you might wanna ask. "Why don't you just wait for 11.04 to come out instead of trying to fix all this now?". Simple. I don't wanna do a reinstall. I want to do a normal upgrade so I don't have to reinstall all my stuff all over again. That thing is a nightmare.
Sorry again, and I know this is a long post for you to read since I've been rambling a lot, so yea. Again, thanks in advance. If you want to help me out, that would be nice. Thanks in advance.
 
I know you have tried lots of things and found some fixes or workarounds from the rest of the thread, but I'll throw out a couple things. First, the Firefox extension FLASH AID will look at your Ubuntu install and prompt you if a newer version of Flash is available direct from Adobe, plus it will install it for you. It's a savior if you don't want to do it all manually and always want the latest Flash installed. All you have to do is open Firefox once in a while so it can run and do it's thing. Takes just a second to know if you need to update and the update is quick as well. Search Google for FLASH AID and follow probably the first link listed to download/install. Your Chromium depends on the same Flash install so you'll benefit in both browsers by installing this in Firefox.
 
Second, do you watch Top while you are having issues to see if something is just maxing out the CPU? Are you hitting your swap partition a lot? Is it big enough? With so much RAM I can't imagine you hitting it much, but possible.
 
Did you disable IPv6 within Firefox? Your system can show it disabled but Firefox can still be trying to use it, making Firefox page loading incredibly slow. This won't help your other issues, just a small thing I wondered if you checked because Firefox can be slow sometimes. There's also a thread on the forum for optimizing the speed of Firefox and it makes some great improvements if you follow it. Just search Firefox Optimization in the forum search function.
 
Just some random thoughts after reading the thread. There could be more culprits for nautilus and other apps being slow, just had these come to me while reading.

---

### Post by colobix on 2011-01-24
Thanks. I Have already tried the first two suggestions, I Have no idea what ipv6 is but I'll check it out. But to be honest, I find Google Chrome to be better on so many levels that I don't think I will put much time into it as I only gonna use Chrome from now on.

---

### Post by tigerstripedcat on 2011-01-24
As for  your music folder and /usr/bin, try not using nautilus.  Open a terminal and navigate to those directories and try a ls -lat.  Is it still slow?  The only time I can remember the display of directory contents being slow is if you have a mountpoint that is taking a while to respond. Do you use samba/ntfs or any remote mountpoints?  Copy and paste your /etc/fstab here.

---

### Post by colobix on 2011-01-24
Yes, My music folder is on a NTFS partition. but that doesn't explain why /usr/bin or /usr/lib is slow, does it?
Here's the output btw.
```
proc /proc proc nodev,noexec,nosuid 0 0
UUID=b7cc69aa-47e9-4316-af09-3232d3d02e07 / ext4 errors=remount-ro 0 1
UUID=D43004B430049F9A /media/Reservert_av_systemet ntfs-3g defaults,locale=nb_NO.utf8 0 0
UUID=FE5C091E5C08D377 /media/sda2 ntfs-3g defaults,locale=nb_NO.utf8 0 0
UUID=36680C9B680C5C4D /media/sda3 ntfs-3g defaults,locale=nb_NO.utf8 0 0
UUID=80105796-f843-4a24-9e10-d5295e594b8c none swap sw 0 0
```

Also, gedit takes forever to load up and so does notepad (in ubuntu, not windows).
I really need to speed up these things.

---

### Post by tigerstripedcat on 2011-01-24
And if you open gedit from another directory

cd <enter>
gedit new

is it slow?

---

### Post by colobix on 2011-01-24
yes it is. even when I open a blank document.
Google CHrome is way better than firefox but still freezing from time to time.
I wish there was an alternative to Nautilus out there. A better one.
I'm sorry I am mentioning all these freezing problems but I really want as many of them as possible to work as smoothly as possible. 
EDIT And the reason why I think this is a CPU problem is because the pc makes more sound when things are about to open, during the freezing and things like that. Sometimes even when I click a link and the spinning ball comes up.

---

### Post by tigerstripedcat on 2011-01-24
Try this:

cd /
sudo gedit 


How long does that take?

Then run 'top'
and copy and paste the contents here.

---

### Post by dhysk on 2011-01-24
Hmm, sounds like either a kernal problem or possibly a drive access problem.

when you do the 'top' comand is you're cpu being taxed?  when you do a 'free -m' command what does you're avialable memory look like, when the computer is running slow.

How did you do the install, on a seperate partition or inside a windows folder?

What distro are you using?  I'm not sure how well a normal ubuntu distro would work on an atom processor? Is this the 'nettop' computer like this one?  [http://www.amazon.com/Acer-AspireRevo-AR1600-U910H-Desktop-Windows/dp/B002O3W44Q](http://www.amazon.com/Acer-AspireRevo-AR1600-U910H-Desktop-Windows/dp/B002O3W44Q)

Maybe the netbook remix would be better for this type of hardware?  Just my 2c, I'm just not familiar with normal x86 vs atom x86 archetecture and how if at all the standard kernal would deal with this.  But if your PC is like the one I showed you it's basically a desktop netbook of sorts so if you're not using the Ubuntu netbook remix maybe it would be worth the try?

Another thought is I think the Atom 230 is also 64bit: [http://ark.intel.com/Product.aspx?id=35635](http://ark.intel.com/Product.aspx?id=35635)  

I may be wrong but maybe runing a 64 bit OS would help as well.  This would also alow all you're ram to be seen.

---

### Post by tigerstripedcat on 2011-01-24
dhysk is right about the 64bit thing (I forgot you said you were only seeing 3gig, is that right?)  but if it works fine in windows it should work fine in ubuntu.  

Also what does the 'mount' command show?

---

### Post by colobix on 2011-01-24
Exactly, it should work right.
Mmemory tests are ok and CPU works fine in windows.
I have Ubuntu installed on an own partition, not wubi.
Ext4, 32bit.
Here's the weird results from free -m
             total       used       free     shared    buffers     cached
Mem:          3023       2821        202          0        398       1675
-/+ buffers/cache:        746       2276
Swap:         7084          0       7084

BUt my pc isn't slow now. now it's not usual speed.
That means somehow jurky, lagging sometimes when I scroll pages, and all the other things I've already told you.
When it's slow it takes forever to preform a the simplest task.

---

### Post by tigerstripedcat on 2011-01-24
Try this:

cd /
sudo gedit 


How long does that take?

Then run 'top'
and copy and paste the contents here.

ALSO: try a live cd and see if you have the same problem.

Jerky scrolling pages can be a video driver problem.  Do you have the latest drivers.  What are the specs for this computer?

---

### Post by dhysk on 2011-01-24
also try to turn off you're desktop effects if you are using them.  Right click go to Visual effects tab click none.  I've had video problems make the computer seem to run slow when it was simply the video drivers issues as well.

alternativly you could go to a terminal and type

```
metacity --replace
```

this should give you a basic gnome metecity window manager and see if that helps.

---

### Post by colobix on 2011-01-24
> **tigerstripedcat said:**
> Try this:

cd /
sudo gedit 


How long does that take?

Then run 'top'
and copy and paste the contents here.

ALSO: try a live cd and see if you have the same problem.

Jerky scrolling pages can be a video driver problem.  Do you have the latest drivers.  What are the specs for this computer?
A blank document takes way less time.
Around 1 sec I guess, so not that slow.
But a document can take between 5 - 10 sec depending on how big it is.
Opening firefox takes a lifetime and gets right to the top of "top".
The thing is though. THings are going way faster now without firefox running, so yea thanks Google. I love you :D
OK here's my "top" list:
```
chris@chris-desktop:~$ top

top - 20:52:35 up 10:34,  4 users,  load average: 0.78, 0.70, 0.73
Tasks: 207 total,   1 running, 205 sleeping,   0 stopped,   1 zombie
Cpu(s): 14.5%us,  2.8%sy,  0.2%ni, 82.4%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   3096368k total,  2910472k used,   185896k free,   405672k buffers
Swap:  7254924k total,        0k used,  7254924k free,  1732864k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1468 chris     20   0  200m  81m  30m S   14  2.7  16:35.86 nautilus           
 3851 chris     20   0  278m 101m  39m S    7  3.4  14:30.10 ktorrent           
 1066 root      20   0 59224  46m  14m S    4  1.5  44:02.72 Xorg               
 1453 chris     20   0 60660  46m  16m S    3  1.6  32:55.54 compiz             
 1159 nobody    20   0  158m  54m 2168 S    2  1.8  21:52.47 tremded            
 6626 chris     20   0  112m  19m  14m S    2  0.7   0:20.14 chromium-browse    
 6851 chris     20   0  2548 1260  924 R    1  0.0   0:00.21 top                
 1172 nobody    20   0 61868 2856 2208 S    0  0.1   2:12.29 wesnothd           
 1235 nobody    20   0  2332 1156  936 S    0  0.0   1:27.86 LCDd               
 1433 chris     20   0  7976 4560 2400 S    0  0.1   0:06.47 gconfd-2           
 1678 chris     20   0 19184 4972 4036 S    0  0.2   0:03.60 indicator-me-se    
 1898 chris     20   0  285m  60m  30m S    0  2.0   8:27.98 chromium-browse    
 3307 chris     20   0 69168  15m  11m S    0  0.5   1:59.36 gnome-terminal     
 6622 chris     25   5  148m  44m  17m S    0  1.5   0:21.73 chromium-browse    
    1 root      20   0  2784 1712 1224 S    0  0.1   0:01.00 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0        

```
EDIT: Now when I clicked the edit button it took literally more than 20 sec for the page to load.
These things happen sometimes and it's quite annoying.

---

### Post by tigerstripedcat on 2011-01-24
try opening a doc but run it with sudo:

sudo gedit <some document>

as for top: run it, and then press 'q' to quit out of it, you should still see the last update but it won't update and you can copy/paste

---

### Post by dhysk on 2011-01-24
although not taking up a bit of processing try what I said.  It looks like you are running compiz

```
1453 chris     20   0 60660  46m  16m S    3  1.6  32:55.54 compiz
```

disble that by what I said earlier, setting visual effects to none, and let us know if it's still slow.  If it speeds up it may be a video issue.

---

### Post by colobix on 2011-01-24
Yes it is slow when I use sudo.
And I edited and posted the top list into the post probably after you wrote that message.

I do run compiz, but I have to because of the zoom function.
But you're probably right, it might have something to do with it.
But here's an odd thing though.
As you can see from the top list, ktorrent which is a KDE software takes less CPU than Nautilus. That isn't normal, is it?
Compiz however doesn't look like a big cpu killer.

---

### Post by dhysk on 2011-01-24
It doest look like an over taxed cpu problem to me.  If disabling compiz fixes it than we could narrow it down to a video issue.  If it doesn't at least make a meaningfull difference than its probably not.

---

### Post by tigerstripedcat on 2011-01-24
Compiz may not take a lot of cpu, but your cpu might not be the thing slowing down the system.  Disable it temporarly until we can narrow down what is causing the problem.

Also, are you running gedit through nautlus?  Does nautlus even use cpu when idle?  Close that out too and try to do all your file browsing and management through the terminal. Also close out of ktorrent.  

Now with those things closed if you go into a terminal and do a

ls -lat /
ls -lat /home/<user>
find . /home

Do these command hesitate at all?

Install emacs and try opening a doc FROM THE TERMINAL with

emacs -nw <filename>

Does that take a long time?

---

### Post by Jouke74 on 2011-01-24
Please run a full disk check utility on your harddrive to see if there are any bad blocks on the Ubuntu parts. This excludes the hardware.

Check if your linux system has not been rooted / hacked.

Clean out the Firefox / Browser history and cache.

How much space is still free on the drive? Enough for all operations?

---

### Post by colobix on 2011-01-24
Yes I already use the terminal for these things.
I installed emacs.
How do I turn off compiz?
Also, I did a few tests. I ran a file compression process in the background while typing in the browser. Things got very jerky.
Which means, I don't have to do much to make the system act like a jerk. THis happened with compiz enabled ofcource.
And Gedit is slower than emacs.
EDIT: Oh and btw, it takes 10 minutes to compress 15mb.
Is it suppose to go that slow? i don't think it is.
But ok, one problem at the time.

---

### Post by tigerstripedcat on 2011-01-24
You need to keep removing things from the equation until something changes.  You seem to keep adding things back.  You seemed to say that it wasn't a browser because chrome fixed it, but then not really because it still has a problem when all browsers are closed, and now you say it significantly slows when you are using your browser. STOP ADDING THINGS BACK TO THE EQUATION!  

* NO BROWSER
* Close nautilus
* Close ktorrent
* Stop compiz - im not quite sure how, I think you go into the gnome control panel and disable any graphical features, must google 'disable compiz' and I bet you'll find your answer.  There was a suggestion above with metacity, try that.

Then try opening "emacs -nw".  Is it nice and fast? can you run 'find ." and no slowdown. This will tell us that it doesn't seem to be a filesystem problem and is probably a gnome/video related problem.

I still think you should boot up with a liveCD and convince yourself that it is not a hardware problem.  Boot with a liveCD and time various things.  How long does gedit take with the liveCD?   This will give us a decent comparison.

---

### Post by colobix on 2011-01-24
ehh ok?
I don't have anything on when I test these things.
OK as I said, changing the browser works alot better, so as I said I use the google browser now. and I don't use nautilus, ktorrent etc when I test these things.
I am not going back and forth on what I'm saying here.
Plz read the posts before you judge.
The only thing is compiz. I don't know how to close it.
So compiz has been running during the tests.

---

### Post by tigerstripedcat on 2011-01-24
"...while typing in the browser. Things got very jerky..."

Sounds like you are using your browser to me.  Do you have a liveCD to try?  Did you find how to turn off compiz?

---

### Post by colobix on 2011-01-24
I was typing in the browser cuz I replied to a message here.
That's why it says EDIT, cuz it was jerky when I typed.
Things got faster when I canceled the compression process though.
LiveCD, yes I do have a livecd. booting took forever but that's normal. typing and everything else that jerks down the pc now was must faster. But I mean, that was without compiz.
I restarted the system and turned off visual effects (compiz)
Things are working much smoother now. That wasn't actually unexpected.
Without COmpiz, things are almost as fast as windows.
However, nautilus is still very slow, opening gedit and emacs without documents went a little bit faster but still hanging 7 seconds when I open a document with them. Emacs took 5 sec and gedit took 7 seconds.
Nautilus speed is still slow on the folders /usr/bin. That's the one I tested since it still took forever.
Zip compressing is still jerking down the pc, and Nautilus is still at the top.
Now I Have to reboot again cuz after running the zip compression process the PC is a laggy nightmare.
Damn why does it have to be this way?
I almost forgot. Yesterday when I edited a video I had to switch over to Windows, cuz OpenShot's video playback was too lagy and horrible. So maybe this is a hardware thing after all. Or maybe not since I have now done all the tests without using Compiz.
I really don't know anymore.

---

### Post by tigerstripedcat on 2011-01-24
Well if everything is ok when booting with the liveCD it is probably not a hardware problem.

1) When you say you run emacs, do you run emacs <file> OR emacs -nw <file>, you should try -nw because this does not rely on any video
2) It seems more and more like it's a video related problem, though this zip compression slowness casts doubt.  Is this a command line compression program, or a gui compression?  

3) What if you try the compression after booting from a liveCD, does it still have the same problem?  Can you try a file compression with the liveCD and without and time both (type the command 'time' before the command to time how long it takes:

time <compression program> <files>

(just type 'time ls' to see what it does.  Hopefully you can mount your drive with the liveCD so you can try and zip the same set of files when you time them both)

4) What is the output of 'lspci'
5) What is the output of 'more /var/log/Xorg.0.log | grep EE' 
6) What is the output of 'more /var/log/Xorg.0.log | grep WW'

---

### Post by colobix on 2011-01-24
OUtputs for lspci:

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)



more /var/log/Xorg.0.log | grep EE

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER


more /var/log/Xorg.0.log | grep WW:

(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0

Emacs without -nw takes a time to shut down but opens when I want it too.
Gedit takes a bit longer time to open but closes when I click the X

Also. compressing doesn't take forever in windows.
The weird thing is, if I try to compress a 7gb file into 3gb files (just had to try something else), the file stoppes at around 15mb even tho the compression process goes to 100%.
I have only seen this problem recently since I have never done that before. But this is just another one of those odd things.
Well, I tried this for a long time ago because I needed a movie on a usb stick formated with FAT32, but it worked back then. That was also ubuntu 10.04 btw.

---

### Post by tigerstripedcat on 2011-01-24
1) What about 'emacs -nw' does that work ok opening and closing?
2) Aside from the compression issue and the gedit thing, (and browser/nautlus slowness) is there anything else that seems slow?
3) Have you updated your video drivers?  Looks like you're running NVIDIA.  Do you know what version video driver you're running? 
4) What might be very helpful is to find that model number of the acer you are running it on.  Usually it's on there, or you open some panel on the tower, there should be a sticker somewehre on there that says what it is.  OR you might be able to install a program called hardinfo and it MIGHT say what model it is.

---

### Post by colobix on 2011-01-24
emacs -nw is in the terminal. it works fine.
Here's my PC:
[http://bestbuyshop.lismblog.com/2010/05/15/computer-desktop-update-1/](http://bestbuyshop.lismblog.com/2010/05/15/computer-desktop-update-1/)

Acer AspireRevo AR1600-U910H Desktop PC

---

### Post by tigerstripedcat on 2011-01-24
1) Have you looked for any bios updates for this computer?
2) Did you install NVIDIA's newest drivers?
3) Are you running the 32bit or 64bit version of ubuntu?

---

### Post by colobix on 2011-01-24
I use the bios that came with the PC. the one with the blue background and yellow text. I have no idea how or why I should change that thing.
2. Yes, the recommended one from the nvidia-common package the website suggested.
3. 32. I think I have mentioned that before a few times but ok :)

---

### Post by tigerstripedcat on 2011-01-24
1) It says that this computer only comes with 1 gb of ram, did you upgrade it?  If so, how many sticks of what size/type ram did you install?
2) If you have 4 in there, it only shows 3.  This could be due to a misseated ram module or *maybe* the fact that you are running 32bit (but even 32bit should support 4gig). So if you do reinstall I suggest you go for 64bit ubuntu. 
3) Which website pointed you to nvidia-common? Try installing the newer NVIDIA drivers:

[http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html)

* download the above
* chmod +x NVIDIAfile.sh
* ./NVIDIAfile.sh
* restart the computer

You might have to be outside of xwindows to do this. Go to the login prompt and select "console login" to kill the xserver and then run the above.

if you are using nvidia-common these are definitely not the best ones and the ones from nvidia may help.

---

### Post by colobix on 2011-01-25
OK first of all. I don't wanna use a 64 bit ubuntu. also I can't because it's a 32 bit processor.
The last time I installed an Ndriva driver manually, it crashed.
That's why I just removed all of them from synaptic and installed the nvidia-common package which gives me the newest one.
Also, the pc I bought came with 4gb so maybe its not that model but the same pc atleast. I had the model number on the bc but not anymore.
But ok, it came with 4gb.
So I don't know if it came with 4 sticks or 2 2gb sticks.
EDIT: Hardware Drivers says that I have the current driver installed, and this is the recommanded one.

---

### Post by tigerstripedcat on 2011-01-25
This computer should be 64bit:

[http://ark.intel.com/Product.aspx?id=35635](http://ark.intel.com/Product.aspx?id=35635)

[http://www.amazon.com/Acer-AspireRevo-AR1600-bits-processor/forum/Fx55YOJU9EY5R0/Tx1YUTH6Y1XMOUQ/1/ref=cm_cd_dp_ef_tft_tp?_encoding=UTF8&s=pc&asin=B002O3W44Q&store=pc](http://www.amazon.com/Acer-AspireRevo-AR1600-bits-processor/forum/Fx55YOJU9EY5R0/Tx1YUTH6Y1XMOUQ/1/ref=cm_cd_dp_ef_tft_tp?_encoding=UTF8&s=pc&asin=B002O3W44Q&store=pc)

You can check yourself by doing:

more /proc/cpuinfo | grep 64


Are you sure it has 4gigs?  Does windows say 4gigs of ram?  64-bit computing is a cleaner model that the industry will one day completely adopt and there is little penalty in installing 64bit [http://techreport.com/articles.x/8131/1](http://techreport.com/articles.x/8131/1)

As for the nvidia driver:  nvidia-current may be the current, but may  not.  When you say it crashed, what did it do?  If you run nvidia-xconfig does it say the version?  does it say if you have glx enabled?  What's the result of 'glxinfo | grep rendering'?  Also run

sudo apt-get install mesa-utils

and then

glxgears

what kind of framerate are you getting?

---

### Post by colobix on 2011-01-25
Yup I am sure.
It came with Windows Vista 32 bit.
So if my pc is 64 bit, they must have installed the wrong version. sounds odd though. Also, yes it has 4gb of ram.

Here's the output from more /proc/cpuinfo | grep 64
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
clflush size	: [COLOR="Red"]64[/COLOR]
cache_alignment	: [COLOR="Red"]64[/COLOR]
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
clflush size	: [COLOR="Red"]64[/COLOR]
cache_alignment	: [COLOR="Red"]64[/COLOR]

EIDT: I also checked more /proc/cpuinfo | grep 32
bogomips	: [COLOR="Red"]32[/COLOR]00.02
address sizes	: [COLOR="Red"]32[/COLOR] bits physical, 48 bits virtual
bogomips	: [COLOR="Red"]32[/COLOR]00.03
address sizes	: [COLOR="Red"]32[/COLOR] bits physical, 48 bits virtual

---

### Post by tigerstripedcat on 2011-01-25
This is definitely a 64 bit processor.  You might want to switch over to a 64bit OS.  Not sure what to do about windows, but a 64bit windows would be good to get too.  

Have you noticed any changes in the speed lately?  We still haven't really determined what the cause is because there seems to be conflicting symptoms.  I think it may be video related, in particular a driver problem. But if don't want to try and load different drivers I'm not sure what else there is to do on that end.  What you can do is boot with a liveCD and time

1) a compression process
2) opening a file in gedit
3) opening a file in xemacs -nw
4) launching a browser
5) loading a flash video

and do the same when you boot with a liveCD and compare the two times in each category.  This may help narrow down if it really is video.

---

### Post by colobix on 2011-01-26
But why is the speed slower on a 64 bit than 32?
Also, is it possible to upgrade from ubuntu 10.04 32 bit to 64 without reinstalling?

---

### Post by tigerstripedcat on 2011-01-26
> **colobix said:**
> But why is the speed slower on a 64 bit than 32?

It's not.  Check the conclusion of the reference:  it's just about the same for things that are not optimized for 64 bit and it's 20-30% faster for things that are.  As time goes on more and more things will be optimized for 64bit code; not everything, but you were talking about compression--that certainly will be depending on the program you use.


> 
Also, is it possible to upgrade from ubuntu 10.04 32 bit to 64 without reinstalling?

Unfortunately, not.  Why are you worried about a reinstall.  I know it is a bit of a hassle, but what you can do is backup your /home and /etc/ (complete with hidden files)  directories and that will save all your settings.  After you reinstall you can copy those back (while keeping a backup of the new stuff of course).

Now the problem with this is that a reinstall is a great opportunity to find out what is slowing down your system, but if you copy large portions of the old OS back you will have a hard time narrowing down the problem.

If you reinstall and then use the computer slowly:

1) reinstall
2) compress a file, open gedit, use the browser
3) If it works ok proceed to step #4
4) install a new piece of software or make a configuration change
5) repeat steps 2 to 4 until you notice a significant slowdown

If  you do things slowly enough this should definitely show you were your problem(s) lie.

---

### Post by colobix on 2011-01-26
Well. When you say reinstall I guess you mean install 64 bit instead of 32 bit.
Also, is it possible to take a backup only of things that I have installed? I mean, the boring thing about a reinstallation isn't the home folder but all the programs I have to reinstall, and some of them aren't in synaptic so now I have to look around and see where all the files for these programs are and copy them.
A Process like this is easier in windows since everything goes under the program files folder. So is it possible to do a backup of all the packages and files that I have installed? Or even easier, is it possible to uninstall ubuntu's file system and install the 64 bit?

Also, what's the differance b difference between 64bit and 32bit?
Is 64bit better or something?
Is that why the programs are slow? because my processor is faster than my OS and the programs?

And, is it possible for me now to make an own partition for the home folder so I don't have to back it up?
If so, how, and how can the installation program recognize the home partition when I install ubuntu again?
And how can you tell if I have a 64 bit system or not?
The thing I posted above does not say anything about 64 bit, but 32bit however comes up.
And if I now do this, will I be able to use programs that are only for 32 bit systems?

I am used to 32 bit, and now when this 64 bit thing came up, well this is just a bit scary you know.

---

### Post by colobix on 2011-01-26
Well. When you say reinstall I guess you mean install 64 bit instead of 32 bit.
Also, is it possible to take a backup only of things that I have installed? I mean, the boring thing about a reinstallation isn't the home folder but all the programs I have to reinstall, and some of them aren't in synaptic so now I have to look around and see where all the files for these programs are and copy them.
A Process like this is easier in windows since everything goes under the program files folder. So is it possible to do a backup of all the packages and files that I have installed? Or even easier, is it possible to uninstall ubuntu's file system and install the 64 bit?

Also, what's the differance b difference between 64bit and 32bit?
Is 64bit better or something?
Is that why the programs are slow? because my processor is faster than my OS and the programs?

And, is it possible for me now to make an own partition for the home folder so I don't have to back it up?
If so, how, and how can the installation program recognize the home partition when I install ubuntu again?
And how can you tell if I have a 64 bit system or not?
The thing I posted above does not say anything about 64 bit, but 32bit however comes up.
And if I now do this, will I be able to use programs that are only for 32 bit systems?

I am used to 32 bit, and now when this 64 bit thing came up, well this is just a bit scary you know.

EDIT: And I have Intel Atom (230 series), and this website says it doesn't support 64bit.
[http://www.sevenforums.com/general-discussion/1591-64bit-intel-atom.html](http://www.sevenforums.com/general-discussion/1591-64bit-intel-atom.html)
And if I really have 64bit, does that mean I have to go for the downloads that says AMD64 from now on?

---

### Post by renkinjutsu on 2011-01-26
Too lazy to read through the whole thread, but I still want to help.

Here are some things to watch out for if your computer's running slowly


**Harddrive running out of space:**
You say that applications take forever to open. This can be a sign of fragmentation of the harddrive which will happen if the disk is almost full.

To check this out, perform this in the terminal:
```
df -h
```
=================

**Not enough RAM / Application hogging RAM:**
The Linux kernel often caches random stuff in RAM. If you don't have enough RAM or if there's a bad program eating up all your precious RAM, the kernel will start swapping, and so applications may take forever to resume, as it needs to read from swap space.

To check RAM usage:
```
free -m
```
=================

**CPU hog:**
This is generally not the case for me since the kernel's scheduler has been getting lots of improvements lately. But there is still a way to check which process or processes are hogging all the CPU time.

to check:
```
# You can use top
top

# or you can use ps
ps -eo pcpu,pid,user,comm --sort=pcpu

```

The ps command above should list processes and the columns are as follow

cpu usage, pid, user, command
The process with the highest CPU usage will be listed at the bottom

---

### Post by tigerstripedcat on 2011-01-26
> **colobix said:**
> Well. When you say reinstall I guess you mean install 64 bit instead of 32 bit.


Yes. I mean reinstall with 64 bit.

> 
Also, is it possible to take a backup only of things that I have installed? I mean, the boring thing about a reinstallation isn't the home folder but all the programs I have to reinstall, and some of them aren't in synaptic so now I have to look around and see where all the files for these programs are and copy them.
A Process like this is easier in windows since everything goes under the program files folder. So is it possible to do a backup of all the packages and files that I have installed? Or even easier, is it possible to uninstall ubuntu's file system and install the 64 bit?


Yes, finding the programs is annoying.  I guess the best way is here:

[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

That will take care of anything you installed through the command line, synaptic, etc as long as it was a deb/apt-get/synaptic command/file.  If it was a gzip/tar file then it won't reinstall those.  You can find some of them by doing a 

history | grep 'tar'

and maybe it will show you what you've installed from source (though history is only about 1000 lines I think).


> 
Also, what's the differance b difference between 64bit and 32bit?
Is 64bit better or something?
Is that why the programs are slow? because my processor is faster than my OS and the programs?

No, that's not why your programs are slow.  We still haven't found out why they are slow.  It MAY be why you are only showing 3gigs of ram out of 4 (though this is also unlikely since 32bit ubuntu should support 4gigs of ram).

You don't have to install 64bit, it's not necessary, and your system should do fine if you don't.  There are both pros and cons.  I think the pros outweigh the cons.  You will see a speed increase in 64bit optimized code.  Now that may be important depending on what you use your computer for.  Personally I wouldn't run any of my computers with a 32bit os because the entire industry will inch towards 64bit and it will eventually be fairly prominent. It's your decision, but if I were you I would bite the bullet and do it now rather than down the road or else you might not know what you are missing.

> 
And, is it possible for me now to make an own partition for the home folder so I don't have to back it up?
If so, how, and how can the installation program recognize the home partition when I install ubuntu again?

It is, but it may be more trouble than it's worth.  If you can, just backup the /home to an online storage site, a usb drive, a cd, or something like that and then wipe the drive clean. You can create a new partition for /home if you like (that's what most people do).  There are many threads and sites on google telling you how to partition.  I personally create a partition for boot /home, /, and a /storage parition (usually another drive though).

When you reinstall it will ask you to create partitions (I can't remember exactly how it calls it, something like "disk setup").  If you do want to create/resize a partition (rather than copy /home elsewhere and start from scratch) it may recognize the /home partition automatically, or you may have to tell it that "/home" mounts there.  Either way, it will definitely show you the partition that you used for "/home" when you try and reinstall (it might just not automatically name it "/home"--you'll have to tell it it's called "/home")


> 
And how can you tell if I have a 64 bit system or not?
The thing I posted above does not say anything about 64 bit, but 32bit however comes up.

Based on your output I was looking for the "lm" string which many sites on the internet say means you have a 64bit processor.  All evidence seems to point that way.  I'm 90% sure you have a 64bit processor.  Here are the lines of evidence:

1) your /proc/cpuinfo shows the "lm" flag, see the second point here:

[http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/](http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/)

2) The intel site says it definitely **IS** 64 bit:

[http://ark.intel.com/Product.aspx?id=35635](http://ark.intel.com/Product.aspx?id=35635)

(says it two places)

3) The product specs on amazon for this comptuer say it is 64bit.




> 
And if I now do this, will I be able to use programs that are only for 32 bit systems?
I am used to 32 bit, and now when this 64 bit thing came up, well this is just a bit scary you know.

No you can use 32bit optimized programs because you will have 32bit libraries installed alongside the 64bit ones, so you can use both so the way it works is:

* 64bit processors can run 64bit code and 32bit code ***IF** a 64bit OS is installed - and will probably run the 64bit instruction set FASTER
* 32bit processors CAN NOT run 64bit code

There was (and still may be) some snags with 64bit OSes for certain drivers/programs that had very infrequent but annoying problems that wouldn't be resolved.  64bit flash was a pain for a LOOOONNG TIME and some people didn't use 64bit ubuntu for that very reason.  But now most of those problems have passed as everyone is developing 64bit code now and there is 64bit flash (ACTUALLY! 64bit flash may help stability and speed issues, which is another reason to try this)

Here's my MAJOR RECOMMENDATION:  Download the 64bit ubuntu live cd to check compatability problems.  Use the computer as normal with the 64bit OS and see how it works (noting that having to go back and forth from the CD will slow it down kinda)  If everything seems to work fine for you, you should consider going over to 64bit ubuntu (and maybe even finding a 64bit windows disk)

> 
EDIT: And I have Intel Atom (230 series), and this website says it doesn't support 64bit.
[http://www.sevenforums.com/general-discussion/1591-64bit-intel-atom.html](http://www.sevenforums.com/general-discussion/1591-64bit-intel-atom.html)

1) that thread is from 2009 before everything was supported (I think) and 2) that was for a laptop not the 200 series desktop.  Here's a thread talking about your exact Atom  model (not the laptop atom 200)

[http://forums.mydigitallife.info/threads/9859-Is-atom-230-a-64bit-cpu-for-2008-r2](http://forums.mydigitallife.info/threads/9859-Is-atom-230-a-64bit-cpu-for-2008-r2)



> 
And if I really have 64bit, does that mean I have to go for the downloads that says AMD64 from now on?
Yes you do.  Now you will have 32bit libraries installed along side your lib64 so you could probably use either one, but you should use AMD64 whenever possible.

---

### Post by colobix on 2011-01-26
nothing uses a lot of cpu.
free -m gave me this:
            total       used       free     shared    buffers     cached
Mem:          3023       2943         80          0        146       2263
-/+ buffers/cache:        534       2489
Swap:         7084          0       7084

but I have no idea what those numbers mean.
Someone said I have 32bit ubuntu instead of 64 and that is why things are slow. I Have no idea.
Anyway. I have about 24gb free space. should be enough, huh?

I havn't really installed much, but I guess that everything you delete from the recycle (trash) folder just goes away but when you remove it, ubuntu doesnt free the used space. At least it seems like that.

It has always been like this. I install ubuntu and one month or so later it gets more and more jerky and slow.

Right now at the "top" is chrome, but the onlsy tap I have open is ubuntuforums and hulu.com (the newest Cops episode).
I used firefox, but for a few days ago someone told me about chrome, and it's really great. its way faster, and it doesn't slow down crash the pc whenever I watch a video on either youtube or hulu. So that helped a lot.
I have also used ubuntutweak and bleachbit to get rid of useless files, but it didn't help that much.
The weird thing is, I also dual boot Windows7, but even tho win7 is also 32bit, it goes as fast and smooth as it should go.
Which makes me wonder about this whole 32/64 thing if it really matters that much.
@tigerstripedcat, what you said about the 4gb ram thing is true.
And that is why I think it's worth it. But I don't think I should back up my debs after all.
Since they are made for 32bit, and maybe some of the things Ive installed, gave me a jerky pc.
As I said above, win7 doesnt act this way.

Btw, thanks a lot for trying to help me out here guys:)
I can't stress that enough.

EDIT: tigerstripedcat, I tried the method you linked me to about the deb list thing but it didn't work.
It made a blank text file.

---

### Post by renkinjutsu on 2011-01-27
32/64bit shouldn't really matter if you're not doing heavy things like video conversions. At least I didn't notice the difference between 32 and 64 bit on my Core 2 duo.. But maybe that's because I don't have those crazy fast CPU's..

Anyway, how much space have you used? We need to compare the free space to the used space.

---

### Post by dhysk on 2011-01-27
Sorry been out for a bit, but if you would like I'll add my $.02 again.

1st 64 bit thing:  the forum you posted was for the **N**200 series wich were the older ones.  You have a 64 bit processor.  However the bigest advantage to you would be the extra ram it would see and probably compression.

Wiki with Atom proc list: [http://en.wikipedia.org/wiki/List_of_Intel_Atom_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Atom_microprocessors)  

**However I wouldn't mess with 64bit untill you get this solved.  I highly doubt it will solve you're problem and at this point would just add extra confusion to the mix. My $.02**


As for you're problem.  I'd follow down the HD space concerns.  How big is you're linux partition, how much have you used, how much of it is still free?

I'm still interested in following down the graphics path as well.  What issues did you have with the Nvidia driver you installed before?  The jittery part acts like a video problem expecially if that part of the issue stoped when you disabled compiz. An easy way to disable compiz is to go to the command line and do a:
```
metacity --replace
```
this will replace compize with the metacity windows manager but disabilng visual effecs should have the same effect.

I think we should do one thing at a time for now.  So if the jitteryness stoped after disabling compize try to install new Nvidia driver...

1.  Download driver here to desktop: [http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html)

than press Ctrl+Alt+F1:  this should bring up a black terminal screen.

2.  type in user name and password.

3. back up xorg config
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

4.  stop display manager
```
sudo /etc/init.d/gdm stop
```

5.  cd to desktop
```
cd /home/username/Desktop
```

6. run the installer with root privlages
```
sudo ./Nvidia_driver_name_here
```

follow the instructions and yes you want it to update you're config file.  It also may make a backup but I can't remember but we already did it in step 3.

7. after the install is complete restart the display manager
```
sudo /etc/ini.d/gdm start
```

this should bring you back to the login screen.  Another tip would be to copy past this how to into a text file and save it to you're desk top.  That way you can open it when in the terminal by 
```
nano /home/usernam/Desktop
```

If you decide to give this a try run it without desktop effects for awhile if the jitteryness is still gone, alhtough other things may be slow we will get there, enable desktop effects and see if the jitteryness comes back.

---

### Post by colobix on 2011-01-27
79.2 GB of free space.
I don't know how big the file system partition is though.
When I go to "computer" and right click on file system, it doesnt give me the info. That annoys me a lot.
I mean, when I do that in windows, it gives me all the info about everything. It really should be like that in ubuntu too I think.
But ok, how do I find this info?
Not even systemmonitor has the info for this.

---

### Post by dhysk on 2011-01-27
in a terminal

```
df -h
```

that should give you all the info for all mouted drives.  Alternatively: Applications--->Accessories--->Disk Usage Analyser

thats for an older version of ubuntu so it may or may not be there. but the comand line will give you an output easy to copy past into the forum.

---

### Post by colobix on 2011-01-27
Ah, many thanks man.

Filesystem            size  Used Available Used Mounted on
/dev/sda5             126G   41G   79G  34% /
none                  1,5G  284K  1,5G   1% /dev
none                  1,5G  1,5M  1,5G   1% /dev/shm
none                  1,5G  216K  1,5G   1% /var/run
none                  1,5G     0  1,5G   0% /var/lock
none                  1,5G     0  1,5G   0% /lib/init/rw
/dev/sda1             100M   25M   76M  25% /media/Reserved_by_system
/dev/sda2              15G   11G  4,0G  73% /media/sda2
/dev/sda3             319G  300G   19G  95% /media/sda3
/dev/sdb1              32G  474M   32G   2% /media/E4A2-F74A

---

### Post by colobix on 2011-01-29
So, does any1 know?

---

