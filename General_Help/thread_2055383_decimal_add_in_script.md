---
title: "decimal add in script"
date: 2012-09-09
forum: General Help
---

### Post by vagelism on 2012-09-09
Hello to all.
I have a script to make a function that I need.
In fact it takes a temperature of a sensor and send it to a server. 
**So the firs question:**
The problem is that it is not sending a double but an indiger.
So for example the sensor sends me a temperature of 281 that means 28,1 and then I calculate it by divide the 281 by 10. But I get 28 and not 28,1.
Here is the code
```
TEMP=`snmpwalk -v 1 -c public 192.168.1.2 iso.3.6.1.4.1.38783.3.9.0 | cut -d" " -f4` 
echo $TEMP
REALTEMP=`expr $TEMP / 10 `   
echo $REALTEMP
```

How can I solve this problem?
**The second question:**

How can I make the script run every 5 or 10 minutes insteade of my executing it on the shell?

THANK YOU ALL!

---

### Post by sisco311 on 2012-09-09
Check out:
[http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)
and BashFAQ 022 (link in my signature)
oh and [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

I'd try something like:
```

num=123
echo ${num%?},${num:${#num}-1}

``` ;)

---

### Post by d3v1150m471c on 2012-09-09
..?

---

### Post by vagelism on 2012-09-09
I dont get it? I am not an expert on bash commands!
Can you clarify more please?

---

### Post by codemaniac on 2012-09-09
> **vagelism said:**
> Hello to all.
I have a script to make a function that I need.
In fact it takes a temperature of a sensor and send it to a server. 
**So the firs question:**
The problem is that it is not sending a double but an indiger.
So for example the sensor sends me a temperature of 281 that means 28,1 and then I calculate it by divide the 281 by 10. But I get 28 and not 28,1.
Here is the code
```
TEMP=`snmpwalk -v 1 -c public 192.168.1.2 iso.3.6.1.4.1.38783.3.9.0 | cut -d" " -f4` 
echo $TEMP
REALTEMP=`expr $TEMP / 10 `   
echo $REALTEMP
```

How can I solve this problem?
**The second question:**

How can I make the script run every 5 or 10 minutes insteade of my executing it on the shell?

THANK YOU ALL!
you can use bc .

Something like below .

```
REALTEMP=`echo "$TEMP/10" | bc -l`
```

---

### Post by vagelism on 2012-09-09
> **codemaniac said:**
> you can use bc .

Something like below .

```
REALTEMP=`echo "$TEMP/10" | bc -l`
```

Yes I was looking bc and trying to find out how to use correct the quotes!
Let me try.
Thank you!

---

### Post by vagelism on 2012-09-09
Works great! But it has scale of 20 that is the default, how can I do it to be in scale of 1 in my script?
Thank you!

---

### Post by thnewguy on 2012-09-09
To get your script to run on a regular basis, you can add it to your crontab file. Run

crontab -e

And add a line that reads something like

15 * * * * /home/youruser/temperature_script

Save the file and close the editor. This will run your script 15 minutes past the hour, every hour. You can add additional lines to run the script multiple times per hour.

---

### Post by codemaniac on 2012-09-09
> **vagelism said:**
> Works great! But it has scale of 20 that is the default, how can I do it to be in scale of 1 in my script?
Thank you!

```
REALTEMP=`echo "scale=1;$TEMP/10" | bc`
```

---

### Post by vagelism on 2012-09-09
> **vagelism said:**
> Works great! But it has scale of 20 that is the default, how can I do it to be in scale of 1 in my script?
Thank you!

solved that with the
code
```
REALTEMP=`echo  "scale=1; $TEMP/10"  | bc -l`
```

Now lets try the repeate problem!
Thank you since now!

---

### Post by vagelism on 2012-09-09
> **thnewguy said:**
> To get your script to run on a regular basis, you can add it to your crontab file. Run

crontab -e

And add a line that reads something like

15 * * * * /home/youruser/temperature_script

Save the file and close the editor. This will run your script 15 minutes past the hour, every hour. You can add additional lines to run the script multiple times per hour.

I try to do it by this way
```
1 * * * * sh /home/unknown/Desktop/TEST/test.sh

```

but no resault!
Anything wrong with my script?
Thank you!

---

### Post by codemaniac on 2012-09-09
> **vagelism said:**
> I try to do it by this way
```
1 * * * * sh /home/unknown/Desktop/TEST/test.sh

```

but no resault!
Anything wrong with my script?
Thank you!

Why you are using sh infront of the script , may be it is overriding bash and forcing your script to run with bourne shell .

Please also make sure your script has the executable bits on .

---

### Post by vagelism on 2012-09-09
> **codemaniac said:**
> Why you are using sh infront of the script , may be it is overriding bash and forcing your script to run with bourne shell .

Please also make sure your script has the executable bits on .

You was write about the executable bit. I was confused...but I could run it on bash without this bit! 
Anyway , I also removed that sh infrond and now my next question...
Do I have to run the crontab as sudo or regular user "unknown" in my case?
Thank you!

---

### Post by codemaniac on 2012-09-09
i dont know if you require superuser privileges to run snmpwalk .
just try out and see yourself .

---

### Post by vagelism on 2012-09-09
No this runs with no sudo ! But nothing works even with sudo or not! :(

---

### Post by codemaniac on 2012-09-09
> **vagelism said:**
> No this runs with no sudo ! But nothing works even with sudo or not! :(

cron is not good at detecting your environment sometimes ,you can try the absolute path of snmpwalk in your script . i.e /absolute/path/to/snmpwalk .

---

### Post by vagelism on 2012-09-09
thanks
!

---

### Post by codemaniac on 2012-09-09
Did it solve your problem ?

---

### Post by vagelism on 2012-09-09
No...! I did all your advices! Is not working! Ouf!!!

---

### Post by codemaniac on 2012-09-09
One more thing if it helps ,the first field in your crontab file denotes minute .Have you tried to give the value "01" instead of "1" .

---

### Post by vagelism on 2012-09-09
I tried it. I will try it again to see if it works!
Thank you!

---

### Post by vagelism on 2012-09-09
Any other way more convinient to run something periodicaly?
Thank you!

---

