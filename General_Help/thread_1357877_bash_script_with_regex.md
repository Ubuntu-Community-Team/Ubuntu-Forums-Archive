---
title: "bash script with regex"
date: 2009-12-17
forum: General Help
---

### Post by kempy1000 on 2009-12-17
Hi

I am trying to write a script to parse data from a filename.

The input file name is always in the format (with spaces):
```

SHOW NAME - SEASOSNxEPISODE - EPISODE NAME.avi
eg:
Ubuntu TV - 01x02 - Using Firefox.avi

```
I want to be able to have a script that when I pass the file to it as $1 it is broken up into variables.
e.g
```

$Showname
$SeasonNumber
$EpisodeNumber
$EpisodeName

```

I did have a working method for this... It is very dirty and as I found out unreliable...
```

outname=${1##*/}
outname=${outname%.*}
outname=$outname".mp4"

tvshowname=${outname%-*}
tvshowname=${tvshowname%-*}
tvshowname=${tvshowname%\ *}

episodename=${outname%.*}
episodename=${episodename##*-}
episodename=${episodename#?}

filename=${outname##*-}
filename=${filename#?}

maincut=${outname%*x}
maincut=${maincut%-*}
maincut=${maincut##*-}

episodenumber=${maincut#*x}
episodenumber=${episodenumber%?}

seasonnumber=${maincut%x*}
seasonnumber=${seasonnumber#?}
seasonnumber=${seasonnumber#?}

```

It worked until I tried a file named: 
```

Ubuntu TV - 01x02 - Using-Firefox.avi

```

So now I have been trying to learn to use regex expressions to get the values for the variables but I'm getting no where...

Anyone who knows bash and regex got a solution or some help?

Thanks
Chris

---

### Post by ghostdog74 on 2009-12-17
```

$ string="Ubuntu TV - 01x02 - Using Firefox.avi"
$ IFS="-"
$ set -- $string
$ echo $1
Ubuntu TV
$ echo $2
 01x02
$ echo $3
 Using Firefox.avi



```

---

### Post by kempy1000 on 2009-12-17
Thank you for the reply!

The code provided will stop my script breaking but it also has one problem:
```

./script Ubuntu\ TV\ -\ 01x02\ -\ Using\ Firefox.avi

```
Gives:
```

Ubuntu TV
01x02
Using Firefox.avi

```

But...

```

./script Ubuntu\ TV\ -\ 01x02\ -\ Using-Firefox.avi

```
Gives:
```

Ubuntu TV
01x02
Using

```

It cuts off after the final "-"

Thanks
Chris

---

### Post by kaibob on 2009-12-17
It's not bash or regex, but perhaps you could use awk. Ghostdog74 is an expert at this (I'm not) and might know a better way to do this. 

```
echo "Ubuntu TV - 01x02 - Using-Firefox.avi" | awk 'BEGIN { FS = " - " } { print $1 }'
echo "Ubuntu TV - 01x02 - Using-Firefox.avi" | awk 'BEGIN { FS = " - " } { print $2 }'
echo "Ubuntu TV - 01x02 - Using-Firefox.avi" | awk 'BEGIN { FS = " - " } { print $3 }'

```

For example, 

> $ echo "Ubuntu TV - 01x02 - Using-Firefox.avi" | awk 'BEGIN { FS = " - " } { print $3 }'
Using-Firefox.avi

You could then separate 01x02 with bash.

---

### Post by kempy1000 on 2009-12-17
> **kaibob said:**
> 
```
echo "Ubuntu TV - 01x02 - Using-Firefox.avi" | awk 'BEGIN { FS = " - " } { print $1 }'
echo "Ubuntu TV - 01x02 - Using-Firefox.avi" | awk 'BEGIN { FS = " - " } { print $2 }'
echo "Ubuntu TV - 01x02 - Using-Firefox.avi" | awk 'BEGIN { FS = " - " } { print $3 }'

```


That works perfect thanks! and thanks to ghostdog for his solution too!

Chris

---

### Post by ghostdog74 on 2009-12-17
```

echo "Ubuntu TV - 01x02 - Using-Firefox.avi" | awk 'BEGIN { FS = " - " } { print $1,$2,$3 }'

```

---

### Post by kempy1000 on 2009-12-17
> **ghostdog74 said:**
> ```

echo "Ubuntu TV - 01x02 - Using-Firefox.avi" | awk 'BEGIN { FS = " - " } { print $1,$2,$3 }'

```

Thats even better for my script thanks!

---

### Post by diesch on 2009-12-17
```
IFS="-"
while read show season name; do 
  echo "$show|$season|$name"
done < input.txt
```

---

### Post by kempy1000 on 2009-12-17
> **diesch said:**
> ```
IFS="-"
while read show season name; do 
  echo "$show|$season|$name"
done < input.txt
```

The problem is i need it to be able to accept user input on the command line ($1 etc)

chris

---

