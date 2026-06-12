---
title: "Beginner, need help with Shell scripting, please :)"
date: 2011-09-07
forum: General Help
---

### Post by iane_casey on 2011-09-07
Hi! I just registered tonight, so I'm new here! ):P

 It's hard searching for lectures on Google, so I thought of just going directly here to get some help. We're currently taking shell scripting in school, so I'm a beginner with scripting in Ubuntu gNatty :)

I was wondering if somebody could please help me with this simple program given to us as an assignment...

Here is the given problem:
Input employee name, rate per hour, hours worked and compute for the  daily wage of an employee. If the number of hours exceeds 8 hours, add  30% to each excess hour as overtime rate. 

(Below is what I have so far...)[COLOR=Navy]

clear
echo "Employee:"
read emp
echo "Rate/hour: "
read rph
echo "Hours worked: "
read hw
dw=$`echo "scale=2; $rph*$hw" | bc`
if [ $hw -le "8" ]
then 
    echo "Employee's Daily Wage= $dw "
else
    **ot=$`echo "scale=2; #I am having trouble with this**
    dw=$`echo "scale=2; $rph*$hw+ot" | bc`
    echo "Employee's Daily Wage= "
fi
[/COLOR]

I have the small program done already, but I'm confused as to how I am to compute for the overtime pay (ot). I honestly do not know how I am to count the hours beyond 8 so that I could add 30% to each hour. 

It would really mean a lot if anyone could help ( and additional tips would be awesome!) :) 

Thanks for taking the time to read! 

~IC

---

### Post by CharlesA on 2011-09-07
We don't really help with homework questions.

---

