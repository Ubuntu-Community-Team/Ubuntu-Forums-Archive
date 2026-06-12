---
title: "script error"
date: 2012-07-25
forum: General Help
---

### Post by wingnut2626 on 2012-07-25
Why does this script not run?


#!/bin/bash -xv
#
#
# This is a command interpreter to get a simple startup page
#


clear
echo What would you like to do

echo 1. Run firefox in private mode

echo 2. Run bleachbit to clean the cache and all personal files
echo 3. Run thunderbird to check email

read $input

if [ $input=1 ]
    then 'firefox -private &'
elif [ $input=2 ]
    then 'sudo bleachbit &'
elif [$input=3 ]
    then 'tunderbird &'
else echo invalid input

fi 

Regardless of $input it gives the error :
./run: line 19: firefox -private &: command not found

---

### Post by steeldriver on 2012-07-25
it's your quoting I think - the single quotes prevent bash from interpreting it as a command plus an option (it looks for a command called "firefox -private &" instead of a command "firefox" with an option "-private" to be run in the background "&")

there may be other issues - I have not tried to run it

---

### Post by cortman on 2012-07-25
> **wingnut2626 said:**
> Why does this script not run?


#!/bin/bash -xv
#
#
# This is a command interpreter to get a simple startup page
#


clear
echo What would you like to do

echo 1. Run firefox in private mode

echo 2. Run bleachbit to clean the cache and all personal files
echo 3. Run thunderbird to check email

read $input

if [ $input=1 ]
    then 'firefox -private &'
elif [ $input=2 ]
    then 'sudo bleachbit &'
elif [$input=3 ]
    then 'tunderbird &'
else echo invalid input

fi 

Regardless of $input it gives the error :
./run: line 19: firefox -private &: command not found

"Thunderbird" is misspelled as well.
You need semicolons at the end of each if/then statement, i.e., 

```
if [ $input=1 ] ; then
    firefox -private & ;
elif [ $input=2 ] ; then
    sudo bleachbit & ; 
elif [$input=3 ] ; then
    thunderbird & ;
else echo "invalid input" ;
fi
```

I believe steeldriver is right; no need to quote.
This would also be a good place for a case statement, but the if/then statements work too.

Without actually testing it, these were some problems that came to mind.

---

### Post by wingnut2626 on 2012-07-25
read $input

if [ $input=1 ];
    "firefox &";
elif [ $input=2 ];
    "sudo bleachbit &";
elif [ $input=3 ];
    "thunderbird &";
else echo invalid input

fi 


#that is my new code
#here is the new error message regardless of $input

./run: line 20: syntax error near unexpected token `elif'
./run: line 20: `elif [ $input=2 ];'


?

---

### Post by cortman on 2012-07-25
> **wingnut2626 said:**
> read $input

if [ $input=1 ];
    "firefox &";
elif [ $input=2 ];
    "sudo bleachbit &";
elif [ $input=3 ];
    "thunderbird &";
else echo invalid input

fi 


#that is my new code
#here is the new error message regardless of $input

./run: line 20: syntax error near unexpected token `elif'
./run: line 20: `elif [ $input=2 ];'


?

Too many late nights... You do need the "then". I was thinking testcases.

It should be "read input" not "read $input". Here's a little example I wrote and tested:

```
#!/bin/sh

echo "press q"
read input

if [ $input = q ] ; then
echo "ha ha!" ;
elif [ $input != q ] ; then
echo "boo-hoo" ;
fi
```

What you're trying is quite possible, but it sounds like you should read up a bit on it- there are a lot of great free resources on scripting out there- see the link in my signature.

---

### Post by Vaphell on 2012-07-25
> You need semicolons at the end of each if/then statement, i.e., 

no, only *case* requires explicit **;;** to end the block.
; are only required if there are multiple commands in 1 line to split them, one command with or without semicolon - doesn't matter.

if you split if to multiple lines you can achieve the same with no semicolon
```
$ if true
> then
>   echo a
>   echo a
> else
>   echo b
>   echo b
> fi
a
a
$ if true; then echo a; echo a; else echo b; echo b; fi 
a
a
```

```
if <stuff>[COLOR="Blue"];[/COLOR] then cmd1[COLOR="Blue"][COLOR="Blue"];[/COLOR][/COLOR] cmd2[COLOR="Blue"];[/COLOR] elif <stuff>[COLOR="Blue"];[/COLOR] then cmd3[COLOR="Blue"][COLOR="Blue"];[/COLOR][/COLOR] cmd4[COLOR="Blue"];[/COLOR] else cmd5[COLOR="Blue"];[/COLOR] cmd6[COLOR="Blue"];[/COLOR] fi
```
all these semicolons can be replaced by newline.
same thing with
```
while/for <stuff>[COLOR="Blue"];[/COLOR] do cmd1[COLOR="Blue"];[/COLOR] cmd2[COLOR="Blue"];[/COLOR] done
```

---

### Post by cortman on 2012-07-25
Thanks for that clarification, Vaphell. Sounds like I should do some reading up as well. :oops:

---

