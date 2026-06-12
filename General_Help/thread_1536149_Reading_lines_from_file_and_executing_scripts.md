---
title: "Reading lines from file and executing scripts"
date: 2010-07-21
forum: General Help
---

### Post by meg23 on 2010-07-21
I am trying to create a script that reads a list of url's from a text file and then executes the same script for each line. This is what I am looking for:

elinks -dump $(url's in file, one by one) | grep "reply" > jobs.txt

How could I do this?

---

### Post by NFblaze on 2010-07-21
Is it the same script to execute for each line?

If so, you might be able to get away with

```
while IFS= read -r line
do

something with $line

done < DumpedUrls.txt
```

---

### Post by meg23 on 2010-07-21
Yeah, its the same script. Where do I input the jobs.txt file for reading?

---

### Post by NFblaze on 2010-07-21
You would substitute DumpedUrls.txt with jobs.txt

---

### Post by meg23 on 2010-07-21
This is what I got so far:

How do I access the actual jobs.txt file that I want to access?

# grab job emails
while read line (jobs.txt)
do
  echo "elinks $line | grep "reply" > /home/moshe/jobs2.txt

---

### Post by NFblaze on 2010-07-21
```

#----------------------------------------------------------
# Initial Dump of the webpage to JOBS.txt
#----------------------------------------------------------
elinks -dump www.example.com | grep "reply" > JOBS.txt

#----------------------------------------------------------
# Read a line from JOBS.txt and run myscript.sh on the line
#----------------------------------------------------------

while read line
do

sh myscript.sh $line

done < JOBS.txt
```

Do you mean like this?

---

### Post by meg23 on 2010-07-22
Yeah, thats what I am looking for. However, instead of using a script to act upon $line, I want to nest the actual script in the code. For instance, something like this:

sh $(/usr/bin/elinks -dump $line)  > /home/moshe/jobs2.txt

However, "elinks" does not seem to be understood along with "-dump" flag. Any ideas about that one?

---

