---
title: "Shell creation help."
date: 2012-10-09
forum: General Help
---

### Post by linuxvstheworld on 2012-10-09
I was reading up how to create a shell script on [http://linuxcommand.org](http://linuxcommand.org) and noticed something, there's a part for an example shell script, as follows.
```
#!/bin/bash
# My first script

echo "Hello World!"
```
Let's say I input that in gedit, will the '#!/bin/bash' part tell gedit to save it there? The site really didn't go in detail.

---

### Post by Vaphell on 2012-10-09
no, that 1st line tells the system which interpreter should be used to run the script. Extension of the filename doesn't matter, all these .sh, .py (python) carry no meaningful information but are used by convention so the user can identify them without looking at contents. Simply put that hashbang line defines which 'family' the file belongs to. /bin/bash is the physical location of the bash executable that will be used to interpret the script.

In your case running the script with *./script.sh* would be equivalent to *bash script.sh*. System looks at the first line, sees bash - bash it is, here you go. You can override that default if you want by explicitly calling some other interpreter, eg. *sh script.sh* but it doesn't make much sense to run scripts in their non-native environments (there are differences in syntax and feature sets, simple shell script may work, but bash has a lot of nifty features that will fail when tried in sh)


you work with shell scripts like with any other plain text files. The only difference is that shell scripts can be run when the hashbang line is present and the file itself is marked as executable.

---

### Post by matt_symes on 2012-10-09
Hi

> Let's say I input that in gedit, will the '#!/bin/bash' part tell gedit to save it there?I'm not 100% sure what you are asking,bit if i understand you correctly, that does not tell gedit where to save the script. You need to tell gedit where to save the file and give it a file name.

```
#!/bin/bash
```What this does is to specify what shell should be used to run the script when the script is run as an executable file with the executable bit set in it's permissions and you do not specify which shell to run it with from the command line.

```

matthew-Aspire-7540:/home/matthew % cat script 
#!/bin/bash
# My first script

echo "Hello World!"

matthew-Aspire-7540:/home/matthew % chmod 755 script 
matthew-Aspire-7540:/home/matthew % ll script      
-rwxr-xr-x 1 matthew matthew 52 Oct  9 18:18 script*
matthew-Aspire-7540:/home/matthew % ./script 
Hello World!
 
```Without the executable bit set you cannot run the script that way......

```
matthew-Aspire-7540:/home/matthew % chmod 664 script
matthew-Aspire-7540:/home/matthew % ll script 
-rw-rw-r-- 1 matthew matthew 52 Oct  9 18:18 script
matthew-Aspire-7540:/home/matthew % ./script
zsh: permission denied: ./script
matthew-Aspire-7540:/home/matthew % 
```....but you can run it without the executable bit set script if you state the shell to run it with though on the command line.

```

matthew-Aspire-7540:/home/matthew % ll script 
-rw-rw-r-- 1 matthew matthew 52 Oct  9 18:18 script
matthew-Aspire-7540:/home/matthew % bash script
Hello World!
matthew-Aspire-7540:/home/matthew % 
```There are a number of shells you can use to run scripts and by putting the shebang (!#) and the path to the shell as the first line of your script, you specify which shell to run the script when the script is run as an executable file.

You can get an idea of the shells on your system by looking at /etc/shells. Here's mine

```

matthew-Aspire-7540:/home/matthew % cat /etc/shells 
# /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash
/usr/bin/screen
/usr/bin/tmux
/bin/zsh
/usr/bin/zsh
/bin/csh
/bin/tcsh
/usr/bin/tcsh
matthew-Aspire-7540:/home/matthew % 
```You can specify different shell to run your script by changing the shebang line (i.e #!/bin/dash) and, when run as an executable script, it will run the script using that shell.

This, below, will change the shell to dash in the file, check it and run the script using the dash shell.

```
matthew-Aspire-7540:/home/matthew % sed -i 's/bash/dash/' script 
matthew-Aspire-7540:/home/matthew % head -n1 script 
#!/bin/dash
matthew-Aspire-7540:/home/matthew % ./script 
Hello World!
matthew-Aspire-7540:/home/matthew % 
```Note there are differences between the shells and some commands wont work in some shells. 

csh and tsch even have a completely different  syntax more in line with the C programming language.

I hope i understood your question correctly and i hope that made sense.

Kind regards

---

### Post by linuxvstheworld on 2012-10-23
> **matt_symes said:**
> Hi

I'm not 100% sure what you are asking,bit if i understand you correctly, that does not tell gedit where to save the script. You need to tell gedit where to save the file and give it a file name.

```
#!/bin/bash
```What this does is to specify what shell should be used to run the script when the script is run as an executable file with the executable bit set in it's permissions and you do not specify which shell to run it with from the command line.

```

matthew-Aspire-7540:/home/matthew % cat script 
#!/bin/bash
# My first script

echo "Hello World!"

matthew-Aspire-7540:/home/matthew % chmod 755 script 
matthew-Aspire-7540:/home/matthew % ll script      
-rwxr-xr-x 1 matthew matthew 52 Oct  9 18:18 script*
matthew-Aspire-7540:/home/matthew % ./script 
Hello World!
 
```Without the executable bit set you cannot run the script that way......

```
matthew-Aspire-7540:/home/matthew % chmod 664 script
matthew-Aspire-7540:/home/matthew % ll script 
-rw-rw-r-- 1 matthew matthew 52 Oct  9 18:18 script
matthew-Aspire-7540:/home/matthew % ./script
zsh: permission denied: ./script
matthew-Aspire-7540:/home/matthew % 
```....but you can run it without the executable bit set script if you state the shell to run it with though on the command line.

```

matthew-Aspire-7540:/home/matthew % ll script 
-rw-rw-r-- 1 matthew matthew 52 Oct  9 18:18 script
matthew-Aspire-7540:/home/matthew % bash script
Hello World!
matthew-Aspire-7540:/home/matthew % 
```There are a number of shells you can use to run scripts and by putting the shebang (!#) and the path to the shell as the first line of your script, you specify which shell to run the script when the script is run as an executable file.

You can get an idea of the shells on your system by looking at /etc/shells. Here's mine

```

matthew-Aspire-7540:/home/matthew % cat /etc/shells 
# /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash
/usr/bin/screen
/usr/bin/tmux
/bin/zsh
/usr/bin/zsh
/bin/csh
/bin/tcsh
/usr/bin/tcsh
matthew-Aspire-7540:/home/matthew % 
```You can specify different shell to run your script by changing the shebang line (i.e #!/bin/dash) and, when run as an executable script, it will run the script using that shell.

This, below, will change the shell to dash in the file, check it and run the script using the dash shell.

```
matthew-Aspire-7540:/home/matthew % sed -i 's/bash/dash/' script 
matthew-Aspire-7540:/home/matthew % head -n1 script 
#!/bin/dash
matthew-Aspire-7540:/home/matthew % ./script 
Hello World!
matthew-Aspire-7540:/home/matthew % 
```Note there are differences between the shells and some commands wont work in some shells. 

csh and tsch even have a completely different  syntax more in line with the C programming language.

I hope i understood your question correctly and i hope that made sense.

Kind regards

I know it's kind of late to reply but, I did everything you did, I actually saved the file through gedit, put it on the desktop,changed permissions to 755, and ran it. At 13 years old I made my first script! And I'd like to thank you so so much on walking me through it! :)

---

### Post by hakermania on 2012-10-23
13 yo is a good age to get your hands dirty with this stuff... Gongrats!

---

### Post by MG&amp;TL on 2012-10-23
You don't know what you're getting yourself into...before you know it, you'll be humming the free software song at your console, with a huge UNIX beard and sandals. ;)

Seriously though, well done and keep it going.

---

### Post by linuxvstheworld on 2012-10-23
> **MG&TL said:**
> You don't know what you're getting yourself into...before you know it, you'll be humming the free software song at your console, with a huge UNIX beard and sandals. ;)

Seriously though, well done and keep it going.

Now you're making me look up that song.....

---

### Post by linuxvstheworld on 2012-10-25
Are there any differences in using different shells? Or is bash the best for basic scripts?

---

### Post by CaptainMark on 2012-10-26
There is no best shell to use, it's down to personal preference but bash is a good shell to learn because a) its basic syntax is quick and easy to learn b) it has lots of clever advanced features so will last forever to learn it c) its the standard shell your computer uses in a terminal so if you learn to bash script you will become more competent at using the terminal to control your computer

Python is another good language to learn for the same first 2 reasons, the thing I like best about bash though is almost immediately you can start using it for real world scenarios like running automated backups of your system and having certain programs run on login.

 I have one script which runs when I login on my system which will run every script I place in a specified folder, in that folder I have scripts to start banshee playing music in the background, start empathy in the background, back up my data folder on a schedule, set the volume to a reasonable level, start transmission, move photos out of my dropbox folder and sort them into appropriate folders of ~/Picutres/year/month   the list goes on and on all done very simply using bash scripts

---

### Post by Lars Noodén on 2012-10-26
> **linuxvstheworld said:**
> Are there any differences in using different shells? Or is bash the best for basic scripts?

bash and ksh are large, fancy and can do more. But if you use sh (dash on Ubuntu), the script is more likely to be POSIX compliant and thus portable to other non-Ubuntu systems like BSD and Solaris.  sh is also a little faster than bash.

---

