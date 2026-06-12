---
title: "How to installl xsublim?"
date: 2009-09-24
forum: General Help
---

### Post by DouglasCaixeta on 2009-09-24
Hi. I would like to use the program XSublim ([http://www.issp.u-tokyo.ac.jp/super/manual/system-b/Altix_command_manual/xsublim.htm](http://www.issp.u-tokyo.ac.jp/super/manual/system-b/Altix_command_manual/xsublim.htm)).

I searched already but I can't find the official page or the files to download. This program is not on the repositories.

There is a few pages talking about it. Do you know another similar program that I could use?

Thanks for the replies.

---

### Post by DouglasCaixeta on 2009-09-28
Nothing? Noone use xsublim?

---

### Post by kane77 on 2009-10-30
> **DouglasCaixeta said:**
> Nothing? Noone use xsublim?

I would be interested too.. In Jaunty xsublim was part of xscreensaver-data-extra package, but it is not there anymore..

---

### Post by buddhaflow on 2010-03-16
Yeah, one more vote for this not being removed. Even if it's hard to use...I have been using a Win32 program in WINE, and it murders my system performance. keep xsublim!

---

### Post by saradeeuk on 2010-06-16
Hmmm.. this is not good... about 3 years and NO ONE can help? is it beneath people or something? lol

I would dearly like to use ubuntu all the time and its so close to perfection... but i think ill have to go back to xp for a while as xsublim seems to be the only way to use subliminal messages on ubuntu and i NEED to quit smoking and really could use the extra help that they would provide me (Ive used them in the past to loose weight... from 28 stone to under 16 now, so even if it is psychosomatic... it works for me)...

Please would someone deign to respond as to a) how to get xsublim installed... and b) how you actually set it up and use it!

Thanks in advance! x

---

### Post by alpharesearch on 2010-07-16
I contacted Greg Knauss (the original author of xsublim) and asked him for the source code... he pointed me a the last xscreensaver version that included his program - I striped the source of xsublim out of xscreensaver added a new build environment and put it here:
[https://launchpad.net/xsublim](https://launchpad.net/xsublim)

Than I created all the Debian stuff and created some DEBs:
[https://launchpad.net/~schulz-alpharesearch/+archive/xsublim](https://launchpad.net/~schulz-alpharesearch/+archive/xsublim)

Regards,
Markus Schulz

PS: I changed all the default negative messaged to positive.
PPS: There will be some more changes soon, like display whole sentiences. A new --help option is already included. And all the options use -- now.
PPPS: Looks like sometimes with compiz runnig it is not displaying - but this is intermittent and I'm not sure what's going on yet.

---

### Post by jimfl on 2010-08-25
[SIZE=2]I would love to get this program, but after following the instructions on [https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html), I got this message:

Failed to fetch [http://ppa.launchpad.net/schulz-alpharesearch/xsublim/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/schulz-alpharesearch/xsublim/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

Jim[/SIZE]

---

### Post by alpharesearch on 2010-08-25
Please try thoses commands in your terminal window:
sudo add-apt-repository ppa:schulz-alpharesearch/xsublim
sudo apt-get update
sudo apt-get install xsublim
Regards,
Markus Schulz

---

### Post by jimfl on 2010-09-09
[SIZE=2]Thanks, Markus, but after running this command
   sudo apt-get install xsublim
I get this message:
   E: Couldn't find package xsublim

I'm running Ubuntu 9.10 and will be upgrading to 10.10 next month, if that makes a difference.[/SIZE] 

Jim

---

### Post by alpharesearch on 2010-09-09
> **jimfl said:**
> [SIZE=2]Thanks, Markus, but after running this command
   sudo apt-get install xsublim
I get this message:
   E: Couldn't find package xsublim

I'm running Ubuntu 9.10 and will be upgrading to 10.10 next month, if that makes a difference.[/SIZE] 

Jim

There are only packages for 10.04 and 10.10 - you could try to download the 10.04 deb file and and use dpkg to force a install (I guess it could work)...

Regards,
Markus

---

### Post by confused_user on 2010-10-11
just wanted to say thanks for this

thanks!

---

### Post by jimfl on 2010-10-20
Okay, I upgraded to Ubuntu 10.10, then successfully downloaded and installed xsublim. When I run it (Alt-F2), it flashes something periodically on the screen. BUT, I can't find out how to access the program to change the message to something of my choosing. Please help.

Thanks,
Jim

---

### Post by Mrokii on 2010-10-27
@Jim

you should use the Terminal (found in Ubuntu's main menu "Applications/Accessories") to test the available options. There, if you use this command:

```
xsublim --help
```

you'll see all the options. I've only tested a few of them, yet. To see the "built-in" messages you should type

```
xsublim --delayShow 4000000 --no-random
```

If you want to use your own messages, you have to create a textfile (with gedit for example). For testing purposes you can create a file named "xsublim.txt" and put it into your home directory. Put this text in:

```
One
Two
Three
```

With the file "xsublim.txt" saved in the home-directory, you can test it with this command:

```
xsublim --delayShow 4000000 --file ~/xsublim.txt
```

Then you should see the three messages flashing randomly. Actually, they're shown a little longer :)
Now just change the text in the textfile to what you like. If it's working the way you want, you can run xsublim again with just the file-option:

```
xsublim --file ~/xsublim.txt
```

Final note: If you want xsublim being started automatically at startup, you should probably add it to "Startup-Applications"-Preferences (found in Ubuntus' System-menu).

---

### Post by jimfl on 2010-11-07
Thanks so much, Mrokii. Everything you detailed worked perfectly.:smile:  I have only one (and I hope final) problem. The font size works fine at my monitor's highest resolution (1280x1024). Unfortunately, this resolution is way too small for me to use. I have to set my resolution to 832x624 to make things readable. At this resolution, only two or three words of my affirmations fit on the screen. In the list of program options, I see where you can change the font but nothing for the font size. 

Any help would be greatly appreciated.

Jim

---

### Post by alpharesearch on 2010-11-07
> **jimfl said:**
>  In the list of program options, I see where you can change the font but nothing for the font size. 

Any help would be greatly appreciated.

Jim

I suggest to use the xlsfonts command to see a list of fonts with size you can use:

...
lucidasanstypewriter-bold-12
lucidasanstypewriter-bold-12
lucidasanstypewriter-bold-14
lucidasanstypewriter-bold-14
lucidasanstypewriter-bold-14
lucidasanstypewriter-bold-14
lucidasanstypewriter-bold-18
lucidasanstypewriter-bold-18
lucidasanstypewriter-bold-18
lucidasanstypewriter-bold-18
lucidasanstypewriter-bold-24
lucidasanstypewriter-bold-24
lucidasanstypewriter-bold-24
lucidasanstypewriter-bold-24
lucidasanstypewriter-bold-8
...

xsublim --delayShow 500000 --font lucidasanstypewriter-bold-24
or 
xsublim --delayShow 500000 --font lucidasanstypewriter-bold-8

Regards,
Markus Schulz

---

### Post by jimfl on 2010-11-10
WOW. I've got it working perfectly now in just the right size font. Thank you so much for your help, Markus. Guess I'll have to dedicate all my subliminal self-improvement to you!:smile:

Jim

---

