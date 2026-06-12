---
title: "Bash Scripting and bc"
date: 2010-02-23
forum: General Help
---

### Post by helixed on 2010-02-23
Hello,

I'm trying to write a base script which will divide an argument by 10 and then use that argument in another program.  Since my argument can be a floating point number, I used bc to accomplish this.  Here's an example of a simplified version of what I have so far:

<code>NUM=$(echo "scale=25;$1/10" | bc)

#make sure the first argument was formatted correctly
if [ $? -ne 0 ]
then
	echo bad
fi</code>

Unfortunately, in my if statement $? returns the result of echo, not the result of bc.  How can I check to see that bc evaluated correctly, or in other words my first argument was correctly formatted?

Thanks,

helixed

---

### Post by nixclusive on 2010-02-23
> ```
NUM=$(echo "scale=25;**_$_**1/10" | bc)
```

there's your problem.

---

### Post by DaithiF on 2010-02-23
i could be wrong, but seems to me that bc prints an error to stderr rather than exiting with a status code of non-zero when it encounters an error.  In that case, you would need to capture stderr, and test whether it is empty, so something like:

example with valid input:
```
$ var=100
$ num=$(echo "scale=25;$var/10" | bc 2>bcerrors)
$ read error <bcerrors
$ echo "number is: $num and error is: $error"
number is: 10.0000000000000000000000000 and error is: 

```

example with invalid input:
```
$ var=1.0.0
$ num=$(echo "scale=25;$var/10" | bc 2>bcerrors)
$ read error <bcerrors
$ echo "number is: $num and error is: $error"
number is:  and error is: (standard_in) 1: parse error
```

---

### Post by helixed on 2010-02-24
@nixclusive: I'm not really sure what you're referring to.  The $1 is the first argument variable in the bash script.  

@DaithiF That solution seems like it will work, but is there a cleaner way to do it?  Is there any way to store the output of bc directly into a variable, or to do the operations separately?

Thanks for the replies,

helixed

---

### Post by DaithiF on 2010-02-25
I suppose you could capture both stdout and stderr from bc into a variable and then examine the variable to decide if an error occurred ...
$ result=$(echo "100/10" | bc 2>&1)
$ echo $result
10
$ [[ $result =~ error ]] && echo "Error occurred" || echo "No error"
No error
$ result=$(echo "100.1.1/10" | bc 2>&1)
$ echo $result
(standard_in) 1: parse error
$ [[ $result =~ error ]] && echo "Error occurred" || echo "No error"
Error occurred

---

