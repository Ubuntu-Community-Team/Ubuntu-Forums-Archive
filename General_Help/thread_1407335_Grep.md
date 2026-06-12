---
title: "Grep"
date: 2010-02-15
forum: General Help
---

### Post by pedrom169 on 2010-02-15
I have learned how to use Grep to search text files. But i was wondering if there was anyway to run a script which produces a popup box which i type in the word i want to find it searches a few text files for that certain word?

Thanks

---

### Post by audiomick on 2010-02-15
I think you can do that using the search utility from
applications> accessories.
The first box accepts a file name as a search criterion, and if you click on the arrow next to the words "further options" (or something like that; I am translating from German) below the box you can add text in the file as a criterion, and you can add various other criteria out of the drop down list below that.

---

### Post by allinejore on 2010-02-15
Grep for lines in the file simple3 that contain nothing except exactly three blank spaces and store the output into a file named dollar2 HINT: We are trying to match the entire line here so we will want to use both the ^ and the $ symbols in our regular expression.

---

### Post by pedrom169 on 2010-02-15
Thank you for the replies. Where the "Search For Files" application searches text for words and displays them.

Like if i searched the document Test. which looked like

Test1
Test2
Test3

I would i would like a pop up box which if When i search Test2. It will either say that it doesn't have it or it will display the line Test2.

Thanks again

---

### Post by bodhi.zazen on 2010-02-15
You can do this with zenity.

---

### Post by pedrom169 on 2010-02-15
I am looking at the help page for zenity. Will it be something to do with the --entry option?

Thanks

---

### Post by bodhi.zazen on 2010-02-15
[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by pedrom169 on 2010-02-15
i think i am getting somewhere. I have run zenity --entry which has produced a pop up where i can type in. Now to figure out how to use what i typed in to search a text file and produce a graphical output.

grep test test | zenity --text-info --width 500 - I ran that which produced a output box with my search results in.

---

### Post by pedrom169 on 2010-02-17
anyone?

---

### Post by rnerwein on 2010-02-17
hi
you can put your zenity calls in a script e.g. zenitycmd.sh with following calls to zenity:
#!/bin/bash
#
command=`zenity  --title "run a command" --entry --text "give me the command"`
$command | zenity --text-info --width 1000 --height 500 - I
exit 0

if you type in: grep -i cpu *
$command will run and the ouput will be shown in the next window.
have fun
ciao

---

### Post by pedrom169 on 2010-02-17
thank you for the reply. How would i then get it a pop up asking me what word i want to search and it then go grep -i (word) (file)?

Thanks again for all help

---

### Post by pedrom169 on 2010-02-17
#!/bin/bash
#
word =`zenity --title "Word to search?" --entry --text "What word?"`
Grep -i $word EW | zenity --text-info --width 500 --height 100 - I
exit 0

would that not work?

---

### Post by pedrom169 on 2010-02-17
Nevermind i had a space after word=

all done. thanks for help

---

### Post by rnerwein on 2010-02-17
> **rnerwein said:**
> hi
you can put your zenity calls in a script e.g. zenitycmd.sh with following calls to zenity:
#!/bin/bash
#
command=`zenity  --title "run a command" --entry --text "give me the command"`
$command | zenity --text-info --width 1000 --height 500 - I
exit 0

if you type in: grep -i cpu *
$command will run and the ouput will be shown in the next window.
have fun
ciao

hi 
just for a remark. the example i give means you can type in the first window in what you want. e.g. grep search_word from_file the whole input will placed in "command" and there for the shell will execute: grep search_word from_file. you can even type another command like: ls -l --> then the shell will execute the command ls -l and the output is given to the next window.
you can use this example for any command.
ciao

---

