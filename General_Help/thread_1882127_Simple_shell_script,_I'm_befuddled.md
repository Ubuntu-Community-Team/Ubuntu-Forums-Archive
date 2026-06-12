---
title: "Simple shell script, I'm befuddled"
date: 2011-11-16
forum: General Help
---

### Post by W@@dy on 2011-11-16
I'm using bash script and...well I'm absolutely confused by the output.
It's a simple task, calculating Hohmann orbit transfer for KSP.
I haven't finished the formula yet as I'm still learning basic math functions of script.

Here's the code

```
echo -n Departure Radius:
read depart_Radi
echo -n Arrival Radius:
read arriv_Radi

v1_Temp="sqrt(518771785000000000000000/$depart_Radi)"| bc -l
v1_Temp2="sqrt((2*$arriv_Radi)/($depart_Radi + $arriv_Radi)) - 1"| bc -l
v1=$(expr $v1_Temp \* $v1_Temp2)
echo $v1
```

I've been entering 90 000 and 80 000  (no spaces) as the two variables.
The output of this script is a listing of the folders in my current directory O_o
Without 'echo $v1' nothing is printed out. So I guess that list is being attached to $v1, but I don't know why

I had a lot of issues getting the multiplication function to work, but I think I've got it now...Idk if that's any source of error there.

My only guess is that there's a mistake somewhere causing the variable to default to my current directory.
I just checked to see if using 'echo -n' then reading the data off there would cause the issue, but removing '-n' didn't change anything.

---

### Post by Vaphell on 2011-11-16
you need to capture the output for v1_Temp and v1_Temp2, just like you did in case of v1: $( ), also you need to echo the formula to pass it further, string alone won't do ( echo FORMULA | bc -l )
print out temp variables, you will see they store nothing

---

### Post by Jose Catre-Vandis on 2011-11-16
There is something wrong with the formulas in v1_Temp and v1_Temp2 as they don't return anything if you echo them, thus the calculation in v1 is trying to work on two "nothings" which in a clever way is return the output of "ls"

---

### Post by W@@dy on 2011-11-16
So it should look more like this?

```

echo -n Departure Radius:
read depart_Radi
echo -n Arrival Radius:
read arriv_Radi

v1_Temp=$(echo sqrt(518771785000000000000000/$depart_Radi))| bc -l
v1_Temp2=$(echo sqrt((2*$arriv_Radi)/($depart_Radi + $arriv_Radi)) - 1)| bc -l
v1=$(expr $v1_Temp \* $v1_Temp2)
echo $v1
```

Why exactly does it need 'echo'?
You said to pass it on further, but isn't that what pipes '|' do?

---

### Post by mutley89 on 2011-11-17
Something like this
```

echo -n Departure Radius:
read depart_Radi
echo -n Arrival Radius:
read arriv_Radi

v1_Temp=$(echo "sqrt(518771785000000000000000/$depart_Radi)"| bc -l)
v1_Temp2=$(echo "sqrt((2*$arriv_Radi)/($depart_Radi + $arriv_Radi)) - 1"| bc -l)
v1=$(echo "$v1_Temp * $v1_Temp2" | bc -l)

```The echo is needed to send the quoted string to stdout. Pipes pass the stdout of 1 command to the stdin of another. The $(...) construction is replaced with the output of the command inside the brackets.  

You could also echo and pipe the last 3 lines to bc in one go, use ';' to separate the bc statements.  If your formulas get more complex you can also write them in a separate bc script , then call this from bash as follows(assuming that you have called the variables arrival and depart in the bc script):
```

echo "arrival = $arriv_Radi; depart = $depart_Radi;" | bc -l /dev/stdin yourbcfile

```wrap this with "variable=$(...)" if you want to assign it to a variable

---

### Post by W@@dy on 2011-11-17
Ah thank you very much. I understand the echo part now clearly.
 
I was aware that I could put all those lines into 1 line, but I decided to separate them since I was having issues.
Having multiple lines helps me locate any bugs and tells me if it's a reoccuring bug (indicating I am misunderstanding some syntax or concept) or if it's a simple typo.
 
