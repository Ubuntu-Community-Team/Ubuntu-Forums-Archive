---
title: "Seemingly random freezing (Possibly graphics related)"
date: 2009-12-19
forum: General Help
---

### Post by Nubsy on 2009-12-19
Hey

So, I'm running Karmic (32bit). When using the comp normally, nothing intensive, it seems to randomly lock up. This isn't a 100% Cpu lockup, this is a mouse moves, nothing responds except alt-sysrq+R+E+I+S+U+B lockup.

lspci | grep VGA put out:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

I know ubuntu has issues with intel i8xx and i9xx graphics. Am I right in assuming this freezing has to do with it? I mean, today alone, it has happened 4 times. Sometimes I go days without it happening.

Any help is appreciated- this is getting to be unacceptable.

thanks.

---

### Post by snowpine on 2009-12-19
I had a similar problem with Intel 945 integrated graphics, which I solved by disabling Compiz desktop effects. Not sure if it will work in your case, but it is an easy solution to try...

---

### Post by Nubsy on 2009-12-19
No go, I don't have compiz enabled... I've been using metacity's compositing. (I love AWN, hard to work without it. lol)
thanks though

---

### Post by Nubsy on 2009-12-19
bump...

---

### Post by Nubsy on 2009-12-19
Just did it again, froze up, had to reboot with magic keys.

---

### Post by doccpu on 2009-12-24
What are the magic keys? I am finding linux (and especially karmic) unusable. Had to "10 sec power down" twice in 30 minutes so rebooted in xp. It locks up leaving only mouse couldnt even open up the terminal window. Between upgrades from hell in karmic over other ubuntu's, lack of codecs and software, not able to make monitor changes in gui of 9.1 and the much slower response of linux gui's i keep having to use xp (yuck ms).

---

### Post by Nubsy on 2009-12-30
The magic keys are:
Alt + SysRq + R + E + I + S + U + B
It reboots the computer when it locks up like you described. (That sounds like what was happening to me) It makes sure all volumes are unmounted and processes have been terminated, and then reboots. Its better than just holding down the power button.

As for the problem I was having, downgrading to the Intel 2.4 graphic driver seems to have fixed the issue, hasn't frozen once in about a week. I have noticed performance is slightly slower, but if it doesn't freeze, I can live with it.

---

### Post by doccpu on 2009-12-30
do you hit the keys one at a time or hold the first 2, release and then type in reisub?  sounds like a prob with the intel 845's . I have one and its a prob even in windows. I am getting a new MOBO soon and will have a amd 215 x2 with integrated gforce 8100. gonna dual boot ubuntu and windoze7 (ack ack) gonna try to wean off windoze xp but its hard as it just works tho it gets slow and stupid quickly.(not so sure about 7)  And the writers of flash 10 should be whipped . eating cpu up whether its moving motion or not and 3 ads on a page eat 100% cpu.
stupid stupid stupid.

---

### Post by Andreas1 on 2009-12-31
Is your freezing related to the computer having been suspended before? Anyway, [this thread]("http://ubuntuforums.org/showthread.php?t=1309015") might be related, although i think that there are dozens of different bugs thrown together in there in the meantime. I have lost track of it myself since i stopped using ubuntu (because of it).

---

### Post by doccpu on 2009-12-31
what versions seem to work. Ubuntu soes have a nice way to get software dont have to find, then make then find depends then find current libraruies then blah blah then forget it.  I am really tired of ubuntus not working though so might go some op system on my new amdx2 215 system. but it may not be ubuntu till they quit screwing up a good thing.

---

### Post by robbielink on 2010-01-01
I'm curious about the "magic key" seqeunce, too. One at a time or all at once?

I've been having this same issue with onboard intel graphics chip in a Dell machine. Couldn't use 9.10 at all. Been running 9.04 but still occassional freeze-ups. Read about a bios setting I'm going to try tomorrow that some folks are having success with on Dell machines.

---

### Post by doccpu on 2010-01-01
tried to hold alt and hit sysreq. it brings up a take screen shot window. if type in reisub and hit enter it saves a screen shot called reisub.png but does little else.
so what am i supposed to be doing?

---

### Post by Nubsy on 2010-01-03
I don't know which alt you used, I had to use the left one. Press and hold alt + sysrq. While holding those two down, do REISUB one letter at a time. When you get to I think "I", the screen should go black.

---

### Post by robbielink on 2010-01-04
Confirming that only the left "alt" key works for me, too. I couldn't figure out why this wasn't working and it was because I was using the right "alt" key.
Hold down left alt and sysrq while typing one letter at a time pausing a few seconds between letters. A full descripton of all the possibilities here:
[http://en.wikipedia.org/wiki/Magic_SysRq_key]("http://en.wikipedia.org/wiki/Magic_SysRq_key")

---

### Post by doccpu on 2010-01-05
went to 
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

very nice so you hold alt+sysreq then hit each of the others with a wait.  bit tough  to do. hold down left alt with left pinkie and sysreq with right pinkie then hit the r e i s u b one at a time with other fingers i quess. will try it next time i am at a linux system. I have a machine running a cctv video surveilance siftware but its getting crashes in the vis and recorded over 9000 files of blank video. Argh it takes forever (over 5 minutes) to open up a browser window to see the files. I like the stability of linux but browsing files in linux is SLOW.

---

### Post by robbielink on 2010-01-05
I'm a musician so the fingering was easy... ;)

There are clearly a lot of stray issues with this version - the forums are peppered with problems seemingly related to graphic cards, sounds cards, I'm having a problem that looks like it's related to my modem but probably isn't (the "serial8250 too much work for irq17" issue). It's overwhelming trying to track down the causes of things that weren't issues in 8.04 or even 8.10 but I hate to go back. 
On the other hand - to get any work done just go back to 8.04 - it was stable and worked with most chips and cards. There are tons of problems on Karmic with certain Dell machnines (mine) and certain Intel video chips (mine) - search the forums - some fixes help (like on a Dell Dimension go into BIOS and legacy settings and increase video memory to 8 meg) a little but even then occasional freeze ups (Firefox, anybody?). It's a crazy time in Ubuntu land right now but I think it might be worth riding out.

---

