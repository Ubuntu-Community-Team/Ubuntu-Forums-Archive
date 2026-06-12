---
title: "programs silently crash when mem use is high"
date: 2010-02-04
forum: General Help
---

### Post by Andy F on 2010-02-04
Hi

I'm a Linux noob. I'm using Karmic on a laptop with 1.5GB RAM and same as swap partition. Generally I'm happy with the mem usage. I have MySQL, SVN, Apache/PHP/xdebug, firefox w/ dev addons, Eclipse PDT and, of course, my music :) running at the same time, generally ok. I have the System Monitor's mem display on the top bar (dunno proper name) and can watch usage increase. Also the swap file's often only 100 - 300 megs.

However... from time to time I notice that as the programs' mem use gets close to 100% in the little sys monitor display the HD thrashes for 5 - 10 mins, after which some progs have silently crashed. AFAIR it always involves Eclipse (so maybe I should post on their boards), but not only. This last time I lost VLC and therefore my music. Obviously losing your music's far more important than losing some coding, so that's why I'm trying to resolve it now:)

I'm running Munin on my system (tho not because of this issue) and took a look at mem usage immediately before it happened. Here's the pic - you can see the sudden drop as the two progs (only AFAIK) closed on the very right side of the image.

[IMG]http://img641.imageshack.us/img641/8937/localhostlocaldomainmem.png[/IMG]

I'm not a guru here and am not sure if there's much to infer. I know some recommend 2xRAM for swap, but max committed was only 2.29 compared to potential 3, so that shouldn't be a problem? In fact the swap file never got large at all AFAICT. (Btw swappiness = default = 60.)

Any help, advice?

Much appreciated,
Andy

---

### Post by warfacegod on 2010-02-04
Try reducing your swapiness. I mine has been at zero for some time and I've had no ill effects.

---

### Post by Andy F on 2010-02-04
thanks warfacegood: 2 Qs

1: Any idea what actually caused the progs to crash? If the HD thrashed a bit *and then everything was as before* I'd understand playing with the swappiness, but why do they die?

2. I'm worried that if I lower the swappiness, I'm gonna have a large working set for apps that don't necessarily need that. Given that I'm tryin to do quite a bit with my 1.5 gigs I'm afraid that putting it to zero will lower overall performance. Could you tell me how much ram you got and what you tend to have running in one go?

Thanks again,

Andy

---

### Post by warfacegod on 2010-02-04
Sorry about the spelling in my last post.

2 GB RAM:

Average load:
ktorrent
Firefox (2 -3 tabs)
Amarok 1.4
Compiz custom effects
screenlets

High load:
1 - 2 Terminals
Configuration Editor
Pidgin
Mplayer
Open office
Rubyripper
Gsmartcontrol
Everything in Average load

---

### Post by Andy F on 2010-02-04
Thanks. Yeah, I guess your max load is less mem hungry plus you have 33% extra ram. Unfortunately I'm on a laptop with ram maxed out. I might give swappiness=0 a go, but I'm really trying to get some work done at the mo and am not at my most experimental...

PS Sorry for spelling your handle wrong:)

Thanks,
Andy

---

### Post by warfacegod on 2010-02-05
Just don't tell anybody. I'll never live it down.

---

### Post by Andy F on 2010-02-05
;p

---

### Post by warfacegod on 2010-02-05
Post the results of:

```
top -d10 -n1
```

You specifically mentioned Eclipse. If that is the culprit, I'm guessing that it is using allot of RAM as cache. When the OS requests it to give up some of that space, it is refusing, forcing the OS to get the needed RAM from something else. Causing it to crash, apparently.

---

### Post by Andy F on 2010-02-05
It's not a CPU% issue I don't think (see below) and once it starts the whole machine's frozen anyway for a fair few minutes during which I can't enter any commands.

[IMG]http://img96.imageshack.us/img96/647/localhostlocaldomaincpu.png[/IMG]

---

### Post by warfacegod on 2010-02-05
What exactly is Eclipse? I went to the project site and couldn't find a precise idea of what it is.

---

### Post by Andy F on 2010-02-05
It's a bit like Netbeans if you know that. It's an opensource IDE written in Java, originally for Java, but with a slew of plugins that make it fairly extendable. I'm using a plugin to use it as a PHP development environment including debugger. As it runs in the JVM I expect it to be a bit memory hungry - just don't expect sudden death! And as I said, if it was _only_ Eclipse, I'd be posting on their forums, but other apps go tits up as well.

---

### Post by Andy F on 2010-02-05
And also, the fact that I jump around a large number of source files is one of the reasons I don't want to set swappiness to 0...

---

### Post by warfacegod on 2010-02-05
Well skip swapiness then. I'm not so sure it will help at this point anyway. Try running for a while without Eclipse, if that's possible. Disable it or turn it off or whatever. If you don't still have the same problem then the issue is with Eclipse and other things crashing can ultimately be brought back to Eclipse.

Java handling for Linux is generally piss poor and you can thank Microsoft for that.

---

### Post by Andy F on 2010-02-05
Thanks for the advice. At the mo I need to keep using it and the problem's not often enough to be a show stopper. I don't know of any free non-Java IDEs that can debug PHP, but I haven't looked thoroughly. Btw, what's the story re MS & the Linux JVM?

---

### Post by warfacegod on 2010-02-05
MS owns virtually everything and forces software and hardware manufacturers to heavily gear their products towards Windows. In some cases it looks like MS is actually actively suppressing Linux and Unix support.

---

### Post by Andy F on 2010-02-05
Going a little OT here :) but I'm really surprised to hear that Java isn't very Linux-friendly: until recently Java was a Sun product, now it's Oracle's, neither of which are particularly MS friendly. Also the JVM specs are available online...

---

### Post by warfacegod on 2010-02-05
Java hasn't worked all that well in Linux from what I have read here and other places. MS, whether they admit it or not, plans for their products to be obsolete fairly quickly. Hence the two year switch from Vista to 7. With companies scrambling to keep up, "lesser" OS's get pushed to the side, getting mediocre support at best. Except in a few cases such as nVidia.

---

### Post by warfacegod on 2010-02-07
I've been reading up on swap a little bit. (here's an example: [http://ubuntuforums.org/showthread.php?t=1399903]("http://ubuntuforums.org/showthread.php?t=1399903"))

I'm now thinking it might help if you *increased* your swapiness. Key word: might. Try around 80 or 85.

---

### Post by Andy F on 2010-02-07
Thanks for sticking with this! I was originally thinking that if anything I'd rather go up than down with swappiness. When first looking up its meaning I found several references to a mail list thread with a Kernel developer Andrew Morton (IIRC), and his points seemed very valid, and he said he ran with swappiness=100.

But... if swappiness was the issue, I'd expect the symptoms to be frequent small pauses waiting for the HD and every app buzzing along merrily. What I actually get is an occasional huge pause plus death to apps. I don't understand how swappiness could help.

I'll prolly play with the value at some point, it's just that I'm quite busy at the mo, quite new to Linux, and feel it's not the best time to be experimenting.

Thanks again.

---

### Post by Andy F on 2010-02-07
Did a quick search for logs that might help. There's an error log that I think is used every time the JVM crashes, which on my installation's at ~/hs_err_pid<pid>.log; and another log for Eclipse at <workspace>/.metadata/.log. Next time it happens (so far it hasn't again) I'll post up the contents of those.

---

### Post by warfacegod on 2010-02-07
Sounds good. I'm much on Error Logs but I know someone that is.

---

