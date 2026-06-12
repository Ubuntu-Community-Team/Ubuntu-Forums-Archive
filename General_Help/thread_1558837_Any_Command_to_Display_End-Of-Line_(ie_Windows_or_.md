---
title: "Any Command to Display End-Of-Line (ie Windows or Unix) of Text Files in a Folder?"
date: 2010-08-22
forum: General Help
---

### Post by OzzyFrank on 2010-08-22
Hi. What I am looking for is a quick and easy - and _accurate_ - way of displaying the **End-Of-Line** (EOL) format of text files, preferably showing that of every text file in a given folder. The only option I know of is to open each in **Gedit**, go to *Save As*, and see what the EOL (apparently) is. But according to it, some files I have converted from Unix to DOS (via **todos** from the **tofrodos** package) are still in Unix format, and I'm leaning towards the developer's theory that they are in fact converted, but Gedit is showing incorrect info.

Actually, I just got clever and went and opened the files in a virtual Windows XP, as you can immediately see if they are in Unix format (due to squares instead of paragraph breaks). All files in my test folder seem fine (ie ANSI/Windows format), so obviously Gedit is intermittently showing me rubbish for whatever reason. And even if it wasn't, I'd still rather have a quicker and easier way of doing this, and having the EOL of every file in a folder displayed would be even more useful.

So if anyone knows of a command that could give me this info in the terminal, that would be great. As I said, even better if the command works on all files (or more specifically all .txt files) in a folder, so if there is an option for that, please include it. Many thanks in advance!

---

### Post by amauk on 2010-08-22
Any hex editor will show you exactly what's in the file

0x0D = CR
0x0A = LF

---

### Post by OzzyFrank on 2010-08-22
Forgive my ignorance, but while I know what a hex editor is, and have used one a couple of times, I have no idea what LF and CR are. And is the relevant info at the end of the file? Just a little clarification on that would be appreciated.

---

### Post by amauk on 2010-08-22
Yes,

LF = line feed (often written as \n)
It's Ascii code 10 (0x0A)

CR = carriage return (often written as \r)
It's Ascii code 13 (0x0D)

It dates back to electronic typewriters, where returning the carriage to the left hand side, and feeding the paper up one line were two separate actions

In modern computers, there's obviously nothing physical going on, but the concept of carriage returns and line feeds stuck

Unix line endings are \n
Mac (traditional) line endings are \r
DOS line endings are \r\n

If you look through a text file, and see
```
0A
```
That's line feed (\n)
Therefore Unix line endings

If you look through a text file, and see
```
0D
```
That's carriage return (\r)
Therefore Mac line endings

If you look through a text file, and see
```
0D 0A
```
That's carriage return + line feed (\r\n)
Therefore DOS line endings

---

### Post by hwttdz on 2010-08-22
grep -LE $'\r\n' *.txt # list UNIX style files (LF terminated)
grep -lE $'\r\n' *.txt # list DOS style files (CRLF terminated)

---

### Post by OzzyFrank on 2010-08-23
Hey **amauk**, that was really informative and interesting, so thanks for taking the time to explain. I'll have to hold onto that info as another way to find out EOL info.

And thanks **hwttdz** - while I still wouldn't mind finding a command to list all (text) files in a folder with their EOL in the terminal, this is certainly another way around it. If I am too lazy to count all DOS files listed and compare with those in the folder, I can always run the command to find files with Unix EOL, which should come up with no output if all the files have successfully been converted (come to think of it, checking for any that didn't get converted is probably the easiest option).

I won't mark this as solved just yet, as chances are someone knows the command I am after, even though with those 2 commands it isn't so urgent now.

---

### Post by OzzyFrank on 2010-08-23
> **hwttdz said:**
> grep -LE $'\r\n' *.txt # list UNIX style files (LF terminated)
grep -lE $'\r\n' *.txt # list DOS style files (CRLF terminated)

Hey, just out of interest, and since amauk mentioned Mac, what is the grep command to list Mac files? Also, since I see in Gedit there is now an option to save as Mac format, does anybody know the command to change text files from Unix to Mac?

---

