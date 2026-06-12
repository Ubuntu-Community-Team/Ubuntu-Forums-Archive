---
title: "adding text to a file from crontab"
date: 2010-07-14
forum: General Help
---

### Post by three_jeeps on 2010-07-14
I want to append a text string onto an existing file from crontab.
These do not work:

0 1 * * * cp "test" >> /home/xys/myfile.txt
0 1 * * * mv "test" >> /home/xys/myfile.txt
0 1 * * * cp 'test' >> /home/xys/myfile.txt
0 1 * * * mv 'test' >> /home/nys/myfile.txt

How can this be done?
Thanks
J

---

### Post by CannibalZerg on 2010-07-14
echo One_Word_Text >> /home/nys/myfile.txt
echo "Text with spaces" >> /home/nys/myfile.txt
echo 'Text with exclamation signs!!!!!' >> /home/nys/myfile.txt

---

### Post by iMisspell on 2010-07-14
You might be better off creating one single bash script and then have the script do all the work for you.

```
0 1 * * * /path/to/script.sh
```

script_file.sh
```
#!/bin/bash

cp file1 file2
echo 'what ever...' >> /home/xys/file2.txt

mv file3 file4
echo 'what ever...' >> /home/xys/file4.txt

cp file5 file6
echo 'what ever...' >> /home/xys/file6.txt

mv file7 file8
echo 'what ever...' >> /home/xys/file8.txt

```

If you give more detail in what you want to do, you might get better suggestions.

_

---

### Post by three_jeeps on 2010-07-14
> **CannibalZerg said:**
> echo One_Word_Text >> /home/nys/myfile.txt
echo "Text with spaces" >> /home/nys/myfile.txt
echo 'Text with exclamation signs!!!!!' >> /home/nys/myfile.txt

precisely what I needed-TY!

The script approach is just a workable but for my specific need, the direct message from cron fits.  

I could also get the info I need from /var/log/syslog, but it is intermingled with a lot of other system entries... and did'nt want to grep it.

Thanks!

---

### Post by three_jeeps on 2010-07-14
> **CannibalZerg said:**
> echo One_Word_Text >> /home/nys/myfile.txt
echo "Text with spaces" >> /home/nys/myfile.txt
echo 'Text with exclamation signs!!!!!' >> /home/nys/myfile.txt

hmmm following the same idea, if I want to append a date stamp together with a text string, how could I do that??

TY
-J

---

### Post by CannibalZerg on 2010-07-14
echo `date +"%F %T"`" Some text here" >> /home/nys/myfile.txt

---

### Post by three_jeeps on 2010-07-14
> **CannibalZerg said:**
> echo `date +"%F %T"`" Some text here" >> /home/nys/myfile.txt

I must be missing something here...does not work on my installation

---

### Post by three_jeeps on 2010-07-14
> **three_jeeps said:**
> I must be missing something here...does not work on my installation

Being more specific, nothing is appended to the target file...
I tried putting &date with same result.

---

### Post by CannibalZerg on 2010-07-15
Try to run this command in terminal:
```

echo $(/bin/date +"%F %T")" Some text"

```

If it works fine, add >> redirection to file.

---

### Post by three_jeeps on 2010-07-15
> **CannibalZerg said:**
> Try to run this command in terminal:
```

echo $(/bin/date +"%F %T")" Some text"

```

If it works fine, add >> redirection to file.

Tried the above from the CL, works fine.  I installed in crontab and no text appears in the file that it is redirected to.
The crontab entry looks like:
* * * * * echo $(/bin/date +"%F %T")" Some text" >> /home/me/foo.txt
the other variation I tried:
* * * * * echo $(/bin/date +"%F %T")" Some text"

I tried the above with no redirection, and got nothing on stdout.

btw, am running bash.  Any other suggestions appreciated..TY
-J

---

### Post by three_jeeps on 2010-07-16
> **three_jeeps said:**
> Tried the above from the CL, works fine.  I installed in crontab and no text appears in the file that it is redirected to.
The crontab entry looks like:
* * * * * echo $(/bin/date +"%F %T")" Some text" >> /home/me/foo.txt
the other variation I tried:
* * * * * echo $(/bin/date +"%F %T")" Some text"

I tried the above with no redirection, and got nothing on stdout.

btw, am running bash.  Any other suggestions appreciated..TY
-J

Using the escape in the date command, in crontab worked:
```


* * * * * echo $(/bin/date +"\%F \%T")" Some text" >> /home/me/foo.txt 
```

Interestingly, using the single quotes did not....hmmm
```


* * * * * echo $(/bin/date +'%F %T')" Some text" >> /home/me/foo.txt 
```

Thank you!

---

