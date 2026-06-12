---
title: "Password Managment Script in Bash &lt;problem with sed&gt;"
date: 2012-08-11
forum: General Help
---

### Post by Primefalcon on 2012-08-11
[s]I have been working on the following bash script (feel free to use it if you wish, you'll need to install xsel, s its usin that to clear the clipboards after a bit for security) it's a simple password managment script that uses gpg to encrypt the file...[/s]

working code is below
```
#!/bin/bash
############
# Settings #
############
location="/home/brad/EncDropbox" #folder where you to save the encrytped file
gpgKey="530A9CB2" #enter the keyID you wish to use
#####################################################################################################
# Unless you know what your doing stay above this line
#####################################################################################################
#check if file exists, if not.... create it
if [ ! -f $location/Passwords.txt.gpg ];
then
    touch $location/Passwords.txt.gpg
fi
reset
#######################
# View a stored entry #
#######################
if [ "$1" == "--view" ]; then
if [ "$3" == "" ]; then
gpg --decrypt --no-use-agent $location/Passwords.txt.gpg | egrep -in "*$2*"; sleep 30s; cat /dev/null | xsel -psb; reset;. ~/.bashrc
else
gpg --decrypt --no-use-agent $location/Passwords.txt.gpg | egrep -in "*$2*" | egrep -i "*$3*"; sleep 30s; cat /dev/null | xsel -psb; reset;. ~/.bashrc
fi
fi
################
# Add an entry #
################
if [ "$1" == "--add" ]; then
site="$2"; username="$3"; password="$4"; tags="$5"
passwordlist=`gpg --no-textmode --decrypt --no-use-agent "$location/Passwords.txt.gpg"`
newEntry="$site U/N:$username P/W:$password TAGS:$tags"
newPasswordlist="${passwordlist}\n${newEntry}"
echo -e "$newPasswordlist" | gpg -e -r $gpgKey > "$location/Passwords.txt.gpg"
fi
###################
# Delete an entry #
###################
if [ "$1" == "--delete" ]; then
lineToDelete=$2
passwordlist=`gpg --no-textmode --decrypt --no-use-agent "$location/Passwords.txt.gpg"`
echo -e "$passwordlist" | sed -e "$lineToDelete"d | gpg -e -r $gpgKey > "$location/Passwords.txt.gpg"
fi
######################
# Help Documentation #
######################
if [ "$1" == "--help" ]; then
echo -e "--view\nAllows up to 2 search criteria with the second search narrowing down the fields from the first\n\nexample:\nmyPass --view ubuntu forums\n"
echo -e "--add\nAdds an entry into the encrytped file syntax is:\nmyPass --add http://example.com joeBlogs p@ssw0rd \"a really awesome forum\"\n" 
echo -e "-delete\nRemoved an entry syntax is myPass --delete <line number>\n"
fi

```
I have everything working perfectly except 1 function the delete line function using sed.... not sure exactly what I am doing wrong there? can anyone help? sed has never been my favorite thing to use but....

---

### Post by Primefalcon on 2012-08-11
still working on it

---

### Post by Primefalcon on 2012-08-11
Solved :-)

---

