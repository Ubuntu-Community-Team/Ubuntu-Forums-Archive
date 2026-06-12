---
title: "A quistion of how things are done, in terminal..."
date: 2012-01-08
forum: General Help
---

### Post by thusgaard on 2012-01-08
Hi

I'm wondering how complex tasks I can solve in the terminal. I'm beliving rather complex, if I know what to do. Here is my current "problem":

I have a folder of 30+ jpg files. All of these files are realy zip files. Each file contains a jpg file of a QR code. I need the information in the QR code to be stored in a TXT file with the name og the original ZIP (jpg) file.

I see the following operations:
1. Convert all .jpg extentions to .zip (this may not be needed)
2. Unzip all files (1 file per zip file) and name them with the name of the zip file. 
3. Read all the new .jpg files (they are all QR codes) and save the information in filename.txt

I'm sure that 1 & 2 can be done, just not sure how. I'm not sure that 3 can be done. 

This is where I'm almost certain that I'll have to do the last 2 steps by hand...

4. Read the text in each filename.txt and process it as an vigenere cipher (I know the key)
5. Count the number of A's, B's and sofort in the new decoded text.

J;-)

---

### Post by alexfish on 2012-01-08
no asking a lot ;)

to extract a file

cd /path/to/dir where you want to extract

tar -x <filename> -f /path/to/*.tar

have a look at man pages
man "wrjpgcom" "cjpeg" "djpeg" "jpegtran"  "rdjpgcom"


for others best look at
for encoding
[http://papacharliefox3.wordpress.com/2009/04/02/desafio-de-crypto-ii-cifra-de-vigenere/for](http://papacharliefox3.wordpress.com/2009/04/02/desafio-de-crypto-ii-cifra-de-vigenere/for) decoding
[http://smurfoncrack.com/pygenere/pygenere.py](http://smurfoncrack.com/pygenere/pygenere.py)

---

### Post by Paqman on 2012-01-08
Looks like there are libs in the repos for decoding QR codes in a few different languages, take your pick.

---

