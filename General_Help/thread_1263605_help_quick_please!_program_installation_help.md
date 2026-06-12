---
title: "help quick please! program installation help"
date: 2009-09-11
forum: General Help
---

### Post by mac666 on 2009-09-11
Hey
Im trying to install a program that i downloaded... its in a tar.bz2 file.
So what i did was:
Unpacked it
cd into the new dir
./configure - And lots and lots of text was outputed, no errors
then after the configure it told me to "make depend && make",
so thats what i did. After that i dont understand what to do, i get no errors or no program installed.... please help!
There is allso some ".sh" file about Install, but i just outputs lots and lots of text and tells me 0 to upgrade, 0 to install.

Please!

---

### Post by mac666 on 2009-09-11
BTW its a Wine Beta im trying to install...

---

### Post by TobiasV on 2009-09-11
I'm having a hard time understanding what exactly you're doing/have done. Would you mind linking to the file so I can have a look at it?

---

### Post by mac666 on 2009-09-11
[http://www.icewalkers.com/download/Wine/356/dld/](http://www.icewalkers.com/download/Wine/356/dld/)

This is where i downloaded it from... 
Thanks

---

### Post by P4man on 2009-09-11
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by akakingess on 2009-09-11
Usually, you direct yourself to the directory you unpacked from within the terminal and then do the following 3 commands seperately (one after the other)
```
sh ./configure
make install
make
```

I believe that is the routine although I am not in front of my Ubuntu machine at the moment, a quick search on google should give you the proper procedure.

---

### Post by mac666 on 2009-09-11
> **P4man said:**
> [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

their mirror is down...

i will try what you write....

---

### Post by TobiasV on 2009-09-11
I downloaded it now, and it does look pretty regular, so what akakingess says should work.

Though I would still suggest P4man's link (that's what I'm using).

---

### Post by mac666 on 2009-09-11
> **TobiasV said:**
> I downloaded it now, and it does look pretty regular, so what akakingess says should work.

Though I would still suggest P4man's link (that's what I'm using).

yeah but their mirror is down and i need the beta version :)

---

### Post by mac666 on 2009-09-11
OK i did what akakingess told me and i still dont have it installed ( what i can see )
When install it the "regular" way you get a Program > Wine shortcut... i dont have anything to run?

---

### Post by P4man on 2009-09-11
Indeed its down. Just wait a bit until its up, otherwise you're gonna get in to trouble trying to uninstall or upgrade wine with the next release.

---

### Post by TobiasV on 2009-09-11
Type in "wine" in your terminal - does that do anything?

If it doesn't, just leave it and wait for the mirror to get back up before you break something. :P

---

### Post by mac666 on 2009-09-11
> **TobiasV said:**
> Type in "wine" in your terminal - does that do anything?

If it doesn't, just leave it and wait for the mirror to get back up before you break something. :P

Its been down for weeks, cant wait much longer..!

It does print out
```
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
```

But i cant run my .msi files, as i could before :)

---

### Post by mac666 on 2009-09-11
EXE files works, but now .msi? 
hmm..?

---

### Post by TobiasV on 2009-09-11
Does wine --version display the version number you wanted to install?

---

### Post by P4man on 2009-09-11
well, I predict another "urgent please help" post in short order when you're gonna try to update wine but ok, to compile and install wine from source try:```

./configure
make
sudo make install
```

Dont blame me if you wreck your setup (again).

---

### Post by TobiasV on 2009-09-11
P4man IS right, you really should just wait.

The mirror can't be down for that long (and it hasn't been down for weeks as you stated, I used it yesterday. :S)

---

### Post by akakingess on 2009-09-11
> **P4man said:**
> well, I predict another "urgent please help" post in short order when you're gonna try to update wine but ok, to compile and install wine from source try:```

./configure
make
sudo make install
```Dont blame me if you wreck your setup (again).

Thanks for correcting me, I knew I would mess it up without being in front of one of my own machines;)  Best of luck, as I am about to have to sign off, may check back in a couple of hours.

---

### Post by TobiasV on 2009-09-11
> **akakingess said:**
> Thanks for correcting me, I knew I would mess it up without being in front of one of my own machines;)  Best of luck, as I am about to have to sign off, may check back in a couple of hours.

Jeez, I feel like such an idiot for not noticing the mistake, and thus suggesting that he'd use 'em.

---

### Post by P4man on 2009-09-11
> **TobiasV said:**
> Jeez, I feel like such an idiot for not noticing the mistake

There I was thinking you were being clever and doing the same as me to make the OP install from the repositories :)

---

### Post by TobiasV on 2009-09-11
> **P4man said:**
> There I was thinking you were being clever and doing the same as me to make the OP install from the repositories :)

Nah, I really was trying to help him. Anyway, I'm wondering how the hell he managed to install it with those commands... he shouldn't have permissions to do so. :S

---

### Post by P4man on 2009-09-11
Im pretty sure he didnt. He just compiled, but didn't install.
Which reminds me. **mac666** make sure you uninstall any existing wine version before trying this.

---

### Post by TobiasV on 2009-09-11
Well, he clearly has some version of Wine installed. And he's complaining about it not showing up in his menu, so I assume he didn't have one installed previously...

---

### Post by P4man on 2009-09-11
or he just ran wine from the compiled directory.. although that wouldnt be in his path, so .. oh well, we'll find out. (Or not, I guess mac666 is off reinstalling his ubuntu for the 85th time this week :p )

---

### Post by TobiasV on 2009-09-11
I'm considering reinstalling too... don't have anything important I'd lose, and maybe it'd fix my problems. :\

---

### Post by mac666 on 2009-09-11
> **P4man said:**
> Im pretty sure he didnt. He just compiled, but didn't install.
Which reminds me. **mac666** make sure you uninstall any existing wine version before trying this.

No problem mates... i made a clean ubuntu install just to be able to play some games thru beta wine,
but it works kinda great now!
Thanks

---

### Post by P4man on 2009-09-11
> **mac666 said:**
> No problem mates... i made a clean ubuntu install 


...as predicted :p
Oh well, if it works, so much the better :)

And I guess you dont have to worry about uninstalling wine before trying to upgrade, by then you'll have done half a dozen fresh install anyway :D

---

### Post by mac666 on 2009-09-11
how do i uninstall this piece of *gods work*?
Im on the brick of abandoning Ubuntu, all these hour i spent just to play a stupid windows game.

One problem after the other... :(

---

### Post by TobiasV on 2009-09-11
What exactly is it you want to uninstall? :S

---

### Post by P4man on 2009-09-11
> **mac666 said:**
> how do i uninstall this piece of *gods work*?
Im on the brick of abandoning Ubuntu, all these hour i spent just to play a stupid windows game.

One problem after the other... :(

If you only installed ubuntu to "play a stupid windows game" you wasted not just your own time..

---

### Post by mac666 on 2009-09-11
i want to uninstall the wine i installed...
I want to use ubuntu as my all day OS but i allso want to game at nights, after work... and i cant do this with ubuntu, even if i see lots of people playing without any problems, i get 100 problems for each step :S

EDIT:
I tried something like apt-get remove wine , and it removed something but i can still run open wine progams and i get lots of errors =), Windows errors....

---

### Post by oldos2er on 2009-09-11
Does this game have a name?

---

### Post by TobiasV on 2009-09-11
Try ```
sudo apt-get --purge wine
```...

---

