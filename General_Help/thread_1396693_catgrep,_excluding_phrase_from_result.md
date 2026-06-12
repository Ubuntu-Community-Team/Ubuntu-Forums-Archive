---
title: "cat/grep, excluding phrase from result"
date: 2010-02-02
forum: General Help
---

### Post by admbe on 2010-02-02
Hello,

I would like to take a file looking like...

uid=user1,ou=People,dc=company,dc=com
uid=user2,ou=People,dc=company,dc=com
uid=user3,ou=People,dc=company,dc=com

and output it to...

user1
user2
user3

Can't seem to figure it out.

Thanks!

---

### Post by bluefrog on 2010-02-02
sed 's/\(.*\)\(user[0-9]*\)\(.*\)/\2/' file

---

### Post by admbe on 2010-02-02
> **bluefrog said:**
> sed 's/\(.*\)\(user[0-9]*\)\(.*\)/\2/' file

Thanks, but how would this work without having the usernames contain the same phrase ("user")? 

Could I do something like display everyone after "=" and before the first ","?

---

### Post by johnnynb on 2010-02-02
cut -d"," -f 1 file.txt | cut -d"=" -f2


or

gawk -F"," '{print $1}' file.txt | gawk -F"=" '{print $2}'

or

gawk -F"," '{gsub("uid=", "", $1); print $1  }' file.txt

---

### Post by rnerwein on 2010-02-02
hi
whats about this:
awk  -F\[,=\]  '{ if ( $2 != "" ) printf ("%s %s\n",$2,$1) }' < file.txt

excluding empty lines too
ciao

---

### Post by admbe on 2010-02-02
rnerwein, I used yours but I got "uid" after each user name - thanks though..

johnny, I used gawk -F"," '{print $1}' file.txt | gawk -F"=" '{print $2}' and It worked like a champ!

Thanks

---

