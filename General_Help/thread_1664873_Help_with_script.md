---
title: "Help with script"
date: 2011-01-11
forum: General Help
---

### Post by JCM_Pico on 2011-01-11
Hello there,
I wonder if it is possible to use a .sh to that changes some character from a text file

_*EXAMPLE:*_
I have a script that runs every day, and I want it to every day it run to change the column 31 and 32 in line 2 form the day of the run plus 1 

_*TEXT FILE EXAMPLE:*_
this is the header (line one)
here goes the date            dd mm yy
.
.
.

I know that I can get the date with the command date +%Y%m%d, but I can't figure out a way of making the script to work

---

### Post by papibe on 2011-01-11
The simplest solution I can think off is using the stream editor sed, and replace the 2nd line using '2s'. Something like this:
```
$ sed 2s/.*/"$(date)"/ file.txt
```
I hope it helps.

---

### Post by JCM_Pico on 2011-01-11
I cant replace the entire line :(
Is there any way of doing this with VIM for example?

---

### Post by hawkmage on 2011-01-11
You could try playing around with this:
```
vi -e -c "2s/${TEXT1}/${TEXT2}/" -c 'wq' /path/to/file
```
Where the TEXT1 and TEXT2 are the text to be replaced and replace with.

---

### Post by JCM_Pico on 2011-01-11
I will give it a try 
Thanks you all

---

### Post by papibe on 2011-01-11
> **JCM_Pico said:**
> I cant replace the entire line :(
That's weird. I tested that code and it works. Maybe this:
```
$ sed 2s/^.*$/"$(date)"/ file.txt
```

---

### Post by hawkmage on 2011-01-11
> **papibe said:**
> That's weird. I tested that code and it works. Maybe this:
```
$ sed 2s/^.*$/"$(date)"/ file.txt
```
I don't think that they were saying that the code didn't work but that they do not want to replace the entire line.

---

### Post by JCM_Pico on 2011-01-12
I use sed to replace the entire line, it was easier than to replace the tex (it could be equal to some in the same line).
And its working perfectly fine, thanks
Now I have a little problem, I need a 3 day ahead date... if I mathematically sum 3 to the day, in the end of the month (31) it will give me day 34... :(... And I can't find a way of solving this....
Any way

Thank you all for the help, it was very useful, Thanks

---

### Post by papibe on 2011-01-12
The command date can do all sorts of tricks like:
```
$ date -d "yesterday"
Tue Jan 11 10:16:27 CST 2011

$ date -d "tomorrow"
Thu Jan 13 10:16:34 CST 2011
```
In your case, you can use:
```
$ date -d "+ 3 days"
```
Regards.

---

### Post by papibe on 2011-01-12
The command date can do all sorts of tricks like:
```
$ date
Wed Jan 12 10:31:09 CST 2011

$ date -d "yesterday"
Tue Jan 11 10:16:27 CST 2011

$ date -d "tomorrow"
Thu Jan 13 10:16:34 CST 2011
```
In your case, you can use:
```
$ date -d "+ 3 days"
```
Regards.

---

### Post by papibe on 2011-01-12
The command date can do all sorts of tricks like:
```
$ date
Wed Jan 12 10:31:09 CST 2011

$ date -d "yesterday"
Tue Jan 11 10:16:27 CST 2011

$ date -d "tomorrow"
Thu Jan 13 10:16:34 CST 2011
```
In your case, you can use:
```
$ date -d "+ 3 days"
```
Regards.

---

### Post by papibe on 2011-01-12
> The command date can do all sorts of tricks like:
Oops, double post.

---

