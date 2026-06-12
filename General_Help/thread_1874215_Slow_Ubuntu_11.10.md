---
title: "Slow Ubuntu 11.10"
date: 2011-11-02
forum: General Help
---

### Post by gdjartov on 2011-11-02
Hey there,

I guess, I shouldn't have upgraded to 11.10 (64-bit), but I did and now I am struggling with its bizarre and erratic behaviour. It might be that my hardware is hopelessly old, but it shouldn't be the case - there are rare instances when it works fine, though just for couple of minutes. Some of the symptoms: 

Skype is particularly bad - on calls the whole computer comes to a halt and the fans go bananas. Chatting is a torture - the delay between hitting the keyboard and getting the letter on the screen is between 5 and 15 seconds.
Thunderbird takes a good minute to load.
Firefox is also behaving strange - flash kills it (no Facebook, nor Youtube) and even Google pages seem to slow it substantially.  

I am wondering if it is my laptop, or there is something wrong with 11.10. Today I updated it hoping for some progress, but nothing :(

Your help is much appreciated!

Specs:
[FONT=Arial, Helvetica, sans-serif][SIZE=2]- **HP Pavilion tx2500z Entertainment NB**
- AMD Turion(TM) X2 Ultra Dual-Core Mobile Processor ZM-82 (2.2 GHz)
- 12.1" diagonal WXGA High-Definition HP BrightView Widescreen (1280 x 800) w/Integrated Touch-screen
- 4GB DDR2 System Memory (2 Dimm)
- ATI Radeon(TM) HD 3200 Graphics
- 250GB 5400RPM SATA Hard Drive
- Webcam + Fingerprint Reader
- 802.11b/g WLAN and Bluetooth
- LightScribe SuperMulti 8X DVD+/-RW with Double Layer Support
- 8 Cell Lithium Ion Battery
- Microsoft(R) Works 9.0[/SIZE][/FONT]

---

### Post by MG&amp;TL on 2011-11-02
Nope, your system can run ubuntu with no problems. :)

Things to debug:

(for all of the following, open a terminal, then type these)

```
thunderbird
```

check your mail or whatever, and post the output from the terminal.

```
firefox
```
as above

```
skype
```

as above.

Then run:
```
top
```

in a terminal so we can see what's hogging it all.

And if all else fails, you can always try Ku- Or Xu-, either of which your system will run very happily. (Xubuntu is probably overkill, but some people don't like eyecandy, and that's what Kubuntu is about.)

---

### Post by gdjartov on 2011-11-02
MG&TL, thanks for your swift response.

This is what I got:

  	 	 	 	 	 	  georgi@GolfDeltaZulu:~$ thunderbird 
 failed to create drawable 
 

 georgi@GolfDeltaZulu:~$ firefox
 georgi@GolfDeltaZulu:~$ failed to create drawable


top:




top - 20:13:29 up 9 min,  1 user,  load average: 2.09, 2.25, 1.34
Tasks: 161 total,   2 running, 158 sleeping,   0 stopped,   1 zombie
Cpu(s):  6.4%us,  2.8%sy,  0.0%ni, 89.5%id,  1.1%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3796312k total,  1408932k used,  2387380k free,    79292k buffers
Swap:   975868k total,        0k used,   975868k free,   610832k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                         
 1327 root      20   0  507m  51m  12m S    9  1.4   0:24.86 Xorg                                                                            
 1711 georgi    20   0  421m  28m  20m S    6  0.8   0:04.47 unity-2d-panel                                                                  
 1787 georgi    20   0  388m  21m  10m S    5  0.6   0:06.53 unity-panel-ser                                                                 
 1656 georgi    20   0 27728 3164  828 S    1  0.1   0:11.17 dbus-daemon                                                                     
 2560 georgi    20   0  312m  17m  11m S    1  0.5   0:01.68 gnome-terminal                                                                  
 2624 georgi    20   0 21460 1376  968 R    1  0.0   0:00.84 top                                                                             
 1638 georgi    20   0  140m 3548 2632 S    0  0.1   0:02.07 ibus-daemon                                                                     
 1698 georgi    20   0  309m  24m  10m S    0  0.7   0:07.00 metacity                                                                        
 1736 georgi    20   0  196m  10m 7304 S    0  0.3   0:01.73 bamfdaemon                                                                      
 1915 georgi    20   0  454m  45m  13m S    0  1.2   0:02.45 gwibber-service                                                                 
 1979 georgi    20   0  292m  45m  10m S    0  1.2   0:04.20 ubuntuone-syncd                                                                 
    1 root      20   0 24180 2204 1264 S    0  0.1   0:01.08 init                                                                            
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                        
    3 root      20   0     0    0    0 S    0  0.0   0:00.10 ksoftirqd/0                                                                     
    4 root      20   0     0    0    0 S    0  0.0   0:00.78 kworker/0:0                                                                     
    5 root      20   0     0    0    0 S    0  0.0   0:00.44 kworker/u:0                                                                     
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                     
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                     
    8 root      20   0     0    0    0 D    0  0.0   0:00.45 kworker/1:0                                                                     
    9 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/1                                                                     
   10 root      20   0     0    0    0 S    0  0.0   0:00.70 kworker/0:1                                                                     
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                          
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                         
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                                           
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                                                                     
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                                     
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                                     
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                                         
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                                         
   20 root      20   0     0    0    0 S    0  0.0   0:00.06 khubd                                                                           
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                                              
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd                                                                      
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                         
   24 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                                            
   25 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged

