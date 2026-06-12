---
title: "cut and grep to extract information"
date: 2011-08-02
forum: General Help
---

### Post by kainalu on 2011-08-02
Hello All,

How would I use cut or grep to take this line :

```
Load......................... 198 Watt(22 %)
```

and make it into this information, in a text file :

```
198 Watts
```

If you don't mind, please explain the process, as I have been trying to figure this command out, and I must be missing something. Regex confuses me. :confused:

Thanks!
Kainalu

---

### Post by Habitual on 2011-08-02
Well, I am assuming that "Load......................... 198 Watt(22 %)" is not the actual data, you will have to grep using positional tokens ($1, $2, $3 etc)

using grep by position:
```
cat x | awk '{print $1}'
``` give us Load.........................
(is position $1)
```
cat x | awk '{print $2}'
``` gives us 198
(is position $2)
```
cat x | awk '{print $2" "$3}'
``` gives us 198 Watt(22
(is position $2 and $3)

"198 Watts(22" is 11 characters, so use "cut" to get the first 8:
```
cat x | awk '{print $2" "$3}' | cut -c 1-8
```
gives us "198 Watt"

Each($1) word($2) in($3) a($4) sentence($5) 
gives you that word when using tokens with grep.


[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_04_02.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_04_02.html)
[http://www.manpagez.com/man/1/cut](http://www.manpagez.com/man/1/cut)

---

### Post by wannabegeek on 2011-08-02
awesome answer...I use a less nice way

cat  filename cut  -c  xx > textfile.txt

where xx is the number of character to cut out.

---

### Post by kainalu on 2011-08-02
I agree, awesome answer. Also very effective.

Actually, that was the output to be cut. I use a cyberpower UPS which nicely monitors power consumption. I make the monitor not require a password for sudo, and then I do
```

while true ; do
sudo pwrstat -status |grep Load | cat | awk '{print $2}' > /tmp/pwr.con
sleep 2s

done

```

and in Conky :
```

Consumption : ${alignr}${execi 2 cat /tmp/pwr.con} Watts

```

Thanks for the help!

---

### Post by sisco311 on 2011-08-03
@Habitual
-10 points for useless use of cat :evil:
-10 points for the link to the outdated guide :evil:

[http://partmaps.org/era/unix/award.html](http://partmaps.org/era/unix/award.html)

@OP
This is a perfect job for sed:
```
command | sed -r 's/(Load.+ )([0-9]+ Watt)(.*)/\2/'
```

[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
[http://mywiki.wooledge.org/RegularExpression](http://mywiki.wooledge.org/RegularExpression)

---

### Post by bodhi.zazen on 2011-08-03
Not sure where you are getting that line from , a file ?

Assuming the file is named "foo.txt"

```
awk '/Watt/ { print $2, "Watts" }' foo.txt
```

---

### Post by sisco311 on 2011-08-03
> **bodhi.zazen said:**
> Not sure where you are getting that line from , a file ?

Assuming the file is named "foo.txt"

```
awk '/Watt/ { print $2, "Watts" }' foo.txt
```

D'oh, nice, I have to improve my awk skills. :)

---

### Post by kainalu on 2011-08-03
sisco & bodhi,

Would you mind explaining what those commands do, so I may learn how they are used and work?

Mahalo!

---

### Post by bodhi.zazen on 2011-08-03
Probably best for you to google search how to sed and how to awk and how to regular expressions.

The awk command I gave basically matches a regular expression, "Watt" in this case, and prints the second field + the word "Watts".

The sed command is a bit more complex. Sed is a method of substituting text.

So the sed command is using regular expressions

match (expression 1)(expression 2) substitute (what matched expression 2)

The "\2" is a variable or short hand for the text the matched expression 2

Try it :

```
echo this | sed 's/this/that/'
```

Now try

```
echo this | sed 's/\(th\)is/\1at/'
```

The pattern in the () , escaped with a \ , so "\(th\)" , is the "\1" or first pattern.

Clear as mud ?

Probably not much of that makes sense without you reading up on regular expressions, sed, and awk, but, both commands were fairly "basic" so should not be too difficult to understand with a little reading.

---

### Post by bodhi.zazen on 2011-08-03
Try this =)

sed -r 's/(Load.+) ([0-9]+) Watt(.*)/\2 Watts/'

```
echo 'Load......................... 198 Watt(22 %)' | sed -r 's/(Load.+) ([0-9]+) Watt(.*)/\2 Watts/'
```

This also works =)

sed -r 's/(.*) ([0-9]+) (.*)/\2 Watts/'

---

### Post by sisco311 on 2011-08-03
or this one :)    
```
awk '/Watt/{printf "%d %s", $2, "Watt"; if ($2!=1) printf "%c", "s"; printf "\n"}' filename
```

---

### Post by kainalu on 2011-08-03
Seems that there are about an infinite number of ways to do this. I certainly will take Bodhi's advice and read up on those commands and regex. I am now very curious, and will have to play with this. 

Thanks guys!

---

### Post by bodhi.zazen on 2011-08-03
> **sisco311 said:**
> or this one :)    
```
awk '/Watt/{printf "%d %s", $2, "Watt"; if ($2!=1) printf "%c", "s"; printf "\n"}' filename
```

Looks as if you are enjoying awk =)

---

