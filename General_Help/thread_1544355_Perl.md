---
title: "Perl"
date: 2010-08-02
forum: General Help
---

### Post by Hosmion on 2010-08-02
Hello everyone.  I am planning on doing some Perl and Python coding since they are going to be the native languages since I am deleting Windows.  I need help getting to Perl though.  I know Python has a Shell which I am using now to program, but I don't know of anything like that for Perl.  I am learning Perl and using SciTE to edit the programs, but, when I try to execute them in terminal with the commands below it gives me errors.  I will paste all the information below.

TestPerl Program coding:

```
#!usr/bin/perl

print "Hello!"
```

Terminal Conversation:

```
tommy@ubuntu:~$ chmod +x /home/tommy/Desktop/TestPerl
tommy@ubuntu:~$ ./TestPerl
bash: ./TestPerl: No such file or directory
tommy@ubuntu:~$ /home/tommy/Desktop/TestPerl
bash: /home/tommy/Desktop/TestPerl: usr/bin/perl: bad interpreter: No such file or directory
```

I marked the file as executable, but when I hit Run In Terminal it just opens and closes really fast.

Thanks,
Tom

---

### Post by WorMzy on 2010-08-02
You've missed out the slash before usr.

The first line should be:

```
#!**[COLOR="Red"]/[/COLOR]**usr/bin/perl
```
 Also, to run the script from a terminal with ./TestPerl, you first need to navigate to your Desktop folder (since that's where it's saved) with
```
cd ~/Desktop
```

---

### Post by Hosmion on 2010-08-02
Ok, that's fixed, much thanks.  But I have another question, how do I take user input?

---

### Post by WorMzy on 2010-08-02
I've not used perl for much, but this tutorial may help you: [http://www.wellho.net/resources/ex.php4?item=p103/greeting](http://www.wellho.net/resources/ex.php4?item=p103/greeting)

---

### Post by Hosmion on 2010-08-02
> **WorMzy said:**
> I've not used perl for much, but this tutorial may help you: [http://www.wellho.net/resources/ex.php4?item=p103/greeting](http://www.wellho.net/resources/ex.php4?item=p103/greeting)
Thank you guys sooo much!  All fixed :).  *Marks thread as solved*.

---

