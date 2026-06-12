---
title: "Bash script to compare current time."
date: 2009-10-25
forum: General Help
---

### Post by dchurch24 on 2009-10-25
Hi all,

I have a bash script that executes when a movie is played through MythTV that turns off my main room light, turns on a backlight behind the TV and then plays the movie. At the end of the movie it reverses the process and turns the room lights back on again:

```

#!/bin/bash
./adu rk0
./adu sk1
mplayer -fs -zoom -quiet -vo xv "$1"
./adu sk0
./adu rk1

```

What I want to do, but have no idea how to, is have something like this:

```

#!/bin/bash
if time > 17:00
./adu rk0
./adu sk1
end
mplayer -fs -zoom -quiet -vo xv "$1"
if time > 17:00
./adu sk0
./adu rk1
end

```

...so that the lights only turn on/off if the time is greater than say, 5pm.

Is this possible?

---

### Post by ApEkV2 on 2009-10-25
I don't know if it will work, but here is what I think is on the right track.
Note that it only gauges time by hours, so it could be 16:29, and in the script it will be 16.
The 17 is actually 5:00 pm, and 9 is 9:00 am. 
 
[php]#!/bin/bash
z_hr=`date +%H`

if [ $z_hr > 17 ] || [ $z_hr < 9 ]; then

 ./adu rk0
 ./adu sk1
 z_mode=1

 else
 z_mode=0

fi

mplayer -fs -zoom -quiet -vo xv "$1"

if [ $z_mode == 1 ]; then
./adu sk0
./adu rk1
fi[/php]

---

### Post by dchurch24 on 2009-10-26
Brilliant!

I shall give that a try when I get home from work later.

Thanks very much!

---

### Post by ApEkV2 on 2009-10-26
You know now that I have gotten some sleep I am an idiot.
I've updated the code above. (can't be greater than 17 **and** less than 9 lol)

---

### Post by Lars Noodén on 2009-10-26
[at](http://linux.die.net/man/1/at) can run programs at a specified time, either an absolute time (17:00) or a relative time (now +68 minutes)

[INDENT][FONT="Courier New"]echo "/usr/local/bin/adu sk0; /usr/local/bin/adu rk1;" | at 17:00;[/FONT][/INDENT]

You might be able to use mplayer's option **-identify** to extract the play time and set at accordingly.  

However, why not just put the lights on and off before and after the movie?

pseudo code:

lights on; mplayer ___ ; lights off;

---

### Post by dchurch24 on 2009-10-26
> **Lars Noodén said:**
> [at](http://linux.die.net/man/1/at) can run programs at a specified time, either an absolute time (17:00) or a relative time (now +68 minutes)

[INDENT][FONT="Courier New"]echo "/usr/local/bin/adu sk0; /usr/local/bin/adu rk1;" | at 17:00;[/FONT][/INDENT]

You might be able to use mplayer's option **-identify** to extract the play time and set at accordingly.  

However, why not just put the lights on and off before and after the movie?

pseudo code:

lights on; mplayer ___ ; lights off;

Hi, that's exactly what I am doing, however, I may not watch movies always at night, so I want to only turn the lights on if it's after a certain time - 17:00 seems to be fair at the moment (that's pretty much the time it gets dark in the UK at the moment).

I am going to change it tonight to run through my Arduino and a remote-controlled dimmer switch (lower voltage than one with a pot), so rather than just switching on and off, the lights slowly go out and the backlight slowly comes up.

Not sure how successful that's going to be, but I figure for the sake of 20 quid on a remote-dimmer, it's got to be worth the gamble.

---

### Post by Lars Noodén on 2009-10-26
When you get it done, it'd be fun to read the write up.  

Following [parkinson's law](http://dictionary.reference.com/browse/Parkinson%27s+Law) here:

If you want to get really fancy use [Astro::Sunrise](http://search.cpan.org/~rkhill/Astro-Sunrise-0.91/Sunrise.pm) or [DateTime::Astro::Sunrise](http://search.cpan.org/~rkhill/DateTime-Astro-Sunrise-0.01_01/Sunrise.pm) to adjust the lamp cutover to some function of civil twilight.  That would be instead using a fixed time.  

There should be an equivalent for java or python or you can use the CPAN modules as models.  

If you want to get fancier still, you can grab the current [weather conditions](http://wiki.wunderground.com/index.php/API_-_XML) from any number of sites and modify that civil twilight based on how overcast it is.

---

### Post by Lars Noodén on 2009-10-26
I got curious about getting the play time from mplayer.  Here's what I found:

```

# show id_length and value
mplayer -identify "$MOV" 2>&1 \
 | awk '/^ID_LENGTH/{ print } '

# show length in number of seconds of $MOV
mplayer -identify "$MOV" 2>&1 \
 | awk '/^ID_LENGTH/{ seconds= $1; sub(/^.*=/,"", seconds); print seconds }'

# show length in minutes of $MOV
mplayer -identify "$MOV" 2>&1 \
 | awk '/^ID_LENGTH/{ seconds= $1; sub(/^.*=/,"", seconds); print int(seconds/60+.5) }'

# assign length in minutes to DELTAT
export DELTAT=\
`mplayer -identify "$MOV" 2>&1  \
 | awk '/^ID_LENGTH/{ seconds= $1; sub(/^.*=/,"", seconds); print int(seconds/60+.5) }'`

# turn lights on at end of movie
export DELTAT=\
`mplayer -identify "$MOV" 2>&1  \
 | awk '/^ID_LENGTH/{ seconds= $1; sub(/^.*=/,"", seconds); print int(seconds/60+.5) }'`
echo "/usr/local/bin/turnlight on" | at now +${DELTAT} minutes

```

---

### Post by dchurch24 on 2009-10-26
Ha - you're not wrong.

I now have the idea to control it from an Arduino board (which I have laying around) - for which I also have photo-sensitive cells ;-)

Now, when a film starts the Arduino will check to see if it's dark outside before turning the lights on.

---

