---
title: "Flash uses 1 - 2 gb of ram. Is this possible to fix?"
date: 2012-07-12
forum: General Help
---

### Post by colobix on 2012-07-12
Hello. I use google chrome, and flash uses almost 2 gb ram in every dab where I have a flash video running.
Is this possible to fix?
And why does it use so much memory?

---

### Post by Redblade20XX on 2012-07-12
How do you know it's using 1gb? Post the output of,
```
top
```

- Red

---

### Post by colobix on 2012-07-12
can't copy from "top".
I was able to copy one of the Chrome line

24897 chris     20   0 1271m 193m  35m S   41  2.4  40:30.65 chrome             

Anyway, I use the task manager to see these things.
I have it shortcutted to Shift+CTRL+ESC like in windows.

Anyway, I assume you know how to fix this since you asked.
So do you know how to fix this?

Btw, the only think that takes more ram than flash is games in fullscreen.
And yes I do vacuum my pc clean.

I do not have this problem in windows, as I'm dual booting.
So I want to know what this is and how do I fix it?

---

### Post by colobix on 2012-07-14
bump

---

### Post by philinux on 2012-07-14
> **colobix said:**
> can't copy from "top".
I was able to copy one of the Chrome line

24897 chris     20   0 1271m 193m  35m S   41  2.4  40:30.65 chrome             

Anyway, I use the task manager to see these things.
I have it shortcutted to Shift+CTRL+ESC like in windows.

Anyway, I assume you know how to fix this since you asked.
So do you know how to fix this?

Btw, the only think that takes more ram than flash is games in fullscreen.
And yes I do vacuum my pc clean.

I do not have this problem in windows, as I'm dual booting.
So I want to know what this is and how do I fix it?

Get some flash going. Bring up top in terminal and screenshot the terminal window. Upload the screenshot.

---

### Post by pe7er on 2012-07-14
> **colobix said:**
> can't copy from "top".
I was able to copy one of the Chrome line

In the terminal can't you select some text and use SHIFT + CTRL + C to copy?

Workaround: direct the output to a file, like
```
top > mytopoutput.txt
```
and press CTRL + C to stop "top".

---

### Post by colobix on 2012-07-15
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3538 chris     20   0 2103m 386m  33m R   34  4.8 428:59.63 chrome             
32241 root      20   0  302m 148m  33m S   21  1.9 290:53.32 Xorg               
 2813 chris     20   0  386m  44m  11m S    6  0.6 120:18.81 compiz             
 9209 chris     20   0  953m 146m  35m S    5  1.8  18:31.20 chrome             
23282 chris     20   0  820m  75m  20m S    3  0.9  66:58.61 /usr/bin/deluge    
 8940 chris     20   0  982m 270m  33m S    2  3.4 159:49.53 chrome             
 2809 chris     20   0  377m 9732 3212 S    2  0.1  86:42.83 pulseaudio         
 1607 root      20   0 45304 1000  812 S    0  0.0   2:37.32 udisks-daemon      
 2402 chris     20   0 19492 1484  968 R    0  0.0   0:00.02 top                
 7147 chris     25   5 1058m 232m  19m S    0  2.9   0:30.53 chrome             
 7341 chris     20   0  283m  19m  14m S    0  0.2   0:11.78 chrome             
 9020 chris     20   0  864m  27m  12m S    0  0.3   1:56.15 chrome             
 9309 chris     25   5  982m 102m  18m S    0  1.3   4:13.95 chrome             
24153 chris     20   0  369m  16m  11m S    0  0.2   0:04.23 gnome-terminal     
25630 chris     25   5  885m  62m  19m S    0  0.8   0:24.56 chrome             
    1 root      20   0 24264 1772  920 S    0  0.0   0:03.57 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.71 kthreadd

---

### Post by colobix on 2012-07-16
Bump

---

### Post by Redblade20XX on 2012-07-16
> **colobix said:**
> Bump

Have you cleared out your chrome cache?

- Red

---

### Post by colobix on 2012-07-16
> **Redblade20XX said:**
> Have you cleared out your chrome cache?

- Red
I do that every once in awhile.
But like I said, it happens with java and games too.
So I really don't think it has anything to do with chrome.

---

### Post by colobix on 2012-07-18
Nautilus uses around 1 gb, and flash on tinychat uses 5 - 7 gb.
why is that, and how do I fix this?
I use google chrome in windows too, but windows is not that heavy at all.

---

### Post by colobix on 2012-07-19
bump

---

### Post by Lyfang on 2012-07-20
> **Lyfang said:**
> I have updated Adobe Flash Player on Chromium to version 11.3.31.103. See: [Re: Chromium Flash Pepper on precise, how?]("http://ubuntuforums.org/showpost.php?p=12072504&postcount=13")
Could you try the link above to install Pepper Flash on Chromium? Post the output after visiting chrome://plugins in the address bar.

---

### Post by colobix on 2012-07-25
> **Lyfang said:**
> Could you try the link above to install Pepper Flash on Chromium? Post the output after visiting chrome://plugins in the address bar.

