---
title: "How does KDE use RAM?"
date: 2006-04-01
forum: General Help
---

### Post by Kimm on 2006-04-01
I have a simple consern.
I recently started using KDE instead of Gnome, and I do like it. Just now I started the System Guard program to see how much memory was used. Aparently I have 100 MB's free. It feels like a tad to little...
I read somewhere that Linux tries to use all RAM on the system and then give the space to programs that need it... is it the effects of that I am seeing?

KDE still runns smoothly so I dont know what to think...

---

### Post by ComplexNumber on 2006-04-01
yes, KDE uses significantly more RAM than gnome. approximately 3 times the amount. it may be something to do with the greater amount of eye candy and stuff that KDE utilises.  or it may be that its just less efficient.

---

### Post by cwaldbieser on 2006-04-01
[QUOTE=Kimm]I have a simple consern.
I recently started using KDE instead of Gnome, and I do like it. Just now I started the System Guard program to see how much memory was used. Aparently I have 100 MB's free. It feels like a tad to little...
I read somewhere that Linux tries to use all RAM on the system and then give the space to programs that need it... is it the effects of that I am seeing?

KDE still runns smoothly so I dont know what to think...[/QUOTE]

Try adding some displays to ksysguard that show you how much of that memory is cached (for disk I/O).  That should give you a better idea of how much free memory you have.  The "free" command also shows this info on the "-/+ buffers/cache: " line.

---

### Post by Barrakketh on 2006-04-01
[QUOTE=Kimm]I have a simple consern.
[...]
KDE still runns smoothly so I dont know what to think...[/QUOTE]

That's not a big deal.  A lot of memory is used (as was stated before me) for disk cache/buffers, among other things.  I have 558 megs tied up for that alone.  The memory will be freed when it's needed, so don't worry :)
[quote=ComplexNumber]yes, KDE uses significantly more RAM than gnome. approximately 3 times the amount.[/quote]
I'm calling BS on that.

---

### Post by Adrian on 2006-04-01
[QUOTE=ComplexNumber]yes, KDE uses significantly more RAM than gnome. approximately 3 times the amount. it may be something to do with the greater amount of eye candy and stuff that KDE utilises.  or it may be that its just less efficient.[/QUOTE]

Where did you get those numbers from?
People usually say that KDE consumes less RAM than Gnome, but more CPU power.

---

### Post by ComplexNumber on 2006-04-01
[quote=Adrian]Where did you get those numbers from?
People usually say that KDE consumes less RAM than Gnome, but more CPU power.[/quote]
my own installations on fedora, suse, and mandriva/mandrake.
it seems to be the other way round for me concerning the CPU and RAM usage.

---

### Post by hizaguchi on 2006-04-01
[QUOTE=Barrakketh]I'm calling BS on that.[/QUOTE]
I'm with you.  I've only got 128 megs of ram and a laptop harddrive that makes swapping = extreme snail speed.  I've tried every window manager and DE I can get my hands on and kept a close eye on my memory usage.  Out of the box, Gnome uses around 100 MB of ram and KDE uses around 85.  But if you go into Kcontrol and choose the "minimize ram usage" option you can cut it down to around 70 megs, which is getting close to the 55-65 meg range of E17, fluxbox, XFCE, etc, but with the advantage that you've already got the Qt libs loaded.

Now, I'm sure you could enable lots of transparencies and fancy effects and make a much bigger dent in the resources, but the default KDE setup is definately not a memory hog.  Processor maybe, but not memory.

---

### Post by Adrian on 2006-04-01
This is my **personal** experience:
When I had 128MB RAM (just one year ago), I did a lot of testing and it felt like KDE handled the situation better than Gnome (on **my** laptop). Actually, running it was a nice experience, and that's why I started using KDE (even though I thought GNOME was much prettier).

Also, if you disable the effects, it's not CPU-demanding at all.

---

### Post by ComplexNumber on 2006-04-01
> KDE uses around 85.   
85MB? :shock:.  you have got to be kidding.[B] 



hizaguchi, Adrian, Barrakketh[/B]
on my system whilst idling, gnome uses on average around 120-170MB whilst KDE uses around 360-380MB of RAM. in this instance, gnome uses 159 MB and kde uses 375MB of RAM :shock:

i got some snapshots of the screen before that show the memory used by kde and gnome together with the list of processes active at that time....so you can see for youself how much more of a memory hog kde is on my system. they were all taken shortly after logging into either gnome or kde. both kde and gnome are on suse 10. the first 2 are kde and the last 2 are gnome.

