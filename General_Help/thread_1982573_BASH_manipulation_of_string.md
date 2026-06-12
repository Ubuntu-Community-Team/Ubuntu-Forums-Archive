---
title: "BASH manipulation of string"
date: 2012-05-18
forum: General Help
---

### Post by Tclarkie on 2012-05-18
Hi all
a current bash scripting project of mine requires the manipulation of a string that looks like this:
```
http://www.example1.com/eg/eg/test.htm?show=jukebox&xmlUrl=http://www.example2.com/eg/eg/eg/trial.xml&mediaType=multi&launchType=play&pluginTarget=undefined&pluginTitle=undefined&pluginColour=undefined
```
And turn it into:
```
http://www.example2.com/eg/eg/eg/trial.xml
```
Any help would be great
Thanks :)

---

### Post by papibe on 2012-05-18
Hi Tclarkie.

I can't see the format of the full link.

Please use 'code' tags instead of 'quotes'.

Regards.

---

### Post by Tclarkie on 2012-05-18
Thanks. If at all possible, it would be best if the solution didn't involve perl or ruby. Ive just been googling various keywords and a lot of the solutions use them

---

### Post by papibe on 2012-05-18
Using bash parameter substitution:
```
original_url="http://www.example1.com/eg/eg/test.htm?show=jukebox&xmlUrl=http://www.example2.com/eg/eg/eg/trial.xml&mediaType=multi&launchType=play&pluginTarget=undefined&pluginTitle=undefined&pluginColour=undefined"

trim_from_beginnig="${original_url#*Url=}"

final_trim="${trim1%&mediaType*}"

```
or, using sed:
```
final_trim=$(echo "$url" | sed 's/^.*Url=\(.*\)&mediaType.*/\1/')
```
Hope that helps.
Regards.

---

### Post by Tclarkie on 2012-05-18
Works like a charm. Thankyou :D

---

### Post by markbl on 2012-05-19
```

echo $url | sed s'/.*=\(.*\)&.*/\1/'

```

I like to save keystrokes ;)

---

