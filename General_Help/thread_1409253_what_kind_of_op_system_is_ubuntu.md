---
title: "what kind of op system is ubuntu?"
date: 2010-02-17
forum: General Help
---

### Post by Jfuse on 2010-02-17
by that i mean, is ubuntu a 32 bit or a 64 bit operating system?

---

### Post by audiomick on 2010-02-17
There is a variation for both architectures. There are commands in this post
[http://ubuntuforums.org/showpost.php?p=8807508&postcount=5](http://ubuntuforums.org/showpost.php?p=8807508&postcount=5)
to find out both if your Ubuntu is 32 or 64 bit as well as to check your hardware.

---

### Post by whoop on 2010-02-17
> **Jfuse said:**
> by that i mean, is ubuntu a 32 bit or a 64 bit operating system?

32 and 64 bit are both available for download...

---

### Post by Jfuse on 2010-02-17
i see. i just recently got the unbunto 9.10 update, and i'm not sure as to which one i've got. how do i find out exactly what the version is?

---

### Post by JackRock on 2010-02-17
> **Jfuse said:**
> i see. i just recently got the unbunto 9.10 update, and i'm not sure as to which one i've got. how do i find out exactly what the version is?

This was already answered

[quote=audiomick]There is a variation for both architectures. There are commands in this  post
[http://ubuntuforums.org/showpost.php...08&postcount=5]("http://ubuntuforums.org/showpost.php?p=8807508&postcount=5")
to find out both if your Ubuntu is 32 or 64 bit as well as to check your  hardware.[/quote]

---

### Post by philinux on 2010-02-17
@Jfuse

Open a terminal, Applications>accessories>terminal

Type in 

```
uname -a
```

Press enter.

Linux philcb-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 **[COLOR="Red"]x86_64[/COLOR]** GNU/Linux

If similar to the above comes back you got 64 bit. Otherwise 32.

---

### Post by dorothykinder on 2010-02-17
How well is that we can identify its a 32 bit or a 64 bit ??

---

### Post by pirateghost on 2010-02-17
> **dorothykinder said:**
> How well is that we can identify its a 32 bit or a 64 bit ??
seriously?

did you read the post above yours?

---

### Post by philinux on 2010-02-17
If someone wants to know if their CPU is 64 bit capable.


```
cat /proc/cpuinfo | grep lm
```

If you get any output, it is 64 bit, if you get nothing then it's 32 bit.

---

### Post by blur xc on 2010-02-17
> **philinux said:**
> @Jfuse

Open a terminal, Applications>accessories>terminal

Type in 

```
uname -a
```Press enter.

Linux philcb-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 **[COLOR=Red]x86_64[/COLOR]** GNU/Linux

If similar to the above comes back you got 64 bit. Otherwise 32.

Woo hoo!  I wrote a dumb bash script to remove ambiguity from those who can't tell that i686 = 32bit and x86_64 = 64bit!

dumb.sh
```
#!/bin/bash

if [ `uname -a | grep i686 -o` = "i686" ]
then
    echo Your computer is running 32bit Linux
else
    echo Your computer is running 64bit Linux
fi

```
It only took me about a 1/2hr...  :D  I couldn't remember the proper if-then-else syntax...

BM

---

### Post by bodhi.zazen on 2010-02-17
> **philinux said:**
> If someone wants to know if their CPU is 64 bit capable.


```
cat /proc/cpuinfo | grep lm
```If you get any output, it is 64 bit, if you get nothing then it's 32 bit.

```
grep ' lm ' /proc/cupinfo
``` :twisted:

you want just the lm and no need to cat | grep (saves on typing)

---

### Post by blur xc on 2010-02-17
dumb.sh version 0.0.0-001

```
#!/bin/bash

if [ `uname -a | grep i686 -o` = "i686" ]
then
    echo Your computer is running 32bit Linux
    if [ -z `grep ' lm ' /proc/cpuinfo` ]
    then
        echo and your cpu is only 32bit capable.
    else
        echo but your cpu is 64bit capable.
    fi
else
    echo Your computer is running 64bit Linux
fi
```

Sorry, it's just that learning to write scripts is more fun this way...

Anyone w/ a 64bit system and or a 32bit system on a 64 bit capable processor wanna try it and let me know if it works?

I'm assuming becasue I'm running Crunchbang in VBox right now, is why it's saying I'm only 32bit capable.  

BM

---

### Post by audiomick on 2010-02-18
Hallo.
I copied your script and pasted it into a terminal and hit enter. Got this
```
mick@ubuntu-desktop:~$ #!/bin/bash
mick@ubuntu-desktop:~$ 
mick@ubuntu-desktop:~$ if [ `uname -a | grep i686 -o` = "i686" ]
> then
>     echo Your computer is running 32bit Linux
>     if [ -z `grep ' lm ' /proc/cpuinfo` ]
>     then
>         echo and your cpu is only 32bit capable.
>     else
>         echo but your cpu is 64bit capable.
>     fi
> else
>     echo Your computer is running 64bit Linux
> fi
bash:[COLOR=Red] [: =: Einstelliger (unärer) Operator erwartet.[/COLOR]
Your computer is running 64bit Linux
mick@ubuntu-desktop:~$ 

```The red means "single character (unrare) Operator expected".

I am running 64bit 9.10.

---

### Post by blur xc on 2010-02-18
> **audiomick said:**
> Hallo.
I copied your script and pasted it into a terminal and hit enter. Got this
```
mick@ubuntu-desktop:~$ #!/bin/bash
mick@ubuntu-desktop:~$ 
mick@ubuntu-desktop:~$ if [ `uname -a | grep i686 -o` = "i686" ]
> then
>     echo Your computer is running 32bit Linux
>     if [ -z `grep ' lm ' /proc/cpuinfo` ]
>     then
>         echo and your cpu is only 32bit capable.
>     else
>         echo but your cpu is 64bit capable.
>     fi
> else
>     echo Your computer is running 64bit Linux
> fi
bash:[COLOR=Red] [: =: Einstelliger (unärer) Operator erwartet.[/COLOR]
Your computer is running 64bit Linux
mick@ubuntu-desktop:~$ 

```The red means "single character (unrare) Operator expected".

I am running 64bit 9.10.

Copy it and paste it into a text file and run it one of two ways, and see if it still does it.

```
sh ./dumb.sh
```or 

```
chmod u+x dumb.sh
./dumb.sh
```Provided that you saved it as dumb.sh

BM

---

### Post by Jackzor on 2010-02-18
```
nicholas@nicholas-laptop:~/Desktop$ sh ./dumb.sh
Your computer is running 32bit Linux
[: 14: flags: unexpected operator
but your cpu is 64bit capable.
nicholas@nicholas-laptop:~/Desktop$ 
```

=D=D=D

---

### Post by blur xc on 2010-02-18
:(

I wonder if there's something wrong w/ my 2nd if statement...

runs fine on my Crunchbang VBox machine...  I should try it from home- I've got a 64bit capable machine running 32 bit Ubuntu, and I've got a couple computers running 64bit as well.

The output when I run it:
```
sh ./dumb.sh 
Your computer is running 32bit Linux
and your cpu is only 32bit capable.
```

Thanks...
BM

---

### Post by audiomick on 2010-02-18
Hi. Just got home.
I copied the text into gedit and stored it into my home folder as "dumb.sh".
I used```

sh ./dumb.sh
```to run it, and got
```
mick@ubuntu-desktop:~$ sh ./dumb.sh
[: 14: =: unexpected operator
Your computer is running 64bit Linux
mick@ubuntu-desktop:~$ 

```
hope that helps.
I can't help you debug, I am sorry. I have very little knowledge of scripts...;)

---

### Post by jamesisin on 2010-02-18
I am just learning BASH but there are two things I see which make me furrow my brow:

```
if [ `uname -a | grep i686 -o` = "i686" ]
...
    if [ -z `grep ' lm ' /proc/cpuinfo` ]
```

I see you are using two different ' styles.  That shouldn't be.

Also, what does the -z do in that second expression?

---

### Post by mjitkop on 2010-02-18
Nevermind, I was gonna suggest something wrong.

---

### Post by blur xc on 2010-02-18
> **jamesisin said:**
> I am just learning BASH but there are two things I see which make me furrow my brow:

```
if [ `uname -a | grep i686 -o` = "i686" ]
...
    if [ -z `grep ' lm ' /proc/cpuinfo` ]
```I see you are using two different ' styles.  That shouldn't be.

Also, what does the -z do in that second expression?

-z checks for a zero length string....  If `grep ' lm ' /proc/cpuinfo` returns nothing, then you don't have a 64bit capable processor...

I'm going to play around a bit now...

BM

---

### Post by jamesisin on 2010-02-18
I see.  So -z is an argument to the if command.

What about the single-quotes issue I mentioned?

---

### Post by bodhi.zazen on 2010-02-19
I re-wrote your script.

```
#!/bin/bash

ARCH=$(/bin/uname -m)
CPU=$(/bin/grep ' lm ' /proc/cpuinfo -o | /usr/bin/uniq)
ECHO='/bin/echo -e'

[[ ! $ARCH = *86* ]] && $ECHO "This script did not recognize your architecture" && exit 1
[[ $ARCH = i?86 ]] && $ECHO "Your computer is running 32 bit Linux\n"
[[ $ARCH = "x86_64" ]] && $ECHO "Your computer is running 64 bit Linux\n"
[[ $CPU = ' lm '  ]] && $ECHO "Your CPU is 64 bit capable" || $ECHO "Your CPU is 32 bit capable"
exit 0
```

---

### Post by Jackzor on 2010-02-19
> **bodhi.zazen said:**
> I re-wrote your script.

```
#!/bin/bash

ARCH=$(/bin/uname -m)
CPU=$(/bin/grep ' lm ' /proc/cpuinfo -o | /usr/bin/uniq)
ECHO='/bin/echo -e'

[[ ($ARCH  != "i386") && ($ARCH != "i586") && ($ARCH != "i686") && ($ARCH != "x86_64") ]] && $ECHO "This script did not recognize your architecture" &&$
[[ ($ARCH = "i386") || ($ARCH = "i586") || ($ARCH = "i686") ]] && $ECHO "Your computer is running 32 bit Linux\n"
[[ $ARCH = "x86_64" ]] && $ECHO "Your computer is running 64 bit Linux\n"
[[ $CPU = ' lm '  ]] && $ECHO "Your CPU is 64 bit capable" || $ECHO "Your CPU is 32 bit capable"
exit 0
```

Maybe I did something wrong?

```
nicholas@nicholas-laptop:~$ cd Desktop
nicholas@nicholas-laptop:~/Desktop$ sh ./dumbnew.sh
./dumbnew.sh: 7: Syntax error: word unexpected (expecting ")")
nicholas@nicholas-laptop:~/Desktop$ 


```

---

### Post by audiomick on 2010-02-19
> **bodhi.zazen said:**
> I re-wrote your script.

```
#!/bin/bash

ARCH=$(/bin/uname -m)
CPU=$(/bin/grep ' lm ' /proc/cpuinfo -o | /usr/bin/uniq)
ECHO='/bin/echo -e'

[[ ! $ARCH = *86* ]] && $ECHO "This script did not recognize your architecture" && exit 1
[[ $ARCH = "i?86" ]] && $ECHO "Your computer is running 32 bit Linux\n"
[[ $ARCH = "x86_64" ]] && $ECHO "Your computer is running 64 bit Linux\n"
[[ $CPU = ' lm '  ]] && $ECHO "Your CPU is 64 bit capable" || $ECHO "Your CPU is 32 bit capable"
exit 0
```

Hallo.
I tried that one by pasting it into gedit and saving as dumbnew.sh in /home/mick.
I got this
```
mick@ubuntu-desktop:~$ sh ./dumbnew.sh
./dumbnew.sh: 7: [[: not found
./dumbnew.sh: 8: [[: not found
./dumbnew.sh: 9: [[: not found
./dumbnew.sh: 10: [[: not found
Your CPU is 32 bit capable
mick@ubuntu-desktop:~$ 


```

As mentioned, I have 64bit hardware and 9.10 Ubuntu.

---

### Post by blur xc on 2010-02-19
All fixed-

Apparently I was missing a few quotation marks...  the output of `grep ' lm ' /proc/cpuino` spit out a lot of text, some of which had special characters which is what I think was causing the problem.

```
#!/bin/bash

if [ "`uname -a | grep i686 -o`" = "i686" ]
then
    echo Your computer is running 32bit Linux
    if [ -z "`grep ' lm ' /proc/cpuinfo`" ]
    then
        echo and your cpu is only 32bit capable.
    else
        echo but your cpu is 64bit capable.
    fi
else
    echo Your computer is running 64bit Linux
fi
```Now it should work.  Hopefully....

BM

---

### Post by audiomick on 2010-02-19
looks good
```
mick@ubuntu-desktop:~$ sh ./allfixed.sh
Your computer is running 64bit Linux
mick@ubuntu-desktop:~$ 

```

---

### Post by bodhi.zazen on 2010-02-19
> **Jackzor said:**
> Maybe I did something wrong?

I updated the script from your first post, must have been while you were copy-paste.

I did just make a small update to the script, removed the " " from "i*86" , but even with the quotes is partially failed without any error message.

With removal of the quotes it works as posted.

> **audiomick said:**
> Hallo.
I tried that one by pasting it into gedit and saving as dumbnew.sh in /home/mick.
I got this
```
mick@ubuntu-desktop:~$ sh ./dumbnew.sh
./dumbnew.sh: 7: [[: not found
./dumbnew.sh: 8: [[: not found
./dumbnew.sh: 9: [[: not found
./dumbnew.sh: 10: [[: not found
Your CPU is 32 bit capable
mick@ubuntu-desktop:~$ 


```As mentioned, I have 64bit hardware and 9.10 Ubuntu.

It is a bash script (This is what the she-bang or #!/bin/bash means), so do not call it with sh

You can bash ./dumbnew.sh or simply ./dumbnew ...

> [COLOR=darkred]ubuntu@ubuntu:~$ sh ./script
./script: 6: [[: not found
./script: 7: [[: not found
./script: 8: [[: not found
./script: 9: [[: not found
Your CPU is 32 bit capable[/COLOR]

ubuntu@ubuntu:~$ [COLOR=green]bash ./script
Your computer is running 32 bit Linux

Your CPU is 32 bit capable[/COLOR]

[COLOR=navy]ubuntu@ubuntu:~$ ./script
Your computer is running 32 bit Linux

Your CPU is 32 bit capable[/COLOR]And the script reads:

```
#!/bin/bash

ARCH=$(/bin/uname -m)
CPU=$(/bin/grep ' lm ' /proc/cpuinfo -o | /usr/bin/uniq)
ECHO='/bin/echo -e'
[[ ! $ARCH = *86* ]] && $ECHO "This script did not recognize your architecture" && exit 1
[[ $ARCH = i?86 ]] && $ECHO "Your computer is running 32 bit Linux\n"
[[ $ARCH = "x86_64" ]] && $ECHO "Your computer is running 64 bit Linux\n"
[[ $CPU = ' lm '  ]] && $ECHO "Your CPU is 64 bit capable" || $ECHO "Your CPU is 32 bit capable"
exit 0
```You can add color if you wish by adding to the echo or using printf, but this basic script may give you some ideas.

---

### Post by jamesisin on 2010-02-19
So what does bash do with this ` character?

---

### Post by blur xc on 2010-02-19
> **jamesisin said:**
> So what does bash do with this ` character?

[SIZE=1](disclaimer- noob understanding)[/SIZE]
The backtick is used when assigning the output of a command to a variable.

If you wrote:
```

MYVAR=date +%m-%d-%y
```

you would get an error.  Put it in backticks and it works...
```

MYVAR=`date +%m-%d-%y`
echo $MYVAR
```

BM

---

### Post by bodhi.zazen on 2010-02-19
> **jamesisin said:**
> So what does bash do with this ` character?

`command` is similar to (command), it runs the command between the ` `

` ` runs the command and returns the output

() runs the command in a sub shell and returns an exit status.

Clear as mud ?

There is a discussion here :

[http://www.perlmonks.org/?node_id=380670](http://www.perlmonks.org/?node_id=380670)

But perhaps an example ;)

> ubuntu@ubuntu:~$ (uname -m); echo $?
i686
0
ubuntu@ubuntu:~$ `uname -m`; echo $?
i686: command not found
127

Notice the "command not found" with ` ` ?

---

### Post by bodhi.zazen on 2010-02-19
> **blur xc said:**
> [SIZE=1](disclaimer- noob understanding)[/SIZE]
The backtick is used when assigning the output of a command to a variable.

If you wrote:
```

MYVAR=date +%m-%d-%y
```you would get an error.  Put it in backticks and it works...
```

MYVAR=`date +%m-%d-%y`
echo $MYVAR
```BM

That is not true, it is a matter of syntax ;

> # Set VAR to an space
ubuntu@ubuntu:~$ VAR=' ' ; echo $VAR

# Set VAR using ` `
ubuntu@ubuntu:~$ VAR=`uname -m`; echo $VAR
i686

# Set VAR using ()
ubuntu@ubuntu:~$ VAR=' ' ;VAR=$(uname -m); echo $VAR
i686

---

### Post by uRock on 2010-02-19
> **bodhi.zazen said:**
> `command` is similar to (command), it runs the command between the ` `

` ` runs the command and returns the output

() runs the command in a sub shell and returns an exit status.

Clear as mud ?

There is a discussion here :

[http://www.perlmonks.org/?node_id=380670](http://www.perlmonks.org/?node_id=380670)

But perhaps an example ;)



Notice the "command not found" with ` ` ?

I understand that.

I think post #6 has the easiest way of telling which version the system is running. If the OP hasn't installed yet, then it is a matter of finding out which he or she needs. So, the OP might need a way of finding out on the Windows OS if that is what he/she has.

---

### Post by bodhi.zazen on 2010-02-19
> **iRock said:**
> I understand that.

I think post #6 has the easiest way of telling which version the system is running. If the OP hasn't installed yet, then it is a matter of finding out which he or she needs. So, the OP might need a way of finding out on the Windows OS if that is what he/she has.

Yes, uname -a or uname -m tell us what arch is running and IMO is the easiest method.

The problems) with uname -a or uname -m are that:

1. Some people want a graphical tool to determin this.

2. uname does not tell us if the CPU is 32 or 64 bit.

---