---

### Post by njf on 2006-04-01
Does the system monitor display cached and buffers at all?

Why don't you post screenies of "free" in cli under kde and gnome?

---

### Post by ComplexNumber on 2006-04-01
>  Why don't you post screenies of "free" in cli under kde and gnome?
free what?

---

### Post by njf on 2006-04-01
[QUOTE=ComplexNumber]free what?[/QUOTE]
type free in command line dude.

---

### Post by Barrakketh on 2006-04-02
And use either GNOME's System Monitor or KSystem Guard for both DEs if you're going to take screenshots.

EDIT:

Here's my screenshots taken with gnome-system-monitor.

GNOME:
[[IMG]http://img47.imageshack.us/img47/7501/systemmonitor4qc.th.png[/IMG]](http://img47.imageshack.us/my.php?image=systemmonitor4qc.png)

KDE:
[[IMG]http://img47.imageshack.us/img47/4749/systemmonitor26eq.th.png[/IMG]](http://img47.imageshack.us/my.php?image=systemmonitor26eq.png)

I didn't bother taking the process list for either of them, because accusations of me "rigging" my comparison don't bother me.  Some things that *might* swing the memory usage in KDE's favor:

Nautilus.  An instance of Nautilus is kept open for GNOME's desktop.  It eats up 18.6 megs of RAM on my system.

gnome-settings-daemon -- 12.8 megs.

gnome-session -- 9.4 megs

I'd have to do some comparisons later to see how much RAM kicker uses for it's applets (GNOME's trash applet uses 8.3 megs of RAM, the notification area uses 7.5, etc.)

The main point is that your claim that KDE using three times (or even two times) the RAM of GNOME is absurd.  KDE has always been rather lightweight compared to GNOME, and when KDE 4 is released (and this everything is ported to Qt 4) things will get even better.

---

### Post by GeneralZod on 2006-04-02
[QUOTE=ComplexNumber]
on my system whilst idling, gnome uses on average around 120-170MB whilst KDE uses around 360-380MB of RAM. in this instance, gnome uses 159 MB and kde uses 375MB of RAM :shock:
[/QUOTE]

It's pretty rare that I do this, but I'm going to have to go and say a flat-out "NO" on this one :)


The first time I installed Kubuntu on my 256MB laptop, I completely forgot to add a swap partition.  I had all of KDE, Firefox, a whole bunch of Konqueror instances, Konsoles and everything else open (including a crappy Java app I wrote), and it all ran fine.  After a few hours of use, Firefox was using more than all of the others combined :)

Eventually, I "crashed" it by trying to load Eclipse - whoops!

But there is no way, no how, that KDE uses anywhere *near* 375MB RAM or my laptop would have just sat there thrashing away indefinitely trying to load the thing!

---

### Post by ComplexNumber on 2006-04-02
>  But there is no way, no how, that KDE uses anywhere *near* 375MB RAM or my laptop would have just sat there thrashing away indefinitely trying to load the thing! but the fact remains is that it does. note that i don't have any transparancy, superkarama stuff...its just a basic install. also note that i switched many of the default services off to cut down on the amount of resources used by KDE. you can see what processes are active from the screenshots and they all add up to 370MB+.

---

### Post by GeneralZod on 2006-04-02
[QUOTE=ComplexNumber]but the fact remains is that it does.
[/QUOTE]

I don't want to be rude, but the fact remains that it *doesn't*.

Lets review two facts that have been brought up in this thread:

- This whopping 370MB DE (plus a whole plethora of apps, including Firefox which alone can *easily* use 100MB of RAM after a few hours use) can magically fit inside my 256MB RAM (there was no swap, remember).  

- According to Barraketh's screenshot which was posted 13 hours ago, KDE uses at most 174MB (as he obviously had some of the GNOME/gtk libraries loaded in order that he could use gnome-system-monitor).


Really (unless both he and I are liars, of course :)) this should be enough to convince you, but it seems it doesn't, and I'd be interested to hear why.  Is it  the amount of RAM usage reported by ksysguard? If so, disregard it - Linux, like most modern OS's, fills your RAM as much as it can with cached files, so a while after use (perhaps, even, by the end of booting, depending on how much RAM there is to fill and whether it's doing any read-ahead) it will use all of your RAM, with a few MB's of wiggle room.  When you type "free" at the command line, as a couple of people have suggested, this RAM usage is printed in the "used/Mem:" column, and it is also this number that is being reported by ksysguard.

