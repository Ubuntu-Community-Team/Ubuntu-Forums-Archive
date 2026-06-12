---
title: "conky custom user variable"
date: 2011-12-18
forum: General Help
---

### Post by Gatemaze on 2011-12-18
Hi,

is there a way I can have custom variables in conky? Specifically I have the following code in my conkyrc file:

```

${font :size=24:bold}${alignc}${tztime Europe/London %H:%M}${font}
${font :size=12}${alignc}${tztime Europe/London %A %d %B}${font}${color}
${font :size=8}${alignc}in Europe/London${font}

```

and i would like to have Europe/London as a variable which I chance only once.

Thanks.

---

### Post by Habitual on 2011-12-18
Are you trying to display the date/time in London using conky?
b/c if you are you can do this in a sh script and call that script from conky...

```
#!/bin/bash
TZ=Europe/London date +%H:%M
TZ=Europe/London date +"%A %d %B"
```save as ~/LondonTime.sh or so...

Terminal > 
chmod 700 ~/LondonTime.sh

and conky would be this:
```
${font :size=24:bold}${alignc}${execpi 3600 /home/yourname/LondonTime.sh | head -1}${font}
${font :size=12}${alignc}{execpi 3600 /home/yourname/LondonTime.sh | tail -1}${font}${color}
${font :size=8}${alignc}in Europe/London${font}
```HTH.

---

