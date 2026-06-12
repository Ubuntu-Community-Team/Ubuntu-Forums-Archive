---
title: "Download scripts"
date: 2009-10-21
forum: General Help
---

### Post by miak on 2009-10-21
Is there any way of writing a script that would download files if I have a list of URLs?
I need to download .pdf files that have almost the same URLs just with minor differences

Thanks
miak

---

### Post by zer0x on 2009-10-21
Hi,

Something along these lines maybe?

```
#!/bin/bash
IFS="
"
for urls in $(cat /home/user/myurls.txt)
do
wget $urls
done
```

This is a bash script, save it as a '.sh' file and set it to executable with 'chmod +x scriptname.sh'.

It sets the bash Internal Field Separator to seperate fields with a newline, then loops through each line of myurls.txt using wget to download each url/line in the text file.

This will work, but it is very simplified. As long as the files have unique names there will be no problem. If that is not the case you might want to look into the -O option of wget and enhancing the script.

---

### Post by miak on 2009-10-21
Thanks for help, but one more question. How can I do this if the server requires authorization? I have the authorization, it is in the form of Internet browser certificate, or just login/password.

---

### Post by zer0x on 2009-10-21
Hi,

It depends on the type of authorization required.

If its just 'basic' or 'digest' authentication you can use:

```
--http-user=user --http-passwd=password
```

If its a login form, you will need to look at the web page source code or look at your http traffic to discover the field names being used. Then you can use wget to store a cookie, and re-use that cookie when downloading:

e.g.

```
wget --save-cookies cookies.txt --keep-session-cookies --post-data 'user=myusername&password=mypassword' http://server.com/login.php

wget --load-cookies cookies.txt http://server.com/download.php
```

If in doubt, check the wget manual (man 1 wget) it is very comprehensive :D

HTH

zer0x

---

