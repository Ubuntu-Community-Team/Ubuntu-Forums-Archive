---
title: "Why does the following python script cause my terminal to crash under Ubuntu 8.04?"
date: 2009-07-28
forum: General Help
---

### Post by nickk on 2009-07-28
Hi,

I'm doing a program from project euler and noticed that this script causes my terminal to crash under ubuntu 8.04. Not a big deal for me but just curious as to why this happens.

```

def listUnique(seq):
        # Not order preserving
        keys = {}
        for e in seq:
                keys[e] = 1
        return keys.keys()
def findProperDivisors(num):
        divisors = []
        for x in range(1, int(num**0.5)+1):
                if num%x == 0:
                        divisors.append(x)
                        if num/x != num: divisors.append(num/x)
        divisors = listUnique(divisors)
        return divisors
def sumList(seq):
        ct = 0
        for x in seq: ct += x
        return ct

#generate all abundant numbers < 28123
abundantNumbers = []
for x in range(1, 28124):
        if sumList(findProperDivisors(x)) > x: abundantNumbers.append(x)

#print abundantNumbers
text = ''
for x in range(1, 28124):
        if x in abundantNumbers: text += 'x'
        else: text += '.'
print text
quit()

```

---

### Post by frunns on 2009-07-28
I'm just editing back and forth. Does it work in any other interpreter? Like Idle. Try some debugging, add some nonsense output to find out where exactly it crashes. And well, make it output to a file so you can see it even because it crashes.

---

### Post by DaithiF on 2009-07-28
Hi,
when you say it causes your terminal to crash, what does that mean specifically -- an error message is generated, or your terminal (e.g gnome-terminal) closes unexpectedly?

works ok for me, by the way :)

---

### Post by nickk on 2009-07-28
It prints the output but then the terminal freezes, i.e. nothing works and when I click the cross in the upper right-hand corner, I have to press the 'Force quit' button to get it to close.

By the way, when the output was somewhat different (. instead of x and _ instead of .) it didn't crash.

---

### Post by frunns on 2009-07-28
That's kind of odd...

---

### Post by DaithiF on 2009-07-28
put a print "All done" after the print text command, to see if it gets that far.  

also the quit() isn't actually required at the end, the script will exit after the last command anyway, so i would also remove that.

---

