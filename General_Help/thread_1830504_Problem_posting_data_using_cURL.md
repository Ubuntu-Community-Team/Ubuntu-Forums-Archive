---
title: "Problem posting data using cURL"
date: 2011-08-21
forum: General Help
---

### Post by stevieP on 2011-08-21
I am having a problem posting data to a website using cURL. 

Here is the website: 
[http://www.random.org/gaussian-distributions/?mode=advanced](http://www.random.org/gaussian-distributions/?mode=advanced)

First, I've manually entered the data, and pressed "Get Numbers", then this webpage comes up:

[http://www.random.org/gaussian-distributions/?num=10&mean=0.0&stdev=1.0&dec=10&col=2&notation=scientific&format=plain&rnd=new](http://www.random.org/gaussian-distributions/?num=10&mean=0.0&stdev=1.0&dec=10&col=2&notation=scientific&format=plain&rnd=new)
which contains: 
```
-4.2099850870e-1   3.7784032210e-1
 1.3588266570e+0  -7.6864461550e-1
 5.5031358630e-2  -4.0747756070e-1
 1.1458655310e+0   1.1082384550e-1
 9.8179348370e-2  -1.0051595740e-1
```

So this cURL command, which explicitly contains the above website, works:

```
curl "http://www.random.org/gaussian-distributions/?num=10&mean=0.0&stdev=1.0&dec=10&col=2&notation=scientific&format=plain&rnd=new"
```

But, I want to post the data the first website using cURL (and other websites that require secure posted data).

I tried :
```
curl -d "num=10&mean=0.0&stdev=1.0&dec=10&col=2&notation=scientific&format=plain&rnd=new" "http://www.random.org/gaussian-distributions/"
```

but that does not work. 

I also tried 
```
curl -d "num=10&mean=0.0&stdev=1.0&dec=10&col=2&notation=scientific&format=plain&rnd=new&submit=Get%20Numbers" "http://www.random.org/gaussian-distributions/"
```

which also doesn't work and now I am just guessing. 

I did download and run formfind.pl on the webpage:
```
$ curl "http://www.random.org/gaussian-distributions/?mode=advanced" -o getrandnums.html
$ ./formfind.pl < getrandnums.html

```

Here is the output of formfind:

```
--- FORM report. Uses GET to URL "/search/"
Input: NAME="cx" VALUE="014319072506142697491:erhsk40qqno" (HIDDEN)
Input: NAME="cof" VALUE="FORID:10" (HIDDEN)
Input: NAME="ie" VALUE="UTF-8" (HIDDEN)
Input: NAME="q" (TEXT)
Input: NAME="sa" VALUE="Search" (SUBMIT)
--- end of FORM
--- FORM report. Uses GET to URL ""
Input: NAME="num" VALUE="10" (TEXT)
Input: NAME="mean" VALUE="0.0" (TEXT)
Input: NAME="stdev" VALUE="1.0" (TEXT)
Input: NAME="dec" VALUE="10" (TEXT)
Input: NAME="col" VALUE="2" (TEXT)
Input: NAME="notation" VALUE="scientific" (RADIO)
Input: NAME="notation" VALUE="standard" (RADIO)
Input: NAME="format" VALUE="html" (RADIO)
Input: NAME="format" VALUE="plain" (RADIO)
Input: NAME="rnd" (RADIO)
Input: NAME="rnd" (RADIO)
Select: NAME=""
  Option VALUE="2011-08-21"
  Option VALUE="2011-08-20"
  Option VALUE="2011-08-19"
  Option VALUE="2011-08-18"

(snip)

  Option VALUE="2006-03-12"
  Option VALUE="2006-03-11"
[end of select]
Input: NAME="rnd" (RADIO)
Button: "enter-id-here" (TEXT)
Button: "Get Numbers" (SUBMIT)
Button: "Switch to Simple Mode" (BUTTON)
--- end of FORM
```

I'm guessing that this output gives a clue as to the correct syntax to post data, but right now I'm stuck as to how to proceed. Is the website address that I am cURLing to correct, or does /search/ need to be added as per the output of formfind? (I tried this without success) Is there some special format to post data that involves clicking buttons (like "Get Numbers")? Does some of the post data need to be url-encoded? Any help would be appreciated!

steviep

---

### Post by stevieP on 2011-08-22
I think I've found an answer to my own question (not the 1st time on these forums)
```
$ curl -Gd "num=10&mean=0.0&stdev=1.0&dec=10&col=2&notation=scientific&format=plain&rnd=new" "http://www.random.org/gaussian-distributions/"
```

From the man page of curl:

>        -G, --get
              When  used,  this  option  will make all data specified with -d,
              --data or --data-binary to be used in a HTTP GET request instead
              of  the POST request that otherwise would be used. The data will
              be appended to the URL with a '?' separator.

              If used in combination with -I, the POST data  will  instead  be
              appended to the URL with a HEAD request.


I don't understand exactly what all this means, but the line in the form report :
> --- FORM report. Uses GET to URL ""
hinted at this solution. 
Any general comments from anyone familiar with the syntax of posting usernames and passwords to a website would be appreciated.

steviep

---

### Post by stevieP on 2011-08-22
Thanks for your reply salemeni. That command does not work for me, and I tried it on 2 different OS's. 
I do see the note in the man page that might motivate such an approach:
> --user-agent <agent string>
              (HTTP) Specify the User-Agent string to send to the HTTP server. Some badly done CGIs fail if this field isn't set to "Mozilla/4.0". To encode  blanks  in  the  string,
              surround the string with single quote marks. This can also be set with the -H/--header option of course.

But I don't think that is the problem here- as I mentioned above I think that the data has to be sent as a GET request rather than a POST request, and indeed this solution works (on both OS's). 

Does that command line really work from your computer? I don't understand how it would change the nature of the data request from get to post. 

steviep

---

