---
title: "Advanced conky codding"
date: 2012-03-05
forum: General Help
---

### Post by Lockheed on 2012-03-05
I can read the CPU's MSR like that
```
# rdmsr -0 0x198 
 061b4c2686004b26
``` 
This is the only way I can do it on my laptop.

This reads register 0x198 from the first CPU. The current voltage ID (VID) is in hexadecimal the last 2 digits and might fluctuate with the core clock if Speedstep is enabled. 
In my case it is 26, or 38 in decimal. On a mobile Core2Duo, the formula is 0.7125V + VID*0.0125V. In my case that corresponds to 1.1875V. (keep in mind that VID is in hex, and desktop CPUs use another formula, too).

Now, how can I feed this value translated into Volts into conky display?

---

### Post by Toz on 2012-03-09
Try this script:
```

#!/bin/bash
VOLT=$(echo "0.7125 + $((0x`rdmsr -0 0x198 | sed 's/^.*\(..\)$/\1/'`)) * 0.0125" | bc)
echo $VOLT"V"

```

with this conky snippet:
```
${execi 5 /path/to/script}
```
...where 5 is the interval in seconds in which you'd like the script to update.

---

