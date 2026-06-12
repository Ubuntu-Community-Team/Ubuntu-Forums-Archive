---
title: "Scipt to add carriage return to text after number of words"
date: 2009-09-26
forum: General Help
---

### Post by Jamesss on 2009-09-26
I'm trying to automatically add a carriage return after a certain number of words in a plain text file. I've opened the file in gedit but can't see any options to format it to include the current word wrap as new lines/carriage returns. So I tried writing a bash script to do the job and this is as far as I've got:

```
#!/bin/bash
MaxWords=10
WordCount=$(head -3 $1 | tail -1 | wc -w)
if [ $WordCount -gt $MaxWords ]; then
	echo "add a carriage return after 10 words"
else 
	echo "don't add a carriage return"
fi 
```

What command could I use to edit the text file? Or is there a better way to do this?

thanks

James

---

### Post by geirha on 2009-09-26
```
#!/bin/bash
MaxWords=10

read -d '' -a words < infile # Read each word of the file into an array
n=${#words[@]}               # Number of words

for ((i=0; i<n; i += MaxWords)); do
  echo "${words[@]:i:MaxWords}"  # output MaxWord words starting from index i
done > outfile

```

Now, multiple spaces will be squeezed to one with this method. And also, it loads the entire file into an array, so memory usage will increase for larger files.

EDIT:
As for editors, I'd use vim. Open the file with vim, set the text-width to, say, 60 «:set tw=60»

Move the cursor to the first paragraph and hit the following four keys: «gqap»
All this must be done in normal mode.

EDIT2:
And I completely forgot about the fmt-command.
```
man fmt
```

---

