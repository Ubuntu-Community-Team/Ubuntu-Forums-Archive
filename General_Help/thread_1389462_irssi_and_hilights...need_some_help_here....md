---
title: "irssi and hilights...need some help here..."
date: 2010-01-24
forum: General Help
---

### Post by YosefKaro on 2010-01-24
After nhandlers IRC session on ubuntu user days, I got inspired to check out irssi.  One thing that I am having trouble with is getting irssi to play an alert sound of some sort when my nick is highlighted.  I've tried this:

"/set beep_when_window_active ON"
                    "/set beep_when_away ON"
                    "/set beep_msg_level MSGS NOTICES DCC DCCMSGS  HILIGHT"
                    "/set bell_beeps ON" 

So I believe that I should get some kind of beep sound but I'm not.  I'm running irssi on byobu and using Karmic Koala.  Please, I welcome all of your advice about irssi even if it is not "on topic"  :)

-Yos

---

### Post by bix15 on 2010-01-24
uuuummmm....no idea. I just got irssi a few days ago.
but since "off topic" comments are welcome, irssi is awsome!! XD
They used the same IRC client on the TV show "Numb3rs" one time....
They tried to catch a hacker and they found his username in like 5 seconds XD

---

### Post by YosefKaro on 2010-01-25
I heard on IRC that others had this same problem with irssi on Karmic, that is, no sound alert for hilight.  So what is the work around or fix for this?

-Yos

---

### Post by andrew.46 on 2010-01-25
Hi Yos,

> **YosefKaro said:**
> I heard on IRC that others had this same problem with irssi on Karmic, that is, no sound alert for hilight.  So what is the work around or fix for this?

As we discussed on irc the problem is that by default irssi looks to the computer speaker to produce sound and by default pcspkr is not loaded in many Linux distros. One solution is to use a script:

```

cd $HOME/.irssi/scripts
wget http://scripts.irssi.org/scripts/beep_beep.pl
wget http://www.andrews-corner.org/tmp/ding_dong.wav
mkdir $HOME/.irssi/scripts/autorun
cd $HOME/.irssi/scripts/autorun
ln -s ../beep_beep.pl

```

Now install sox (you can use another sound program if you want):

```
sudo apt-get install sox
```

Now open up irssi and run the following:

```

/set bell_beeps
/set beep_msg_level MSGS DCC DCCMSGS HILIGHT NOTICES
/set beep_cmd play -q ~/.irssi/scripts/ding_dong.wav &
/save

```

and you should be right to go, and I know you got this running while we discussed the issue on irc :). There are several other scripts like this that might be worth having a look at and also a few different settings to experiment with on this particular script. That's irssi though, lots of room for customising and experimentation...

All the very best,

Andrew

---

### Post by YosefKaro on 2010-01-25
Thank you andrew.46 for your time and patience helping me to get this all set up and working.  :D  And thanks to the guys (and girl) on freenode #irssi channel for helping us both out.  You all rock: :guitar::guitar::guitar:

-Yos

---

### Post by anlag on 2011-03-24
This looks like a very nice solution to getting beeps in irssi. Now, my question is whether it's possible to do this same thing but with an irssi session that runs remotely and that is accessed over an ssh connection?

---

### Post by suicidefunky on 2011-07-04
Thanks Andrew for this info!

At first this did not work for me, here are the adjustments i did to make it work, maybe it will help someone else.

[LIST]
ding_dong.wav did not work with aplay, so i guess there might be something wrong with the wav file. I used another one from: [http://www.soundjay.com/beep-sounds-1.html](http://www.soundjay.com/beep-sounds-1.html)[/LIST]
[LIST]
Added ALL to the beep levels (/set beep_msg_level MSGS DCC DCCMSGS HILIGHT NOTICES ALL).[/LIST]
[LIST]
Replaced play with aplay (/set beep_cmd aplay -q ~/.irssi/scripts/ding_dong.wav &)[/LIST]
[LIST]
Changed beep_flood in the perl script to 300000 (5 minutes). If you get a message on irc within the flood time, it will NOT beep, otherwise, it will.[/LIST]
[LIST]
I didnt installed sox (used aplay)
[/LIST]

Now it works :)

---

### Post by andrew.46 on 2011-07-07
Glad to hear that at least a modified version of the solution that Yos and I hammered out a while back worked for you :). BTW I have re-encoded the wav file so now it will work with aplay as well.

@anlag I am afraid I am not sure about this, it has been a while since I have used irssi in this way.

---

