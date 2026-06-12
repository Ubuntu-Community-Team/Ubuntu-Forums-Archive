---
title: "Conky curl fold problem"
date: 2011-04-23
forum: General Help
---

### Post by Laen on 2011-04-23
Hello everyone,

I'm downloading a file via curl and then trying to "fold" the output to prevent it from being too wide:

```
${curl http://weather.noaa.gov/pub/data/observations/metar/stations/CYHM.TXT | fold -w80 -s}
```

Unfortunately this doesn't do it - the output is still in one line.

If I use that command in terminal I get the output that I want.

The problem is that "curl" is a conky command, so I tried using


```
${execi 900 curl http://weather.noaa.gov/pub/data/observations/metar/stations/CYHM.TXT | fold -w80 -s}
```

to try and force conky to use the bash command, but I still got the same output.

Any ideas?

Thanks!

Stan

---

