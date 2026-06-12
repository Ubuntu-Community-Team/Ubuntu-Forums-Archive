---
title: "Updates have caused system to stop booting properly"
date: 2011-02-09
forum: General Help
---

### Post by Berry Greene on 2011-02-09
Scaleo Pentium 4 system with several HDDs 3Gb RAM
UBUNTU 8.04 (I think) inside a 50Gb partition (J:\)

Operating dual boot with Windows XP all OK until ......
sanctioning the updates. Now  Ubuntu will not complete a boot up.

Studio  Starts to scroll its name then screen goes back to A/numemeric reports  and hangs for time-outs which never resolve. Power - down only way to  exit

Example of screen report at point of stopping:-

Starting hardware abstraction layer hold
104.628464] ata3.00 revalidation failed (errorno -5)
{DELAY FOR TIME-OUT} THEN:
135.768905] ata3.01 revalidation failed (errorno -5)
{ANOTHER DELAY}
172.281028 ata3 

and so on until I initiate a power down.

I would be very grateful for any guidance on how best to proceed from here.
I thank you
Berry G

---

### Post by Berry Greene on 2011-02-10
It's OK! Don't fret I have solved this all by myself. As I would have thought this would happen to others, here's how (for the very shy like myself):smile::-

When the system starts up and the BIOS has run, the dual boot choice screen appears.
You have a few seconds to make your second choice (UBUNTU) after which the first choice (WINDOWS) will run. This worked OK as per normal.

When you want UBUNTU to run you must highlight that choice and press ENTER

You are now given another few seconds in which to press ESCAPE (a choice I had never made) after which UBUNTU starts its boot process. This was, as I said in my first post, not working as normal. However.......,

I tried pressing escape key within the time-out period and was presented with a menu.
Noticing the word "RECOVERY" in the second line (2nd choice), I opted for that.

After a few more seconds I was asked if I wanted to do something about corrupt (something(s) ??:confused:?), and I opted for that.

This seemed to clear up all my problems and the system now starts up normally and runs as it always did before.

And there.... you have it!
Do I get any beans for this diagnosis? :smile:

Regards to you all:guitar:

Berry G:grin:

---

