---
title: "Acrobat Reader"
date: 2009-11-23
forum: General Help
---

### Post by lory on 2009-11-23
I have a special program for accounting, and when I try to print to file (PDF) I receive an error "cannot find commmand for acroread %1", and ask for the path to the file. Strange because I have installed the Acrobat reader.

---

### Post by koenn on 2009-11-23
```
acroread %1
```
looks like windows syntax.

Do you have this problem on Windows or on Ubuntu ?

---

### Post by hwttdz on 2009-11-23
What's the output of "which acroread"? What happens if you change the command to /full/path/to/acroread %whatever, perhaps it's not succeeding in finding the executable, either that or make sure it's in the path of whatever user executes the command (it might not be the user you are logged in as (annoyingly) (but it might be (less annoyingly))).

Also acroread requires one to accept a license on first execution, so I recommend running it once just to make sure it's not failing because it requires interaction from the user. That is if you haven't run it already.  

Also why the loyalty to acroread over evince or pdftk?

---

### Post by lory on 2009-11-23
The problem is on Ubuntu. What I did now is searching whatever file named acroread* and give this path. I found two files under usr/lib/pymodules/phython2.5/orca/scrips/apps called acroreader.py and acroread.pyc. Bu it still doesn t work.

---

### Post by hwttdz on 2009-11-23
No, that's not right.  Ask the system which acroread is being used when you call acroread (or if there is on in the path at all).

First try running acroread from the command line.  If it works then it's in your path.

Second ask "which acroread", that will tell you the full path to acroread.  

Then try replacing "acroread %1" with "/path/to/acroread %1" to see if it was having some trouble finding the executable.

---

### Post by lory on 2009-11-23
didn't work. there is only a window where to put the path. Or do you mean asking in the terminal?

---

### Post by hwttdz on 2009-11-23
Open a terminal and run 
1st: acroread
2nd: which acroread

Then assuming both the above commands worked replace acroread in the window for the print command with the output of "whch acroread".

---

### Post by lory on 2009-11-23
did'n work

lorenzo@lorenzo-desktop:~$ acroread
acroread: command not found
lorenzo@lorenzo-desktop:~$ which acroread
lorenzo@lorenzo-desktop:~$

---

### Post by hwttdz on 2009-11-23
Try
$ sudo apt-get install acroread (accept when prompted)
$ acroread (accept when prompted)
then try printing to file again.

---

### Post by lory on 2009-11-23
It has installed it successfully. and by typing acroread it opens. I tiped then in the terminal 

lorenzo@lorenzo-desktop:~$ which acroread
/usr/bin/acroread

and inserted the path
 "usr/bin/acroread"
in the field

but it didn't work again

---

### Post by fluffman86 on 2009-11-23
You must use "/usr/bin/acroread" instead of "usr/bin/acroread"

They are not the same.

---

### Post by Wiebelhaus on 2009-11-23
May we ask for the name of the Special Accounting program?

---

### Post by koenn on 2009-11-23
> **lory said:**
> I
and inserted the path
 "usr/bin/acroread"
in the field

but it didn't work again

there's a / missing in that path, try
```
/usr/bin/acroread
```


If that doesn't work, try with the parameter as in the axample you give
```
/usr/bin/acroread $1
```
or
```
/usr/bin/acroread %1
```

$1 is waht you'd expect on a linux system, %1 is the corresponding windows syntax. Are you running this with wine ?

---

### Post by lory on 2009-11-23
I gave him the correct path by searching with its browser

"/usr/bin/acroread" %1

but is still not working

---

### Post by lory on 2009-11-23
THAAAAANKS it worked. 
I had to insert 

/usr/bin/acroread %1

without "" and adding manually %1, without %1 it opened acrobat with no document

thanks again

---

