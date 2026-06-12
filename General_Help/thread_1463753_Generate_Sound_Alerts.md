---
title: "Generate Sound Alerts?"
date: 2010-04-27
forum: General Help
---

### Post by gk_manutd on 2010-04-27
Hello All,

1) How do I generate sound alerts if I'm running a long script and it needs my attention?

2) Also, is there any way in which I can just make the script answer 'Y' for me whenever it prompts me (if I'm installing stuff using the script) ?


For example:

If my script is installing miro:

sudo aptitude install miro

then it will tell me the amount of disk space that will be used, and ask me if it should continue Y/N...

I want it to say Y without me having to pay attention to it.



Thanks, as always!

---

### Post by StuartN on 2010-04-27
> **gk_manutd said:**
> 1) How do I generate sound alerts if I'm running a long script and it needs my attention?

You can run the command **printf "\a"** to make a beep, or install the package beep for more variety, or run the command **mplayer mybeep.mp3** to play your own beep sound.

---

### Post by gk_manutd on 2010-04-27
> **StuartN said:**
> You can run the command **printf "\a"** to make a beep, or install the package beep for more variety, or run the command **mplayer mybeep.mp3** to play your own beep sound.


I tried **printf "\a". **It didn't work.

The beep package was a good idea. But this still does not tell me how I could generate a sound alert when the shell/system needs my attention.

At most, I could do something like:

sudo aptitude install miro && beep

This would wait for miro to get installed and then beep.

---

### Post by towheedm on 2010-04-28
> **gk_manutd said:**
> But this still does not tell me how I could generate a sound alert when the shell/system needs my attention.

To have the system generate alerts, you need to enable sound effects in sound preferences.  However, if you would like to generate your own alerts from your script, for example, to sound the system bell when it asks a question, you can use the **[COLOR=Red]canberra-gtk-play[/COLOR]** function from the libcanberra library. To sound the system bell:

```
canberra-gtk-play --id="bell"
```For a tutorial on using the **[COLOR=Red]canberra-gtk-play[/COLOR]** function check out the link at the beginning of this post:

[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

It starts on page 41 of the pdf file.

Hope this helps.

---

### Post by gk_manutd on 2010-04-29
Hi... I tried the canberra libraries... but they don't seem to work for Lucid Lynx?

Even the GNOME System Ready sound refuses to play.

---

### Post by gk_manutd on 2010-04-29
I think there's a problem with canberra-gtk play in lucid? 

That is what it says here: [http://ubuntuforums.org/archive/index.php/t-1418217.html](http://ubuntuforums.org/archive/index.php/t-1418217.html)

But my Login sound works just fine. :confused:

That needs canberra, right?

---

### Post by kostkon on 2010-04-29
You could just use aplay (or paplay) with your favorite alert sound (mp3 or wav) :P

---

### Post by towheedm on 2010-04-29
> **gk_manutd said:**
> I think there's a problem with canberra-gtk play in lucid? 

That is what it says here: [http://ubuntuforums.org/archive/index.php/t-1418217.html](http://ubuntuforums.org/archive/index.php/t-1418217.html)

But my Login sound works just fine. :confused:

That needs canberra, right?

I just tried it on Lucid and it works fine for me  Even the GNOME System Ready Sound works.    I'm running Lucid in VMWare vmplayer.  Try completely removing the libcanberra libary and all of its dependencies and then re-installing.  Did you upgrade to Lucid or did a clean install?

Just looked at the bug report.  The line:
[B]ProcCmdline: /usr/bin/canberra-gtk-play --id=desktop-login --description=GNOME\ Login
[/B]has a syntax error, desktop-login is a string value and must be wrapped in quotes ie: --id="desktop-login" and not [COLOR=Red]--id=desktop-login.[/COLOR]

Did you put in the quotation marks?

---

### Post by amsterdamharu on 2010-04-29
If you're looking for a way to have the script run automatically without the need of user input you could add the -y parameter (for many commands that works)

```
sudo aptitude install -y miro
```

---

### Post by gk_manutd on 2010-04-29
> **amsterdamharu said:**
> If you're looking for a way to have the script run automatically without the need of user input you could add the -y parameter (for many commands that works)

```
sudo aptitude install -y miro
```


Thanks! This is EXACTLY what I was looking for- I'm a noob, so I didn't know how to do that.   :P

---

### Post by gk_manutd on 2010-04-29
> **towheedm said:**
> Try completely removing the libcanberra libary and all of its dependencies and then re-installing.  Did you upgrade to Lucid or did a clean install?

Just looked at the bug report.  The line:
[B]ProcCmdline: /usr/bin/canberra-gtk-play --id=desktop-login --description=GNOME\ Login
[/B]has a syntax error, desktop-login is a string value and must be wrapped in quotes ie: --id="desktop-login" and not [COLOR=Red]--id=desktop-login.[/COLOR]

Did you put in the quotation marks?


I did a clean install. 

Yes, I did put the quotation marks. I'll try reinstalling it- thanks!

---

### Post by gk_manutd on 2010-04-30
> **kostkon said:**
> You could just use aplay (or paplay) with your favorite alert sound (mp3 or wav) :P


The problem with that is that I would have to PLAY it. If it is a script, then it might need authentication (sudo).

I can't do 

sudo aptitude install miro && aplay xxx.mp3   because it would wait for authentication or a Y, and would play music only after it is done with the first command.

But, I did try out what you said (I didn't know about aplay before), and it is giving me a horrible, static. Do you know why that might happen?

---