---

### Post by MG&amp;TL on 2011-11-02
"Failed to create drawable" is what I'm worried about. Have you got your graphics driver installed? Looking at top, you're running Unity2d, I guess you haven't? To do that,  search for hardware drivers in the unity dash, then install the one you need.

---

### Post by anselm on 2011-11-02
I would try Lubuntu :D

---

### Post by MG&amp;TL on 2011-11-02
So would I...but with a processor and graphics card like that and 4GB? 

Although if you have any old hardware...

---

### Post by gdjartov on 2011-11-02
> **MG&TL said:**
> "Failed to create drawable" is what I'm worried about. Have you got your graphics driver installed? Looking at top, you're running Unity2d, I guess you haven't? To do that,  search for hardware drivers in the unity dash, then install the one you need.

I've installed ATI/AMD proprietary FGLRX graphics driver and now it's working much, much better (like there's a working driver) :P

I was just wondering, if  ATI/AMD proprietary FGLRX graphics driver (post-release updates) would have been more suitable choice?

---

### Post by MG&amp;TL on 2011-11-03
What do you mean, post-release updates? Manufacturer's updates to driver?

I personally would just get the most recent one in the addition drivers windows.

---

### Post by hydroxph on 2011-11-03
Maybe you should try the 64bit version.

---

### Post by gdjartov on 2011-11-03
Thank you all for your help! :D

---

### Post by holycow131415 on 2011-11-03
Maybe backup your stuff, and clean install 11.10 instead of upgrading.

---

### Post by MG&amp;TL on 2011-11-03
...although if it works, I wouldn't make the effort. Yet. Maybe wait for 12.04 to do clean install. And no problem, happy to help. :)

---

### Post by peetaur on 2012-03-07
I had the same "failed to create drawable" issue. I tried installing the nvidia drivers, which refused to install due to incompatible kernel module software (dkms I guess), and then I rebooted, and Thunderbird worked again.


The long story:

I wanted an addon. I installed it. Thunderbird would no longer start. So I tried the "-safe-mode" option, which did not work. From command line, it just quits with no messages.

So I removed the ubuntu thunderbird and added the downloaded one from mozilla.org, which said "failed to create drawable" instead. Then I added the Ubuntu repository listed on the mozilla.org website, and installed that one instead, also with the "failed to create drawable" message.

So I found this thread which suggested installing 64 bit video drivers, which I tried (and gave up on; next plan was going to be either installing the latest Kubuntu or something else: Debian or SuSe), but after rebooting, my new Thunderbird and the addon were working.

Possibly it is related to dbus-daemon                                                                      being dead months ago, killed dead a la  -9 for misbehaving; Thunderbird was likely started before that. I saw  that mentioned somewhere else. I forget where, but this page at least has some error messages in common: [http://askubuntu.com/questions/92211/both-thunderbird-and-emacs-throw-d-bus-errors-unless-sudoed-x-ok](http://askubuntu.com/questions/92211/both-thunderbird-and-emacs-throw-d-bus-errors-unless-sudoed-x-ok)

---

### Post by neubauerp on 2012-03-31
Disabling IPv6 or Enabling Pipelining didn't fix the slow-firefox-problem for me (11.10 latest updates).

I want to share another forum's post that solved this problem:
:!: :!: :!: "Disable Ubuntu Firefox Modifications" and it worked like a charm. Firefox behaves as normal again. :!: :!: :!:

As far as I read, this only disables the installation of firefox addons via the package manager.

---

