---
title: "A &quot;once in a lifetime&quot;-problem"
date: 2006-01-28
forum: General Help
---

### Post by glinsvad on 2006-01-28
Eeeh, I need to open a 10 GB binary datafile in some sort of text viewer. I have 1 GB of RAM and another 1 GB of SWAP, what do I do? :-k

I tried opening it in gEdit as read-only, but after a while it gets killed (most likely by the os). No editing is involved, I just need to view the raw data... help?

---

### Post by Quirky on 2006-01-28
Perhaps you could use "od" if you just need to see the data. It's command line only, but you can skip X bytes (-j) and change the format of the output (-t). If you know roughly where the data is. Or if you need to read some text, perhaps the "strings" program could help you. Both are command line only, but should use little memory since they stream the file rather than opening all of it into a buffer.

---

### Post by glinsvad on 2006-01-28
That worked perfectly... thanks Quirky

To aswer why (poll):
I'm looking into an application for GPS-data which has the surface of the Earth as an interface. Thus I downloaded a map in 500m/pixel resolution from [NASA's Earth Observatory]("http://earthobservatory.nasa.gov/Newsroom/BlueMarble/BlueMarble.html"), but I needed a smaller sample to test it out first.

---

