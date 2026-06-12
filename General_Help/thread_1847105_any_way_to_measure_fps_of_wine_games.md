---
title: "any way to measure fps of wine games"
date: 2011-09-20
forum: General Help
---

### Post by ddr3XD on 2011-09-20
Im want to measure the fps of my wine games but dont know how to. I've seen threads asking about this but none seem to be of any help. Does anyone know any way i can measure fps of my wine games?

Any help would be appreciated.

---

### Post by dino99 on 2011-09-20
hm, fps is about hardware graphic output not software

---

### Post by Toz on 2011-09-20
See:
[http://www.linuxquestions.org/questions/linux-software-2/how-can-i-measure-fps-in-wine-781321/]("http://www.linuxquestions.org/questions/linux-software-2/how-can-i-measure-fps-in-wine-781321/")

---

### Post by ddr3XD on 2011-09-20
> **Toz said:**
> See:
[http://www.linuxquestions.org/questions/linux-software-2/how-can-i-measure-fps-in-wine-781321/](http://www.linuxquestions.org/questions/linux-software-2/how-can-i-measure-fps-in-wine-781321/)

Thank You!!! :p

I also dug further and found out how to display fps onscreen by using osd_cat. To do this first get osd_cat by typing in the terminal
```
sudo apt-get install xosd-bin
```Then you can display fps onscreen by using this command
```
WINEDEBUG=fps wine [COLOR=Red]YOURGAME.exe[/COLOR] 2>&1 | tee /dev/stderr | grep --line-buffered "^trace:fps:" | osd_cat
```

---

### Post by ddr3XD on 2011-09-20
I did'nt know if I should have made a new thread for this since i already marked this thread as solved. So forgive me if i was suppose to do so. So anyways i got my fps counter working beautifully. I improved it further with the code below
```
WINEDEBUG=fps wine [COLOR=Red]YOURGAME.exe[/COLOR] 2>&1 | tee /dev/stderr | grep --line-buffered "^trace:fps:" | osd_cat --lines=1 --font="lucidasanstypewriter-bold-18" --color=yellow
```And now it almost looks like the Fraps OSD :). The only thing is that it outputs a bunch of other stuff along with the fps output, which im trying to take out and just output the actual FPS. So i tried to use the cut command like this:
```
WINEDEBUG=fps wine [COLOR=Red]YOURGAME.exe[/COLOR] 2>&1 | tee /dev/stderr | grep  --line-buffered "^trace:fps:" | [COLOR=DarkOrange]cut -c25-30[/COLOR] | osd_cat --lines=1  --font="lucidasanstypewriter-bold-18" --color=yellow
```but i get no output from osd_cat(well atleast until i exit the game then osd_cat flashes the output for slight second). Why is it doing this? What am i doing wrong?

---

### Post by Toz on 2011-09-20
After a bunch of trial and error (mostly error), I came upon this that seems to work:
```
WINEDEBUG=fps wine [COLOR="Red"]YOURGAME.exe[/COLOR] 2>&1 | tee /dev/stderr | sed -u -n -e '/trace/ s/.*approx //p' | osd_cat --lines=1 --font="lucidasanstypewriter-bold-18" --color=yellow
```

---

### Post by ddr3XD on 2011-09-20
> **toz said:**
> after a bunch of trial and error (mostly error), i came upon this that seems to work:
```
winedebug=fps wine [COLOR=red]yourgame.exe[/COLOR] 2>&1 | tee /dev/stderr | sed -u -n -e '/trace/ s/.*approx //p' | osd_cat --lines=1 --font="lucidasanstypewriter-bold-18" --color=yellow
```
Nice!!! =D>

[COLOR=Red]**Thank You**[/COLOR]

---

