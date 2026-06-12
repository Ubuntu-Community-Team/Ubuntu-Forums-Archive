---
title: "Xubuntu 12.04 memory requirements?"
date: 2012-06-01
forum: General Help
---

### Post by /dev/n on 2012-06-01
I read in wiki ([https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Xubuntu](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Xubuntu)) that minimum recommended RAM for the newest Xubuntu was around 512MB, which made me wonder what's been cooking. I've been running 10.04 on an old Celeron with only 384MB RAM, no special desktop effects or other resource hogs, and while not fast by any means, it's still been totally functional. In fact, it uses under 100MB after login, and with OpenOffice (a vital app used daily), not much more than that (usually under 120MB), and nothing in swap.

So, before making that leap into 12.04 (and possibly running into trouble), I'd like to ask 12.04 Xubuntu users whether their systems actually use ~512MB RAM on the desktop (not including other apps started by the user). Has Xubuntu become terribly bloated or have the numbers above been pulled out of a hat by someone with top-of-the-line equipment and several apps running simultaneously (unlike yours truly)? I hope you don't steer me toward Lubuntu or LXDE. I didn't like what I saw in it, especially compared to Xfce, which is good enough for me, neat and effective. Since it's not hogging a ton of resources in 10.04, can it be doing that in the latest version? 

As far as buying more RAM, I'd rather not spend anything on an old box that's obviously past its prime but still usable.

---

### Post by QIII on 2012-06-01
Mine idles somewhere around 640MB, but I have a pretty robust conky running and calling several scripts frequently.  I also have a few start up programs running.

YMMV

---

### Post by brainwash on 2012-06-01
> To **install** or **try Xubuntu** within the Desktop/Live CD, you need 256 MB of memory. Installing with the Alternative CD requires only 64 MB. **Once installed**, it is strongly recommended to have at least 512 MB of memory, but you can run with 256 MB too.

