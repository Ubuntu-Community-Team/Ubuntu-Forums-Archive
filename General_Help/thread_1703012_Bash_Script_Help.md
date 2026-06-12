---
title: "Bash Script Help"
date: 2011-03-08
forum: General Help
---

### Post by gtirsmiley on 2011-03-08
Hello, 

Firstly i'd like to introduce myself before I ask my question, i am currently studying a "Network Operating System 2" course, and in the syllabus the professor decided to use Ubuntu Linux for us.

This is a first for me and I am truly greatly interested in the OS. It seems like a solid system once you get to know the deep foundations of it.

The professor has already given us an assignment, but I feel its not fair as its just a bit too much from out of what he taught us .. He did not teach us what he is asking for.

He asked us to create to a text file which lists the Sales from two Salespersons, and each one will have an amount for each month .. So 12 entries for each salesperson.

Using that text file, we should write a bash script which would read the values from the above text file, and produce a "Monthly Sales" text file, which shows the total sales of each month (combined from both the salespersons)..

I would like to ask for some guidance, some help on how to start. It's just that he didn't teach us any commands about this matter..

Thank you so much for reading !

I understand this may be looked down upon, but please note I am just looking for directions on how to start.

---

### Post by AlphaLexman on 2011-03-08
Generally, homework questions are frowned upon in the forums.

However, since it seems you have the liberty to create you own sales data, you should do so in a way that you are comfortable in extracting it. Keep in mind how you separate your data between fields.

---

### Post by gtirsmiley on 2011-03-08
> **AlphaLexman said:**
> Generally, homework questions are frowned upon in the forums.

However, since it seems you have the liberty to create you own sales data, you should do so in a way that you are comfortable in extracting it. Keep in mind how you separate your data between fields.

I completely understand about the homework questions being frowned upon in forums, as I expect people just post their assignments and assume someone to do it for them.

However, I am not doing that, rather just looking for advice on how to begin.

Im just annoyed because the most we have learned in our class is arrays, and we briefly touched upon for loop.

I am trying to learn by myself but can't see what to apply in this scenario?

---

### Post by AlphaLexman on 2011-03-08
As I stated before I will NOT do your homework for you. Post your data, what you have tried, what your expected results are, and where you are running into problems. 

Sometimes there is more than one way to a solution, and one can get stuck into forcing a direction... I've been there more than once!

---

### Post by pqwoerituytrueiwoq on 2011-03-08
you should start with googleing "sh math" and "sh read file"

BTW sh math only supports integers not float
15/2*10 will give you 70 cause 15/2 gets the decimal cut off

---

### Post by blueridgedog on 2011-03-08
The first thing I would do is some research on shell scripting.  

There are thousands of sites like this one:  [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

The next would be to chart how you wanted your script/application to work.  You can share your ideas here and get feedback.  Break the challenges and the learning into pieces.  How do you open and read a file?  How to you do you read lines of the file and parse values?  How to you do math on running totals?  How do you write to a file?

Finally, I would start trying to implement blocks of the chart.  You can also share those efforts here and get help with the specific problems you encounter.  If you post some code that attempts to do one small part of your overall goal and a statement as to what is working and what is not working, you will get some pointers.

For a person with shell scripting experience, your assignment is about a hour's worth of work.  To learn each step then test it and move on to the next, may take a few days.  I know it is sometimes hard to find a beginning with a complex problem, so start with the basics.

---

### Post by sisco311 on 2011-03-08
> **blueridgedog said:**
> 
There are thousands of sites like this one:  [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)


Unfortunately most of the sites/guides are outdated and/or full of bugs.

The only site I would recommend for a beginner is:  [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) along with BashFAQ and BashPitfalls on the same wiki.

> **blueridgedog said:**
> 
The next would be to chart how you wanted your script/application to work.  You can share your ideas here and get feedback.  Break the challenges and the learning into pieces.  How do you open and read a file?  How to you do you read lines of the file and parse values?  How to you do math on running totals?  How do you write to a file?

Finally, I would start trying to implement blocks of the chart.  You can also share those efforts here and get help with the specific problems you encounter.  If you post some code that attempts to do one small part of your overall goal and a statement as to what is working and what is not working, you will get some pointers.


a big +1

> **blueridgedog said:**
> 
For a person with shell scripting experience, your assignment is about a hour's worth of work.


Which includes a working and bug-free code with proper error handling and good comments, massive testing and a coffee break. :)

> **blueridgedog said:**
> 
To learn each step then test it and move on to the next, may take a few days.  I know it is sometimes hard to find a beginning with a complex problem, so start with the basics.

once again, a big +1

---

### Post by gtirsmiley on 2011-03-09
Thanks for all the responses. I will try to start on a small code in the next few days and will post it here for you all to see and hopefully not have to help me too much.

---

### Post by Habitual on 2011-03-09
Here's a sample of 3 ways to do math in a shell environment:

Split a Car Rental and a Hotel Bill for a week with a co-worker?
```
echo -n $;echo "scale=2; 408.55+1008.56/2" | bc
```

$912.83

or

Simple addition and subtraction problems:

```
echo "1+1" | bc
```
or
```
echo $(( 1+1 ))
```

HTH.

---

### Post by gtirsmiley on 2011-03-11
Well i'm trying to work on it now .. its been about 2 hours and I haven't managed anything to work successfully..

i've formatted the Sales text file in the following manner
```

Salesman 1
100
200
300
400
500
600
700
800
900
1000
1100
1200

Salesman 2
1200
1100
1000
900
800
700
600
500
400
300
200
100

```In my script file im trying to do something like read the contents into an array .. 

#!/bin/bash
mapfile -t p1array < <(grep -A 12 "Salesman 1" Sales)
mapfile -t p2array < <(grep -A 12 "Salesman 2" Sales)
echo ${p1array[@]}
echo ${p2array[@]}

Just want to check if im in the right path? The following command shows this in the terminal once run:

Person A 100 200 300 400 500 600 700 800 900 1000 1100 1200
Person B 1200 1100 1000 900 800 700 600 500 400 300 200 100

How would I go about next..

---

### Post by sisco311 on 2011-03-11
Now you need a loop to calculate the "Monthly Sales". In pseudocode:
```
for index in 1..12
do
  print sum = p1array[index] + p2array[index]
done

```

---

### Post by gtirsmiley on 2011-03-11
I managed to get everything to work.

Just wanted to know if its possible to use decimal values in the Sales list, trying to do so results in an error: invalid arithmetic operator (error token is ".50")

---

### Post by sisco311 on 2011-03-11
BASH does not have built-in floating point arithmetic. You have to use an external program like bc, dc or awk. Check out: [http://mywiki.wooledge.org/BashFAQ/022](http://mywiki.wooledge.org/BashFAQ/022)

---

