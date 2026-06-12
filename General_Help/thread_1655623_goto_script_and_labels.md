---
title: "goto script and labels"
date: 2010-12-29
forum: General Help
---

### Post by degarb on 2010-12-29
I have written bat batch cd rippers, podcaster etc.  Spent lots of time, and love logic.  I hate complicated syntax, legacy, and any excuse to not use inevitable logic.

Anyway, googling a simple goto and label in linux is yielding thread after thead of unanswered question: how do I label and goto.

[http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/dosbatch.html](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/dosbatch.html)

was written by retard.  Showing no logic and only legacy syntax that replaces logical needed steps with sweeping meaningless  syntax. 

I need :

label:
ping google.com >> test.txt
goto label

 
I don't buy that linux command line is more  powerful than dos, because dos has thousands of helper com's and command line exes dating back from 1980.  I a simple google search with dos would offer an answer on first hit.  Not on linux.  

Thinking we can take hundreds of hours converting dos scripts over, is unrealistic.

---

### Post by hawkmage on 2010-12-29
Unfortunately for converting DOS batch files into shell scripts there is no label/goto in shell scripting.

It is not that DOS has a great feature that shell scripting doesn't it that shell scripting did not include the horrible programming construct of a goto.  

The infinite loop you gave in your post would be done like this:

```
while true; do
    ping google.com >> test.txt
done
```
Not sure why you would want to do an infinite loop but there you go.

---

### Post by degarb on 2010-12-29
> **hawkmage said:**
> Unfortunately for converting DOS batch files into shell scripts there is no label/goto in shell scripting.

It is not that DOS has a great feature that shell scripting doesn't it that shell scripting did not include the horrible programming construct of a goto.  

The infinite loop you gave in your post would be done like this:

```
while true; do
    ping google.com >> test.txt
done
```Not sure why you would want to do an infinite loop but there you go.


Thanks.  [It is not yours to question why.  I have good reason--in this case to create endless hd churn for a test.  It is only to the grant power that matters.]

You would need a really good essay to explain the linux logic.  While the dos is self-evident.  Needing no explanation, as it conforms to everyday thought.

---

### Post by hawkmage on 2010-12-29
I hate to disagree but any scripting or programming language that makes heavy reliance on goto is a poorly structured language.  I will agree that making the switch from DOS batch files to shell scripting does take a bit of mental adjustment.  

I started using DOS in version 2.1 and any relatively complex bat file was always more of a kludge that a logical script.  One of the reasons I learned PERL is because of the major limitations of DOS batch scripting.  

One of the reasons I asked about the loop is that in shell scripting there are usually many ways to accomplish a task.  

First of all the command "ping google.com >> test.txt doesn't require a loop to keep going.  Unlike the Windows ping the linux ping doesn't stop after 4 packets.  Second of all if you just want to write to a file you could try "cat /dev/zero >> test.txt"

---

### Post by Crusty Old Fart on 2010-12-31
> **degarb said:**
> Thanks.  [It is not yours to question why.  I have good reason--in this case to create endless hd churn for a test.  It is only to the grant power that matters.]
...
I don't believe the forum staff requires such profound humility from the the folks who post here. So, in the future, you're probably safe to direct a little bit of arrogance towards those who show up to help you without worrying about being castigated by the moderators. Hope that makes you feel better.

---

