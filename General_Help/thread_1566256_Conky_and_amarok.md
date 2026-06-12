---
title: "Conky and amarok"
date: 2010-09-02
forum: General Help
---

### Post by hiding on 2010-09-02
I should probably say upfront I'm new to trying to work with any kind of script or whatever, so forgive me if this a totally elementary problem.

I've been having a bit of trouble trying to set up Conky to display artwork from the track playing in Amarok 2.3, and it would be very much appreciated if someone were able to point me in the right direction to solving this problem.

I'm working from the solution offered here:
[http://ubuntuforums.org/showthread.php?t=1498033](http://ubuntuforums.org/showthread.php?t=1498033)

I've copied askamarok and nocover.png from the OP to ~scripts/conky

I've copied getcover from the 2nd post and saved it at ~scripts/conky

Edited getcover script to change:
```
tempdir="$HOME/.conky/"
```
to:
```
tempdir="$home/ian/scripts/conky/temp"
```

I then modified my conky script to include:

```
${if_running amarok}${font sans-serif:bold:size=8}MUSIC ${hr 2}${execi 8 ~/scripts/conky/getcover}${image ~/scripts/conky/cover.png}
${font sans-serif:normal:size=8}Track: $alignr ${execi 8 ~/scripts/conky/askamarok title}
Artist: $alignr ${execi 8 ~/scripts/conky/askamarok artist}
Album: ${execi 8 ~/scripts/conky/askamarok album}
${endif}
```

This does display the correct title, artist and album info in conky so I guess the askamarok script works, but the artwork resolutely refuses to change.

So I guess there's either a problem with:

1) the getcover script
2) this part of the conky script:
${execi 8 ~/scripts/conky/getcover}${image ~/scripts/conky/cover.png}
or 3) (Most likely) something else I've done or haven't done.

Sorry that's a bit vague. Any ideas?

---

