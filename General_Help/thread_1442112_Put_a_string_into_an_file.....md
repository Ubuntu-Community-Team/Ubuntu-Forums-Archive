---
title: "Put a string into an file...."
date: 2010-03-29
forum: General Help
---

### Post by hakermania on 2010-03-29
I have a file with this text inside: 1,
I want to put the string 2, inside it 
The file then will contain the string:
1,2,
Can this be done with the cat command?

---

### Post by cjhabs on 2010-03-29
> **hakermania said:**
> I have a file with this text inside: 1,
I want to put the string 2, inside it 
The file then will contain the string:
1,2,
Can this be done with the cat command?

If your file is called file.txt, the following command will do this:
sed -i 's/\(1,\)/\12/' file.txt

It is a little complicated because you want the appended text to be on the same line as the existing text.

I am sure someone here will chime in with a solution with 1/2 the keystrokes!

If you don't understand what I have done here, just ask.

---

### Post by hakermania on 2010-03-29
> **cjhabs said:**
> If your file is called file.txt, the following command will do this:
sed -i 's/\(1,\)/\12/' file.txt

It is a little complicated because you want the appended text to be on the same line as the existing text.

I am sure someone here will chime in with a solution with 1/2 the keystrokes!

If you don't understand what I have done here, just ask.
I don't understand what you've done here

---

### Post by cyprys on 2010-03-29
```
file=`cat your_file_name`; echo $file\your_string_here > your_file_name; unset $file;
```

e.g.
```
cyprys@greenshit:~$ cat stuff.txt
1,
cyprys@greenshit:~$ file=`cat stuff.txt`; echo $file\2, > stuff.txt; unset $file;
cyprys@greenshit:~$ cat stuff.txt
1,2,
```

@cjhabs, is this virago 535 in your av?

---

### Post by cjhabs on 2010-03-29
> **hakermania said:**
> I don't understand what you've done here

sed -i 's/\(1,\)/\12/' file.txt

sed is a search and replace program
-i says to make the changes to the original file
s/../.../ = search for the string between the first /../ and replace with that in the second /.../
\(1,\) = search for the string "1," It is in parens so that it is remembered - parens need to be escaped with a \ so that they are treated as special characters.
\12 = 2 things \1 followed by 2
The \1 is the first thing that was remembered from the first string, i.e. "1,"
2 is the number 2, which is what you wanted added to the "1,"

Phew! sed is a very powerful string manipulator, but it takes some getting used to.
As I mentioned previously, yopu can simply append the "2" to the file if there is a return after the "1," as the "2" will end up on the next line.

Compare the sed command with:
echo "2" >> file.txt
and you will see what I mean.

In my examples I have assumed that the original string, "1," is held in a file named file.txt

---

### Post by hakermania on 2010-03-30
> **cyprys said:**
> ```
file=`cat your_file_name`; echo $file\your_string_here > your_file_name; unset $file;
```e.g.
```
cyprys@greenshit:~$ cat stuff.txt
1,
cyprys@greenshit:~$ file=`cat stuff.txt`; echo $file\2, > stuff.txt; unset $file;
cyprys@greenshit:~$ cat stuff.txt
1,2,
```@cjhabs, is this virago 535 in your av?

Nice dude!
Very nice solution to my problem.
The problem now is that I want to put the numbers 1, 2, 3, etc in a row without spaces!
Your solution does not support this!
e.g.
```
file=`cat arxeio`; echo $file\$a, > arxeio; unset $file;
```
this will not work! This will write to the file "arxeio" $a,$a,$a,$a,$a etc
This will work
```
file=`cat arxeio`; echo $file\ $a, > arxeio; unset $file;
Notice the space between $file\ and $a
```
but the numbers will appear like this:
 1, 2, 3, 4, 5, 6, 7, 8, etc
and I don't want spaces!

---

### Post by cjhabs on 2010-03-30
> **cyprys said:**
> 
@cjhabs, is this virago 535 in your av?

It's a Yamaha Roadstar Silverado - I wish I was on it right now!

---

### Post by cjhabs on 2010-03-30
> **hakermania said:**
> Nice dude!
Very nice solution to my problem.
The problem now is that I want to put the numbers 1, 2, 3, etc in a row without spaces!
Your solution does not support this!
e.g.
```
file=`cat arxeio`; echo $file\$a, > arxeio; unset $file;
```
this will not work! This will write to the file "arxeio" $a,$a,$a,$a,$a etc
This will work
```
file=`cat arxeio`; echo $file\ $a, > arxeio; unset $file;
Notice the space between $file\ and $a
```
but the numbers will appear like this:
 1, 2, 3, 4, 5, 6, 7, 8, etc
and I don't want spaces!

Try
file=`cat arxeio`; echo ${file}${a}, > arxeio; unset $file;

---

### Post by hakermania on 2010-04-01
Thx Solved!

---

