---
title: "Computer Randomly goes to weird screen and stops working."
date: 2010-12-03
forum: General Help
---

### Post by Nicksth on 2010-12-03
Okay I am new to Linux and this forum, so I apologize If my question is stupid or I am asking in the wrong place or anything like that, I tried to understand the Tutorials, but I am only human:D Oh and I am not a native speaker of English, So I also apologize for that...
Okay enough apologizing, I will assume that you are all nice people and wouldn't have made fun of my stupidity anyway:D
As I said I am new to Linux and also to my PC. I bought it a couple of weeks ago and I tried to install Windows on it, but it was displayed in only 16 colors ( I assume this is not connected to my current problem but it might be...) and I couldn't fix that so I installed Ubuntu 10.4.something( It asked me if I wanted to upgrade to the newest version...) . Since then I have been really happy, I only had minor problem with the chat software but after I googled it I found a solution and I even used the console for the first time in my life.
The problem with the chat software is back now, but I don't care about that. 
My Computer randomly stops working and the screen goes all weird. It switches between a mix of white and black bars, something really colorful and a black screen with text ( I have the feeling it's different text every time) I am not sure what happens after that, because I always turn it off and restart it. It won't react to anything when it is in this weird mode. I don't think there are any special situations in which it happens and I can't reproduce it, it just happens when I don't want it to happen. A friend who uses Linux said it might be a temperature problem, he only knew what I just told you. I am not sure if there is a connection between the time the computer has been on and the time it shuts off...
I really like Linux and I would love to use it without it dying all the time:D
Oh when I said that I got my PC new ( it was used though:D) I was trying to say that I don't know whether this is a Ubuntu problem or not...
I never used it on any other system...
I hope you guys are able to help me!

With Penguin Greetings( is that Linux correct Terminology?)

Nicksth

---

### Post by sikander3786 on 2010-12-03
Welcome to the forums :popcorn:

Your post was quite entertaining believe me :-)

We need to know more about your hardware. RAM, graphics card etc. Did you install any graphics drivers?

Go to Applications > Accessories > Terminal and paste these commands. Copy/paste the output back here.

```
lspci | grep VGA
```

```
lsb_release -a
```

```
free
```

---

### Post by Nicksth on 2010-12-03
I am glad I was able to entertain you:D

Hear the first one:
nick@nick-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)


The second one:
nick@nick-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid

The last one:
nick@nick-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        501180     459656      41524          0      31944     166332
-/+ buffers/cache:     261380     239800
Swap:      1469908      59636    1410272
Is this a list of how my memory is used, because it looks like it:D

I didn't install any drivers. Just what Ubuntu installed for me...

I hope this helps you to help me

Nicksth

---

### Post by sikander3786 on 2010-12-03
Yes the last one was regarding your RAM. I am a little bit concerned about the amount of RAM. 512MB feels average RAM. It would definitely improve performance if you can manage to add another 512MB.

I would just recommend to try and reconfigure your graphics.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Ubuntu already contains the drivers for Intel cards by default so no big deal there.

If Windows encountered a problem and used to run in 16-bit colours only, there might be a problem with your graphics chip. And it might be overheating as your friend already suggested.

I don't know of any temperature probing software for Linux. Hopefully there are many and someone may suggest you later.

You can also feel the heat on the graphics chip by touching it with your finger. **Be cautious** though. Make sure to disconnect the power plugs and don't touch anything metallic in there. Compare its temperature with other chips on the board and you may know the difference. Do it as soon as the graphics problem arises again (if you plan to).

---

### Post by Nicksth on 2010-12-03
nick@nick-desktop:~$ sudo dpkg-reconfigure -phig xserver-xorg
debconf: Ignoriere ungültige Priorität „hig“
debconf: Gültige Prioritäten sind: low medium high critical

So I copied what you said to copy and he told me that "hig" is not a valid priority ( My system is german so I am just translating what I see above) and that high is one
so I just replaced hig with high ( I assume you forgot the h?:D):
nick@nick-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
and nothing happened, is that normal? 

So you are suggesting I disconnect the power and open the PC the next time this happens and look if the graphics chip is warmer than other chips?
How do I know which one it is?

---

### Post by sikander3786 on 2010-12-03
Yes that was phigh and not phig. My bad :-k

And yes, if successful, it shouldn't return any output. Now you need to test your computer for the next couple of days or may be hours or may be minutes, until the problem appears again :-)

Yes you can check the graphics chip for overheating if you feel confident. It would be labelled intel something and might be the biggest or the second biggest chip on the board. No more clues ;-)

Don't open your PC if you don't feel confident. Instead, search for a temperature probe software.

---

### Post by Nicksth on 2010-12-03
So you are saying it might actually already be fixed? 
My computer has been running for over an hour now, without crashing, I think that isn't unusual yet though...
So I guess we will find out, the next time it crashes I will look for a software and if that is too hard I will probably take a look at it's inside:D

Thanks a lot so far!

---

### Post by Nicksth on 2010-12-03
Okay, so It just crashed again, I would say it was running for about 90 minutes, so it might have overheated...
First there is a purple screen with some weird colorful stuff in the middle.
Then there was a black screen with a little white "_" and after that there was a screen with the bottom half just black and the top half with black and white stripes. The stripes run vertically and are about 1 cm wide.
This screen took turns with the black screen until I turned it off and restarted. When I restarted it there were some weird terminal like error messages , but I assume that was just about the fact that I turned it of by switching of the power...
So the question is do the screens tell anyone anything, and where do I get a software to find out if this thing is overheating? and if it is actually overheating what do I do?

---

### Post by sikander3786 on 2010-12-03
If you can manage to obtain/borrow a PCI-E Graphics card and put it in there, it would be greatly helpful.

If you get one, put it in and switch your display to that one. If Ubuntu doesn't crash on that, definitely a problem with your integrated graphics chipset ;-)

Thats the best workaround coming to my mind at the moment.

---

### Post by Shenachie on 2011-02-07
I am having the same sor of issues though my screen goes white with regular thin black lines on a vertical axis. 

My out put from the questions above are:01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid

            total       used       free     shared    buffers     cached
Mem:        896916     488020     408896          0      32040     258288
-/+ buffers/cache:     197692     699224
Swap:      2624504          0    2624504


Any suggestions welcome

Pete

---

