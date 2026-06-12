---
title: "run-parts not working ?"
date: 2010-06-13
forum: General Help
---

### Post by gyre007 on 2010-06-13
Hi I have a very dumb questions regarding run-parts utility...

I've created few shell scripts, chmod them to be executable, placed them into one particular directory and tried to run them using run-parts utility like this

run-parts dir_name

However it doesn't seem to be working or I might just be missing out something....
I have even tried different options like --test or --list - NONE of them produced any output. If I run each of the script manually they all work just fine. Is this is a known bug or somethng ?? or am I really missing out something...how are the /etc/crontab entries then being executed when the run-parts doesn't seem to be working on such a simple case ?
Thanks a lot for all the help!

ps: I noticed one interesting thing though...when I run run-parts like this:

run-parts --list --regex 'some_regexp_patern' dir_name  -> the output actually produces a list of the files whose file names match the given regexp pattern ....so IM TOTALLY CONFUSED

---

### Post by john newbuntu on 2010-06-14
Scripting 101: Never forget the shebang. If your scripts do not have this, please add "#!/bin/sh" or "#!/bin/bash" or whatever the case may as the first line of your script.  Although not required, return the correct exit status wherever appropriate.

Now, assuming 'mydir' to be the directory containing your scripts, run it from the parent directory as follows:
```
run-parts mydir
```
or with any other options. If you run it from elsewhere, provide the full path to mydir in order for it to work.  I am assuming that you are the owner of the scripts and the directory.

---

### Post by gyre007 on 2010-06-14
> **john newbuntu said:**
> Scripting 101: Never forget the shebang. If your scripts do not have this, please add "#!/bin/sh" or "#!/bin/bash" or whatever the case may as the first line of your script.  Although not required, return the correct exit status wherever appropriate.

Now, assuming 'mydir' to be the directory containing your scripts, run it from the parent directory as follows:
```
run-parts mydir
```or with any other options. If you run it from elsewhere, provide the full path to mydir in order for it to work.  I am assuming that you are the owner of the scripts and the directory.

Hi,
all very valid points and when I was testing it all points were satisfied...
Interesting thing is that it actually works fine on my fedora13 box:

[gyre@fedora13 scripts]$ ls -l runptest/
total 12
-rwxrwxr-x 1 gyre gyre 21 Jun 14 09:22 first.sh
-rwxrwxr-x 1 gyre gyre 21 Jun 14 09:22 second.sh
-rwxrwxr-x 1 gyre gyre 21 Jun 14 09:22 third.sh


[gyre@fedora13 scripts]$ cat runptest/first.sh 
#!/bin/bash

echo $0
[gyre@fedora13 scripts]$ cat runptest/second.sh 
#!/bin/bash

echo $0
[gyre@fedora13 scripts]$ cat runptest/third.sh 
#!/bin/bash

echo $0


as you can see for testing purposes each script basically only prints out the name of the script...
this is the result of running the run-parts:

[gyre@fedora13 scripts]$ run-parts runptest
runptest/first.sh:

runptest/first.sh
runptest/second.sh:

runptest/second.sh
runptest/third.sh:

runptest/third.sh

so that's great ....but the question really is why isn't this working on my ubuntu box 10.04
Cheers

---

### Post by john newbuntu on 2010-06-14
That works right out of the box for me on 10.04 and 9.10.  I am running run-parts version 3.2.2 on Lucid.
Just for the heck of it change #!/bin/bash to #!/bin/sh and see if that helps. That'll me news to me if it works.

---

### Post by gpsmikey on 2010-08-09
I realize I am just a *bit* late to the party, but in snooping around I came across this just after reading the bug report where it indicates there is a problem running scripts that end in .sh

See here - I think this is what you are running into:
[https://bugs.launchpad.net/ubuntu/+source/debianutils/+bug/38022](https://bugs.launchpad.net/ubuntu/+source/debianutils/+bug/38022)

mikey

---

