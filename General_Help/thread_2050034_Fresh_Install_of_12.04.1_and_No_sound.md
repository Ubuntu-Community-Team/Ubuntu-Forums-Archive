---
title: "Fresh Install of 12.04.1 and No sound"
date: 2012-08-29
forum: General Help
---

### Post by WonkyDisco on 2012-08-29
Hi, I have no clue wear to begin. I have a fresh install of Ubuntu 12.04.1 and I have no sound currently. I'm not sure what soundcard I have or how to find that out. I was hoping someone could help on the right path to getting my sound working.

---

### Post by beboylips on 2012-08-29
Run 
```

alsamixer

```
in terminal. You'll see the list of possible outputs along with your sound cards (click F6 to list your soundcards).

---

### Post by WonkyDisco on 2012-08-30
It states that it's an HDA ATI SB, and the chipset is  Realtek ALC888

I do get sound from the headphone jack in the front. However I can't get sound from any of six jacks in the back of my tower.

---

### Post by beboylips on 2012-08-30
Every jack in the back should have it's own mixer with Alsa (or at least the surround sound should have it's own mixer and the normal output and the microphone should have their own as well). Check if any of them are muted or are at really low volume. 

Also post a screenshot of the terminal when you run Alsamixer, it'll help.

---

### Post by WonkyDisco on 2012-08-30
Here is a picture of my AlsaMixer,

[IMG]http://i48.tinypic.com/n1ukv6.jpg[/IMG]

---

### Post by beboylips on 2012-08-30
Excellent. Note how the Master branch is almost silent (leftest one). Try increasing it and see if you get sound.

---

### Post by WonkyDisco on 2012-08-30
I increased it to 100%, tried every jack, and no sound.. :(

---

### Post by beboylips on 2012-08-30
There are more available mixers on the right of the terminal screen. Scroll there and screen shot them as well. Also, F6 to see the selection of sound cards. If you have more than one, select the other and screenshot it as well. I am pretty positive you are not getting sound because some mixer is on mute or disabled.

---

### Post by WonkyDisco on 2012-08-30
[IMG]http://i45.tinypic.com/2mdm4ip.png[/IMG]

[IMG]http://i47.tinypic.com/e03k80.png[/IMG]

---

### Post by beboylips on 2012-08-30
Increase Line mixer. If that doesn't work, we would have to explore radically different routes for the solution.

Note: the output jack for regular stereo is the *green* one. Others wouldn't work if you tried plugging your earphones into them. You probably have two shades of green jacks, take the light green one. Sorry, had to double check.

---

### Post by WonkyDisco on 2012-08-30
Increasing the Line-in did not work. And yes, I have it plugged into the light green jack.

---

### Post by beboylips on 2012-08-30
Go to Sound configuration utility and select the Output tab. Screenshot it. Make sure that the proper device is selected for output.

---

### Post by WonkyDisco on 2012-08-31
[IMG]http://i50.tinypic.com/2qsyu0y.png[/IMG]

[IMG]http://i46.tinypic.com/317hysi.png[/IMG]

---

### Post by WonkyDisco on 2012-09-02
Just to make sure it's clear what I am trying to do,

The headphone jack in the front of the tower does work properly with sound; none of the six ports in the back work. On my windows partition I am able to use two of these six ports for setting up two sets of speakers. However on my Ubuntu partition it does not allow me to do this.

---

### Post by senorian on 2012-10-15
I also have a fresh 12.04.1 Xubuntu install and NO sound. ( on an old Celeron 2 gig cpu.)
I am unable to scroll to the right to see all the audio bar graphs
Whap happened to this thread?
Please point me to a solution
thanks

---

### Post by senorian on 2012-10-15
Found how to extend window to show more bars
still no sound

How to I increase/decrease the settings?
Clicking on the base of te column does nothing.

---

