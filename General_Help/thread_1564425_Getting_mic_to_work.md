---
title: "Getting mic to work"
date: 2010-08-30
forum: General Help
---

### Post by Hmmster on 2010-08-30
First of all, do NOT tell me to google this, i've googled it several times and read most of the threads about it on here.

Now, my problem is; My mic doesn't take up sound, if i try to record, nothing, if i try to talk on Ventrilo, nothing.

I run Ubuntu 10.04.

---

### Post by ctsdownloads on 2010-08-30
Without a LOT more detail, this is not likely to go anywhere very quickly. ;)

1) Mic brand/type/USB?

2) Being Ventrilo is Windows only, you're going to have to elaborate a lot for us to have any idea how a mic in Ubuntu talks to Ventrilo.

I'd start there. :)

---

### Post by Hmmster on 2010-08-30
1) This has nothing to do with the mic i'm sure, but okay.
No, not USb. Standard mic slot, some cheap "trust"-mic, and it's not connected to a headset.

2) Well, let's skip the ventrilo part then and get it to work in the standard ubuntu sound recorder first, shall we? ;)

---

### Post by Tanayar on 2010-08-30
After you fixed the mic, there's a program called Mangler. It's open source and let's you connect to Ventrilo servers from your Ubuntu computer (Haven't used it, but it sounds promising)
Good luck!

---

### Post by ctsdownloads on 2010-08-30
Now based on my own experiences with the same issue of the mic plugged in, but not working. I have found it falls into two likely categories.

1) On my Eee netbook, there is no love with my built in mic, but inserting one into the mic port works okay. You are not using a built-in, so this leads us to the next thing.

2) As amazingly dumb as this is going to sound, chances are excellent based on my own repeats with this that there is a volume slider down somewhere. Yes, I said it sounds insane, but I see it every day as sometimes it just comes this way.

Check the following, assuming Ubuntu 10.04

1) System>Preferences>Sound

Look for the first attached image labeled #1.

Then click the input tab so it looks like attached image #2.

Notice the bars going horizontally across? Tap the mic with the volume slid up to see if you get a visual response there. Also make sure the right soundcard (headset, soundcard, webcam) is toggled for this test.

If you see that the mic shows the bars lighting up, so to speak, then it comes down to the application playing ball or not. 

For better application sound control, I find that the sound preferences, well, suck toes. I instead install padevchooser and then set it up to start under System>Preferences>Startup Applications. Just make the name and command for the app padevchooser  

Once that is installed and running, look near the clock for what seems like an audio cable looking thing, left click it and choose 
"volume control".

It will look like attachment #3

Now with this open, start the program you want to record with, then see attachment #4. Notice how I have the device menu pulled down? Kind of a big deal, since there are also device monitors available. You want to make sure the input device reflects your soundcard, not its monitor.

And with all of these settings, triple check all input sound sliders... especially with padevchooser and the Recording tab. Make sure the little speaker next to the slider is not clicked. This would mute your mic.

---

### Post by Hmmster on 2010-08-30
Hmm, that's odd.
In the input tab, the only choice i have is "Internt ljud Analog Stereo", wich basiclly is Internal sound analog stereo.
I have tried with two mics and it doesn't work. What should i do?
ARGH, i'm stupid, built in micports, ofcourse, works as intended i presume?
But no, it does not record sound at all still.The bars doesn't move.

---

### Post by Hmmster on 2010-08-31
Bump..

Bump for greater justice.

Rebump

Bump

Bump

*sigh*, and this is why i hate you guys.
Bump.

---

### Post by zaphod777 on 2010-08-31
> **Hmmster said:**
> *sigh*, and this is why i hate you guys.
Bump.

usually not a way to get people to help you. But anyway. What model of laptop do you have and what version of Ubuntu are you running?

---

### Post by zaphod777 on 2010-08-31
well anyway it is almost 1AM here but if you can post all of your hardware info here and Ubuntu version and what you tried so far I will take a look and see if I can find an answer in the morning when I wake up.

---

### Post by Hmmster on 2010-08-31
> **zaphod777 said:**
> well anyway it is almost 1AM here but if you can post all of your hardware info here and Ubuntu version and what you tried so far I will take a look and see if I can find an answer in the morning when I wake up.
Intel i5 750
Powercolour Ati HD 5770
Corsair dominator 2x2 1600MHz
Asus p7p55d mobo
Corsair TX 650w
Ubuntu 10.04
I don't know how my hardware would help though..
And i honestly cannot remember what i've tried, i just remember that my closest attempt was when i got it to record every sound that should come out of my headset.

> **zaphod777 said:**
> usually not a way to get people to help you.  But anyway. What model of laptop do you have and what version of Ubuntu  are you running?

What? I don't have a laptop? Where did you get that from? o.O
And i run Ubuntu 10.04

---

### Post by zaphod777 on 2010-08-31
Sorry I assumed you were on a laptop as most of these kinds of problems arise on a laptop.

here is what I turned up.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359)

when posting this type of problem it is good to include your motherboard model as most of these problems have to do specifically with what kind of hardware you are using and it is easier to search for a specific fix rather than one of use just posting a bunch of random generic "fixes" which can be hit or miss and a bit frustrating.

I found the above bug report when when I Googled for "asus p7p55d ubuntu mic"

According to the info in the bug report it looks like you need to install the alsa backports module and purge the current alsa package re-install and reboot.

```

sudo apt-get install linux-backports-modules-alsa-lucid-generic
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

```
then reboot

let me know if it works for you.

---

### Post by btown1987 on 2010-08-31
I would guess that you either do not have the correct driver installed or you need to add the correct option line to alsa-base.conf.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I just got my own sound issue worked out and the above page was tremendously helpful.

---

### Post by rockager on 2010-08-31
to: 
zaphod777 
hey !! are you zaphod beeblebrox, the president  of the galaxy?

---

### Post by zaphod777 on 2010-08-31
> **rockager said:**
> to: 
zaphod777 
hey !! are you zaphod beeblebrox, the president  of the galaxy?

Hey man you know ... I'm just like this guy ... 

Can I interest you in a gin and tonixs? You know what they say 2 heads are better than none.

---

### Post by zaphod777 on 2010-09-02
Is this working for you now?

---

