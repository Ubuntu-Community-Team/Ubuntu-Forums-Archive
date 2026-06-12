---
title: "problem with PATH"
date: 2011-05-14
forum: General Help
---

### Post by sfyoung on 2011-05-14
I just upgraded from 10.10 to 11.04 and am having a problem with my PATH.  I keep a bunch of executables and scripts in a subdirectory of $HOME, and that has allowed me to run them from where the data reside.  Problem is that since the upgrade, I can't run my Perl scripts unless they are in my working directory, then they work fine.  When I do  'echo $PATH'  I can see that the directory that holds my Perl scripts is the first one listed. This arrangement worked before the upgrade.  I assume it doesn't work now because of something that has changed.  In my experience, these kinds of problems are usually due to something I did wrong, but I can't think of how I screwed this up this time.  If the scripts are executable and the directory is the first in my PATH, what else should I check?

---

### Post by sfyoung on 2011-05-14
Let me restate my problem.  I just upgraded from 10.10 to 11.04.

I need to run some Perl scripts on very large data files (over 100 million lines each).  
Because they are big, the files are on an external NTFS drive but most of the analyses must be done in
Unix/Linux.  I have a subdirectory in my home directory where I keep my scripts, I set my
path to include that directory, and the OS accepted my path.  In fact, my Scripts directory is the first directory in my path.

$HOME:~$ echo $PATH

[COLOR=Red]$HOME/Programs/Scripts[/COLOR]:$HOME/Programs/samtools-0.1.16/bcftools:
     $HOME/Programs/samtools-0.1.16:$HOME/Programs/bowtie-0.12.7:
    /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

I have an executable test script named MyTest.pl in Program/Scripts

$HOME/Programs/Scripts:~$ ls -l MyTest.pl
-rwxr-xr-x 1 name name 92 2011-05-14 18:02 MyTest.pl

If I run the script from $HOME (or anywhere else besides $HOME/Programs/Scripts) 
the OS can't find the script even though it is in my path and is executable.

$HOME:~$ perl MyTest.pl
Can't open perl script "MyTest.pl": No such file or directory

If I cd to $HOME/Programs/Scripts and run the script, it runs and gives
me my expected dummy output.

$HOME:~$ cd Programs/Scripts/
$HOME:~/Programs/Scripts$ perl MyTest.pl
Okay.
Done.

I can't figure out why my PATH setting isn't working anymore.  
I have tried writing out the pathnames when I set my PATH and that has not helped.
I have tried running the script as sudo and that has not helped.

What do I need to do differently to get the OS to find stuff in my path?

---

### Post by enimeizoo on 2011-05-14
I might be wrong, but the program you use is perl, not your script. Ubuntu does find perl in your path, but perl doesn't look in your path to find your script.

Assuming your script is in your $PATH , and begins with the path of your interpreter, you should be able to run :
```
MyTest.pl
```
from anywhere.

---

### Post by 5149.5 on 2011-05-14
If the $PATH variable ceased to function, you would have more problems than your script trouble. Show us an echo $PATH command and the output.

---

### Post by lmarmisa on 2011-05-14
I have no experience with Perl but I think you are a bit confused.

If your perl script starts with the line:

```

#!/usr/bin/perl

```

and the perl script has activated its attribute +x, you can type simply the name of the script (do not precede it with perl!!!):

```

$HOME:~$ MyTest.pl

```

In this case, the environment variable $PATH applies.

Other option is to use the command **perl** typing the perl script as first parameter. In this case the environment variable $PATH does not apply:

```

$HOME:~$ perl ~/Programs/Scripts/MyTest.pl

```

I hope this information could help you.

Best regards,

Luis

---

### Post by 5149.5 on 2011-05-15
Luis and enimeizoo are correct. I had never tried calling perl and then the script. I just put a proper shebang line as the first line in the script and then run the script. Doing it the other way like you are doesn't work.

---

### Post by sfyoung on 2011-05-15
I showed it in my second post.  Here it is again.  Note that the first entry in the list, /home/sewall/Programs/Scripts, is where I keep my scripts.

sewall@sewall-AcerOne:~$ echo $PATH
/home/sewall/Programs/Scripts:/home/sewall/Programs/samtools-0.1.16/bcftools:/home/sewall/Programs/samtools-0.1.16:/home/sewall/Programs/bowtie-0.12.7:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by lmarmisa on 2011-05-15
> **sfyoung said:**
> I showed it in my second post.  Here it is again.  Note that the first entry in the list, /home/sewall/Programs/Scripts, is where I keep my scripts.

sewall@sewall-AcerOne:~$ echo $PATH
/home/sewall/Programs/Scripts:/home/sewall/Programs/samtools-0.1.16/bcftools:/home/sewall/Programs/samtools-0.1.16:/home/sewall/Programs/bowtie-0.12.7:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

sfyoung,

the solution is quite simple: simply type the names of the script files.

This is wrong ([COLOR="red"]perl[/COLOR]):

```

$HOME:~$ [COLOR="Red"]perl[/COLOR] MyTest.pl

```

This is correct:

```

$HOME:~$ MyTest.pl

```

---

### Post by 5149.5 on 2011-05-15
> **lmarmisa said:**
> sfyoung,

the solution is quite simple: simply type the names of the script files.

That will only work with a proper shebang line as the first line in the script. I'm not so sure it's there.

---

### Post by 5149.5 on 2011-05-15
> **sfyoung said:**
> I showed it in my second post.  Here it is again.  Note that the first entry in the list, /home/sewall/Programs/Scripts, is where I keep my scripts.

sewall@sewall-AcerOne:~$ echo $PATH
/home/sewall/Programs/Scripts:/home/sewall/Programs/samtools-0.1.16/bcftools:/home/sewall/Programs/samtools-0.1.16:/home/sewall/Programs/bowtie-0.12.7:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Hmmm. I still don't see that in your second post.

You don't want/need your script names in the path.

---

### Post by sfyoung on 2011-05-15
Thanks to all who responded.  Yes the problem seems to be with perl.  I'll try to track down whether it's the 'shebang' line, which worked last week, or maybe perl wasn't happy with the upgrade.  So problem not resolved yet, but I think you have put me on a better track.

Thanks again,

Sewall

---

### Post by sfyoung on 2011-05-15
Okay, with a lot of help getting on the right track, I have resolved my problem.  As all respondents suggested, this was not a PATH problem after all, and it really wasn't a perl problem.  I think it was Dan who suggested that my shebang line (#! usr/bin/env perl) might be faulty, and in fact that was the problem.  I work between Windows at work, and Ubuntu Linux at home.  I had copied some of my scripts from Ubuntu to Windows and back, and had edited some of those scripts in Windows.  Those scripts had the hidden characters '^M' ending the shebang lines and the OS apparently was looking for '/usr/bin/env perl^M'.
Somehow, I got that ^M into my test script.  I used 'dos2linux' to clean the hidden control characters from my test script, and it runs as it should, that is, I type 'MyTest.pl' from anywhere in my system and it works.

In short, it wasn't the computer that screwed up, it was me.

Thanks again to all who helped me resolve this.  My next challenge will be to figure out how to flag this thread as resolved.  I'll really be embarrassed if I need to start a new thread for that.

Sewall

---

### Post by 5149.5 on 2011-05-15
Look under thread tools at the top.

---

