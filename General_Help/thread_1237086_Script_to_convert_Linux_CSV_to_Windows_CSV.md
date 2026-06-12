---
title: "Script to convert Linux CSV to Windows CSV"
date: 2009-08-11
forum: General Help
---

### Post by CTenorman on 2009-08-11
Hi,

I've just exported my evolution address book to CSV format (evolution-addressbook-export --format=csv >contact_list.csv) hoping to import it into the Timex Datalink software. 

However the software, and even windows notepad, don't seem to recognize the carriage returns, but instead shows a square box where the carriage return should be.

Does anyone know of a quick script to convert those little boxes into windows-style carriage returns so that the Timex program can properly recognize and deal with line ends?

Thanks!!

---

### Post by lisati on 2009-08-11
There is a tool I'm aware of called [unix2dos]("http://www.shareup.com/Unix2Dos-download-35984.html") which will do the job. If you don't mind compiling stuff, a short C program to do the job can be found [here]("http://ubuntuforums.org/attachment.php?attachmentid=117144&d=1244668823")

---

### Post by yabbadabbadont on 2009-08-11
```
apt-get install tofrodos
```

No need to compile anything.

---

### Post by roharme on 2009-08-11
Good info

---

### Post by CTenorman on 2009-08-11
Perfect, thank you!! Is it ever good to have people like you guys floating around on the forum! :)

---

### Post by lisati on 2009-08-11
> **yabbadabbadont said:**
> ```
apt-get install tofrodos
```

No need to compile anything.
Thank you: something new for me to remember, and a good reminder of how there's sometimes more than one answer to questions.
> **CTenorman said:**
> Perfect, thank you!! Is it ever good to have people like you guys floating around on the forum! :)
Good luck, and I hope some of the ideas presented so far are of some help.

---

### Post by DaithiF on 2009-08-11
Hi,
just for variety :), a couple more ways using the command line:

1. using tr to delete the carriage returns
```
tr -d '\r' < windowsfile > unixfile

```
2. using sed
```
sed 's/\r//' windowsfile > unixfile
```

---

### Post by ad_267 on 2009-08-11
A bit more info:
Windows uses a carriage return followed by a newline (\r\n) to mark the end of a line, whereas Unix/Linux used a newline only. Wordpad rather than Notepad can be used to read files with Linux/Unix style line endings in Windows.
The above post would work to convert Windows files to the Unix/Linux style, but not the other way around. You would want:
```
sed 's/\n/\r\n/' unixfile > windowsfile
```

---

