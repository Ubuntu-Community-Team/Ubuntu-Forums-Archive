---
title: "Using sed or awk to keep certain text within a line."
date: 2009-07-25
forum: General Help
---

### Post by i.wanna.corndog on 2009-07-25
Hey,

I'm working on a customized command line weather utility to feed data into a program, but I'm not that familiar with using sed or awk to keep only certain values.

I have gotten to the point where I have this line of text:
```
<yweather:condition  text="Partly Cloudy"  code="30"  temp="80"  date="Sat, 25 Jul 2009 10:53 am CDT" />

```

I need to figure out how to just get the value of "temp." It seems like this should be easy, but I have been trying different things with no luck.

Any help would be appreciated! Alternatively, if you could point me in the direction of an easy-to-understand tutorial for sed or awk, I'd be fine with trying to figure it out on my own.

Thanks!

---

### Post by bodhi.zazen on 2009-07-25
Use grep 

grep temp | grep <other_search terms> | awk '{print $4}'

---

### Post by kjohri on 2009-07-25
Try,

echo '<yweather:condition  text="Partly Cloudy"  code="30"  temp="80"  date="Sat, 25 Jul 2009 10:53 am CDT" />' | sed 's/.*temp//' | awk -F\" '{ print $2 }'

---

