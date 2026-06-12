---
title: "ubuntu very slow"
date: 2009-09-12
forum: General Help
---

### Post by C14 on 2009-09-12
Hello,  I'm a Linux-noob who just migrated from Windows XP and I am very disappointed:  Ubuntu 9.04 is dead slow  (reaction speed of applications, moving windows on the screen...) on my System: - Pentium 4 2.4GHz - 512MB RAM - GeForce 4200  I installed the nvidia graphics driver (version 96) and tried out other desktop environments like xubuntu-desktop, but it didn't help much?  Any idea what it could be? (I know this system is a bit dated, but Windows XP ran fine on it)

---

### Post by P4man on 2009-09-12
Can you try and quantify the problem a bit more? Is it slow in booting and running apps, or "only" displaying things (scrolling, dragging,  and the like).

Do you have desktop effects enabled ? If so, try turning them off: system > preferences > appearance > visual effects. Set it to "none".

Anyway, I suspect a problem with the videodrivers. nVidia only properly supports down to the geforce 6 series for the current releases of ubuntu (actually: x.org). The nVidia legacy drivers you're using, I don't know how well they work with jaunty, judging by your post, not too well :s;

---

### Post by NoaHall on 2009-09-12
Are you running compiz? If turning off the effects doesn't help, turn them on, and try using compiz instead - it should take some pressure off.

---

### Post by pawlu89 on 2009-09-12
Even in mine was running slow, especially when copying files from one place to another. Also with my wireless, the computer either connected to the network or stopped working at all, even if it is doing any major processes like updating or using a software that uses a lot of resources.

All my hardware was 100% compatible.

I think that in ubuntu 9.04 there are several issues and bugs that have not been tackled.

I prefer to have a longer boot (although i do not see any difference) and the system is stable instead of a shorter boot with a buggy system.

Now I am running hardy heron which is a long term release. Oki, I had to make some configurations since I have a dsl connection, but on the whole it is way faster and stable.

In my opinion hardy must be installed for users who want a hard and stable os.

Thank you UBUNTU DEVELOPERS

---

### Post by ckonestroh on 2009-09-12
Ram 512mb????


Your XP would have been slow to??????

:)


Is someone pulling or chain and giving us fake questions??????



Pentium 4 with 512mb of ram and a Geforce 4200  !@#$%%!^^!&& What????

Buy more ram this system will fly get 2 gigs on the system?????

---

### Post by P4man on 2009-09-12
> **ckonestroh said:**
> Ram 512mb????


Your XP would have been slow to??????

:)


Is someone pulling or chain and giving us fake questions??????



Pentium 4 with 512mb of ram and a Geforce 4200  !@#$%%!^^!&& What????

Buy more ram this system will fly get 2 gigs on the system?????

I dont think such responses are needed. His system specs are what they are, and he's trying to make the most of it (and it should be fast enough for simple tasks). Lots of users run ubuntu or other distro's on far slower hardware. BTW,  XP would also work reasonably well with 512 Mb if you can manage to fight added bloat.

---

### Post by Hreinsi on 2009-09-12
more memory :) you can run memtest on live cd

---

### Post by Aearenda on 2009-09-12
I have an old laptop that uses the Nvidia 96 driver on Jaunty and it is just fine, so long as desktop effects are turned off, as P4man advised. And I don't think 512Mb RAM would cause what you are seeing alone.

---

### Post by NoaHall on 2009-09-12
Your memory isn't too bad, despite what the others say. It's almost certainly your graphics card. And, because it's Nvidia, it's probably easily solved too!

---

### Post by ckonestroh on 2009-09-12
> **NoaHall said:**
> Your memory isn't too bad, despite what the others say. It's almost certainly your graphics card. And, because it's Nvidia, it's probably easily solved too!

I can at least see where you are coming from.....  I don't know about it being the graphics card... ????

Last I checked it only was good up to Direct X 8 ???? With a Pentium 4????

It was only released for a short time with Windows computers do to its cost was more then the ATI card??????

Like I said again are you pulling my chain... This only came out for laptops.....

---

### Post by P4man on 2009-09-12
> **ckonestroh said:**
> 
Last I checked it only was good up to Direct X 8 ???? With a Pentium 4????


Dude.. please, lay down the tin foil hat. A GF 4200 was introduced in 2001 when Pentium 4s where everywhere. Its a perfectly normal combination, and even if it weren't, I got a not so old Athlon 64 with an 8 year old ATI card and far weirder combinations by mixing and matching recycled stuff.

The OP has a valid question and probably we have an easy solution. All the rest is waste of time.

---

### Post by NoaHall on 2009-09-12
@ckonestroh 
I have no idea what you're talking about. I'm sorry. The graphics card is causing the problems because it either can't handle the work, or the drivers are incorrect, or both.

