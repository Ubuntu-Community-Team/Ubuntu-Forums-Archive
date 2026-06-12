---
title: "Redshift won't start in Natty"
date: 2011-05-05
forum: General Help
---

### Post by mystified123 on 2011-05-05
Hi, I'm fairly new..

Redshift will not start in Natty....

the errors seems to be that I'm unable to input the GPS coordinates..

I think it's because now that its Unity is the default, not Gnome, the  default clock and date settings has no provisions to input the GPS  settings..

If any one has a solutions..
it would be greatly appreciated.


Thanks 

Mystified123

---

### Post by slibuntu on 2011-05-05
You can start it via the command line. 

Open up a terminal, CTRL + ALT + t and type

```
redshift -l LAT:LON
```

where LAT:LON are your latitude and longitude.

If you need more configuration options, see the man page.

```
man redshift
```

---

### Post by your imaginary friend on 2011-05-05
A nicer workaround is described here:
[http://jonls.dk/2010/10/redshift-1-6-released/]("http://jonls.dk/2010/10/redshift-1-6-released/")

note the screen=1 option which refers to the 2nd monitor (count starting from zero).  as per the comments section in the link above, removing this line should apply the colour shift to all monitors.

---

