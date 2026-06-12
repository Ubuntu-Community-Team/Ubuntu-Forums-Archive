---
title: "Two Conky questions:"
date: 2012-05-09
forum: General Help
---

### Post by M_Mynaardt on 2012-05-09
Hi!

Just two quick questions about Conky:

First; how do you write up an **$if** block?

I'd like to have a battery power bar that changes to red when the battery power drops below, say 20%.  I just don't want to mess up.  The logic I have is something like this:
```
if battery_power > 20%
then show-a-yellow-bar
else show-a-red-bar

```

I'm okay with $battery_bar and $color #nnnnnn} statements.  I just want to put it all together with an **$if** block.

Second; Xubuntu, my PC's OS, doesn't seem to like the ${tab (pixels)} statement.  I tried using it four blank spaces with ${tab 30}.  But when I did, the Conky display started to flicker and the right edge, maybe 20 pixels' worth, got cut off the display.  I used ${tab 30} in Lubuntu (for my laptop) without any problems.

Is there something else I need to make this work properly?

Thanks!

---

### Post by M_Mynaardt on 2012-05-09
ADDITIONAL:

I played around with $tab for a bit and realized that what it's doing is that it is marking off from right to left.  I just assumed it was going from left to right.

So, when I used, say, **${tab 20}**, it was _not_ going 20 pixels from the last thing on the left going right, but measuring off 20 pixels from the far right edge going left.

That would explain that strange behaviour!

Is there some way to make $tab measure off from the left to the right?

---

### Post by Habitual on 2012-05-09
This real life example *may* help.
```

${if_mounted /media/flash}${goto 600}${color red}USB$color is ${fs_free_perc /media/flash/}% Free$color${else}${color red}USB Not Mounted$color${endif}

```Have a Great Day!

---

### Post by M_Mynaardt on 2012-05-09
> **Habitual said:**
> This real life example *may* help.
```

${if_mounted /media/flash}${goto 600}${color red}USB$color is ${fs_free_perc /media/flash/}% Free$color${else}${color red}USB Not Mounted$color${endif}

```Have a Great Day!

Right on...

I'll see if I can use that as a model to get the battery bar to do what I want it to.

Thanks!

---

### Post by Habitual on 2012-05-10
Glad it helped you out.

---

### Post by M_Mynaardt on 2012-05-10
> **Habitual said:**
> Glad it helped you out.

It was a great help, actually!  Part of the problem was I didn't realize you had to pick the right **$if_*** statement.  I managed to figure out it was **$if_match** that I needed.  And from that I also did a search to find this example too; [http://crunchbanglinux.org/forums/topic/4485/conky-low-battery-warning/]("http://crunchbanglinux.org/forums/topic/4485/conky-low-battery-warning/")

With your example and that other one, I was able to figure out how to make the display work as I wanted.  Namely, to have a light green colour for a battery that's got over 25% charge, and a jarring shade of red if the battery percentage goes to 25% or less.

Here's the block from my **.conkyrc** file that I used to display my battery status and all that:
```
${hr}
Battery$alignr${if_match $battery_percent <= 25}${color #ff0033}${else}${color #00fe79}${endif}${battery_bar 10,200}${color}
$battery$alignr time; $battery_time
# display battery bar, status, percent and time left for battery charge, AND
# if the battery charge is 25% or more, show the battery bar in light green
# else (charge is under 25%) show the batter bar in jarring red to warn of 
# the need to recharge the laptop battery
# on my Toshiba, this percentage plummets from 20% to 5% quickly
${hr}
```

So, I made a few other cosmetic changes to my Conky displays and ended up with the two that are attached.  One with the batter above 25% and the other hitting 25% and going red on the bar.  I like them!

I'm getting pretty cocky with Conky now, I think!
\\:D/

---

### Post by Habitual on 2012-05-10
Sweet!

---

### Post by M_Mynaardt on 2012-05-11
> **Habitual said:**
> Sweet!

It is rather.  But after I posted that, I noticed that when the battery was fully charged, my line showing the time left ended with "time;" because once fully charged the $batter_time variable goes blank.  So, I had to use another **$if** block to make sure that the display still makes sense once the battery is fully charged.  Here's the result:
```
${hr}
Battery$alignr${if_match $battery_percent <= 25}${color #ff0033}${else}${color #00fe79}${endif}${battery_bar 10,200}${color}
# display battery bar; light green for okay, red for running low
# if the battery charge is over 25%, show the battery bar in light green
# else show the batter bar in jarring red to warn of low power
# on my Toshiba, this percentage plummets from 20% to 5% quickly
$battery$alignr${if_match $battery_percent != 100} time; $battery_time${else}  fully charged${endif}
# when the battery is fully charged, no time shows and line ends with "time;"
# display is modified to avoid this
${hr}

```

It works too; so once the battery charge hits 100%, the time is replaced nicely with "fully charged".  Looks less confusing than a line just ending with "time;"

I like it when these things work!
:guitar:

---

