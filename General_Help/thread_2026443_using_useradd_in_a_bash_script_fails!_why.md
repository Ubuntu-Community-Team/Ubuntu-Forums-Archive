---
title: "using useradd in a bash script fails! why?"
date: 2012-07-15
forum: General Help
---

### Post by go4unkwn on 2012-07-15
hello bash experts

I try to write a bash script to create user accounts from a cvs file. the problem is the command useradd fails (even the same command used on the command line works).

til now i wasn't able to find the mistake i have in my script. please, check the script below (any hint will be appreciated).

script:

#!/bin/bash
# Script to add a user from a KeePass2 CVS file to Linux system
# Script creats a user without a shell

# test if script is running unter root (only root can add user)
if [ $(id -u) -eq 0 ]; then

    # create temporary folder structure in /etc/skel for /home/$username
    mkdir -p /etc/skel/{privat,unterricht/{abu/{suk,ges},fachkunde}}

    # bash script need a CVS Filename as parameter
    CVSFILE=$1
    
    # remove special characters from CVS File created by KeePass2
    sed -i 's/"/\ /g' $CVSFILE
    sed -i 's/,/\ /g' $CVSFILE
    
    # remove the first line of the CVS File (description line)
    sed -i '1d' $CVSFILE
    
    # read the modified CVS File
    cat $CVSFILE | \
    
        # read a line of the CVS File and extract second name first name
        # user name and a tail string which includes the user password
        while read SNAME FNAME UNAME TAIL
        do
            
            # test if user LNAME already exists
            egrep "^$UNAME" /etc/passwd >/dev/null
            if [ $? -eq 0 ]; then
                echo "$UNAME exists!"
                exit 1
            else
                # create comment
                COMMENT=$SNAME" "$FNAME
                
                # extract password from string PASSWORD
                PASSWORD=`echo $TAIL | cut -d' ' -f 1`
                    
                # encrypt PASSWORD using perl
                EPASSWORD=$(perl -e 'print crypt($ARGV[0], "PASSWORD")' $PASSWORD)
                                
                # add user to the linux system
                # useradd options
                # -c comment about the user
                # -m create users home directory if it doesn't exist already
                # -k copy folders from /etc/skel to /home/$UNAME
                # -p the encrypted password as returned by crypt
                # -s the name of the users login shell
                useradd -c "${COMMENT}" -m -k -d /home/${UNAME} -p ${EPASSWORD} -s /usr/sbin/nologin ${UNAME}
                [ $? -eq 0 ] && echo "User has been added to system!" || echo "Failed to add a user!"
              # check variables  
                echo $COMMENT
                echo $EPASSWORD
                echo $UNAME
            fi
        done
        
    # remove temporary folder structure in /etc/skel
    rm -rf /etc/skel/*
    
else
    echo "Only root may add a user to the system"
    exit 2
fi


the CVS file has the following format
"secondname","firstname","loginname","unencryptedpassword","comments"

i check the variables in the script using echo and they seem to be fine.

if you have any idea, please let me know.

kind regards, go4unkwn

---

### Post by Vaphell on 2012-07-15
could you wrap your script in ```
[/co****de] tags? thx

few advices not related to the failure in question:

[code]cat file | while read ... done
```
unnecessary cat, while reads files just fine
```
while read ... done < file
```
or in case of command output
```
while read ... done < <( cmd )
```


```
PASSWORD=`echo $TAIL | cut -d' ' -f 1`
```
- all caps variables should be avoided, because you risk overriding some environment variable (they are all-caps by convention)
- `` are deprecated and $() should be used instead (better readability and less pain in case of embedding). You use $() in another part, so be consistent ;-)
- builtin parameter expansion can perform basic string operations without spawning other processes
```
password=${tail%% *}
```


```
CVSFILE=$1
sed -i 's/"/\ /g' $CVSFILE
```
will fail in case of whitespace, always quote your variables


```
sed -i 's/,/\ /g' $CVSFILE
...
while read SNAME FNAME UNAME TAIL
```
sed is unnecessary
```
while IFS=, read SNAME FNAME UNAME TAIL
```

---

### Post by codemaniac on 2012-07-15
very good improvements suggested by vaphell .

the bug in your script however lies in the useradd commandline .The corrected commandline should be .

```
useradd -c "${COMMENT}" -m -k -d ${UNAME} -p ${EPASSWORD} -s /usr/sbin/nologin
```

---

### Post by go4unkwn on 2012-07-16
hello vaphell, hello codemaniac

i have to confess i'm a newbie in relation to bash scripting
and therefore i really appreciate your comments.
so I have to say thank you to both of you!!!!

in future i will follow your advice, vaphell. but one advice i don't understand what you mean

```

cvsfile=$1
sed -i 's/"/\ /g' $cvsfile

```what do you mean with "will fail in case of whitespace"? could you give a futher explanation, please.

could you make an example for "always quote your variables", please.

another question (if you have the time for another advice):
how could i test if the script is invoked with or without parameter $1 (so the script stops with a message in case parameter $1 is missing).

kind regards, go4unkwn

---

### Post by codemaniac on 2012-07-16
> **go4unkwn said:**
> could you make an example for "always quote your variables", please.


When referencing a variable, it is generally advisable to enclose its name in double quotes. This prevents reinterpretation of all special characters within the quoted string -- the variable name except $, ` (backquote), and \ (escape). Keeping $ as a special character within double quotes permits referencing a quoted variable ("$variable"), that is, replacing the variable with its value .

Please refer have the below example .

```
variable1="a variable containing five words"
COMMAND This is $variable1    # Executes COMMAND with 7 arguments:
# "This" "is" "a" "variable" "containing" "five" "words"

COMMAND "This is $variable1"  # Executes COMMAND with 1 argument:
# "This is a variable containing five words"


variable2=""    # Empty.

COMMAND $variable2 $variable2 $variable2        # Executes COMMAND with no arguments. 
COMMAND "$variable2" "$variable2" "$variable2"  # Executes COMMAND with 3 empty arguments. 
COMMAND "$variable2 $variable2 $variable2"      # Executes COMMAND with 1 argument (2 spaces). 
```

---

### Post by Vaphell on 2012-07-16
cvsfile=$1
sed -i 's/"/\ /g' $cvsfile

like codemaniac's example shows, if you use a filename with space, in case of unquoted $cvsfile you will get it broken up to pieces, sed will see multiple names and will complain that these files don't exist.

> how could i test if the script is invoked with or without parameter $1 (so the script stops with a message in case parameter $1 is missing).

you can use $#, it returns the number of parameters. Obviously if you compare it to 0 you will get your answer
```
if [ $# -eq 0 ]
```
you can also test if the file exists
```
if [ ! -f "$cvsfile" ]
then
  echo "file $cvsfile doesn't exist"
  exit <N>  # exit with status (integer), non-0 indicates error so failure can be detected
else
  ...
fi
```

---

### Post by go4unkwn on 2012-07-16
hello again

THANK's A LOT taking time to answer my questions!!!:)

kind regards, go4unkwn

---

