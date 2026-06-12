---
title: "Script im making.. need help.."
date: 2010-09-02
forum: General Help
---

### Post by o Steven x on 2010-09-02
> site=http://www.facebook.com/login.php
name=************************
pass=************************
cookies=/tmp/cron-cookies.txt
profile=0
jointurl="http://apps.facebook.com/passjoints/modules/rollitup.php?weed=32&mfs_typeahead_req_form_4c7b370361a5770212fee=Start+Typing+a+Name&ids[]=${profile}";
passes="1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41";

int main(int argc, char *argv[]){
char *profileid;	
if((argc < 3 || argc > 4)) {
	fprintf(stderr,"Please type a User ID to send Joint's to.", argv[0]);
		exit(1);
}
profileid = argv[1];
$profile=profileid;
}

echo "Starting Mail Address: $name"
wget -q -O /dev/null --user-agent="Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.6) Gecko/20070725 Firefox/2.0.0.6" --save-cookies /tmp/ba-cookies.txt --keep-session-cookies --load-cookies $cookies "${site}"
wget -q --user-agent="Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.6) Gecko/20070725 Firefox/2.0.0.6" --keep-session-cookies --save-cookies $cookies --load-cookies $cookies -O /dev/null \
        --post-data="email=$name&pass=$pass" \
        "${site}"

for i in $passes
do
wget -q -O /dev/null --user-agent="Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.6) Gecko/20070725 Firefox/2.0.0.6" --save-cookies /tmp/ba-cookies.txt --keep-session-cookies --load-cookies $cookies "${jointurl}"
echo "Sent $i Joint's to $profile using $name"
done
"/home/steven/Desktop/Pass Joints/Pass Joints 2.sh"

This is my script.. it is called Joints.sh
When I run it.. 

> /home/steven/Desktop/Pass Joints/Pass Joints: line 9: syntax error near unexpected token `('
/home/steven/Desktop/Pass Joints/Pass Joints: line 9: `int main(int argc, char *argv[]){'


Any Ideas? Im just trying it so I have to put the script into the terminal then type a Profile ID so it sends them stuff.

> '/home/steven/Desktop/Pass Joints/Pass Joints.sh' IDHERE


---

### Post by hakermania on 2010-09-02
Is this unix script :| ? Is this C++ ? You have mix them up a bit or am i wrong? Unix script hasn't got a main function. it doesn't uses functions at all...
Call every variable as $name_of_variable
e.g.
hello="Hello, my name is hakermania"
echo $hello
instead of parentheses() on if and while use brackets []
Instead of || try -o
Instead of && try -a

This is one of the most mixed up apps ever to tell the truth.. Correct the things i told you and reshow us the code...

---

### Post by apmcd47 on 2010-09-02
The line starting ```
int main
```is the first line of a C program in the middle of your shell-script. This is the source of your syntax error.

I can't see why it's there.

Andrew

---

### Post by hakermania on 2010-09-02
Andrew, is this the only error you can see?
Do you find this normal: char *profileid;
[o Steven x]("http://ubuntuforums.org/member.php?u=1138841"), listen man, there are plenty of Programming Languages out there, but each one has its own syntax. You shouldn't mix them up. It's wrong! Go to google.com and search for a unix scripting tutorial. There are plenty of them and they are pretty good. You have to start from 0 to achieve the 100, you cannot jump from 0 to 70, then to 20 and then back to 0 (like now)

---

### Post by apmcd47 on 2010-09-04
> **hakermania said:**
> Andrew, is this the only error you can see?

It's the only error I *bothered* to see. I said:

> **apmcd47 said:**
> The line starting ```
int main
```is the first line of a C program in the middle of your shell-script. This is the source of your syntax error.

I looked at the error being generated, looked down to line 9 and saw the C program. I suspect it's a copy/paste error rather than a deliberate combination of languages. I stopped, like the shell interpretor, at that error.

Andrew

---

