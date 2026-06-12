---
title: "make .txt alphanumeric only"
date: 2011-07-17
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-07-17
running 11.04 x64 if needed.

i have a 1.2 gb txt file that i would like to open and read. unfortunately,libre office freezes and text editor wont even try. i used split to cut it down into way smaller chunks, which only took maybe a minute, but most of the files still freeze on opening with libre office and still wont open with text editor. i have decided to just go back to the source file (which is copied in case i fudge up a command) to try to just cut out all the special characters. i tried this command from looking around before coming here.
"tr -dc ‘[:alnum:]‘"
 got back
"tr: extra operand"
"Only one string may be given when deleting without squeezing repeats."

i then retried it without the -dc option, and its been sitting there for about 40 plus minutes like it's doing something (no error message, went to next line without new prompt) but the file is still the exact same size-i would think it would slim down even a little bit if the command was doing anything. 

if someone has a quick way to remove all special characters, making it alphanumeric text only, keeping the spaces... i would greatly appreciate it, and please make it simple to follow for a noobie. i love linux but its real easy for me to get lost in steps.

---

### Post by lmarmisa on 2011-07-17
I recommend to use the command **strings**:

```

strings yourfile > alphanumericfile.txt

```

More information about this command typing:

```

man strings

```

Best regards,

Luis

---

### Post by SE7EN-LOCSTA on 2011-07-18
i did that command, replacing 'yourfile' with the file n location of my file, and it did give me an actual text file that i can open up.thank you a bunch. i am one step closer to my final product. is there a command to make it just delete all non (a-z, 0-9) characters?

---

### Post by Zebediah49 on 2011-07-18
should be doable with tr, but given that you said that wasn't working properly, you can try sed
```

sed 's/[^0-9A-Za-z]//g'

```
will do it via substitution, you could use direct deletion if you would prefer though.

---

### Post by Habitual on 2011-07-18
```
sed -e 's/[^0-9A-Za-z]//g' file 
```to examine what the result would be.

```
sed -i 's/[^0-9A-Za-z]//g' file
``` to actually do the job.

---

### Post by SE7EN-LOCSTA on 2011-07-18
thanks very much, worked great

---

