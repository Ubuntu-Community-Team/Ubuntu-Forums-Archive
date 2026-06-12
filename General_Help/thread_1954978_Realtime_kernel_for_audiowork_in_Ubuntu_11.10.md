---
title: "Realtime kernel for audiowork in Ubuntu 11.10"
date: 2012-04-09
forum: General Help
---

### Post by sirriffsalot on 2012-04-09
Hello!

After a series of inconvenient and breathtakingly annoying events with my computer, I had to go for another one to continue my audio work. Long story short, I now have a plain Ubuntu Natty 11.10 installed on a 64bit system.

I've been looking around for an hour trying to find a comprehensive and structured way to incorporate a realtime kernel for this Ubuntu version, but all of the results are either outdated, piecing together many variables of which I am not sure would be futile in applying to my system, or very dodgy as they involve a lot of terminal work which I in so many cases have screwed up, also mostly due to outdatedness, that I had to reinstall the entire partition to get things installed the right way.

So, could someone please direct me to the right link(s) or give me the most recent and safe way of setting up a realtime kernel in Ubuntu 11.10? As I have done about an hour's worth of looking, simply going to google and replying with some promising-looking links is rather unwelcome, haha:D I'd appreciate very much if you are certain you know that what you're saying is correct, since I am a bit pressed with time:)

Thank you so much for your time!

--> Leo

---

### Post by sirriffsalot on 2012-04-09
bump:=)

---

### Post by CatKiller on 2012-04-09
The changes that were worth maintaining for the real-time kernel were merged back into the mainline kernel some time ago, which is why all the tutorials you're found are old.

---

### Post by sirriffsalot on 2012-04-12
Thanks pal! In other words, trying to get a realtime kernel these days is unnecessary?

---

### Post by CatKiller on 2012-04-12
That's my understanding. Certainly JACK is able to be run in realtime mode with the mainline kernel, which is provably what you're interested in.

---

### Post by kiirokurisu on 2012-04-12
What he said. The one thing I would add is that for high-end (sensitive) audio hardware, you might need to disable tickless timing to prevent static/crackle in your audio. This is done by adding nohz=off to your kernel boot parameters.

---

### Post by sirriffsalot on 2012-04-14
I think that would be realtime schedualing?

---

### Post by sirriffsalot on 2012-04-14
Cheers!

---