from [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

---

### Post by erind on 2012-06-01
I have mine idling at 320 MB, with some light custom scripts running at start-up, and some default apps disabled.

---

### Post by stoneheart on 2012-06-01
I am using a 6 year old dual core laptop at this moment with 2 gigs of ram, running Xubuntu 12.04.  The system with Firefox opened with 9 tabs takes about 422 megs of ram according to the free -m command.

---

### Post by /dev/n on 2012-06-03
All right, thanks for your numbers. I suppose it should be running in my modest settings too. BTW, I did notice the RAM numbers in my initial post (from system-monitor) differ quite a bit from those after running  ```
 free -m 
```  which shows about 240MB used after login, and once OpenOffice is running, it rises to ~350MB, leaving precious little for anything else (not that I tend to run several apps simultaneously, except for Thunar and Terminal). I've disabled and/or removed quite a few unnecessary start-up apps to minimize the memory use.   I guess I could post some data after install, should anyone with old hardware find that useful.

---

### Post by Peripheral Visionary on 2012-06-03
I have an 8-year-old Dell with 512 RAM that ran awesomely on Xubu 10.04 and runs *even faster* on Xubu 12.04! I have just a little bit of compositing on for the panels and such, and use the lightweight Seamonkey suite instead of Firefox and Thunderbird, but most of the default apps in Xubu Precise are pretty lightweight anyway. This ol' dinosaur runs great on the new Xubu!

---

### Post by /dev/n on 2012-06-19
The upgrade to 12.04 didn't turn out well, to put it mildly. The install went without a hitch, but using the system has been a rather painful experience. I've tried to disable/get rid of unnecessary elements (cups, bluetooth, several startup scripts etc.) to reduce the memory use, but it still uses ~300MB RAM after login alone, and it sure won't take long for all the RAM to be consumed, which obviously makes everything unbearably slow. Even opening a simple text file in Leafpad, without anything else running, seems like a huge endeavor for my system. Oh, and I've tried a number of themes and icon styles that came with the install, with little impact on overall performance. There's no compositing or stuff like that enabled that would explain this. I even added a new user (after preserving my /home from 10.04) in case some old settings were messing with everything, but no change.     
Then there's Thunar, which used to be fast even to my modest standards, but now ... SLOOOOOOOOOOOOOOOOW. BTW, I've read some threads here about Thunar's slowness in opening (supposedly related to the network/samba), but I've already removed gvfs-backends, so there's no network folder in Thunar anymore, yet the problem persists. It affects all use of Thunar, like changing into another folder, right-clicking and even scrolling, which is absolutely frustrating. It's amazing how this fast file manager has evolved into a lumbering giant my system can no longer handle.    
So, to answer my own question after this experiment, Xubuntu's memory requirements **are** higher than the 384MB my old Celeron has. A faster CPU with equally little memory might fare better, but that's another story.     
There are probably three options with the current setup:     
1. deal with the slowness, stock up on patience and maybe strip down the system even further to make it somewhat bearable and usable.   
2. return to familiar 10.04 territory, make all the adjustments I had that allowed me to use it daily, and forget about upgrades and updates. Next year is so far away anyway.   
3. consider switching to Lubuntu. I'm not sure if xfce can be chosen/installed instead of whatever windows98 horror show it features. It's not like I'm looking for fantastic eye candy, but something pleasant enough that doesn't distract or interfere with my work.     
Or I might pick up better hardware of *this* century and clear these hurdles once and for all.      
Anyway, if possible, I'd gladly hear some tips how to drop the excess baggage the newest Xubuntu is carrying. The only supposedly &quot;heavy&quot; apps I frequently use/need are gimp, oowriter (or lowriter) and vlc. I'd also like to keep xfce, but other than that, I could remove whatever unnecessary in 12.04. I just don't know which of the dozens of processes could be removed or disabled without dismantling the entire desktop.

---

### Post by sudodus on 2012-06-19
I'm quite happy with Lubuntu, LXDE has a smaller footprint than XFCE. It uses less memory and makes the graphic rendering much faster, also valuable when playing video even on computers of this milennium ;-)

And you can run ```
sudo apt-get install xubuntu-desktop
``` and install other tools you might like better than the simple ones of Lubuntu.

What I am saying is that I think it is easier to start with a small desktop environment, that works well on your computer, and then add some features, that you want, rather than trying to peel off features from a desktop environment, that is too big.

---

### Post by /dev/n on 2012-06-22
I had a chance to test my install in different circumstances, an old Pentium 4 but miles better than my pathetic Celeron. None of the slowness and other symptoms were present anymore, so clearly, hardware is an issue. Anyway, I got to borrow a hard disk with a 10.04 install and took it to my computer, and voila, it's working again at its normal speed. Looks like I'll be returning to Lucidland again, a comfort zone without bugbears and the like.  

Thanks for all your comments.

---

### Post by mastablasta on 2012-06-22
you could try posting result from 
```
 
top

``` 
```
 
lshw

``` 
commands. maybe ther eis something we could do.
 
i don't think Xubuntu should use so much RAM. it should use about 130-140 MB on boot. Lubuntu will use even less (i think 80-90).
 
if you want a light XFCE try Debian (freeze is comming in a week or two). you could also give Mint debian XFCE a try (i think it's still debian based) or chrunchbang with xfce...
 
other lighter DE options are e17 (e.g. ubuntu based bodhi linux), razorqt (still in beta, but i gave it a try in live and it worked ok in that session).
 
if you don't need the bling then you can try IceWM (window manager looks a bit like win95)

---

### Post by dukedoug on 2012-08-12
Definitely struggling with Xubuntu 12.04. I have an old Tosh Satellite Pro 4300 laptop on which I'm running Ubuntu (Gnome) 10.04. Slow ... but useable for general browsing etc. with Firefox (Ad blocking enabled).

Decided to try Xubuntu 12.04 as have had good past experience with Xfce on an even older laptop.

LiveCD will load and run (sloooowly), but Install (Desktop) fails with "Unrecoverable Error". Likely a memory problem as the machine has only 194MB RAM. Xubuntu 12.04 pages state in one place that min. RAM is 192MB and elsewhere 256MB for Desktop install.

OK ... so try Alternate, which is slated to install with 64MB RAM. Alternate CD does not load drivers for either of my Xircom PCMCIA cards, which work flawlessly with Ubuntu 10.04 AND Xubuntu 12.04 Live CD and the first stages of Desktop Install. So, no network with Alternate install ...

I'm a 40-year IT industry veteran. I have solved installation problems with more op. systems and applications than most of you have had hot dinners - including Fedora 5, 6 and 7; Ubuntu going back to 7; Puppy; Lubuntu; Fluxbox; various versions of Java on Linux, Unix and Windows ... and a whole lot more. Why is it STILL so hard to get a reasonable install of something that should be relatively easy ??? Why, in particular, do Xircom LAN adapter drivers work in the Live CD / Desktop and NOT in Alternate ?

I guess the message is as noted elsewhere in this thread ... leave the laptop at Ubuntu 10.04, forget any hopes of loading Xubuntu 12.04 and stop wasting my time beating my head against the wall (nearly 2 weeks wasted now, trying to fit this install into my "hobby" time ... I do this for "fun" and "relaxation" ... I might as well play golf !!).
:(

---

### Post by bodhi.zazen on 2012-08-13
I do not believe *buntu is targeting old hardware.

---

### Post by mastablasta on 2012-08-13
> **dukedoug said:**
>  Why, in particular, do Xircom LAN adapter drivers work in the Live CD / Desktop and NOT in Alternate ?
 
 
because alternate doens't install the same things as desktop? have you tried text installer from DVD?
 
a few other options to consider for low spec mashcine:
Bodhi linux (ubuntu based with a very nice e17 desktop)
AntiX - (debian based) with latest kernel pathed to work with old maschines, iceWM installed uses about 55-60 MB on boot.
Slitaz - ment to be used on old maschines.

---

### Post by dukedoug on 2012-08-13
OK ... so Xubuntu Alternate install completed eventually with no network connection. I managed to boot from the hard disk and things don't look too bad (that is, not much - if any - slower than 10.04 Gnome).

Got one Xircom PCMCIA adapter to work ... but with a strange problem. Connections Indicator showed that Xircom was connecting to the router with DHCP but I had no actual network connectivity (could not even ping the router). ifconfig showed irda0 (yes, this laptop has an IR interface) was configured, supposedly with connection to the home network. Took irda0 down and connectivity via the Xircom PCMCIA adapter was fine.

Currently doing a massive catchup update ... Think I'll go to bed and let it run.

Once the update completes I will try to work through NDIS config. for my Netgear PCMCIA WiFi adapter. I've had all manner of fun with this on previous *buntus ... primarily with WPA security. Eventually discovered that only an exactly 13-character passphrase is accepted ... even though all my other machines (and my kids' and their mates' machines, iPxxs and Androids etc.) are happy with other passphrase lengths.

I'll keep playing with 12.04 for a while on the Tosh laptop and, if I'm happy, will eventually update my "real" Linux laptop (the one on which I'm posting) ... a HP / Compaq nx6120 - currently running 10.04. I'm expecting that process to be a lot less painful.

After that I'll be looking for another, lighter-weight distro. for the next adventure on the Tosh.
:D

---

### Post by kurt18947 on 2012-08-13
If you're using a 64 bit O.S., you might try 32 bit.  32 bit seems to use less RAM.    My experience with Lubuntu has been pretty positive on older or netbook class machines.

---

### Post by dukedoug on 2012-08-14
Well, the saga is completed satisfactorily and the results are quite good.

Xubuntu 12.04 is now running on the Tosh Satellite Pro 4300 in what I believe to be 192MB RAM (64MB standard + 128MB expansion ... couldn't add up correctly in my first post). Interestingly, the Panel monitor app I have running says 243MB so I'm probably wrong. The app reports 197MB of 243MB used as I type this ... along with 31MB of 299MB swap.

My Netgear WG511v2 (Marvell chipset) PCMCIA WiFi adapter came up immediately once I achieved a successful installation of ndiswrapper by installing the extra modules as advised in another post on this forum. Still don't have my old Xircom iiPS 10Mbit PCMCIA "credit card" adapter working ... but who cares ? (Well, me ... so if anyone has any suggestions on obtaining and activating the "xe" kernel module in 12.04 ...).

Firefox is useful - including for this post - and I've checked it with some of my other favourite sites. The big challenge for this old machine with limited resources is media-content rich sites and applications. One of my favourites (comics.com) pushes huge amounts of advertising, including Flash movies and flashy ads with lots of changing graphics. Firefox AdBlocker Plus "fixes" this ... I've also found Ubuntu Software Centre to be heavy going and slow.

Conclusion: Xubuntu 12.04 "works" in less than 256MB ... but with limited functionality.
:D

---

### Post by mastablasta on 2012-08-14
try lighter browser such as Midori, Seamonkey or Dillo. or a text browser such as lynx :-D
 
With 256Mb ram a better option might be Lubuntu or ubuntu based Bodhi linux.
 
I use Chrunchbang with XFCE (Debian 6) on such an old mashicne and the usage is about 80 MB on boot. some older appcliaitons but patched for security. so no issues browsing or wathicng you tube videos for example.

---

### Post by sudodus on 2012-09-06
> **mastablasta said:**
> try lighter browser such as Midori, Seamonkey or Dillo. or a text browser such as lynx :-D
 
With 256Mb ram a better option might be Lubuntu or ubuntu based Bodhi linux.
 
I use Chrunchbang with XFCE (Debian 6) on such an old mashicne and the usage is about 80 MB on boot. some older appcliaitons but patched for security. so no issues browsing or wathicng you tube videos for example.
+1
or try the Opera browser with 'turbo', which means that heavy sites are preprocessed by Opera servers, and a smaller page is sent to your computer. This is mainly intended for slow internet connections, but might work also in your case with an old computer.

---

### Post by TenPlus1 on 2012-09-06
I have Xubuntu installed on an old Compaq M2000 with 1gb memory and a 1.6ghz processor and it sits after boot at around 120mb and goes up to 370mb while browsing and playing background music...  I use Opera 12.02 for browsing...

---

