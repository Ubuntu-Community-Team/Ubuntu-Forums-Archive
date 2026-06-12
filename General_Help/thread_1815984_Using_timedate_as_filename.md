---
title: "Using time/date as filename"
date: 2011-08-01
forum: General Help
---

### Post by Kallun on 2011-08-01
Hello there :)

I use a Hauppauge HD PVR capture card set up in Ubuntu using MythTV to capture the video output.

As it stands I have a launcher that runs an sh script with the necessary commands in to reach the desired directory, load the driver and then start the capture process. The part of the script that initiates the capture is:

```
cat /dev/video1 > Cap.ts
```

As you can see, this creates a ts video called 'Cap', I would like to be able to name the captured video as the time and date it was saved.

I have done a few searches, but each of my attempts fail.

If anyone could advise what I can put in place of 'Cap.ts' to achieve this, I would greatly appreciate it :D

Thanks in advance!

---

### Post by SoFl W on 2011-08-01
See if this works

```
> DT=$(date +"%b-%d-%y_%H-%M")
> cat /dev/video1 > Cap-$DT.ts
```If it does, set up a script or bash file and call that command instead of typing it each time.


**EDIT:**
Here are the date strings if you need them

> %a :   Abbreviated weekday name (Sun..Sat)
%b :  Abbreviated month name (Jan..Dec)
%B :    Full month name, variable length (January..December)
%d :   day of month (01..31)
%e :   day of month, blank padded ( 1..31)
%H :    24 hour format (00..23)
%I :   12 hour format (01..12)
%j :   day of year (001..366)

---

### Post by hakermania on 2011-08-01
```

cat /dev/video1 > "$(date '+%a') $(date '+%d') $(date '+%h') $(date '+%H'):$(date '+%M'):$(date '+%S')"

```

---

### Post by blind2314 on 2011-08-01
> **SoFl W said:**
> See if this works
 
```
> DT=$(date +"%b-%d-%y")
> cat /dev/video1 > Cap-$DT.ts
```
 
If it does, set up a script or bash file and call that command instead of typing it each time.
 
 
While 'hakermania's answer is correct, this one wins for succintness and readability (which makes a big difference, trust me, especially when you want to modify your script or have to debug it in the future).

---

### Post by Kallun on 2011-08-01
Awesome, thanks for the swift replies guys!

I'll test this out as soon as I'm home :)

---

### Post by Kallun on 2011-08-01
One quick question actually, do I need the '>' in front of those two lines in my script?

As it stands it's something along the lines of

```
cd /home/****/Videos/Capture/ && modprobe hdpvr && cat /dev/video1 > Cap.ts
```

How would I go about implementing SoFl W's suggestion? :)

---

### Post by blind2314 on 2011-08-01
> **Kallun said:**
> One quick question actually, do I need the '>' in front of those two lines in my script?
 
As it stands it's something along the lines of
 
```
cd /home/****/Videos/Capture/ && modprobe hdpvr && cat /dev/video1 > Cap.ts
```
 
How would I go about implementing SoFl W's suggestion? :)
 
```
DT=$(date +"%b-%d-%y_%H-%M")
cd /home/****/Videos/Capture/ && modprobe hdpvr && cat /dev/video1 > $DT.Cap.ts
```

---

### Post by nothingspecial on 2011-08-01
> **SoFl W said:**
> See if this works

```
> DT=$(date +"%b-%d-%y_%H-%M")
> cat /dev/video1 > Cap-$DT.ts
```If it does, set up a script or bash file and call that command instead of typing it each time.




You don't need to put the output of the date substitution in a variable and then expand the variable in another command.
```

cat /dev/video1 > Cap-$(date +"%b-%d-%y_%H-%M").ts
```

---

### Post by Kallun on 2011-08-01
> **blind2314 said:**
> ```
DT=$(date +"%b-%d-%y_%H-%M")
cd /home/****/Videos/Capture/ && modprobe hdpvr && cat /dev/video1 > $DT.Cap.ts
```

Cheers! This'll save me a lot of hassle

---

### Post by blind2314 on 2011-08-01
> **nothingspecial said:**
> You don't need to put the output of the date substitution in a variable and then expand the variable in another command.
```

cat /dev/video1 > Cap-$(date +"%b-%d-%y_%H-%M").ts
```
 
True. However, this gives the advantage of having to only modify one location to change the 'date' command, if he decides to make his script more robust or use the same data in multiple places.

---

### Post by hakermania on 2011-08-01
> **blind2314 said:**
> While 'hakermania's answer is correct, this one wins for succintness and readability (which makes a big difference, trust me, especially when you want to modify your script or have to debug it in the future).

&#921; know :) I just gave the quick solution :)

---

### Post by SoFl W on 2011-08-01
I think you have your question answered but the ">" was used to represent the prompt.

If this worked, please mark this as "[solved]" with the "thread tools" option at the top of the thread.

---

### Post by Kallun on 2011-08-01
All worked great, thanks for the help guys! :D

---

