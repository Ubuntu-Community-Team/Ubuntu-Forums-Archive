---
title: "Append a blank line to every file in a directory?"
date: 2009-09-24
forum: General Help
---

### Post by Sarteck on 2009-09-24
Right, so I have a directory, **save** (/home/sphere/save, actually).  I was to create a few files in it, and just recently found out that I was supposed to put a blank line on each of the files.

I thought I was finally getting the hang of using the command line, but just about everything I try results in failure.  XD

Here's what I was trying, basically:```
find save/ -type f -exec cat {} | echo "\n" > {} \;
```But that tells me I'm missing an argument to exec.

I did read the find manual page, and it said that everything from the **-exec** to the **\;** should be executed for each file, and I've got **cat {} | echo "\n" > {}** as an argument there, so I'm not seeing what I'm doing wrong...

A little help?

---

### Post by Sarteck on 2009-09-24
Solved, kind of:
```

cd save
for FILE in *; do cat $FILE | echo "\n" > $FILE; done

```This accomplished what I needed, but I still would like to know why the **find** command didn't work like I expected, if someone could enlighten me.

---

### Post by bigboy_pdb on 2009-09-24
You could have also used 'echo "" >> file'. This appends the string (which is an empty string) followed by a newline to the end of the file.

One of your problems is that the brackets have to be escaped using back slashes because brackets are used by the bash shell to group and execute commands within the current shell. For example:

```

 # Prints error message and exits when error is a number greater than 0
error=1
(( error == 0 )) || { echo 'Error occurred.'; exit 0; }

```

An example of how you would escape the brackets is as follows:
```

# List files using long listing format
find -type f -exec ls -l \{\} \;

```

The second problem is the pipe character. The shell is assuming that you want to redirect the files that were found to the command "echo".

There are no examples where redirection is used with the "exec" option in the man page for find and I wasn't able to escape the pipe character using a backslash. This is one of the reasons that I don't use the "exec" option with the find command.

Alternate ways to handle the output of find are to redirect it to a loop or to use it with xargs.

```

# List files using long listing format
while read f; do
	ls -l "$f"
done < <(find -type f)

# Concatenates the contents of all files
# (where printed file names are separated by null characters instead of newlines)
find -type f -print0 | xargs -0 cat

```

---

### Post by Slim Odds on 2009-09-24
You do know that >> will append to a file, right?

---

### Post by bigboy_pdb on 2009-09-25
> **Slim Odds said:**
> You do know that >> will append to a file, right

Yes. The OP is trying to append a newline to the end of some files.

---

### Post by Slim Odds on 2009-09-25
> **bigboy_pdb said:**
> Yes. The OP is trying to append a newline to the end of some files.

My point was that it's a lot simpler to do this:
```
cd save
for FILE in *; do echo "\n" >> $FILE; done
```No need to cat the original file.

---

### Post by kaibob on 2009-09-25
> **Slim Odds said:**
> My point was that it's a lot simpler to do this:
```
cd save
for FILE in *; do echo "\n" >> $FILE; done
```No need to cat the original file.
Just as a point of information, so as not to mislead the OP, wouldn't you need to use the -e option with echo in the above command if running bash?

---

### Post by Slim Odds on 2009-09-25
> **kaibob said:**
> Just as a point of information, so as not to mislead the OP, wouldn't you need to use the -e option with echo in the above command if running bash?

Yes..... that is true.

Could also just do this:```
echo "" >> $FILE
```

since you get the newline for free....

---

### Post by bigboy_pdb on 2009-09-25
> **Slim Odds said:**
> My point was that it's a lot simpler to do this:
```

cd save
for FILE in *; do echo "\n" >> $FILE; done

```
No need to cat the original file.


I agree with using ">>" instead of cat (that's why it's the first line of my first response), but the for loop shouldn't be used because it lists directories.

My first post was intended to be a hint, more than a solution. I figured that the OP might want to try to get the solution from the information him/herself.

The code for the solution would be:
```

while read f; do
	echo '' >> "$f"
done < <(find -maxdepth 1 -type f)

```

This is only for the changing the files in the current directory. To recursively apply the solution to files remove '-maxdepth 1'. Furthermore, you can modify the find command to apply the solution for specific criteria (such as appending only changing files with a certain extension or size).

---

### Post by scragar on 2009-09-25
Just to let you know I've got a slightly shorter(well, a fair bit shorter :p) version :p
```
for i in *;do
  >>"$i"
done
```Just **cd** to the directory, then run it. For an explination the loop goes through all files that match *, so all of them(except hidden files), then attempts to add an empty string on to the end(with a new line in there as well :p).

---

### Post by bigboy_pdb on 2009-09-25
> **scragar said:**
> Just to let you know I've got a slightly shorter(well, a fair bit shorter :p) version :p
```

for i in *;do
  >>"$i"
done

```


I don't think this works. There's nothing in the bash shell manual that indicates it would. I tried using ">>a" to append a newline to an existing file and there was no difference (I checked this using 'od -c').

---

### Post by Sarteck on 2009-09-25
Thanks for all the answers, guys.  XD  It'll take me a bit to sort through everything, but I do appreciate the wealth of input.

---