Thank you very much, I'll report back with my results when I get some time to test it out

---

### Post by matt_symes on 2011-11-17
Hi

You are are going to have a whole load of problems here, i think, doing it the way you are trying to.

For a start, because of the size of the numbers i believe you are going to get overflows. Take a look at this.

```

matthew@matthew-Aspire-7540:~$ echo $((518771785000000000000000 / 10));
-599858493372009676
matthew@matthew-Aspire-7540:~$  
```The above calculation is nonsense unless the is some kind of overflow going on.

You will also have problems with integer division and will lose precision because of that.

You can do something what you are trying to achieve using here documents but this will not work. It's shown as an example only.

```

#!/bin/bash
echo -n Departure Radius:
read depart_Radi
echo -n Arrival Radius:
read arriv_Radi

v1_Temp=$(bc << END_BIT
sqrt($((518771785000000000000000 / $depart_Radi))) # Overflow problems here.
END_BIT
);

v1_Temp2=$(bc << END_BIT
sqrt($(($((2 * $arriv_Radi)) / $(($depart_Radi + $arriv_Radi))))) - 1 # Precision loss here.
END_BIT
);

v1=$(($v1_Temp * $v1_Temp2))
echo $v1
```> **Jose Catre-Vandis said:**
> There is something wrong with the formulas in v1_Temp and v1_Temp2 as they don't return anything if you echo them, thus the calculation in v1 is trying to work on two "nothings" which in a clever way is return the output of "ls"

Just to clarify the last line is (somehow) returning

```
echo *
```That will return all the files and directories in the current working directory.

```
matthew@matthew-Aspire-7540:~/tmp_desktop$ echo *
test1 test2
matthew@matthew-Aspire-7540:~/tmp_desktop$
```Very useful if *ls* stops working as the *cd* command is also a bash builtin.

EDIT: Someone will correct me in this post if i have missed something as it's late here.

Kind regards

---

### Post by Vaphell on 2011-11-17
i don't think there will be an overflow problem, OP doesn't use builtin integer division anywhere, everything is done by bc and there is no $(()) in equation strings

```
$ echo "518771785000000000000000 / 10" | bc -l
51877178500000000000000.00000000000000000000
$ echo "sqrt(518771785000000000000000 / 10)" | bc -l
227765621857.20653659403003937206
$ echo "227765621857.20653659403003937206^2" | bc -l
51877178499999999999999.99999999555291152602
```
looks ok

---

### Post by matt_symes on 2011-11-17
Hi
[FONT=monospace]
[/FONT]> [FONT=monospace][/FONT]echo "518771785000000000000000 / 10" | bc -l

That's because, in this case, bc is doing the calculation and not the shell.

It's an interesting point and maybe that's the way to do it.

Kind regards

---

### Post by matt_symes on 2011-11-17
Hi

Thanks for keeping me honest Vaphell :)

```
#!/bin/bash
echo -n Departure Radius:
read depart_Radi
echo -n Arrival Radius:
read arriv_Radi

v1_Temp=$(echo "sqrt(518771785000000000000000/$depart_Radi)" | bc -l);
v1_Temp2=$(echo "sqrt((2*$arriv_Radi)/($depart_Radi + $arriv_Radi)) - 1" | bc -l);

v1=$(echo "$v1_Temp * $v1_Temp2" | bc -l)
echo $v1

```Kind regards

---

### Post by W@@dy on 2011-11-17
Script works! Thanks for the help!

Unfortunately the formula is wrong for some reason >_>
I bet a mistake in the order of operations arose out me splitting the formula across multiple lines.

Ah well, I can go to another forum for help on that :D

Thanks again, and if you're wondering why, I found a game called Kerbal Space Program. It's a light, humours, space-flight sim. The game is for windows, but it runs on Wine as far as I've seen. Keep in mind the game is early alpha though, and highly un-optimized currently. It might be pretty slow on Wine. Next update will be the last of the free versions and optimizations out the wazoo

---

