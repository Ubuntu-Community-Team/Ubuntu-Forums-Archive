---
title: "Ubuntu 8.04 very slow"
date: 2012-01-29
forum: General Help
---

### Post by vladimirx on 2012-01-29
Hello everybody,
I wonder if anyone can help me with Ubuntu 8.04 Hardy Heron LTS release. I used it for several years on a dual boot machine (PIII-800 MHz, 512 MB RAM, Radeon 7000 video card) along with Win XP Pro. Initially, both Ubuntu and WinXP were running with the comparable speed. Then recently I noticed that Ubuntu has become slow;I replaced the video cart to Radeon 7500 (didn't help),then reinstalled the system - if anything it became even slower,and I also lost the ability to play avi files (although the bad/ugly plug-ins for Gstreamer are installed, I can hear the sound but cannot see video) !
The slowness is especially noticeable in comparison with WinXP. Browsing the internet is a pain,even if only few tabs in Firefox are open (disabling ipv6 doesn't have any effect). The system monitor shows that the system utilizes a lot of resources even if no applications are running.
I will be thankful for your suggestions - I don't mind reinstalling the system if it will be helpful,but I did it few months ago without any effect.
The kernel version returned by uname -r command is 2.6.24-30-generic.
Thanks,
Vladimir

---

### Post by carl4926 on 2012-01-29
Trouble is 8.04 is so yesterday and I doubt many are using it.
And to say it is slow is rather subjective. Try and be more specific. Have you tried watching the processes in a terminal running top?

---

### Post by carl4926 on 2012-01-29
And the fact that a fresh install didn't improve matters suggests something deeper than the OS itself

> The system monitor shows that the system utilizes a lot of resources even if no applications are running.This is normal

Are you say XP is still fine?

---

### Post by vladimirx on 2012-01-29
carl4296,
Thank you for your quick reply. I understand that 8.04 is old and no longer supported. However, the computer I am using it on is old too, and I am afraid the newer Ubuntu versions will be even slower than 8.04. Regarding the subjectivity - it is much slower than it used to be, and Win XP runs on the same PC quite comfortably (as I said, XP and 8.04 were running on this PC with the similar comfort level previously - and isn't linux supposed to be less demanding on resources ?). Could it be that the newer versions of linux kernel need more PC power compared to the kernel initially included with 8.04 ? 
Also, could you please explain ow can I try "watching the processes in a terminal running top" ?
Thanks again.

---

### Post by wolfen69 on 2012-01-29
On a computer with those specs, I would try a more lightweight version of Ubuntu called [Lubuntu]("http://lubuntu.net/").

---

### Post by mcduck on 2012-01-29
> **vladimirx said:**
> The system monitor shows that the system utilizes a lot of resources even if no applications are running.


The first thing to do would of course be taking a look at what exactly is using the resources.

Go to the Processes-tab in System Monitor, and click the CPU field to sort the programs by CPU usage. Then do the same with the memory usage. (and make sure you've set the system monitor to show all processes instead of only your own, by selecting View->All Processes from the menu)

What comes to Linux being less demaning on reosurces, that's true. It doesn't, however, mean that every desktop environment or application you run on Linux would be less demanding. Only that the Linux itself is lightweight, and that you can customize your system to be very light by selecting desktop environemnt and applications that are less resource hungry.

Anyway, the biggest problem with a machine like that is that the world has changed since the days when it was a new system, web pages themselves are a lot more resource-intensive with all the images, flash, javascript etc, and there's nothing you can do about it. Having multiple tabs open on a browser would be quite a task for older machine no matter what you do. (of course running a very lightweight desktop, and using extensions like adblock, flashblock and noscript to reduce the active content on web should help at least a bit).

What comes to using a more up-to-date Ubuntu version, the system itself doesn't become more resource-hungry like new Windows and OS X versions tend to do. So it's perfectly possible to run a modern new Linux system on an old machine, you just need to pick desktop environment and programs that fit the machine's capabilities.

---

### Post by vladimirx on 2012-01-29
Thank for the suggestions.

I understand that this machine is slow, but still it should not be that *slow*; after all, WinXP runs pretty comfortably on the same hardware. In Ubuntu, I feel slowness just typing this message with few Firefox tabs open, and see occasional screen dimming when opening new tabs. System monitor shows 40-80% CPU usage (major contributors: Xorg, gnome-system-monitor, firefox, plugin-container), ~70% memory usage and no swap file activity. 

I wonder if this has to do something with the video card - I have seen discussion on some ubuntu forums that it may happen with the certain ATI video cards. This brings me to another question, shall I install a special driver for my Radeon 7500 ? At this time I use what was installed by Ubuntu,and I don't even know what video driver is there. Does anyone know how to clarify this issue - or at least to find our if video card driver is not a problem (other hardware on this machine is quite typical and should not give any conflicts). 

What else you think I can do before full re-install ? I know something is broken with my current installation (inability to play avi files supports this as well), but I am not sure that reinstallation would help (did it once already).

My hope is that my situation is not unique, and perhaps there are known solution for this slowness problem.

---

### Post by wolfen69 on 2012-01-29
> **vladimirx said:**
> I know something is broken with my current installation (inability to play avi files supports this as well)
Did you install the proper codecs? (ubuntu restricted extras)


> My hope is that my situation is not unique, and perhaps there are known solution for this slowness problem.
There is a solution. Use the proper version of ubuntu for the machine. It is not surprising to me that your computer is slow. As someone that has done a few hundred installs, I can assure you that switching to a more appropriate OS will make all the difference. Ideally, a minimal command line install would be ideal, but is not for someone who is not comfortable with the command line. I strongly recommend trying Lubuntu, as it is made specifically for older hardware. (but not limited to)

I installed Lubuntu on my limited resource netbook, and now it runs faster than my mother's $2500 mac. But in the end it's up to you.

---

### Post by bluexrider on 2012-01-29
> **wolfen69 said:**
>  I can assure you that switching to a more appropriate OS will make all the difference. Ideally, a minimal command line install would be ideal, but is not for someone who is not comfortable with the command line. I strongly recommend trying Lubuntu, as it is made specifically for older hardware. 
  I have to agree. If you are able to run XP then you wont have any issues with Lubuntu. 

Give it a try [http://lubuntu.net/blog/lubuntu-1010-released](http://lubuntu.net/blog/lubuntu-1010-released)

---

### Post by holycow131415 on 2012-01-30
You could also try crunchbang debian. Uses the openbox DE which is lighter than lxde

---

### Post by vladimirx on 2012-01-31
Tried Lubuntu 11.10 live CD - it boots to the command prompt. When enter "startx" the system freezes ...

---

### Post by 3rdalbum on 2012-01-31
> **vladimirx said:**
> Tried Lubuntu 11.10 live CD - it boots to the command prompt. When enter "startx" the system freezes ...

It shouldn't boot to the command prompt, and I don't think "startx" will do anything useful on any modern Linux.

Have you checked the integrity of the Lubuntu disc? And how much RAM have you actually got?

What does:

```
sudo service lightdm start
```

do?

---

### Post by vladimirx on 2012-02-01
Thanks, 3rdalbum !
Your advice was very useful and helped me a lot. Initially, the command

[FONT=Courier New][SIZE=2]sudo service lightdm start[/SIZE][/FONT]

returned: [FONT=Courier New][SIZE=2]lightdm: unrecognized service[/SIZE][/FONT]

Then I tried "[FONT=Courier New][SIZE=2]service --help[/SIZE][/FONT]", which led me to [FONT=Courier New][SIZE=2]"service --status-all[/SIZE][/FONT]", and in the appeared list I found service called [FONT=Courier New][SIZE=2]"lxdm[/SIZE][/FONT]". That looked interesting, and the command

[FONT=Courier New][SIZE=2]sudo service lxdm start[/SIZE][/FONT]

brought to me the Lubuntu desktop, and everything worked (this PC is PIII-800 with 512 MB RAM).

Another interesting thing is that I tried this live CD on my three other computers: one really old (Pentium Pro with 256 MB RAM) and one quite new (i5-2400, 8 GB RAM), and in both cases the Lubuntu desktop appeared as it supposed to. However, on my IBM T23 notebook (PIII-1200, 1 GB RAM) it refused to boot even to the command prompt.

---

