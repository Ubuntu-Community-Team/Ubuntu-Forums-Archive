---
title: "Telmore Saldo conky script"
date: 2009-10-05
forum: General Help
---

### Post by exutable on 2009-10-05
This is for Danish users with the mobile carrier telmore.

Here is a script to pull your telmore saldo and print it in conky, it's good for keeping an eye on how much money you have left on your account.

You will need the BeautifulSoup library to use this script.

```
import urllib
import urllib2
import sys
import cookielib
import hashlib
from BeautifulSoup import BeautifulSoup

#Accept cookies to browse telmore website
cookieJar = cookielib.LWPCookieJar()
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookieJar))

#Add headers
opener.addheaders = [('User-agent', "Mozilla/5.0")]

#Accept arguments for username and password
username = sys.argv[1]
password = sys.argv[2]

#Url requests, first page is login, second is a frame of the login page
url = "https://www.telmore.dk/t2/j_security_check"
url2 = "https://www.telmore.dk/t2/mytelmore/index.do"

#Fill the forms with the username and password arguments
form = { "j_username" : username,
         "j_password" : password }

#Encode the form and create request		 
encodedForm = urllib.urlencode(form)
request = urllib2.Request(url, encodedForm)
page = opener.open(request)

#Request the second page
request = urllib2.Request(url2)
page = opener.open(request)
contents = page.read()

#Beatiful soup to parse the html and sort out the span tag with class saldo
soup = BeautifulSoup(contents)
saldospan = soup.findAll('span')
saldo = saldospan[0].contents[0].strip()
print saldo

```

Example line in conkyrc:

```
${font PizzaDude Bullets:size=18}0${font}  Telmore Saldo:  ${execpi 300 python ~/Scripts/telmoresaldo.py username password} kr.
```

---

