---
title: "pdftk stamp function"
date: 2010-04-08
forum: General Help
---

### Post by gary.h on 2010-04-08
Hi All,

I've been trying to use the stamp function in pdftk. I'm trying to stamp a pdf document with a pdf I generate on the fly that contains the current date. Below is what I have so far. The problem is that pdftk says "Error: failed to open stamp PDF file". the file is in the same dir as execution, I've made it 776, I've specified full paths... nothing seems to work. I've even tried the "prompt" option and specify it manually but I get the same behavior. This is pdftk version 1.4. Many thanks to whoever can tell me what I'm doing wrong!

**Script (named "go"):**
```
# date in YYYY-MM-DD format

umask 0

# create a variable with a formatted date
TODAY=`date +%Y-%m-%0e`;

# create a variable with a working directory to save some typing
DIR=/home/testbox/test

# Tested and complete, need notes
enscript -B -h --underlay=$TODAY --ul-style=outline --ul-position='+55-0' --ul-gray=.6 --ul-font=Courier135 -f Courier10 fingerprint.txt -o $DIR/today.pdf

pdftk $DIR/fw4.pdf stamp $DIR/today.pdf output $DIR/fw4-stamped.pdf verbose
```**Directory listing:**
testbox@sps-testbox-test ~/test $ ll
total 204K
drwxr-xr-x  2 testbox testbox 4.0K 2010-04-08 13:21 .
drwxr-xr-x 44 testbox testbox 4.0K 2010-04-08 12:07 ..
-rw-r--r--  1 testbox testbox    2 2010-04-08 11:28 fingerprint.txt
-rwxrwxrw-  1 testbox testbox 164K 2010-04-06 14:12 fw4.pdf
-rwxr-xr-x  1 testbox testbox  720 2010-04-08 12:07 go
-rwxr-xr-x  1 testbox testbox   83 2010-04-06 14:15 go.sh
-rw-r--r--  1 testbox testbox   75 2010-04-07 16:49 gs
-rwxrwxrw-  1 testbox testbox  12K 2010-04-08 12:07 today.pdf
-rw-r--r--  1 testbox testbox   11 2010-04-08 11:38 today.txt
testbox@sps-testbox-test ~/test $

**Output:**

testbox@sps-testbox-test ~/test $ pwd
/home/testbox/test
testbox@sps-testbox-test ~/test $ ./go
[ 1 pages * 1 copy ] left in /home/testbox/test/today.pdf
Command Line Data is valid.

Input PDF Filenames & Passwords in Order
( <filename>[, <password>] )
   /home/testbox/test/fw4.pdf

The operation to be performed:
   filter - Apply 'filters' to a single, input PDF based on output args.
      (When the operation is omitted, this is the default.)

The output file will be named:
   /home/testbox/test/fw4-stamped.pdf

Output PDF encryption settings:
   Output PDF will not be encrypted.

No compression or uncompression being performed on output.

Creating Output ...
Error: Failed to open stamp PDF file:
   /home/testbox/test/today.pdf
   No output created.
testbox@sps-testbox-test ~/test $ 
testbox@sps-testbox-test ~/test $ pwd
/home/testbox/test

---

### Post by gary.h on 2010-04-08
ok so the issue isn't with pdftk, it's with enscript. pdftk can't open pdf created with this tool for some reason. hopefully I'm missing some kind of option with enscript

---

### Post by gmargo on 2010-04-08
**enscript(1)** creates a PostScript document, not a PDF document.  Try running **ps2pdf(1)** on the output of **enscript(1)**.

---

### Post by gary.h on 2010-04-09
Ah, yes that does it! I thought I had to be missing something basic.

Many thanks!

---

