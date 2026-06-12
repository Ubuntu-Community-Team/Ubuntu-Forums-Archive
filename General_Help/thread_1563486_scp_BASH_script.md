---
title: "scp BASH script"
date: 2010-08-29
forum: General Help
---

### Post by marrabld on 2010-08-29
I am trying to knock up a quick script for my bro to use as he is not very comfortable at the command line.   

I am trying to use zenity to pick multiple files and then use scp to shoot them over to my media server.

this is what I have so far.

```
#!/bin/sh

HOST="10.1.1.2"
DESTINATION="/home/djserver/Videos"
password="xxxxxxx"

        FILE=`zenity --file-selection\
	--title="Select a File"\
	--multiple\
	--separator=","`

# add \ for spaces in folders
echo $FILE | sed 's/ /\\ /g' > temp.txt

FILE=`cat temp.txt`

# replace the comma separating the file names with spaces
echo $FILE | sed 's/,/\ /g' > temp.txt
FILE=`cat temp.txt`

scp "${FILE}" djserver@$HOST:$DESTINATION
#echo scp "${FILE}" djserver@$HOST:$DESTINATION


```


I get the list of files that I choose with an error saying file does not exist.  It is like it is treating the whole list as one file.  

If I uncomment out the last line in the script, then copy and past it into a new shell.  The transfer works.  So I am not sure how I pass the command I wan't verbatim.

Any Ideas ? 

Thanks

I am a BASH n00b

---

### Post by Vaphell on 2010-08-29
maybe it craps out at spaces in file names? Are they escaped?

try something like this
```

IFS='
'

for file in `put listing command here`
do
  echo $file
done

```

IFS is a separator of arguments, default space sucks when you deal with spaced filenames. Changing it to newline makes commands more resistant.

---

### Post by sharathcshekhar on 2010-08-29
Your quotes around FILE in scp command is making it to believe it is one file!!
Replace "${FILE}" with just $FILE. It should work. Also, you will have to take care of other things like a single quote, etc., in the file name by putting escape backslash before it to make your script more robust.

---

### Post by marrabld on 2010-08-29
Thanks for the reply guys

@Vaphell

If I use IFS like this 

```
for i in $FILE; 
	do echo $i > temp.txt; 
done
```

Then it puts each file on a new line which doesn't work with the scp command

scp file1.txt file2.txt u_name@<ip address>:< destination >

so I think I need my $FILE variable to be space separated strings not \n

@sharathcshekhar

If I take away the "" then scp doesn't like the spaces in the file names ie 'my new file1'  it says 
no such file new 
no such file file1

that is why I did this line 
```
echo $FILE | sed 's/ /\\ /g' > temp.txt
```

I am not sure how to use the escape slash because I thought that this takes care of it but it doesn't 

I still get 
no such file my\
no such file new\
so such file file1
 
I am not sure what you mean by 

"Also, you will have to take care of other things like a single quote, etc., in the file name by putting escape backslash before it to make your script more robust."

are you saying to use single '  instead of " for my variable declaration?  will this make my script more robust ?




So I am still a little stuck.  If I use IFS method it transfers the first file and then ends.

any other ideas will be most welcome

Cheers

---

### Post by Lars Noodén on 2010-08-29
> **marrabld said:**
> I am trying to knock up a quick script for my bro to use as he is not very comfortable at the [**shell**]   


The variable PASSWORD is problematic.  

What you can do instead is use [public key authentication](http://sial.org/howto/openssh/publickey-auth/). That will make it either more secure or lot more secure depending.

The client can use the public key to connect and if it is passwordless (riskier) that can be done.  Or else the key can be loaded into ssh-agent and held there.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by marrabld on 2010-08-29
Thanks Lars,

the password is a relic, I actually do use a public key.  You can seen in the script that I posted, it isn't actually used anywhere.

I have removed it now.  but that is good advice

---

### Post by sharathcshekhar on 2010-08-29
> 
If I take away the "" then scp doesn't like the spaces in the file names ie 'my new file1' it says
no such file new
no such file file1

Yes. That is perfectly all right and adding \ using your sed command is correct. But "new file" and "new file1" should be expanded in scp as
scp new\ file new\ file1 [DESTINATION]
and not
scp "new\ file new\ file1" [DESTINATION]
When you put "$FILE" it expands to later and when you out $FILE is expands to former.

> 
I am not sure what you mean by

"Also, you will have to take care of other things like a single quote, etc., in the file name by putting escape backslash before it to make your script more robust."

are you saying to use single ' instead of " for my variable declaration? will this make my script more robust ?

Nope. I just meant, if you file name is say "new file '09". Bash does not like and single quote there! So similar to adding a backslash before space you will have to give the file as "new\ file\ \'09"
Hope I am clear now.

---

### Post by Vaphell on 2010-08-29
> Then it puts each file on a new line which doesn't work with the scp command

scp file1.txt file2.txt u_name@<ip address>:< destination >

so I think I need my $FILE variable to be space separated strings not \n

my line of thinking was more about running scp for each file separately, if the name echoes just fine, it will work as a scp parameter just fine :)
```
for file in `...`
do
  scp $file $destination
done
```

easier to debug, not as cool as one-liners though :) i prefer lame but safer approach, i lack knowledge of many fine details and doing simple stuff saves me a lot of headache

---

### Post by marrabld on 2010-08-29
yea that works.  

Just means that it logs in and out that many times.  And I was going to try and do an update dialogue next too.

I guess that will have to do it for now.  I'm still curious why I cant get this to work though.  

Cheers

---

### Post by McNils on 2010-08-29
You can copy files with tar. It might seem like silly thing to do, but you can copy all files with one connection.

```
FILE=$(zenity --file-selection\
        --title="Select a File"\
        --multiple\
        --separator=",")
IFS=,
for f in $FILE
do
  echo $f
done > files.tmp

cd $(dirname $f)
tar -T files.tmp -cf - | ssh djserver@$HOST "(cd $DESTINATION && tar xf -)"
rm files.tmp

```

---

