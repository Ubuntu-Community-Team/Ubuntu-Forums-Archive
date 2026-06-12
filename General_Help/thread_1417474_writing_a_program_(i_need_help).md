---
title: "writing a program (i need help)"
date: 2010-02-27
forum: General Help
---

### Post by marcus00 on 2010-02-27
i need help writing a program **that calculates world population growth each** **year for the next 75 years. useing the simplifying assumption that the current growth rate will stay constant. print results in table, the first column should display the year from year 1 to year 75, second column should display the anticipated world population at the end of that year, the third column should display the numerical increase** **in the world population that would occur that year, usein results determine the year in which the population would be double what it is today, if this years growth rate were to persist.    :popcorn: any help please**

---

### Post by DeadSuperHero on 2010-02-27
First thing I would do is write a simple algebraic formula detailing what you want, then find the programming language of your choice to write it in. Python ought to be fairly easy.

so, if y = 75, that's the variable we input for how many years.

I think it could work like

(Current population * years) + (numerical population increase * years) = desired number

(cp * y) + (npi*y) = x

Of course, this is off the top of my head and feels like I've missed something, but that's my general idea of an implementation.

Of course, if you wanted a GUI to display this, you would need to isolate the variables and have it show bars and numerical values based on each variable.

---

### Post by skierkyles on 2010-02-27
Python...
```

year = 2010
pop = 1000 #Obviously this isn't right, but I think you will get the picture
while year != 2086: #This is 2086 so that the while loop goes up to 2085 and NOT 2084
	print "Current Population: %d And The Year is: %d" % (pop, year) #Print the Current Population and Year here.
	
        pop_growth = pop * 0.05
	pop = pop + pop_growth #Now add to the population, whatever the expected growth rate is.
	year = year + 1 #Now add 1 to the year.
	

```

Obviously not the program, but the concept is pretty much the same.
Just do a loop, and have the population, and year be added to each time, until it reaches what ever year you want.

---

### Post by gmargo on 2010-02-27
You should read the book and do your own homework.

---

