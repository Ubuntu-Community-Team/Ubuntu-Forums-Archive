---
title: "executing perl from browser"
date: 2010-03-28
forum: General Help
---

### Post by Felix Lionheart on 2010-03-28
Alright, I'm running Apache2 on my Ubuntu 9.10 desktop and have been having problems with perl executing from my browser. I'm sure perl is working because I can execute it from the terminal using perl /usr/lib/cgi-bin/test.pl and get an output from the print command.

Here is the perl script I'm using:
```
#!/usr/bin/perl

print <<E_O_F;
content-type: text/html

<HTML>
<HEAD>
<TITLE>Test CGI script</TITLE>
</HEAD>
<BODY>
Perl is working.
E_O_F

print'<BR></BODY></HTML>';
```

And here is the error from the apache error.log file:

```
[Sun Mar 28 15:14:29 2010] [error] [client ::1] (2)No such file or directory: exec of '/usr/lib/cgi-bin/tester.pl' failed
[Sun Mar 28 15:14:29 2010] [error] [client ::1] Premature end of script headers: tester.pl
```

Would really appreciate any help with my problem because I need to write 5 perl scripts for my college course work by tomorrow. If any information is needed to help with the problem I'd be happy to provide it.

thanks.

---

### Post by gmargo on 2010-03-28
1. Is the file executable?
2. Is the file named correctly? (you ran it by hand with "perl /usr/lib/cgi-bin/test.pl" but the error message refers to '/usr/lib/cgi-bin/tester.pl' - note the spelling difference.)

Update: In another thread, I posted a "hello world" type cgi script that might help you: [http://ubuntuforums.org/showthread.php?t=1429467](http://ubuntuforums.org/showthread.php?t=1429467)

---

### Post by Felix Lionheart on 2010-03-28
> **gmargo said:**
> 1. Is the file executable?
2. Is the file named correctly? (you ran it by hand with "perl /usr/lib/cgi-bin/test.pl" but the error message refers to '/usr/lib/cgi-bin/tester.pl' - note the spelling difference.)

Update: In another thread, I posted a "hello world" type cgi script that might help you: [http://ubuntuforums.org/showthread.php?t=1429467](http://ubuntuforums.org/showthread.php?t=1429467)

Ah, I was testing the same script inside 2 different files to see if one was working over the other but they both returned the same error. Also have no idea how but when I went away for around 30 minutes and got back I could execute the perl scripts from the browser without any problems.

Thanks for the reply though :)

---

