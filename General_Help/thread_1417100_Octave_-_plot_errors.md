---
title: "Octave - plot errors"
date: 2010-02-26
forum: General Help
---

### Post by eeprom on 2010-02-26
[SIZE=2]Hello, 
I just loaded octave.  I ran through a few examples of how to implement a script file.  Everything works until I get to "plot".  When I run the "plot" command I get the following.

octave:2> test1.m
error: can't perform indexing operations for <unknown type> type
sh: gnuplot: not found

Just to double check my work, I ran the following code:
y=[1 2 3];
plot(y);

This results in the same errors.  Any ideas?

thanks,
EE
[/SIZE]

---

### Post by Steven_B on 2010-02-26
Make sure you've got gnuplot installed.
```
sudo apt-get install gnuplot
```

---

### Post by eeprom on 2010-02-27
Steven_B,
That worked.  Thanks.  Maybe I can ask you another question... I just installed octave using snyaptic yesterday.  Why would the install exclude the plot function?

---

### Post by Alexandre Putt on 2010-02-27
> **eeprom said:**
> Steven_B,
That worked.  Thanks.  Maybe I can ask you another question... I just installed octave using snyaptic yesterday.  Why would the install exclude the plot function?

Perhaps because gnuplot is in recommended packages for Octave. It should be a requirement, really.

---

