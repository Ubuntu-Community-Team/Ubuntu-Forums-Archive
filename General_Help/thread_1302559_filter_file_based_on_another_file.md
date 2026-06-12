---
title: "filter file based on another file"
date: 2009-10-27
forum: General Help
---

### Post by daveli on 2009-10-27
Dear list
I am trying to filter by row numbers a delimited text file with 8 columns (myfile.txt) , based on the row numbers included in another text file (rows.txt). myfile.txt has 5 million rows and the rows.txt file has 2 million positions in one single column. 
I checked for examples of grep similar to this problem with no luck. I tried using ```
grep -f rows.txt myfile.txt >filtered.txt
``` but the output is empty. 

Can anyone help me with this? maybe grep is not the right option?

thanks for your help

Dave

---

### Post by Giblet5 on 2009-10-27
Can you post example content from both files?

There's always a way to do it...

Assuming rows.txt looks like ```
13
125
17177
...
```

Then the following, while slow, will do the job: ```
for i in `cat rows.txt`
do
    if [ "$ix" -neq "x" ] ; then
        sed -n $ip myfile.txt
    fi
done
```

If you want that done quickly, you'd be much better off writing a python or perl script, or a dedicated C program.

---

### Post by daveli on 2009-10-27
thanks a lot for the quick answer!

that is right, the rows.txt file is as you say, and here is a short head output of myfile.txt (which had 7 and not 8 columns!)

ref1        1       G       0       @       @       @
ref1        2       A       0       @       @       @
ref1        3       G       0       @       @       @

I will try your suggestion while I struggle with a Perl script.

Best,

Dave

---

### Post by daveli on 2009-10-27
Sorry again, but your script gave an error which I can't work out:

line 3: [: -neq: binary operator expected


could you please explain to me how to sort it out?

---

### Post by Giblet5 on 2009-10-27
> **daveli said:**
> Sorry again, but your script gave an error which I can't work out:

line 3: [: -neq: binary operator expected


could you please explain to me how to sort it out?

Here's a full-on script ```
#!/bin/bash

for row in `cat rows.txt`
do
    if [ "$row" = "" ] ; then
        :
    else
        sed -n $rowp myfile.txt
    fi
done

exit 0
```

If you need specific columns from the output, use the "cut" command.

---

### Post by daveli on 2009-10-27
sorry Giblet5, but it still does not work. I get another error saying that a command is missing. What I am doing is saving the script to a .sh file and redirecting the output to a results file.

```
$bash /home/dave/Programs/filterRows.sh >results.txt
sed: -e expression #1, character 1: command missing (translated from spanish)
```

---

### Post by Giblet5 on 2009-10-27
> **daveli said:**
> sorry Giblet5, but it still does not work. I get another error saying that a command is missing. What I am doing is saving the script to a .sh file and redirecting the output to a results file.

```
$bash /home/dave/Programs/filterRows.sh >results.txt
sed: -e expression #1, character 1: command missing (translated from spanish)
```

We're just using sed to extract specific lines from the data.

```
sed -n 1p data.txt
```
will print the first line of data.txt

```
sed -n 10176p data.txt
```
will print the ten thousand one hundred seventy sixth line of data.txt

The code I provided reads line numbers (rows) from the first file and passes them as the numeric argument to sed.

If the first file has something in it other than positive integers, there will be trouble...

You should verify that the first file, rows.txt, contains only positive integers.

---

### Post by daveli on 2009-10-27
All lines seem to be positive.

```
$wc -l rows.txt
2453365 rows.txt
$awk '$1>0' >aaaa.txt
$wc -l aaaa.txt
2453365 aaaa.txt

```

---

### Post by daveli on 2009-10-27
Giblet5, I think the problem lies around "$rowp"

it seems not to recognise the parameter p after variable $row and is taking it as a new variable name.

I changed it tothe following and seems to be working now (at least no error)
sed -n $row"p" myfile.txt[FONT=Verdana]


[/FONT]

---

### Post by Giblet5 on 2009-10-27
> **daveli said:**
> All lines seem to be positive.

```
#!/bin/bash

for row in `awk '{ printf("%dp\n",$1); }' rows.txt`
do
    sed -n $row myfile.txt
    if [ $? -ne 0 ] ; then
        echo "sed -n $row failed"
        break
    fi
done

exit 0
```

---

### Post by Giblet5 on 2009-10-27
I changed the script and verified that it works on small data sets.

---