---

### Post by ckonestroh on 2009-09-12
Lets see my Windows XP computer beside me I ran it up...

It took about 6 minutes to boot... about another 3 minutes to load all startup programs... I have edited my config fill... Stopped all my Spyware from running... Did a couple of extras to make it boot faster...


This remind you is a 
Athlon 64 X2 dual core Processor 4200+  2.2 ghz 
1 gig of ram...
220 gig hard drive 
free space 200 gigs...


It still takes another 2 minutes to load a program weather it be Firefox, Office, Windows Media Center etc...


My linux box is a 


Athlon 64 dual core processor tk 55
2 gig ram...
120 gig hard drive...
free space 30 gigs...

Takes this box 8 minutes to run up Ubuntu. 7 minutes to run up Linux Mint and 7 minutes to run up Fedora,  8 minutes to run up Suse...

Windows XP still runs slower then my Linux box on just about ever thing I do from internet, copy files to burning disks..

So most of the time my Windows box is off...

I use it for Making music....

---

### Post by P4man on 2009-09-12
ckonestroh, do you have anything to contribute to this thread, or are you just trolling?

---

### Post by NoaHall on 2009-09-12
@ckonestoh

What's your point? How is this helping the OP in any way? And what on earth are you talking about? 

@OP

Ignore ckonestoh, he doesn't know what he's talking about(and neither do we). So just do what P4man and I recommend to do, and then post again on here.

---

### Post by philinux on 2009-09-12
GF's desktop runs xp fine with 512m ram.

To the OP, Applications>accessories>terminal

Run the command

```
top
```

See whats going on.

---

### Post by noelvh on 2009-09-12
> **ckonestroh said:**
> Lets see my Windows XP computer beside me I ran it up...
It took about 6 minutes to boot... about another 3 minutes to load all startup programs... I have edited my config fill... Stopped all my Spyware from running... Did a couple of extras to make it boot faster...
This remind you is a 
Athlon 64 X2 dual core Processor 4200+  2.2 ghz 
1 gig of ram...
220 gig hard drive 
free space 200 gigs...
It still takes another 2 minutes to load a program weather it be Firefox, Office, Windows Media Center etc...
My linux box is a 
Athlon 64 dual core processor tk 55
2 gig ram...
120 gig hard drive...
free space 30 gigs...

Takes this box 8 minutes to run up Ubuntu. 7 minutes to run up Linux Mint and 7 minutes to run up Fedora,  8 minutes to run up Suse...

Windows XP still runs slower then my Linux box on just about ever thing I do from internet, copy files to burning disks..

So most of the time my Windows box is off...

I use it for Making music....

You have got to be kidding us!!! How in gods name can it take 6 minutes to boot a xp 64bit computer? You have to have some thing going on there. I have a hyper thread that boots XP in a minute and a half (to no blinking hard drive light). The only machine I have that takes more that 3 minutes is a Pista Tablet and it takes up to 4 minutes. 

The PC I use the most is my laptop.
P4 single core running at 1.86ghz
2gb of system ram,
60gb hd, ATI x300 with 128mb ram

Boot time on this system is just about a minute. On boot it runs compuz, with emerald, AWN. I would not stand for such slowness on my machines.

I do think that the real problem of this OP is system memmory, and the video drivers. I have a fast box running slow cause it has an intel video card.

Noel

---

### Post by ckonestroh on 2009-09-12
Lets see I'm running p2p server which keeps running down my box.... because I didn't partition my folder seperate from my os on linux


don't bother me again period...........


good bye..........

If you are admin for this Ubuntu forums please delete my profile completely 

thank you....

---

### Post by Perfect Storm on 2009-09-12
Please keep this on topic, and stop turning OPs thread into a discussion group. There're other places on this forum for that.
OP ask for support/help with his/her problem

Thanks.


regards
A.I. Dude
Ubuntu Forum Staff

---

### Post by Aearenda on 2009-09-12
C14, please be reassured that this kind of conversation does not normally happen in Ubuntu forums. The recommendations to check desktop effects are off, and to see what is happening to your cpu usage using 'top' (or from the menu, system->admin->system monitor) are worth trying.

---

### Post by stuart.reinke on 2009-09-12
> **C14 said:**
> Hello,  I'm a Linux-noob who just migrated from Windows XP and I am very disappointed:  Ubuntu 9.04 is dead slow  (reaction speed of applications, moving windows on the screen...) on my System: - Pentium 4 2.4GHz - 512MB RAM - GeForce 4200  I installed the nvidia graphics driver (version 96) and tried out other desktop environments like xubuntu-desktop, but it didn't help much?  Any idea what it could be? (I know this system is a bit dated, but Windows XP ran fine on it)