gnome-system-monitor, on the other hand, prints out the result of actual RAM usage *minus* cached files, which in the "free" output is the figure in the "used:/ +/- buffer cache".  Try it for yourself - open up both gnome-system-monitor and ksysguard at once and compare the reported figures, and compare  them to the numbers reported by typing "free" on the command-line, as described.

[QUOTE=ComplexNumber] you can see what processes are active from the screenshots and they all add up to 370MB+.[/QUOTE]

Can you point this out more precisely? I can't seem to find this anywhere :)

---

### Post by ComplexNumber on 2006-04-02
>  I don't want to be rude, but the fact remains that it *doesn't*. well then , would you like to be so kind and explain to me why it does on my system for every single distro that i've ever used? you can clearly see that it does.


>  Can you point this out more precisely? I can't seem to find this anywhereits the 1st photo that i've given. it shows the process list for kde. 



btw what are those kdeinit process in gnome?


> 
 compare them to the numbers reported by typing "free" on the command-line, as described. KDE still uses significanty more RAM. here is what i got:

---

### Post by hizaguchi on 2006-04-02
ComplexNumber, your last screenshots verify my numbers almost exactly.  The first line of "free" is your actual memory usage, but it includes some things that your system does with whatever physical memory you are not using for other things.  It will almost always show that you're using most of your RAM because Linux puts the free memory to work doing something if you're not using it.  The second line, "+/- buffers/cache" is how much memory you are actually using before your system fills up the rest with, well, whatever it does with free memory.  Somebody else could give you a much better explanation.  Anyhow though, that 2nd line is the point of focus.  Note that Gnome is using around 99 megs (I had said 100 on my system) while KDE is using about 89 (again, more like 85 for me).

---

### Post by ComplexNumber on 2006-04-02
**hizaguchi**
fine.  but the total memory used by kde is still far too excessive.
also, perhaps you could answer this: what are those kdeinit, klauncher, kded processes in gnome (see the screenshot of the gnome processes that i've given on the first page of this thread)? killing them reduces memory a usage a lot but makes no difference to gnome. thanks.

kde is slimmed down as much as it will go (eg transparaccy and everythign is switched off). i wonder if not using transparancy on gnome will make a difference to the figures to make it fair.



EDIT:

i switched off terminal trasnparancy in gnome and got rid of those kdeinit process (to make things fair) and the amount of memory available in gnome went up from 43MB to 101MB, as can be seen here:

---

### Post by GeneralZod on 2006-04-02
> **ComplexNumber]well then , would you like to be so kind and explain to me why it does on my system for every single distro that i've ever used? you can clearly see that it does.
[/QUOTE]

Did you not read what I wrote? 

The number reported is the total RAM used, *plus cached files*.  This will almost always end up approaching the total RAM in your system.  

So I cannot "very clearly see that it does", as it very clearly doesn't!  said:**
> 
its the 1st photo that i've given. it shows the process list for kde. 


This one?

[http://ubuntuforums.org/attachment.php?attachmentid=7901&d=1143947298](http://ubuntuforums.org/attachment.php?attachmentid=7901&d=1143947298)

As I said, ksysguard reports the total RAM used including cache, which is what we are seeing in the screenshot.

> 
btw what are those kdeinit process in gnome?


Dunno, but they are definitely KDE processes.  You *should* be able to kill them off if you are not running any KDE apps, but they may respawn! :D

> 
KDE still uses significanty more RAM. here is what i got:

As can be inferred from the analysis in my last post, and as hizaguchi has explained, your screenshots prove that KDE is using *less* RAM than GNOME :)

> 
fine. but the total memory used by kde is still far too excessive.


Why is it? It's just files cached (by the Linux kernel - not by KDE), each portion of which will be instantly cleared and re-allocated as soon as an application demands that portion.  It has absolutely 0 effect on performance and shouldn't be viewed as a bad thing - again, all operating systems do this, and they do it by design.  At worst, it shows that the process of initialising KDE mmaps a greater amount of files from disk than does GNOME, which would very likely translate to a slower start-up as compared to GNOME.  But it shows nothing about the actual peak memory usage of KDE, and is yet more proof that KDE does not use ~370MB of RAM, and definitely does not use more than three times that of GNOME.

---

### Post by ComplexNumber on 2006-04-02
>  Dunno, but they are definitely KDE processes.  You *should* be able to kill them off if you are not running any KDE apps, but they may respawn! i did. see my edited post above ;).
hmmm maybe i need to do a crash course in memory usage.

---

