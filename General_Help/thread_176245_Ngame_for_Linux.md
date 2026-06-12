---
title: "Ngame for Linux"
date: 2006-05-14
forum: General Help
---

### Post by berwickboy on 2006-05-14
Hi, there was a game i used to play on my windows PC called Ngame and its really addictive and fun.. Well on their site there is a link to download Ngame for Linux. When i download it and extract it i dont know what to play it with. Can anyone help? Thanks in advance. Below are some links around the N website.

[Their Homepage](http://www.harveycartel.org/metanet/)
[Download is located on this page](http://www.harveycartel.org/metanet/downloads.html)

Its a flash game i think.. but im not sure how to find the extention of the file to post it could be *.SWF or *.EXE... I dont see how it could be exe if its a linux file? but when i go to properties it says that it is an executable file. Please help and if any more info is needed just ask. Thanks.

-John

---

### Post by jonnymccullagh on 2006-05-14
I took a look at that for you.
I downloaded the Linux version and extracted it. It contains several files but the important one is an executable file called n_v14
Because it is executable I took a chance at double-clicking on it but nothing happened.
So I opened up a shell console and went to the directory I had extracted it into e.g. ```
cd /home/jonny/thegame
```
I then tried executing the game e.g. 
```
./n_v14
```
I got an error message saying:
```
./n_v14: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

That told me that I needed some other library so I opened Synaptic and searched for libstdc and got a list of libraries - I ticked the libstdc++2.10 and installed it.
I then tried running n_v14 again and it worked.
I could now double-click it to play it or add a link from my K menu.

I'm no expert but hopefully you will have learnt a few things from this?
jonny

p.s. it doesn't look that good of a game!

---

### Post by Dryer Lint on 2006-05-15
Doen't let the GFX fool you, it's a great and very challenging game!

If you like tough platform games you should give it a try.

---

### Post by berwickboy on 2006-05-15
Okay, thanks jonnymccullagh, but i have another problem. It works but is really laggy/glitchy on windows its really smooth. When i play the replay its smooth but when playing the actual game its bad. Any ideas?

-John

---

### Post by GeneralZod on 2006-05-15
[QUOTE=berwickboy]Okay, thanks jonnymccullagh, but i have another problem. It works but is really laggy/glitchy on windows its really smooth. When i play the replay its smooth but when playing the actual game its bad. Any ideas?

-John[/QUOTE]

If you read the README file that comes with the Linux version, you'll see that there are problems caused by Macromedia's Flash Linux port to do with the sound (Flash keeps opening and closing thesound device needlessly, causing horrible performance problems).  I think it gives some steps that may help remedy the problem, but I just gave up, personally.  It's a shame they don't open-source the (free) game, but oh well :)

---

### Post by berwickboy on 2006-05-15
Ah i see, well that's really annoying. I hope they do something better for Ngame in the future as i need it smooth but i prefer Linux than Ngame i can play it at school if i must even though i leave on friday.. Cheers for the help though guys.

-John

---

### Post by cardinals_fan on 2008-01-31
You've probably forgotten this thread by now, but I solved this problem.  Create a user (call it whatever you want - here it will be ninja).  Do NOT give them audio permissions.  Then install sux  (sudo aptitude install sux) and run ```
 sux ninja /wherever/your/ninja/executable/is 
```
I got most of this [[COLOR="Blue"]_here_[/COLOR]]("http://metanet.2.forumer.com/a/stickiness-in-linux-due-to-sound-in-flash_post2593.html").

---

### Post by aliciapg on 2008-02-17
Okay, I'm having the same problem, except mine isn't as easy to fix.... I've tried loading libstdc++2.10...but it didn't exactly work... Plus when I typed all that other stuff in, it told me permission was denied...help?

---

### Post by cardinals_fan on 2008-02-18
> **aliciapg said:**
> Okay, I'm having the same problem, except mine isn't as easy to fix.... I've tried loading libstdc++2.10...but it didn't exactly work... Plus when I typed all that other stuff in, it told me permission was denied...help?

What exactly is the problem?  What doesn't work?

---

### Post by Z.V on 2008-06-27
Hey Guys! 

Just to let you know, I had these problems with N under Linux too, so about a year ago I created an unofficial version that uses the latest Flash player (player 9). The game is identical to the original, except that it works out of the box under the latest linux distros (including Ubuntu), uses GTK2 (so it looks much better) and a ton of other fixes. 

If you are interested in giving it a go, you can find it [here]("http://www.ziva-vatra.com/index.php?aid=24&id=U29mdHdhcmU=")

It should be a lot easier to run than the official version, just download and click on the file (and let me know how it turns out).

Thanks! :)

---

### Post by cardinals_fan on 2008-06-27
> **Z.V said:**
> Hey Guys! 

Just to let you know, I had these problems with N under Linux too, so about a year ago I created an unofficial version that uses the latest Flash player (player 9). The game is identical to the original, except that it works out of the box under the latest linux distros (including Ubuntu), uses GTK2 (so it looks much better) and a ton of other fixes. 

If you are interested in giving it a go, you can find it [here]("http://www.ziva-vatra.com/index.php?aid=24&id=U29mdHdhcmU=")

It should be a lot easier to run than the official version, just download and click on the file (and let me know how it turns out).

Thanks! :)
Wow, thanks!  That works flawlessly here on Slackware 12!

---

### Post by Ng Oon-Ee on 2008-06-29
Ah, downloaded this but it doesn't detect any of my keypresses at all (i literally tried every key in frustration :().

I've got limited understanding of these things, but would I be correct in surmising that you've packaged flash player into the executable binary and its not affected by the flash plugin I have in my computer at all?

Thanks anyway for this, good effort, unfortunately doesn't work for my setup....

---

### Post by Z.V on 2008-07-06
> **Ng Oon-Ee said:**
> Ah, downloaded this but it doesn't detect any of my keypresses at all (i literally tried every key in frustration :().


Strange, first time I heard of that issue, it might be something to do with window focus. After running the game, try clicking on the applications toolbar on the top then using the keyboard. 
  
> 
I've got limited understanding of these things, but would I be correct in surmising that you've packaged flash player into the executable binary and its not affected by the flash plugin I have in my computer at all?


Yes, the flash player is a binary package, and should not interfere with your flash plugin at all (at least I don't see why it would interfere). 

So far it has been tested on Ubuntu Feisty, Arch linux, Debian, Gentoo and Slackware with no issues, so I don't see why it would not work for you. Are you using the default window manager (Gnome) or something else?

---

### Post by Ng Oon-Ee on 2008-07-06
Hey, thanks for replying =).

> **Z.V said:**
> Strange, first time I heard of that issue, it might be something to do with window focus. After running the game, try clicking on the applications toolbar on the top then using the keyboard. 

The window does have focus, there's one key I pressed (F10 if I'm not wrong) which brings up the window menu, and my arrow keys can navigate in that menu no problem.

> **Z.V said:**
> Yes, the flash player is a binary package, and should not interfere with your flash plugin at all (at least I don't see why it would interfere). 

So far it has been tested on Ubuntu Feisty, Arch linux, Debian, Gentoo and Slackware with no issues, so I don't see why it would not work for you. Are you using the default window manager (Gnome) or something else?

I'm on Ubuntu Hardy, using Compiz's window manager (is it called Compize, or Metacity or something?). I apologize as I'm in the office now, but maybe tonight I'll get to checking it with Compiz turned off.

---

