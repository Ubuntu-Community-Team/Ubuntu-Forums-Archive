---
title: "Creating users with password from bash script"
date: 2011-05-18
forum: General Help
---

### Post by Gilded on 2011-05-18
Hello! I got a school assignment to create users from a file whit a script on a linux server(I'm on Ubuntu server 11.04 in VirtualBox).

I choose to have the users listed like this:
```

user1:pass1
user2:pass2
user3:pass3
```these are located in a file called "users"

I've been mainly looking at [THIS]("http://www.cyberciti.biz/tips/howto-write-shell-script-to-add-user.html") guide for the script

and my scrip now looks like this:
```
#!/bin/bash
if [ $(id -u) -eq 0 ]; then
    for row in `more $1`
    do
    username=${row%:*}
    password=${row#*:}

    egrep "^$username" /etc/passwd >/dev/null
    
    if [ $? -eq 0 ]; then
        echo "$username exists!"
        exit 1
    else
        pass=$(perl -e 'print crypt($ARGV[0], "password")' $password)
        useradd -m -p $pass $username
        [ $? -eq 0 ] && echo "User has been added to system!" || echo "Failed to add a user!"    
    fi
    done
else
    echo "Only root may add a user to the system"
    exit 2
fi
```when i then run the scrip like this:
```
sudo ./script ./users
```Everything seems to work but (at least the script doesn't give me any errors).

But when i try to log in some the new user with su - user1 and password pass1 it gives me this error:

```
su: Authentication failure
```What am i doing wrong?

Any help appreciated. =)
Btw I'm pretty new to Unix so please be kind :D

---

### Post by sisco311 on 2011-05-19
Hi,

First of all, instead of **for row in `more $1`** you should use something like" 
```
while read -r line
do
   echo "$line"
done < "$1"

```

or even better:
```
while IFS=: read -r user pass
do
  echo "user: $user"
  echo "pass: $pass"
done < "$1"

```

Check out: [http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001)

The real issue with your script is the part where you generate the encrypted password. crypt defaults to [DES]("http://en.wikipedia.org/wiki/Data_Encryption_Standard"). The DES encryption method truncates the passwords to 8 characters in length. So if the password is longer than 8 characters you still should be able to log in as the new user with the first 8 characters of it.

Check out:
```
man 3 crypt
```

If you want to improve your script, then use [SHA-512]("http://en.wikipedia.org/wiki/SHA-2") and a random salt.

I'm not very good in perl, but something like:
```
 #!/usr/bin/perl

@letters = ('A' .. 'Z', 'a' .. 'z', '0' .. '9', '/', '.');
$salt .= $letters[rand@letters] foreach(1..8);
$passwd = crypt($ARGV[0], "\$6\$" . $salt);
print "password:" . $passwd . "\n";

```should do the trick.

But instead of a perl script you could use the mkpasswd command to encrypt the password. See:
```
man mkpasswd
```

If the salt is omitted, mkpasswd uses a random one. Just make sure that you specify sha-512 as the method.

Your script is good, but in the "real life" I would use newusers. ;)

---

### Post by Gilded on 2011-05-19
[FONT=Verdana]Thanks for the help, i will take a look at that. :)

Got it working tho with my script, just had to make some minor adjustments.
Here's what i got it working with:
[/FONT]```
#!/bin/bash
  for row in `cat $1`
  do
      if [ $(id -u) -eq 0 ]; then
  

          username=${row%:*}
          password=${row#*:}
          #echo username
          #echo password
  

          egrep "^$username" /etc/passwd >/dev/null
  

          if [ $? -eq 0 ]; then
              echo "$username already exists"
              exit 1
          else
              pass=$(perl -e 'print crypt($ARGV[0], "password")' $password)
              useradd -m -p $pass $username
              [ $? -eq 0 ] && echo "User has been added to system" || echo "Failed to add a user"
          fi
  

      else
          echo "Only root may add user(s) to the system"
          exit 2
      fi
  done

```

---

