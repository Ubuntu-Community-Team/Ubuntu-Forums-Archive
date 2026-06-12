---
title: "new to programming - need help with python error!!!!!"
date: 2012-02-06
forum: General Help
---

### Post by watercoloring on 2012-02-06
i'm trying to write a program that has a user input a number and then sums all the cubes from 0 to that number. i wrote that fine and my program works and everything. but now i'm trying to have it check to see if what the user entered is an integer and if it's not it needs to stop and print my error message. i have been working on this for HOURS and i cannot figure out how to make it work. please help!! thank you :) 

here's my code, hopefully it will post correctly. i'm new to these forums too. 



n = input ("Enter the number of cubes to sum: ")
s = 0
orig = n
isinstance (n, str):
    print ("You did not enter a number; you must enter a non-negative number")
    return 
if n < 0:
    print ("You entered a negative number; you must enter a non-negative number")
else:
  s = s + n**3 
  n = n - 1
  print ("The sum of the first %d cubes is %d" % (orig, s))

---

### Post by watercoloring on 2012-02-06
oh crap. umm pretend there are indents where there should be

---

### Post by watercoloring on 2012-02-06
also please let me know if i posted this in the wrong area of the site :/

---

### Post by Vaphell on 2012-02-06
programming subforum
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

and when you want to post code put it in [code] [****/code] tags

---

