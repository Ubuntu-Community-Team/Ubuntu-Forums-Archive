---
title: "Help with wget login:pass to http//www.site.com/login.php"
date: 2010-03-20
forum: General Help
---

### Post by Ventil on 2010-03-20
What my script does:
1. logs into ww.siteA.com
2. check if the stuff on ww.siteA.com/somesutff/ has changed.
3. notify me

**Finished script at the bottom of this post.**


This is the site's login.php file I need to login:
```
<form id="login" method="POST" action="/user/login.php"> 
<input type="hidden" value="" name="previous"> 
<label>Username</label> 
<br/> 
<input name="uname" type="text" class="textinput" /> 
<br/> 
<br/> 
<label>Password</label> 
<br/> 
<input name="pword" type="password" class="textinput" /> 
<br/> 
<input type="image" src="/images/login/login.gif" width="120" height="40" vspace="10" /><br /> 
<label> 
&nbsp;&nbsp;<a href="/tips/logfail.php">Login Problems</a> 
</label> 
</form>
```

This was the tricky part that I missed and spent few hours figuring whats wrong:
<form id="login" method="POST" **action="/user/login.php**"> 

```
#!/bin/bash


#site login
url='http://www.site.com'

#username, password
user='MyUSERNAME'  
pass='MyPASSWORD'

#check if file.html file does exist
if [ -f file.html ]; then
   # temp file size
   OLDFILE_SIZE=`cat file.html`

   wget  -O - --save-cookies=cookies.txt --keep-session-cookies --post-data "uname=$user&pword=$pass" ${url}/user/login.php
   HTML_STRING="$(wget -O - --keep-session-cookies --load-cookies=cookies.txt \
	"${url}/members/stuff.html")"
   NEWFILE_SIZE=${#HTML_STRING}

   if [[ $((${#OLDFILE_SIZE})) -gt $(($NEWFILE_SIZE-10)) && $((${#OLDFILE_SIZE})) -lt $(($NEWFILE_SIZE+10)) ]]
   then
      exit 1;
   else
      dialog  --title "site changed" --msgbox "Site Changed!" 10 30
      echo -e "$HTML_STRING" > file.html
   fi
else
   # run if file.html does not exist yet
   wget  -O - --save-cookies=cookies.txt --keep-session-cookies --post-data "uname=$user&pword=$pass" ${url}/user/login.php
   wget -O file.html --keep-session-cookies --load-cookies=cookies.txt \
	"${url}/members/stuff.html"
fi
```

---

### Post by Ventil on 2010-03-21
Can anyone help me?

---

### Post by keplerspeed on 2010-03-21
Here is a blog post of mine, I did a log in using curl:
[http://keplerspeed.blogspot.com/2010/01/ftp-http-and-extracting-data-from-html.html]("http://keplerspeed.blogspot.com/2010/01/ftp-http-and-extracting-data-from-html.html")

This is the guts of it:
```

# curl to fetch ISP usage data
curl -A "Mozilla/4.73 [en] (X11; U; Linux 2.6.31 x86_64)" \
--cookie cjar --cookie-jar cjar \
--data "check_username=yourusername" \
--data "password=yourpassword" \
--data "login=Login" \
--location "https://isp.com">data.html

```

---

### Post by Ventil on 2010-03-21
It's working!! woohoo! I just need help with a few small fixes. 
1. I need to copy file1.html file to file2.html (see the code where ####)
2. I don't think it reads the file1.html and file2.html well. When it compares them it allways say the site changed.
3. I want the script to tolerate comparisment by %. (If file1.html is 98% similar to file2.html then the site hasn't changed)
4. I want output to be just echo "Site changed" or "Site hasn't changed"


```
#!/bin/bash


#site login
url='http://www.site.com/'

#username, password
user='MYUSERNAME'  
pass='MYPASS'


# temp file
file1="$HOME/file1.html"
file2="$HOME/file2.html"

if [ -f "$file1" ]; then
  wget  -O - --save-cookies=cookies.txt  --keep-session-cookies \
  --post-data "uname=$user&pword=$pass" ${url}login.php
  wget -O "$file2" --keep-session-cookies --load-cookies=cookies.txt \
	"${url}file.pdf"
  check_here="$(cat "$file1")"
  check_there="$(cat "$file2")"

  if [ "$check_here" != "$check_there" ]; then
    # site's changed
    echo "site changed"
    aplay ~/Downloads/mail_here.wav
######    This is where I am stuck!! I need to copy file "file2.html" to "file1.html"  ######
  else
  echo "site hasn't changed"
  fi
else
  # first run
  wget  -O - --save-cookies=cookies.txt  --keep-session-cookies \
  --post-data "uname=$user&pword=$pass" ${url}login.php
  wget -O "$file1" --keep-session-cookies --load-cookies=cookies.txt \
  "${url}file.pdf"
fi
```

---

### Post by Ventil on 2010-03-21
I've done it! I've done it!! MY 1st script! :cool:  :D

```
#!/bin/bash


#site login
url='http://www.site.com'

#username, password
user='MyUSERNAME'  
pass='MyPASSWORD'

#check if file.html file does exist
if [ -f file.html ]; then
   # temp file size
   OLDFILE_SIZE=`cat file.html`

   wget  -O - --save-cookies=cookies.txt --keep-session-cookies --post-data "uname=$user&pword=$pass" ${url}/user/login.php
   HTML_STRING="$(wget -O - --keep-session-cookies --load-cookies=cookies.txt \
	"${url}/members/stuff.html")"
   NEWFILE_SIZE=${#HTML_STRING}

   if [[ $((${#OLDFILE_SIZE})) -gt $(($NEWFILE_SIZE-10)) && $((${#OLDFILE_SIZE})) -lt $(($NEWFILE_SIZE+10)) ]]
   then
      exit 1;
   else
      dialog  --title "site changed" --msgbox "Site Changed!" 10 30
      echo -e "$HTML_STRING" > file.html
   fi
else
   # run if file.html does not exist yet
   wget  -O - --save-cookies=cookies.txt --keep-session-cookies --post-data "uname=$user&pword=$pass" ${url}/user/login.php
   wget -O file.html --keep-session-cookies --load-cookies=cookies.txt \
	"${url}/members/stuff.html"
fi
```

---