I can't see it in chrome.
Also, I'm not using chromium.
But same software pretty much.

But it's not just flash. A lot of games and videos make my pc very noisy, and things will start to use between 2 and 9 GB of ram.
I have to restart the pc because it gets really slow, resource heavy and hot. This doesn't seem very normal.
Sometimes the pc turns itself off after 5 - 10 min when I play games.

---

### Post by colobix on 2012-07-26
bump

---

### Post by Lyfang on 2012-07-26
You could try LXDE, install from Terminal (at your own risk as usual):
```
sudo apt-get install lubuntu-desktop
```

I'm using Lubuntu 12.04 & Chromium 18 with Pepper Flash. You should be able to find Pepper Flash from Chrome (if installed) on Ubuntu from the Terminal:
```
nautilus /opt/google/chrome/PepperFlash/
```

I think that you should monitor your temperature. I would recommend lm-sensors, can be installed using Synaptic. Then run from the Terminal:
```
sudo sensors-detect
```

---

### Post by colobix on 2012-07-30
How can that help?
That's just a lighter environment.
It doesn't make the software less resource heavy or anything.
Besides, the problem is that they eat memory. Unusually much memory even.

---

### Post by Lyfang on 2012-07-30
Both the LXDE desktop environment & the Uzbl web browser are light-weight. I recommend for an advanced user: [How to install Debian 7 "Wheezy" testing with LXDE]("http://ubuntuforums.org/showthread.php?t=2016082")

---

### Post by QIII on 2012-07-30
Forgive me if I missed this, but are you by chance using an ATI graphics card?

---

### Post by colobix on 2012-08-05
> **QIII said:**
> Forgive me if I missed this, but are you by chance using an ATI graphics card?
No. Nvidia

---

### Post by Dylan1473 on 2012-08-05
Regarding using another desktop environment, it might be worth a shot. You don't need to make a permanent change, but the desktop environment can make a big difference sometimes. I remember a while ago I had Openbox installed and my entire computer crashed when I tried to use certain graphically intensive games or else they experienced serious graphical problems. I installed XFCE and I guess it installed some extra graphical libraries I needed or something because suddenly the problems stopped in all of my desktop environments. Anyway, my point is that it's not just a matter of lower system resources, you might find that the issues are indirectly tied to your desktop environment and it may assist in troubleshooting.

You might also try using a different web browser such as Firefox to see if the issue still occurs, though I doubt that will help in itself based on the fact that Nautilus is also having problems (I don't use Nautilus personally but I'm positive 1GB is way too much memory for it to be using).

---

### Post by colobix on 2012-08-13
A different web browser isn't gonna help much.
Flash, games, videos and so on will still use 1 gig of ram, heat up my pc and make it noisy.
Any actual solution, please?
And like I said, I don't have this problem in windows, so it can't be a hardware problem.

---

### Post by TenPlus1 on 2012-08-13
Your windows flash player uses DirectX to offload some of the cpu time to your graphics card and make things run cooler/smoother, this can be done in Ubuntu as well but it only works on certain graphics cards since Adobe isn't really updating the player anymore for linux...

You could try running a 2D desktop environment to help with the heat issues if any and keep the fan running a little quieter...  Also, making sure you have the latest driver for your graphics card may help also...

---

### Post by evilsoup on 2012-08-13
Can't help you with games, but for youtube videos you could try out the FlashVideoReplacer add-on for Firefox - it uses mplayer to show youtube videos. Unfortunately it doesn't work on videos embedded on other sites, and it doesn't work for certain videos even on the site (those with ads mostly), but for most videos it should reduce the heat/RAM usage to a reasonable level.

---

### Post by colobix on 2012-08-13
> **evilsoup said:**
> Can't help you with games, but for youtube videos you could try out the FlashVideoReplacer add-on for Firefox - it uses mplayer to show youtube videos. Unfortunately it doesn't work on videos embedded on other sites, and it doesn't work for certain videos even on the site (those with ads mostly), but for most videos it should reduce the heat/RAM usage to a reasonable level.

Thanks, but I don't use youtube.
I use hulu, southparkstudios and flash games.
But thanks.
I can't understand why things use so much more ram in linux than windows. It's ridiculously weird.

---

### Post by colobix on 2012-08-14
bump

---

### Post by Lyfang on 2012-08-15
Make shure you have hardware acceleration or GPU-acceleration turned on when using Flash Player. You could try to enable VDPAU. See also: [Getting flash hardware acceleration for nVidia]("http://ubuntuforums.org/showthread.php?t=1872979")

---

### Post by Lyfang on 2012-10-20
[QUOTE=Christopher Forster]Hi, Chromium used too much CPU usage with Pepper Flash. I don't know if the Pepper API has really had time to be tested in the real world? New technology may sometimes cause problems, consume more resources until extensive rigorous testing & until fine-tuning for the performance. I found Chromium had higher CPU usage than normal when playing an online game using Pepper Flash.[/QUOTE] - Source: [Chromium CPU usage high with Pepper Flash]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1029702") 

Are you using the latest stable version of Google Chrome? Google Chrome uses Pepper Flash.

---