I had a similar problem on my computer. I also have a p4 but I run at 2.2 GHz and have half ram you do, and an ATI card.

I solve my problem by first disabling the desktop effects. (as already posted)  Second I increased my swap file to 2Gb. (The installer made it 1Gb) 

After doing both of these things, Ubuntu runs smooth and quick. I can even watch streaming Flash video, which I couldn't do before because it was too chopy and would stop to buffer all the time.

Just my 2 cents. Hope it helps.

---

### Post by mike555 on 2009-09-12
When you installed are you sure you have a swap file ?    if not you should make one (about 1 GB )

---

### Post by C14 on 2009-09-12
Thx alot for your fast replies!

further specification of the problem:
As I said, it's just laggy: When dragging windows, the content lagged behind (now i turned off showing the content completely), when minimizing windows, redrawing the rest of the screen takes too long. Even the cursor in gedit lags behind some time.
I added the system-monitor to the task bar and got 100% cpu-usage when constantly changing the active window. Running &quot;free -m&quot; resulted in the following output:

 total       used       free     shared    buffers     cached Mem:           497        473         24          0         45        196 -/+ buffers/cache:        231        266 Swap:         1451         15       1435 
top shows X.org eating up most of the cpu-time:
 Tasks: 112 total,   1 running, 111 sleeping,   0 stopped,   0 zombie Cpu(s):  1.0%us,  0.7%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st Mem:    509520k total,   487556k used,    21964k free,    46532k buffers Swap:  1485972k total,    16056k used,  1469916k free,   202904k cached    PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                           2587 root      20   0 60876  29m 9772 S  0.3  6.0   5:40.72 Xorg                                                                                              4858 ruoff     20   0  205m  73m  23m S  0.3 14.7   3:31.40 firefox                                                                                           5657 ruoff     20   0 29172  12m 9028 S  0.3  2.5   0:17.59 multiload-apple                                                                                  11743 ruoff     20   0  2452 1172  908 R  0.3  0.2   0:00.01 top                

effects:
That was the first thing I tried, forgot to mention it:
I turned the effect setting to None and even tried using metacity instead of compiz. It didn't help much.

---

### Post by C14 on 2009-09-12
damn, how can i post preformatted data here instead of using the break tag  all the time?

---

### Post by bapoumba on 2009-09-12
> **ckonestroh said:**
> 
If you are admin for this Ubuntu forums please delete my profile completely
Done.

---

### Post by P4man on 2009-09-12
> **C14 said:**
> damn, how can i post preformatted data here instead of using the break tag  all the time?

You could try [ code ] tags, without those spaces.

Its indeed kind of hard to parse, but just tell us, how much cpu is xorg using while dragging windows? It should be zero give or take a few %. If its significant, something is wrong.

Im not sure what the problem is, with effects turned off (which means you are using metacity btw, and not compiz) i can't imagine 2D performance being a problem with binary drivers. At least Ive never seen it. Before you installed, during the live CD session,  was it equally slow? Or worse? Or normal?

---

### Post by C14 on 2009-09-13
ok, just checked the performance with the live CD:
same problem, X.org uses up to 74% !! cpu when moving windows around
Looks like some video driver problem, doesn't it?
 I'm using NVidia driver version 96 and Hardware Drivers sais it's working properly (green light)
Any idea how to fix it?

---

### Post by nuclear216 on 2009-09-13
try posting you xorg.conf file and the result of this

```
glxinfo | grep direct
```maybe some expert can see if there's something wrong

---

### Post by HealWHans on 2009-10-08
I have been experiencing the same system lag after a given period of time. Thanks for the advice on running top. I kept top open until it happened. I found that gnome-panel was pushing the CPU to the mid-30's.

I killed the gnome-panel process, it re-spawned and everything went back to normal. A couple more times after that gnome-panel lagged the system. Killed the process again and everything went smooth again.

What I don't know is the root cause so it never happens again. Thoughts and suggestions are welcome. :)

Thanks,
Heal

---

### Post by misfitpierce on 2009-10-08
I run Ubuntu 9.04 super fast. I can open FF and other things in the blink of an eye on single core AMD Turion 64. So it is not bugged up or slow... Something is just not set right. Also try using the scale plugin you can add to the top panel by right clicking and clicking add to panel. Then Cpu Freq Scaling and set to highest freq which turns off on demand and makes cpu a bit more snappier but uses more power! Can try that for starters!

---

### Post by HealWHans on 2009-10-09
Thanks for the tip. I the slowness came back again. This time I enabled the CPU scale panel tool. I also set my CPU to the next to highest level. I am also running on an AMD Turion 64 bit processor. We'll see what happens.

Thanks again!!

Heal

---

