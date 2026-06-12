---
title: "Desperate Quick Need Of Help"
date: 2011-12-17
forum: General Help
---

### Post by JoabW on 2011-12-17
Hi, this is going to be a long read, but I could do with a hand.
Right, I've just installed Ubuntu 10.04 Netbook edition, and apparently it didn't auto detect the **Ralink RT2860 WiFi chipset** (If you have a dl link that'll work on ubuntu that would be amazing). Anyhow, I was following [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007) guide, which requires "gcc". I have no idea how to get that (without Internet connection) - when I search gcc into [FONT=Verdana, sans-serif]Synaptic Package Manager then it says I've installed all of the programs, however using these:
[/FONT]
      **Code:**
     [FONT=Verdana, sans-serif]sudo make[/FONT] 
[FONT=Verdana, sans-serif]sudo make install[/FONT] 
[FONT=Verdana, sans-serif]sudo ifconfig wlan0 down[/FONT] 
[FONT=Verdana, sans-serif]sudo rmmod rt2860sta[/FONT] 


These result in errors, even sudo make, which gives the following errors:

make[1]: gcc: command not found
make[1]: *** [all] Error 127
make[1]: Leaving directory '/home/user/...............' (.... being folder)
make: *** [build_tools] Error 2


Also, I was trying an alternate way, but I can't use the root command, because when doing what terminal suggests it says "Couldn't fins package root-system-bin". Meaning I have no access to root commands....

Thanks a lot for your help,

---

### Post by JoabW on 2011-12-17
Oh, I also want to add that, I still have WinXP installed on another partition, so if anyone knows a way to transfer the driver over then please give a tutorial. 
Thanks a lot for the help!!!

---

### Post by hansdown on 2011-12-17
Hi, JoabW.

Do you have access to a wired connection?

I fear the link here, may be useless, if you can't connect to the net.

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

---

### Post by dcstar on 2011-12-18
> **JoabW said:**
> Hi, this is going to be a long read, but I could do with a hand.
Right, **I've just installed Ubuntu 10.04** Netbook edition
......
[LIST=1]
[*]Why did you not install a later Ubuntu version that has better hardware support?
[*]Install the **build-essential** package.
[/LIST]

---

### Post by 3rdalbum on 2011-12-18
I would DEFINITELY recommend using a later version of Ubuntu. Versions 11.04 and 11.10 both have the driver preinstalled and ready to rock'n'roll out-of-the-box.

It's also easier to get support for the latest version of Ubuntu.

So head over to [www.ubuntu.com](www.ubuntu.com) and download Ubuntu 11.10; it'll work better on your netbook than 10.04.

---

### Post by JoabW on 2011-12-18
> **hansdown said:**
> Hi, JoabW.

Do you have access to a wired connection?

I fear the link here, may be useless, if you can't connect to the net.

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

No, I'm using my phone just to write this...


@3rdalbum and dcstar:
I did it because the .iso's on the ubuntu website were not a clearly named as a netbook version. I wasn't sure whether there was much of a difference between them in terms of things like this (I have used 10.04 on my older netbook with absolutly no problems)
I'll try that and hopefully it'll be better

Thanks guys

---

### Post by JoabW on 2011-12-18
Hi, I'm back, so I've installed 11.10 and it has recognised the drivers, but now I can't actually connect to my wireless network, it just sits there loading then after a minute or so it will disconnect.
I have no idea why as it performed great through the install with downloading updates from the internet..
Any help would be appreciated
Cheers,

---

### Post by wildmanne39 on 2011-12-18
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

