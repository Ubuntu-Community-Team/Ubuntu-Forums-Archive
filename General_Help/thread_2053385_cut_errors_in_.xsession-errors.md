---
title: "cut errors in .xsession-errors"
date: 2012-09-05
forum: General Help
---

### Post by Statia on 2012-09-05
My .xsession-errors is over 3 megabytes and consists for 95% of:

```
09/05/12 12:13:58 PM            cut: the delimiter must be a single character
09/05/12 12:13:58 PM            Try `cut --help' for more information.
09/05/12 12:14:08 PM            cut: the delimiter must be a single character
09/05/12 12:14:08 PM            Try `cut --help' for more information.
09/05/12 12:14:08 PM            cut: the delimiter must be a single character
09/05/12 12:14:08 PM            Try `cut --help' for more information.

```It repeats every ten seconds. Any idea where this is coming from and how to stop it?
Another strange entry (possible related to something I asked earlier about in the network part of the forums):

```
09/05/12 12:14:18 PM            Resolving checkip.dyndns.org (checkip.dyndns.org)... 91.198.22.70, 216.146.38.70, 216.146.39.70
09/05/12 12:14:18 PM            Connecting to checkip.dyndns.org (checkip.dyndns.org)|91.198.22.70|:80... connected.
09/05/12 12:14:18 PM            HTTP request sent, awaiting response... 200 OK
09/05/12 12:14:18 PM            Length: 106 [text/html]
09/05/12 12:14:18 PM            Saving to: `index.html'
09/05/12 12:14:18 PM            
09/05/12 12:14:18 PM                 0K                                                       100% 11.9M=0s
09/05/12 12:14:18 PM            
09/05/12 12:14:18 PM            2012-09-05 12:14:18 (11.9 MB/s) - `index.html' saved [106/106]
09/05/12 12:14:18 PM            
09/05/12 12:14:28 PM            plasma-desktop(2212)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 


```

I don't use any dyndns services, my router has a fixed IP.

---

### Post by Statia on 2012-09-05
Found it.
It's a Superkaramba widget called sysmaloon.
It creates an outgoing connection to find out my external IP.
I think in cutting info out of /proc or sensors, there is some syntax error, because instead of the temperature of /dev/sda it shows "Force"
(The disk is a Corsair Force GT)

Does anyone have an idea where (configuration) files for Superkaramba files can be found?

---

### Post by Statia on 2012-09-09
Bump

---

### Post by Statia on 2012-09-11
I solved the wrong reading of hddtemp, but that was using awk, the cut errors are from somewhere else in the configuration.

This is the offending line:

```
hddtemp /dev/sdb | awk '{print $3}' | cut -d '°' -f 1
```

How do I fix this?

---

### Post by steeldriver on 2012-09-11
have you tried replacing with the hex ascii code for the degree symbol?

```
$ sudo hddtemp /dev/sda | awk -F ':' '{print $3}' | cut -d $'\xb0' -f 1
 47
```

---

### Post by Statia on 2012-09-11
```
$ hddtemp /dev/sda | awk -F ':' '{print $3}' | cut -d $'\xb0' -f 1
 33&#65533;

```Interesting that I get a &#65533; and you just the value.

---

### Post by Statia on 2012-09-11
If the intention of the maker of the theme was to get just the numbers, without degree C, this should do the trick too:

```
$ hddtemp /dev/sdb | awk '{print $3}' | cut -c -2
```

---

### Post by steeldriver on 2012-09-11
Hmm... so it seems to be (disk)-vendor dependent - on a different box I get a 2 character sequence 'c2b0'

```
$ sudo hddtemp /dev/sda
/dev/sda: HTS721010G9SA00: 39Â°C
$ sudo hddtemp /dev/sda | awk -F ':' '{print $3}' | od -tx1
0000000 20 33 39 c2 b0 43 0a
0000007
$ sudo hddtemp /dev/sda | awk -F ':' '{print $3}' | cut -d $'\xc2' -f 1
 39
