---
title: "Conky bug"
date: 2010-04-30
forum: General Help
---

### Post by zakoo2 on 2010-04-30
Hi!

It seems, that there's a bug in conky used in the new ubuntu 10.04 by the battery_bar function.

In .conkyrc I wrote:

${battery_bar 6,60 BAT1}

This is the correct way to write it, but the bar didn't show anything, and I got the error message:

"Conky: can't open /sys/class/power_supply/6,60/uevent: No such file or directory

Conky: /proc/acpi/battery/6,60/state: No such file or directory"

After this I tried to write the variables the other way around, like this:

${battery_bar BAT1 6,60}

Got no error messages, everything seemed fine, but the bar disappeared.

Looks like conky uses the same variable to get the location of the files and the height and width of the bar, which of course leads to an error message. Everything else works just fine (membar, swapbar, fs_bar). Before 10.04 I had 9.04 and this exact same .conkyrc worked without problems.

Can anyone help me with this?

PS: Sorry for the possible mistakes, I'm from Hungary. :)

---

### Post by P.T. on 2010-05-01
I happen to have the same problem.  ${battery_bar 10,50 BAT1} gives me the error &quot;can't open /proc/acpi/battery/10,50/state&quot;.  When I changed it to ${battery_bar BAT1 10,50} it gives me the correct amount of power in the battery, but my bar is more like 5px high and 100 long.  Hope someone has a workaround or this can be fixed.

---

### Post by dino99 on 2010-05-01
remember to have seen few report bugs on launchpad about that

---

### Post by SamD42 on 2010-05-06
I ran into this, and the only solution I could find was to [reinstall Conky]("http://binbashblog.blogspot.com/2010/05/conky-problematic-in-lucid-battery-bar.html") from the [source tarball]("http://sourceforge.net/projects/conky/files/conky/") on the website. Everything then behaved correctly again.

---

### Post by P.T. on 2010-05-10
Thanks, this fixed it for me!

---

### Post by 4tro on 2010-07-31
a workaround for this is to declare default bar size in the settings like
default_bar_size <width> <height>

you can then declare ${battery_bar BAT0} without barsize

all other bars can use either the same setting or their own

---

