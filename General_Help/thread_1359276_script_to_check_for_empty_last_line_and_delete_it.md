---
title: "script to check for empty last line and delete it"
date: 2009-12-19
forum: General Help
---

### Post by inphektion on 2009-12-19
I have a cool conky from
[http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/)

lately i've not been getting the temps to show up.  I've figured out its because the weather file it generates now has an empty last line and the script reads the last line as the temp.  So what i want to do is check for an empty last line and if its there delete it (hence making the temp the last line again).
But this code isn't working, what am i doing wrong:

```
#!/bin/bash
plik=~/weather2
        w3m -dump http://weather.yahoo.com/forecast/"$kod".html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik
 if [ "`tail -1c "$plik"`" == " " ];
                then
                        sed '$d' $plik >> $plik;
        fi

```

---

### Post by mo.reina on 2009-12-19
> **inphektion said:**
> I have a cool conky from
[http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/)

lately i've not been getting the temps to show up.  I've figured out its because the weather file it generates now has an empty last line and the script reads the last line as the temp.  So what i want to do is check for an empty last line and if its there delete it (hence making the temp the last line again).
But this code isn't working, what am i doing wrong:

```
#!/bin/bash
plik=~/weather2
        w3m -dump http://weather.yahoo.com/forecast/"$kod".html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik
 if [ "`tail -1c "$plik"`" == " " ];
                then
                        sed '$d' $plik >> $plik;
        fi

```

i would change
```
if [ "`tail -1c "$plik"`" == " " ]
```
to
```
if [ "`tail -1c "$plik"`" == "" ]
```

---

### Post by inphektion on 2009-12-19
your messing with me right?  seriously i see no difference....
I've literally stared at it for 5 minutes now...:confused:

---

### Post by kaibob on 2009-12-19
> **inphektion said:**
> your messing with me right?  seriously i see no difference....
I've literally stared at it for 5 minutes now...:confused:
The first command has a space between quotes near the end--the second one doesn't.

---

### Post by inphektion on 2009-12-19
ah thanks.  i'm sick so not at 100%.  
Still didn't help it yet though... must be something wrong.

---

### Post by inphektion on 2009-12-19
I've even tried this:  with either the commented out like or the other.  Each time the file that is $plik end up completley empty....

```
#!/bin/bash
plik="/home/joel/weather2"
b=`tail -1c "$plik"`

        w3m -dump http://weather.yahoo.com/forecast/"$kod".html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik
 if [ "$b" == "" ];
                then
#                        `sed '$d' < $plik > temp`;
			head -n -1 $plik > temp
			mv temp $plik
        fi

```

---

### Post by StuartN on 2009-12-19
> **inphektion said:**
> I've even tried this:  with either the commented out like or the other.  Each time the file that is $plik end up completley empty....

```
w3m -dump http://weather.yahoo.com/forecast/**"$kod"**.html ...
```

Are you setting kod to your location? E.g. kod="NPXX0003" will download the weather in Kathmandu.

If Yahoo is not returning a valid location code in the address, then copy it from Aol at [http://weather.aol.com/](http://weather.aol.com/) after searching for city country, or the name of your nearest airport.

(Nice script - I was doing the exact same thing off NOAA earlier today and not nearly as neatly!)

---

### Post by inphektion on 2009-12-19
yes i am setting kod.  sorry i only posted the snippet that was giving me a problem.

its just the temp stopped displaying and I need to remove the last line from the file but only if its blank.  can't seem to get that part right.

---

### Post by CaKiwi on 2009-12-19
Or use

 ```
sed -i -e '$d' filename
```

to edit the file in place

---

### Post by StuartN on 2009-12-20
> **inphektion said:**
> its just the temp stopped displaying and I need to remove the last line from the file but only if its blank.  can't seem to get that part right.

Try adding **tail -1c $plik | od -c** after the w3m line and before the if test. This will print the characters contained in the last line, which might be something other than blank or a single space. Then put them those characters into the if test.

---

### Post by inphektion on 2009-12-20
well i realized other things besides the temp were off too...
so if you look at the script on the site i linked to I changed it to this:
	# ustalenie warto&#65533;ci zmiennych
        stan=`head -n2 $plik | tail -n1`		# Conditions
        temp=`tail -n2 $plik | awk '{print $1}'`	# Temperature
        tempo=`head -n7 $plik | tail -n1`		# Barometer
        cisn=`head -n9 $plik | tail -n1`		# Humidity
        wiatr=`head -n15 $plik | tail -n1` 		# Wind
        wilg=`head -n11 $plik | tail -n1`		# Visibility
        wsch=`head -n17 $plik | tail -n1` 		# Sunrise
        zach=`head -n19 $plik | tail -n1`		# Sunset


now its grabbing the correct values..

---

