---
title: "URGENT- ubuntu has gone nuts"
date: 2010-05-24
forum: General Help
---

### Post by mrgreaper on 2010-05-24
ok i have a pc i run as a headless server box, i am not very linux minded so please treat me as a novice
details
The server pc was running ubuntu 9.10 desktop perfectly fine 
I use it for sickbeard, sabnzbd, file storage(use samba for the windows os`s to acess), mediatomb and use the growisofs(its actually more reliable then imgburn lol)
to access it i use ssh on my iphone or vnc on my winxp netbook

ok as i say on 9.10 all things worked, then i "upgraded" to 10.04 big mistake!

first glitch all my minimise maximise and the kiss of death (little cross) jumped to the left side of windows instead of the right, a minor thing but extremely annoying

second thing i noticed is it shuffled my hard drives about, took me 3 hours to find how to fix them with such useful posts found in google such as change your fstab..follwed by oh that worked ... when i found out finaly fstab was a text file in /ect/ and 
then what to do with it i was abble to set all my drives to uuids and they now work but why the hell did ubuntu 10.04 decide to shuffle them about ...?

then i found it couldnt shut down, i pluged a monitier into it and watched to see what happens, it closes all the windows and displays ubuntu and some dots animate after 5 minutes the dots stop and then nothing happens (left it for 30 minutes ....nothing) had to power it off by holding the power button)

vnc into it generated a black screen , for headless box thats a nightmere! i have to plug a mouse and keyboard into it lug the moniter over to it wave the mouse about put in the password (it never asked for before!) then i can vnc into it (defeats the purpose somewhat)

synaptic package manager stoped working, if i type synaptic into the terminal i get "segmentation fault"

firefox has stoped working same as above segmentation fault

loading ubuntu up now it tells me a load of gnome applets cant load do i want to delete them (since i only have the default needed applets i have said no lol) i am missing the stuff at the top right of the screen (username etc) on the plus side it now shuts down

so ummm HELP
i either need to fix this or need to convert it into a server ubuntu install (that uses less resources yes? but would allow me to stil do all i do do?)

---

### Post by mrgreaper on 2010-05-24
some extracts from the sys.log (all double dutch to me)

> May 24 13:08:54 alpha-omega polkitd[1505]: started daemon version 0.96 using authority implementation `local' version `0.96'
May 24 13:08:54 alpha-omega gnome-session[1405]: WARNING: Could not launch application '104e005cfdce66f6eb127430200495668500000013030033.desktop': Unable to start application: Failed to execute child process "evolution-exchange-storage" (No such file or directory)
May 24 13:08:54 alpha-omega kernel: [   35.679916] __ratelimit: 147 callbacks suppressed
May 24 13:08:54 alpha-omega kernel: [   35.679922] nm-applet[1507]: segfault at 1c4f ip 01056e21 sp bfc2e10c error 4 in libc-2.11.1.so[fdd000+153000]
May 24 13:08:54 alpha-omega rtkit-daemon[1501]: Sucessfully made thread 1499 of process 1499 (n/a) owned by '1000' high priority at nice level -11.
May 24 13:08:54 alpha-omega rtkit-daemon[1501]: Supervising 1 threads of 1 processes of 1 users.
May 24 13:08:55 alpha-omega rtkit-daemon[1501]: Sucessfully made thread 1558 of process 1499 (n/a) owned by '1000' RT at priority 5.
May 24 13:08:55 alpha-omega rtkit-daemon[1501]: Supervising 2 threads of 1 processes of 1 users.
May 24 13:08:55 alpha-omega rtkit-daemon[1501]: Sucessfully made thread 1560 of process 1499 (n/a) owned by '1000' RT at priority 5.
May 24 13:08:55 alpha-omega rtkit-daemon[1501]: Supervising 3 threads of 1 processes of 1 users.

> May 24 13:02:02 alpha-omega kernel: [42312.526202] gnome-screensav[9947]: segfault at 1c4f ip 03ee2e21 sp bfac227c error 4 in libc-2.11.1.so[3e69000+153000]
May 24 13:02:30 alpha-omega kernel: [42340.750773] gnome-screensav[9949]: segfault at 1c4f ip 00dd4e21 sp bfac8e1c error 4 in libc-2.11.1.so[d5b000+153000]
May 24 13:02:30 alpha-omega kernel: [42340.958427] gnome-screensav[9950]: segfault at 1c4f ip 014cfe21 sp bfc533ec error 4 in libc-2.11.1.so[1456000+153000]
May 24 13:02:31 alpha-omega kernel: [42341.142168] gnome-screensav[9951]: segfault at 1c4f ip 02a0de21 sp bff7918c error 4 in libc-2.11.1.so[2994000+153000]
May 24 13:02:39 alpha-omega kernel: [42349.995824] gnome-screensav[9952]: segfault at 1c4f ip 06db6e21 sp bf86adcc error 4 in libc-2.11.1.so[6d3d000+153000]
May 24 13:02:40 alpha-omega kernel: [42350.381557] gnome-screensav[9953]: segfault at 1c4f ip 04411e21 sp bfae8c5c error 4 in libc-2.11.1.so[4398000+153000]
May 24 13:02:41 alpha-omega kernel: [42351.781491] gnome-screensav[9954]: segfault at 1c4f ip 03d48e21 sp bfa1964c error 4 in libc-2.11.1.so[3ccf000+153000]
May 24 13:02:42 alpha-omega kernel: [42352.133770] gnome-screensav[9955]: segfault at 1c4f ip 017b6e21 sp bfd356ec error 4 in libc-2.11.1.so[173d000+153000]
May 24 13:02:42 alpha-omega kernel: [42352.565224] gnome-screensav[9956]: segfault at 1c4f ip 00fd1e21 sp bf89ec8c error 4 in libc-2.11.1.so[f58000+153000]
May 24 13:02:55 alpha-omega kernel: [42365.772738] gnome-screensav[9957]: segfault at 1c4f ip 0842de21 sp bf87508c error 4 in libc-2.11.1.so[83b4000+153000]
May 24 13:02:56 alpha-omega kernel: [42366.268641] gnome-screensav[9958]: segfault at 1c4f ip 00f26e21 sp bffce7fc error 4 in libc-2.11.1.so[ead000+153000]
May 24 13:02:57 alpha-omega kernel: [42367.679074] gnome-screensav[9959]: segfault at 1c4f ip 01060e21 sp bfe8b46c error 4 in libc-2.11.1.so[fe7000+153000]
May 24 13:03:41 alpha-omega kernel: [42411.230530] yelp[9972]: segfault at 1c4f ip 01022e21 sp b44550fc error 4 in libc-2.11.1.so[fa9000+153000]
May 24 13:04:49 alpha-omega kernel: [42479.598722] synaptic[9979]: segfault at 1c4f ip 05bdfe21 sp bfe4d0ec error 4 in libc-2.11.1.so[5b66000+153000]
May 24 13:05:51 alpha-omega kernel: [42541.513921] synaptic[10046]: segfault at 1c4f ip 01183e21 sp bfcec5cc error 4 in libc-2.11.1.so[110a000+153000]
May 24 13:06:57 alpha-omega kernel: [42607.211543] yelp[10057]: segfault at 1c4f ip 0100de21 sp b44fd0fc error 4 in libc-2.11.1.so[f94000+153000]
May 24 13:07:34 alpha-omega kernel: Kernel logging (proc) stopped.

theres more so i put it on a pastebin (hope theres nought i shouldnt show)
[http://pastebin.com/YdaYNQYM](http://pastebin.com/YdaYNQYM)

---

### Post by mrgreaper on 2010-05-24
due to time restraints i have not been able to fix it and am having to reinstall ubuntu, this is very very very annoying and will resault in loss of data for me (nothing that cant be replaced but still grrr) 
i would urge this to still be looked at and if someone can come up with a solution post it as it may help others also can a mod merger these 3 posts nto one please, edit seemed to not work for me

---

### Post by iponeverything on 2010-05-24
There was not even an hour between your first post and the time that you posted back saying that you are going to reinstall and lose your data. Too bad about your data, if had waited saving it would have been fairly trivial.

---

### Post by mrgreaper on 2010-05-24
> **iponeverything said:**
> There was not even an hour between your first post and the time that you posted back saying that you are going to reinstall and lose your data. Too bad about your data, if had waited saving it would have been fairly trivial.

i had a limited amount of time to fix the problem and get the sytem back up and running, i posted here so i could link people to it in irc and they could see all the details with out flooding the channel. no one online was able to help though soyo gave it a damn god try (again thank you) it was clear to me that too much had gone wrong and after a solid hour (felt like more to be honest) of trying suggestions and about 2 hours of google before i posted here i had to admit defeat and wipe the drive to do a reinstall, as it was it was a close call and managed to get most of what i need on the system before i went to work, the rest i can do over vnc (i hope) 

i did not give up lightly

the fresh version of 10.04 boots faster closes quicker and looks a lot nicer then the 10.04 i upgraded to from 9.10 so theres benefit to my data loss. though the min max and close icons are still on the wrong side of the windows, im guessing thats just a design choice...a damn stupid one, but meh only a problem when using my iphone to vnc into it and scrolling around the windows and ofcourse the fact it resenates wrongless when i see them

I would like to also point out that your post solved no purpose other then to point out my impaitence though im sure that wasnt your intention as that would be considered "trolling"

have a good night, i gotta go do some work

---

### Post by iponeverything on 2010-05-24
Wasn't trolling just trying to understand. 

Since you all had already reinstalled, I didn't think that there was any point in telling you how to move forward and not destroy your existing data.

It was just odd, you seemed bothered by losing you data and yet it didn't appear that you made a good faith effort in trying preserve it. I am not sure that spending an hour on IRC counts. 

Another thing that came to mind was the fact that you had good working system that was apparently, in some sense a production machine, and yet you went for the upgrade to 10.04 without giving yourself a back out plan. A casual searching of the forums would have revealed that an upgrade 10.04 is far from a sure thing. 

Still not troll, just a tisk, tisk..

---

### Post by mrgreaper on 2010-05-24
> **iponeverything said:**
> Wasn't trolling just trying to understand. 

Since you all had already reinstalled, I didn't think that there was any point in telling you how to move forward and not destroy your existing data.

It was just odd, you seemed bothered by losing you data and yet it didn't appear that you made a good faith effort in trying preserve it. I am not sure that spending an hour on IRC counts. 

Another thing that came to mind was the fact that you had good working system that was apparently, in some sense a production machine, and yet you went for the upgrade to 10.04 without giving yourself a back out plan. A casual searching of the forums would have revealed that an upgrade 10.04 is far from a sure thing. 

Still not troll, just a tisk, tisk..

ok granted i should of checked the forums before going ahead on the upgrade but i thought "hay they wouldnt of offered it if its not ready" lol 
the urgency was to preserve the way i had it setup i had samba set perfectly, the faffing i did in fstab the way sabnzbd worked, the scripts etc this was more important then the data, the lost data is a shame but livable with, everything i had time to back up was transfered to my secondary drive and saved all that was lost was a back up image of my ps3s hd some large beta files and a couple of mmorpg clients that wer stored there, all too large to quickly copy over and all a mere anoyance rather then a oooooo nooooeeessss lol

the other annoying stuff is the fact i had set it up with 3 ps3 eye cams so i could keep an eye on my cat when she had to wear a collar after an operation, it was a very hard thing to set up and though i no longer need it i knew the option was there should i need it again. wine was all set up and working great. 

its all stuff i can do again but couldnt really back up 


the annoying thing is i cant vnc into it at the moment with out having to run the command "tightvncserver" and my iphones battery is flat so i cant use that to ssh in and run the command, i do have windows xp but cmd dont seem to do the trick lol

[http://www.bitvise.com/download-area](http://www.bitvise.com/download-area) seems to do the trick of ssh from windows to ubuntu :)

---

### Post by shawncplus on 2010-08-23
> Too bad about your data, if had waited saving it would have been fairly trivial.

Well what exactly is this "trivial" fix because I'm running into the same issue.

Side Note: Don't makes those kinds of posts: "Hey, I fixed my problem, thanks *doesn't post fix*" or "Did you solve your issue because I know the solution *doesn't post solution*" They make googling for a fix unbelievably frustrating

---

### Post by JBAlaska on 2010-08-23
The way to avoid these problems with loosing data and configuration settings, could be easily avoided by:

1-**Make a separate HD partition for your /home folder.**
2-**Backup your home folder before any major upgrade.**

You can also save and restore your installed programs by doing:

**Save Packages list to your home folder:**
```
sudo dpkg --get-selections > mypackages.new
```

**Restore programs to Ubuntu:**
```
sudo dpkg --set-selections < mypackages.new && sudo apt-get dselect-upgrade
```

---

### Post by shawncplus on 2010-08-23
So is there a solution to the problem aside from "You're boned, reinstall"?

---

### Post by JBAlaska on 2010-08-23
What was the question again?

---