```All I can suggest is you look at the particular string your box is giving and hard code the value appropriately

---

### Post by Statia on 2012-09-11
I fixed everything with the  cut -c -2.
This not only solves the .xsession-errors filling up, it also causes the graphic bars for temperature to work.
Like in the screenshots here:

[http://http://kde-look.org/content/show.php?content=61406](http://http://kde-look.org/content/show.php?content=61406)

GPU temp was still a bit of a puzzle, but I found out the minimum temperature in the configuration was higher than the actual temperature of the GPU.

Now if only there would be a working sensors module for my motherboard (Asus V6-P8H61ELX), it could display voltages and fans as well

---

### Post by steeldriver on 2012-09-11
```
cut -c -2 
```is a little bit risky imho - especially if you plan to use this for GPU temps as well (which may get into the triple digits C)

Perhaps you should think about abandoning 'cut' altogether and just piping the field through 'tr' to strip it down to digits?

```
hddtemp /dev/sda | awk -F ':' '{print $3}' | tr -cd '[:digit:]'
```or

```
hddtemp /dev/sda | awk -F ':' '{print $3}' | tr -cd '[[:digit:][:space:]]'
```if you want to keep the newline and/or whitespace

---

### Post by Statia on 2012-09-11
Maybe I don't understand this correctly, but if the last two characters get stripped, it should not matter if it is cutting from 101°C or from 99°C?
Besides, I have a modest GPU and am not much of a gamer. I just ran Unigine Heaven on high settings for a while and the GPU went to about 52 degrees.

---

### Post by Statia on 2012-09-11
Strange. Now I get complaints about lines that gave no errors before:

         ```
/bin/bash: line 0: [: -gt: unary operator expected
cut: the delimiter must be a single character
Try `cut --help' for more information.
cut: the delimiter must be a single character
Try `cut --help' for more information.
/bin/bash: line 0: [: -gt: unary operator expected
/bin/bash: line 0: [: -gt: unary operator expected

```These are probably the offending lines:

```
text x=248 y=0 sensor=program program="if [ `sensors | grep 'CPU Temp' | cut -d + -f 2 | cut -d '.' -f 1` -gt 55 ]; then play -q sound/alarm.ogg ; sleep 1 ; play -q sound/alarm.ogg ; sleep 1 ; echo 'Processor has a critical temperature, please, down it now' | artsdsp -m festival --tts ; fi;" interval=120000 fontsize=1

text x=248 y=0 sensor=program program="if [ `sensors | grep 'Sys Temp' | cut -d + -f 2 | cut -d '°' -f 1` -gt 50 ]; then play -q sound/alarm.ogg ; sleep 1 ; play -q sound/alarm.ogg ; sleep 1 ; echo 'North Bridge has a critical temperature, please, down it now' | artsdsp -m festival --tts ; fi;" interval=120000 fontsize=1

text x=248 y=0 sensor=program program="if [ `nvidia-settings -q gpucoretemp  |grep '):' | awk '{print $4}' | cut -d '.' -f 1` -gt 90 ]; then play -q sound/alarm.ogg ; sleep 1 ; play -q sound/alarm.ogg ; sleep 1 ; echo 'Graphic card has a critical temperature, please, down it now' | artsdsp -m festival --tts ; fi;" interval=120000 fontsize=1

text x=248 y=0 sensor=program program="if [ `hddtemp /dev/sda | awk '{print $3}' | cut -d '°' -f 1` -gt 47 ]; then play -q sound/alarm.ogg ; sleep 1 ; play -q sound/alarm.ogg ; sleep 1 ; echo 'Hard disk number one has a critical temperature, please, down it now' | artsdsp -m festival --tts ; fi;" interval=120000 fontsize=1

text x=248 y=0 sensor=program program="if [ `hddtemp /dev/sdb | awk '{print $3}' | cut -d '°' -f 1` -gt 47 ]; then play -q sound/alarm.ogg ; sleep 1 ; play -q sound/alarm.ogg ; sleep 1 ; echo 'Hard disk number two has a critical temperature, please, down it now' | artsdsp -m festival --tts ; fi;" interval=120000 fontsize=1

```For now I just commented out these lines, as I don intend to use the speech function of the theme.

---

