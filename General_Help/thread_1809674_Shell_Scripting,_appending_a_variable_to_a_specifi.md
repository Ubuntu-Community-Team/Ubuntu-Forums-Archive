---
title: "Shell Scripting, appending a variable to a specific line in a file"
date: 2011-07-21
forum: General Help
---

### Post by skawilly on 2011-07-21
How goes it, I am as novice as it gets. I am trying to find a way to append to a file a variable that I have assigned from user input. a sample script of what I did and need done:

echo "Please enter your username"
read USRNM
echo "Please enter your password"
read PSWD


This is simple so you know what my variables are. I have nothing else to show because I dont even know where to begin. I am on Ubuntu 10.04 using Bash. I am trying to get $USRNM and $PSWD to the 2nd line of a file which is also a script, so that the script can run an assignment with that login info. Yes I realize the security risk but ill address that next. I can use the echo command to append this information to the end but I need it on the 2nd line. I found a sed command that does kinda this but when I use it I get output $USRNM and $PSWD and not the parsed input, its annoying.

Thank you for your replys

---

### Post by galvatron408 on 2011-07-21
I think your second script is flawed. It shouldn't need a username and password hard coded. Store the user name and password in a file like this. (or better yet, just have your second script ask?)

user=username
pass=password

your second script should simply source that file.

here is a sample of your second script...

first line
. /dir/subdir/.secret-file #this is sourcing that file
$user $pass
second line
third line....and etc...

but.... if you really just wanted to echo those variables in to the second line....

head -1 samplefile.txt >> newfile.txt
echo "$user $pass" >> newfile.txt
grep -v "somekeywordfromfirstline" >> newfile.txt

good luck, maybe someone knows a better way of doing this... well, i do with PERL but thats another story. :)

---

### Post by galvatron408 on 2011-07-21
whooops, i just noticed a little problem...

Try that instead.
grep -v "somekeywordfromfirstline" samplefile.txt >> newfile.txt

---

