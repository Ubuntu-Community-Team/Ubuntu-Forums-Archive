---
title: "need help executing a python file"
date: 2010-09-25
forum: General Help
---

### Post by maxrpowell on 2010-09-25
I have a python file for finding prime numbers. but when i run it in the terminal it does nothing. I have very little knowledge of python and would appreciate if someone could tell me if this is supposed to give any output and/or how i can make it show me the primes that it finds

here is the script

> def erat_sieve(bound):
   if bound < 2:
      return []
   max_ndx = (bound - 1) / 2
   sieve = [True] * (max_ndx + 1)
   #loop up to square root
   for ndx in range(int(bound ** 0.5) / 2):
      # check for prime
      if sieve[ndx]:
         # unmark all odd multiples of the prime
         num = ndx * 2 + 3
         sieve[ndx+num:max_ndx:num] = [False] * ((max_ndx-ndx-num-1)//num + 1)
   # translate into numbers
   return [2] + [ndx * 2 + 3 for ndx in range(max_ndx) if sieve[ndx]]


---

### Post by niteshifter on 2010-09-25
Hi,

What you've posted is a python function, that is, a subroutine. It produces no output to the screen. It returns a result. To use:

```
# clean up and paste erat_sieve
# here
b = 4  # example, setting bound to 4.
print erat_seive( b )

```

Notice where I wrote clean up erat_sieve: Python is sensitive to indentation. What you posted will not work "as-is". Stuff under def needs
to be indented, as does under if statements and under for statements.

I'll get you started:
```
def erat_sieve(bound):
    if bound < 2:
        return []
    max_ndx = (bound - 1) / 2

```

After cleaning up, save the file, let's call it eratprime.py
and save it in your home folder.
To run:
```
python ~/eratprime.py
```

Analysis of the code posted (Sieve of Eratosthenes) and how to indent, along with how to make the script stand-alone is left as an exercise for the student ;)

---

### Post by maxrpowell on 2010-09-25
thank you. I'll try it out and post results

---

### Post by maxrpowell on 2010-09-25
```
def erat_sieve(bound):
	if bound < 2:
		return []
	max_ndx = (bound - 1) / 2
	sieve = [True] * (max_ndx + 1)
#loop up to square root
	for ndx in range(int(bound ** 0.5) / 2):
# check for prime
		if sieve[ndx]:
# unmark all odd multiples of the prime
			num = ndx * 2 + 3
		sieve[ndx+num:max_ndx:num] = [False] * ((max_ndx-ndx-num-1)//num + 1)
		# translate into numbers
		return [2] + [ndx * 2 + 3 for ndx in range(max_ndx) if sieve[ndx]]
b = 40000  # example, setting bound to 4.
print erat_sieve( b )
```

this is my end result. It works great. Thanks. How could i get it to print to a .txt file?

---

### Post by maxrpowell on 2010-09-25
Maybe I could get a code to count how long it takes to find all of the primes. I would like to improve on the sieve and and finder a faster sieve.

---

### Post by niteshifter on 2010-09-26
> **maxrpowell said:**
> Maybe I could get a code to count how long it takes to find all of the primes. I would like to improve on the sieve and and finder a faster sieve.

In a terminal type:
```
man time
```

Output to a file? Many ways. [Here]("http://www.python.org/doc/") (python.org) is a good place, find the version of Python you are using, check out the Tutorial (chap 7). The package devhelp is also handy: Python is normally installed with it's documentation, devhelp will display it and let's you navigate much like a web browser.

Not that I mind answering questions - I enjoy it - but consider "fishing where they be biting" by posting "programming stuff" in the Development & Programming / Programming Talk forum. My participation in the forums is on and off depending upon life's intrusions* and you'll find no shortage of helpful folk there :)

*Such as this weekend, can't work, nursing an extracted wisdom tooth.

---

### Post by maxrpowell on 2010-09-26
than you!

---

