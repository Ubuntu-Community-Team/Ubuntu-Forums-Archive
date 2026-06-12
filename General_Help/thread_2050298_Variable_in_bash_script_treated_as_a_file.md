---
title: "Variable in bash script treated as a file?"
date: 2012-08-30
forum: General Help
---

### Post by telemaster on 2012-08-30
Hey,

I have a fairly simple bash script here. It's purpose is to find some data values from a large script of numbers, fairly standard. 

[code]
#!/bin/bash
j=1;
i=1;
while [ j < 8 ]
  do
    
    if [i==30]
      then
        j++;
        i=1;
    fi

    
    while [ i < 30 ]
    do
    awk -v counter=$j ' BEGIN { state=0; }
                        /band No/                            {  state++; };
                        $0 == counter && state != 0;         { print $1 >> "bands.txt"; i++; };
                        $0 == counter && state == 0;         { };
                        $0 =! counter                        { };' OUTCAR
    done
  done
[\code]

So I made this script executable using the command 

[code]
chmod +x FILENAME.sh
[\code]

(This is Mac OSX 7.0, by the way)

Then when I tried to run it (./FILENAME.sh) I got this error, which i have never encountered before:

./bands_control.sh: line 4: 8: No such file or directory

Could this be a bug somewhere, or a genuine mistake in the code?

---

### Post by drmrgd on 2012-08-30
I think you're mis-calling your variables lines 4 and 8.  Try as $i and $j

---

### Post by steeldriver on 2012-08-30
Also I don't think the 'single bracket' test syntax allows the '<' numerical operator - you could do either

```
while [ $j -lt 8 ]
```or use the [[ form

```
while [[ $j < 8 ]]
```[As well, please preview your posts to make sure the tags are working!]

---

### Post by drmrgd on 2012-08-30
> **steeldriver said:**
> Also I don't think the 'single bracket' test syntax allows the '<' numerical operator - you could do either

```
while [ $j -lt 8 ]
```or use the [[ form

```
while [[ $j < 8 ]]
```[As well, please preview your posts to make sure the tags are working!]

Oh!  I totally missed that.  Good call!

---

### Post by telemaster on 2012-08-30
```

#!/bin/bash
$j=1;
$i=1;
while [[ $j < 8 ]]
  do
    
    if [$i==30]
      then
       j++;
        i=1;
     fi

    
    while [ $i < 30 ]
    do
    awk -v counter=$j ' BEGIN { state=0; }
                        /band No/                            {  state++; };
                        $0 == counter && state != 0;         { print $1 >> "bands.txt"; i++; };
                        $0 == counter && state == 0;         { };
                        $0 =! counter                        { };' OUTCAR
    done
  done







```

Changed as above, now it associates one of the values with a command as well:

./bands_control.sh: line 7: 3: command not found
./bands_control.sh: line 14: 30: No such file or directory

I am baffled, how is that bash ends up interpreting numbers as objects with meaning outside the program?

---

### Post by steeldriver on 2012-08-30
it's the same problem - go read up on which test constructs take which operators (remember you are trying to do an integer comparison)

[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

[http://tldp.org/LDP/abs/html/testconstructs.html#DBLBRACKETS](http://tldp.org/LDP/abs/html/testconstructs.html#DBLBRACKETS)

---

