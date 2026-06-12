---
title: "How to install tar.gz files?"
date: 2010-02-17
forum: General Help
---

### Post by karthick87 on 2010-02-17
I have extracted the file and when compiling it i get the following error..Can someone help me??This is the error i get....

karthick@Learners-desktop:~/Desktop/logkeys-0.1.0$ sudo ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: in `/home/karthick/Desktop/logkeys-0.1.0':
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

---

### Post by MinimalBin on 2010-02-17
By the first and foremost, don't use *sudo*. Is [build-essential]("http://packages.ubuntu.com/karmic/build-essential") installed ?

---

### Post by karthick87 on 2010-02-17
No build essential is not installed..How to install it from terminal??And if i dont use sudo i get the error...

karthick@Learners-desktop:~/Desktop/logkeys-0.1.0$ ./configure
./configure: line 1816: config.log: Permission denied
./configure: line 1826: config.log: Permission denied

---

### Post by MinimalBin on 2010-02-17
> **getyourkarthick said:**
> No build essential is not installed..How to install it from terminal??And if i dont use sudo i get the error...

karthick@Learners-desktop:~/Desktop/logkeys-0.1.0$ ./configure
./configure: line 1816: config.log: Permission denied
./configure: line 1826: config.log: Permission denied

```
sudo apt-get install build-essential
```

---

### Post by rnerwein on 2010-02-17
hi
i guess the error messages you get: ./configure: line 1816: config.log: Permission denied
comes from your former call using[COLOR=Red] sudo[/COLOR] and there for the log files was created with [COLOR=Red]owner root[/COLOR].
ciao

---

### Post by karthick87 on 2010-02-17
So what should i do now?

---

### Post by steveneddy on 2010-02-17
Log out of the terminal, open your terminal up again, cd to the directory and try installing again.

From the Read Me file:

> $ ../configure               # invoke configure from parent directory
 $ make                       # make compiles what it needs to compile
 ( become super&#8601;user now )    # you need root to install in system dir
 # make install               # installs binaries, manuals and scripts


---

### Post by oldos2er on 2010-02-17
Have you read through the docs here: [http://code.google.com/p/logkeys/wiki/Documentation](http://code.google.com/p/logkeys/wiki/Documentation)

---

### Post by darolu on 2010-02-17
Analyze the **bold** text:
```
karthick@Learners-desktop:~/Desktop/logkeys-0.1.0$ sudo ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... **no**
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... **no**
checking for c++... **no**
checking for gpp... **no**
checking for aCC... **no**
checking for CC... **no**
checking for cxx... **no**
checking for cc++... **no**
checking for cl.exe... **no**
checking for FCC... **no**
checking for KCC... **no**
checking for RCC... **no**
checking for xlC_r... **no**
checking for xlC... **no**
checking for C++ compiler default output file name... 
configure: error: in `/home/karthick/Desktop/logkeys-0.1.0':
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
```
*./configure* check you meet all the dependencies needed to compile your source code; all items marked with **no** are not met, and you need to install them. Build-essential package installs most of them, but some of them may need to be installed manually, first install *build-essential* as MinimalBin said; and try again, if you get more **no** when you run *./configure* you will need to install them manually. To find the package (i.e. "gawk") you can use:
```
sudo apt-cache search gawk
```
It'll tell you the name of the package so you can install with *apt-get install*
I also recommend installing *automake* and *cmake* besides *build-essential*.
```
sudo apt-get install automake cmake
```

---

