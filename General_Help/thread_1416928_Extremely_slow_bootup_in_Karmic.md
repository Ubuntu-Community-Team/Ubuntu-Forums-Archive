---
title: "Extremely slow bootup in Karmic"
date: 2010-02-26
forum: General Help
---

### Post by VikingMetalGod on 2010-02-26
I know this has technically been posted but I think my situation is a bit different. People have been complaining that karmic is slower to boot. But from what I gather, it's only a few seconds extra due to an extra splash screen. I'm running Ubuntu Studio and mine takes like 5 minutes and is showing me 3 splash screens! 2 for regular Ubuntu and 1 for studio, which is the most sluggish of the three. I'm a newbie so go easy on me here, lol.

My computer is a Toshiba Satellite A75
2.8 ghz pentium M
1.5 gb ram
Radeon graphics
60gb hdd

EDIT: Also, recovering from hibernate takes a few min. Related?

---

### Post by VikingMetalGod on 2010-02-26
bump? :-(

---

### Post by Johnny B on 2010-02-26
try bootchart
[http://www.linux.com/archive/feed/151496](http://www.linux.com/archive/feed/151496)

---

### Post by NefariousNobo on 2010-02-26
That is probably just because Ubuntu is extremely bloated, as a Linux it is so bloated that it can be slower than Windows at times. I recommend you switch to Debian if the boot is taking far too long for you. If you can manage with these boots, then stick with Ubaontu.

---

### Post by nerdopolis on 2010-02-26
Your RAM and CPU specs seem fine.

It *could* be an under-performing hard drive.

to determine the speed of your hard disk copy and paste the command I have below in the code field into a terminal.

run it exactly as I have it below, because if you specify the wrong option to hdparam, it can do some nasty things to the data on your drive... 
```
 sudo hdparm -t /dev/sda 
```
Post the output of the command here. it should look somewhat like this.
```


/dev/sda:
 Timing buffered disk reads:  104 MB in  3.02 seconds =  34.41 MB/sec


```


Oh. Just a word of caution: If you use bootchart to analyze your system start up times, as soon as you are done using bootchart uninstall it, because bootchart will fill your disk with  2mb files or so every boot. (and that adds up)

---

### Post by VikingMetalGod on 2010-02-27
Thanks for the responses! I tried the easiest thing first, so here's my output from the hdparm command:

/dev/sda:
 Timing buffered disk reads:   80 MB in  3.06 seconds =  26.11 MB/sec

Also, I noticed that sometimes it seems to freeze on the actual ubuntu studio splash. The hard drive light is lit but it doesn't seem to be running. When this happens the screen starts to look all mixed up and glitchy. Doesn't happen every time. I also didn't notice any difference between booting with a regular kernel or the real time one. I hope that info is useful :)

I'll take a look at the bootchart thing next.

---

### Post by VikingMetalGod on 2010-02-27
After many failed attempts to boot (kept freezing on the first Ubuntu Studio splash screen), I managed to get a bootchart log. It says it only took about 1:40 but i timed it about 3 min. Anyway I attached the log if anyone is interested.

---

### Post by nerdopolis on 2010-02-27
Bootchart only times from the time after grub starts loading your OS to approximately the time. that the cursor appears on the screen, so thats probably why its measurement reports its quicker.

I can't really read the text on that bootchart as its too small (probably because you had to fit it within the max upload size for the forum), but I can see on the first top bar,which measures CPU usage, there is a lot of grey, which means its waiting for the data from the disk (if there was more blue, then that means a higher CPU usage),

The second bar from the top, measures the disk usage. the more grey in that bar means the harder the disk is being used, and your bootchart reports a high amount of disk usage.

The yellow line in that bar means how much data is actually being read from the disk at a time. The more the disk is being used, there usually should be more data being read from the disk, but by the looks of your bootchart, you hard disk at points is being used heavily, and it doesnt seem to be reading much data. 

Your hdparam value is also about 8MB smaller then my 5400 RPM IDE drive... (which is not the newest of technology, but you at that speed you probably have a 4200 rpm drive)

How long have you had this paticular install, and how long has it been slow?


EDIT: I missed the part in your post where you said that your hard drive lights up, and doesn't seem to be running. I think your hard drive might be failing, if thats the case.

---

### Post by VikingMetalGod on 2010-02-28
This install is actually not even a week old and has been slow the whole time. This actually used to be my windows computer and my other laptop was my linux one. With windows XP it was perfect. I switched them because I was having big problems with sound and the live kernal wouldn't load (i've been told that the geforce graphics were to blame). But I digress, Seeing as how the bootup is so tempermental, I would agree that the hdd is the problem. Another clue to this was that recently I noticed the hard drive was making that clicking noise. The same sound I hear when I have to force the computer to shut down. Well, I guess I'll see what happens when I stick another hard drive into it. Thanks guys for your advice!:)

---