### Post by GeneralZod on 2006-04-02
[QUOTE=ComplexNumber]i did. see my edited post above ;).
hmmm maybe i need to do a crash course in memory usage.[/QUOTE]

I see at least one post a week about complaining about Linux using 1GB RAM, so you're in good company ;)  It's a very tricky thing to get right, especially as some process monitoring apps (notably naughty ksysguard!) only report the VM size for an app, which is about the worst possible measurement that can be taken if you want to see how much RAM an app is taken (as you can see from some of your screenshots - there's no way mono could possibly be taking up over half a gig of RAM! :)).

I came across a pretty cool link the other day that explained why readings from these kind of apps are misleading - I'll post it here if I can find it ...


Edit:

This might be it.  It's pretty heavily KDE-slanted, but applies pretty much universally:

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

A very interesting read which someday I might ask to be included in an FAQ :) It doesn't touch on cache, though - there's a separate link for that that I'll have to try and track down again ...

Edit2:

I can't find the link that is normally posted, but this one looks pretty good!

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by Segovia on 2006-04-02
Why do you think it's too much?  Unused memory is wasted memory.  The ideal amount of memory the OS should use is EVERY BIT IT CAN.  This has been explained by Windows and KDE devs many times...to no avail.

Trying to force KDE or GNOME to use less memory is just going to slow you down.  Why in the world would you want it to swap stuff out to disk when you've got hundreds of MBs of free physical memory?

Of course there can be sloppy apps using far more memory than necessary, but that's not what you're referring to here.

Right now I've got kopete, kontact, konqueror, ktorrent, and konversation running and I'm using 244 out of 1024.  For KDE to start conserving memory and swapping stuff to disk, just so that I can see a lower number with "free", would be utterly retarded.  It's running like a well oiled machine right now, smooth as silk and lightning fast.  The memory is there to be used, that's why I bought it?

---

### Post by ComplexNumber on 2006-04-02
> I came across a pretty cool link the other day that explained why readings from these kind of apps are misleading - I'll post it here if I can find it
yes, please do. one thing you may notice is that, when i switched off the kde processes in gnome and made the terminal opaque, the amount of "free" ram increased whilst the amount used by the cache/buffers (ie indicated by the 2nd line in the output of the 'free' command) increased :confused:

---

### Post by GeneralZod on 2006-04-02
[QUOTE=ComplexNumber]yes, please do
[/QUOTE]

Done - see the edits to my last post :)

> 
. one thing you may notice is that, when i switched off the kde processes in gnome and made the terminal opaque, the amount of "free" ram increased whilst the amount used by the cache/buffers (ie indicated by the 2nd line in the output of the 'free' command) increased :confused:

I noticed that, and just chalked it up to the Black Magic that is the Linux memory management system :)

I'm just reading through this link

[http://kerneltrap.org/node/3216](http://kerneltrap.org/node/3216)

(particularly the post entitled "It is dynamic, and it's more slippery than you might think") and it's making my head spin - I'm not even going to attempt to second-guess just what was going on behind the scenes there :) It's possible that invoking the "kill" command read the "kill" program and whatever libraries it needed from disk which, of course, would then be added to the cache.  Also, kill'ing a process usually sends a "I need you to shut down; save your work but make it fast!" signal to the process, and any files needed for writing would (I think) be added to the cache.  These are all pretty uneducated guesses, though, so I may be *waaay* off!

---

### Post by ComplexNumber on 2006-04-02
hehe cheers for that :). i'll have a good read of that because it seems like i have a lot to learn.

---

### Post by vem0m on 2006-07-20
if u start loading alot of programs, then u will see higher. Its not KDE managing ram that progrma just reports linuxs usage. Desktop Environments have nothing to do with how memory is managed from what i know correct me someone if i am wrong but its the acuall linux that does.

---

### Post by phenest on 2007-04-06
I used to develop software for Windows. There is a fad amongst programmers to have a small memory footprint for their applications. This is pointless practice as it's not necessary.

It is Linux that is responsible for memory management. KDE & Gnome simply report its usage. Don't forget that KDE & Gnome *will* use slightly different quantities as they use different modules to run and this could cause a difference of 20Mb or so. Also, Gnome doesn't report disc caching which can amount for approx. 250Mb or more. Opening Gnome's System Monitor and KDE's System Guard at the same time, proves this point.

Only concern yourself with memory when your computer starts to slow down due to Linux using the Swap partition.

Memory is significantly faster than the hard drive, so if there is RAM to spare, let the system and applications use it. Remember: just because you aren't using any applications, it doesn't mean Linux isn't doing anything.

---