### Post by kaspin on 2010-02-18
[FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"]Hi there,
I'm a stupid 70-year old Noobie. The above seems much too techie and I'll probably have full blown dementia before managing to read and understand all the links .
I've downloaded and want to install "labelnation-1.187.tar.gz" on my computer which is happily using Ubuntu 9.10.
Can't that be done simply - i.e. using just a couple of lines in a terminal ?[/COLOR][/SIZE][/FONT]

---

### Post by idiamin on 2010-02-18
Is there a readme?

---

### Post by stripling20 on 2010-02-18
> **kaspin said:**
> [FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"]Hi there,
I'm a stupid 70-year old Noobie. The above seems much too techie and I'll probably have full blown dementia before managing to read and understand all the links .
I've downloaded and want to install "labelnation-1.187.tar.gz" on my computer which is happily using Ubuntu 9.10.
Can't that be done simply - i.e. using just a couple of lines in a terminal ?[/COLOR][/SIZE][/FONT]
@ Kaspin

I'll help u to install the [FONT=Comic Sans MS][SIZE=2][COLOR=Navy]"labelnation-1.187.tar.gz".

[COLOR=Black]step1: [/COLOR]tar zxvf [/COLOR][/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2][COLOR=Navy]labelnation-1.187.tar.gz
[COLOR=Black]This command will extract the package to the current directory [/COLOR]
[COLOR=Black]step2: [/COLOR]cd labelnation
[COLOR=Black]step3:[/COLOR] ./configure
[COLOR=Black]step4:[/COLOR] make && make install


[/COLOR][/SIZE][/FONT]

---

### Post by kaspin on 2010-02-18
[FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"]Thanks a lot Stripling20 for a speedy, clear reply. Unfortunately I'm stuck at the ./ configure stage.
To recap, in a terminal I put "cd /home/dl" to get to where I'd downloaded labelnation-1.187.tar.gz
Then I entered "tar zxvf labelnation-1.187.tar.gz"
So I ended up with a file called labelnation-1.187 in /home/dl
Then I did "cd /home/dl/labelnation-1.187"
This outputs a line "~/labelnation-1.187$" 
If I then type ./configure after the $ sign, I get the message
"bash: ./configure: no such file or directory"
So I'm stuck here. Have installed "build-essential", but that doesn't seem to have made any difference.
Any ideas you have would be most welcome before I get on to step4: make && make install.
Thanks again,  kaspin[/COLOR][/SIZE][/FONT]

---

### Post by MinimalBin on 2010-02-18
> **kaspin said:**
> [FONT=Comic Sans MS][SIZE=2][COLOR=Navy]Thanks a lot Stripling20 for a speedy, clear reply. Unfortunately I'm stuck at the ./ configure stage.
To recap, in a terminal I put "cd /home/dl" to get to where I'd downloaded labelnation-1.187.tar.gz
Then I entered "tar zxvf labelnation-1.187.tar.gz"
So I ended up with a file called labelnation-1.187 in /home/dl
Then I did "cd /home/dl/labelnation-1.187"
This outputs a line "~/labelnation-1.187$" 
If I then type ./configure after the $ sign, I get the message
"bash: ./configure: no such file or directory"
So I'm stuck here. Have installed "build-essential", but that doesn't seem to have made any difference.
Any ideas you have would be most welcome before I get on to step4: make && make install.
Thanks again,  kaspin[/COLOR][/SIZE][/FONT]

You don't need to compile it - rename the folder, move it to /opt and you are done.

---

### Post by kaspin on 2010-02-18
[FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"]Thanks for that MinimalBin,
After renaming, I couldn't transfer it to /opt, but it went into my /desktop all right.
Now to work out how to run it...Happy days,  kaspin[/COLOR][/SIZE][/FONT]

---

### Post by MinimalBin on 2010-02-18
Open the folder in your file browser - there should be an executable. Run it and see what happens.
 
** */opt* isn't owned by you so you need to trasnfer the files as *root* ( *sudo* ).

---

### Post by ethan33 on 2010-02-18
I've been trying to compile metakit for a couple of days now, and thanks to this tread I have gotten the closest today. However I got an error, as follows;
```
./regress: error while loading shared libraries: libmk4.so: cannot open shared
object file: No such files or directory
make: *** [test] Error 127
```Does this mean that I need to make a shared objects directory? If so, where, and would this mean shared as in, between multiple users, or on a network? Finally, how would I go about making this file?

---

### Post by kaspin on 2010-02-19
Thanks again MinimalBin and stripling20 (how do you dream up such names?:confused:)
With your combined help I've now got the program in /opt. It was all very basic stuff, and had I read my notes first I would have saved you some trouble (although I still have to find out why tar apparently needed zfvx after it). 
Just shows how patient and helpful people can be on these forums, even when the questioner is a bit past it....
Bye for now,  kaspin[FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"][/COLOR][/SIZE][/FONT]

---

### Post by kaspin on 2010-02-20
[FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"]Sorry - it's me again. 
It seems that I should end up with an executable file after the "tar xfvc ...." procedure. In fact the result was a directory called "labelnation-1.187" (in /opt), inside which were:
- a directory called "examples" in which there were 6 text files giving suggested types of address labels
- a file called "COPYING" which contained the GNU public license text
- a README file saying what the program does, and suggesting you input , under UNIX, "prompt$ labelnation --help | more" to find out how to use it
- a file called "csv_to_in" which contains a program to convert a csv (comma separated values) file into one parseable by labelnation
- a file called "labelnation" which contains the program in python. If I double click on this I'm told it's an executable text file, but if I select the option "Run" nothing seems to happen.

I'm obviously missing something pretty basic somewhere along the line, and again, if anyone can put me right I would be grateful.
Thanks kaspin[/COLOR][/SIZE][/FONT]

---

### Post by MinimalBin on 2010-02-20
Run it in Terminal and post the output here so we can investigate the case a bit further.

---

### Post by kaspin on 2010-02-20
[FONT="Comic Sans MS"][SIZE="2"][COLOR="Navy"]Hi again MinimalBin,[/COLOR]
If I open a terminal and complete the first line as follows:

[COLOR="Red"]dl@dl-laptop:~$ /opt/labelnation-1.187/labelnation[/COLOR]

I receive the following text file (tne chevrons indicate where I've deleted chunks of text to shorten this reply):

[COLOR="Red"]LabelNation, version 1.187

LabelNation is a program for making labels: address labels,
business cards, or anything else... >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
How To Use It:
==============

Let's start with return address labels.  If you wanted to print a
sheet of them using the Avery 5167 standard (80 small labels per
page), you might invoke LabelNation like this:

   prompt$ labelnation -t avery5167 -i myaddress.txt -l -o myaddress.ps

The "-t" stands for "type", followed by one of the standard predefined
label types.  The "-i" means "input file", that is, where to take the
label data from.  The "-l" stands for "lines input", meaning that the
format of the incoming data is lines of text (as opposed to PostScript
code).  The "-o" specifies the output file, which you'll print to get
the labels.

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


Options:

   -h, --help, --usage, -?     Show this usage
   --version                   Show version number
   --explain                   Show instructions (lots of output!)
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
   --first-label N             Start printing at label number N
                               (bottom left is 1, count up each
                               column in turn, top right is last)
   --font-name NAME            Use PostScript font FONT
   --font-size SIZE            Scale font to SIZE
   -o, --outfile FILE          Output to FILE ("-" means stdout)
dl@dl-laptop:~$ [/COLOR]

If I go to the folder /opt/labelnation-1.187/labelnation and left double click, I get the options
 "Run in Terminal" which results in a text being briefly displayed (too fast to read)
 "Display" which shows the source code of the program
 "Run" which doesn't seem to do anything

I hope this is the sort of information you needed.
[COLOR="Navy"]Thanks again,  kaspin[/COLOR]
[/SIZE][/FONT]

---

