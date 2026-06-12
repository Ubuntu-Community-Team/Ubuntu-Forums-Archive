---
title: "Liberty Basic Question - Standard Deviation Formula"
date: 2010-04-06
forum: General Help
---

### Post by greeneyes on 2010-04-06
I am working on a homework question and I cannot get it to work. 

The problem says to input a list of numbers in an array and calculate the mean and standard deviation of the numbers. 

The mean comes out correctly but the standard deviation is not correct and my program is not inputing all the numbers entered. 

Can anyone help?

sum = 0
count1 = 0
mean = 0
count2 = 0
x = 0
sumx2 = 0
standeviation = 0
variance = 0
sumsigma = 0
frequencysum = 0

dim num(999)




Input "Please enter a number (press 0 when selections are complete): ";num(x)
while num(x) <> 0
    count1 = count1 + 1
    sum1 = sum1 + num(x)
    mean = sum1 /count1
    frequencysum = frequencysum + ((num(x) - mean)^2)
x = x+1
Input "Please enter a number (press 0 when selections are complete): ";num(x)
wend

for x = 0 to (x-1)
print "Entry ";x+1;": ";num(x)
next x

If num(x) = 0 then
Print "Exiting Program"

    fraction = frequencysum / (count1 - 1)
standeviation = sqr(fraction)
print "Mean = ";mean
print "Standard deviation = ";standeviation

end if

---

### Post by gmargo on 2010-04-06
> **greeneyes said:**
> 
    mean = sum1 /count1
    frequencysum = frequencysum + ((num(x) - mean)^2)


Inside your "frequencysum" calculation, you are using a running mean, not the overall mean.

---

### Post by Iowan on 2010-04-06
> While we are happy to serve as a _resource for hints and for asking questions when you get stuck and need a little help_, the Ubuntu Forums should not be thought of as a homework service. [s]Please do not post your homework assignments expecting someone else to do it for you.[/s] Any such threads will be taken offline and warnings or infractions may be issued.Closed for review...

Consensus is that you are using the forums as a resource (as intended) instead of expecting someone else to do it for you. Sorry for the inconvenience!

---

