---
title: "No data, signing ubuntu code of conduct"
date: 2009-10-22
forum: General Help
---

### Post by tommynz1975 on 2009-10-22
Hi guys....  
I am attempting to sign the ubuntu code of conduct on launchpad with out success.

I followed steps 1-3 on step 4 is when it falls apart


I try to follow step 4 with the result 
1 error no data.

I have deleted my .txt.asc file, gone back to terminal and followed step 3 again.
Please help with step 4.

The wrong thing I am doing is more than likely simple.

your help I appreciate
-------
Sign the Ubuntu code of Conduct 
         
                                                                                                                                                                                                                  To sign the code of conduct:                 
                 
[LIST=1]
[*]                                            [Download]("https://launchpad.net/codeofconduct/1.0.1/+download")                       the file to your own computer and read it carefully                       to ensure you agree to it.
[*]                                            If you want to, add extra spaces or blank lines between words                       in the file.                       (This helps protect against other people trying to                       forge your signature.)
[*]                                            In a terminal, run the command:[INDENT]                       gpg --clearsign UbuntuCodeofConduct-1.0.1.txt                       [/INDENT](or whatever filename you gave to the code).                       This will create a file with a name like                       UbuntuCodeofConduct-1.0.1.txt.asc.
[*]                                            Open that new file,                       and copy and paste its contents into this box.                       Then click “Continue”.
[/LIST]

---

### Post by Johnny B on 2009-10-22
are you pasting something like this?
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1 

ORIGINAL MESSAGE


rfgsergwergdfgwet423tb654y9034u509tut
rt893y24-3yht-8f9024vhgy2-rop-0uerg=04j9
r02933h4----g
-----END PGP SIGNATURE-----

---

### Post by tommynz1975 on 2009-10-22
no I am not

I have now in my folder the txt file (with spaces and the asc file created in step 3

in the deleted file. I had decyrpted the file and tried send in plain text

was I not ment to do this

---

### Post by tommynz1975 on 2009-10-22
found what I did wrong


after step 3 I had dycrpt the file....  this was NOT meant to happen.
fixed by
 opening  text editor, opened the file
then I cut and pasted..

this got me step.4 complete

---

