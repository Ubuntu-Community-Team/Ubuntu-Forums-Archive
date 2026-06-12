---
title: "Automatically download files from password protected site"
date: 2009-08-04
forum: General Help
---

### Post by maino82 on 2009-08-04
I've tried googling this a bit and searched through the forums a bit but so far my search hasn't really turned up anything. I'm also not exactly sure where in the forums this should go, so I figured this would be a good place to start. 

What I'd like to do is to set up a cron job to automatically log on to PG&E's website (pge.com) each month and download the last month's worth of electricity and gas usage in a CSV file and then pump that into a database that I can then manipulate, examine, graph, etc. I have the cron part and the database part figured out quite nicely, but for the life of me I can't figure out how to get a script to "log in" to PG&E's website so that it can access my specific information. I've tried fiddling around with lynx and wget, but haven't had any success yet. Any ideas? Is there any way to push the login credentials to the site automatically and then download the file I want? Any help you could offer is greatly appreciated.

---

### Post by Dr Small on 2009-08-04
Does the website use cookies for authentication? If so, you can use wget with the --post-data option. (See the man page for more information and usage)

Just send the login information to the login page, save the cookies, then download your file while using the cookies (the wget man page for --post-data has a very good illustration on how to do this.)

Best of luck!
Dr Small

---

### Post by maino82 on 2009-08-09
Thanks for the suggestion, I'll have to look into that. I'm not sure if they use cookies or not. What's the easiest way to check?

---

### Post by Barafu Albino Cheetah on 2009-08-09
Look for the iMacro plugin for the Firefox. I never used it, but the advertisement mentioned similar things.

---

### Post by maino82 on 2009-08-10
The iMacros plugin looks interesting, and if I can set that up to run on a cron job I may go that route. I've also been reading the man page for wget a little more and even if the site doesn't use cookies, it looks like I can still save session info and send POST information, so I may be able to login that way by sending the username and password directly to the login script.

---

### Post by maino82 on 2009-08-11
OK, So I've made a little progress, but I've hit a little bit of a wall. I've figured out how to use the --keep-session-cookies and --save-cookies options, as well as the --load-cookies option in certain circumstances. Here's where I run into trouble:

```
pdrive@superman:~$ wget --load-cookies cookies.txt --post-data '__EVENTTARGET=objUCBHDataView$lnkExport&__EVENTARGUMENT=&__VIEWSTATE=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' -p https://www.energyguide.com/CustomerCare/BillHistoryRes.aspx
--2009-08-11 14:27:02--  https://www.energyguide.com/CustomerCare/BillHistoryRes.aspx
Resolving www.energyguide.com... 65.214.50.100
Connecting to www.energyguide.com|65.214.50.100|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: /customercare/DefaultError.aspx?aspxerrorpath=/CustomerCare/BillHistoryRes.aspx [following]
--2009-08-11 14:27:04--  https://www.energyguide.com/customercare/DefaultError.aspx?aspxerrorpath=/CustomerCare/BillHistoryRes.aspx
Reusing existing connection to www.energyguide.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 1448 (1.4K) [text/html]
Saving to: `www.energyguide.com/customercare/DefaultError.aspx?aspxerrorpath=%2FCustomerCare%2FBillHistoryRes.aspx'

100%[===================================================================================================>] 1,448       --.-K/s   in 0s

2009-08-11 14:27:04 (158 MB/s) - `www.energyguide.com/customercare/DefaultError.aspx?aspxerrorpath=%2FCustomerCare%2FBillHistoryRes.aspx' saved [1448/1448]

Loading robots.txt; please ignore errors.
--2009-08-11 14:27:04--  https://www.energyguide.com/robots.txt
Reusing existing connection to www.energyguide.com:443.
HTTP request sent, awaiting response... 404 Not Found
2009-08-11 14:27:04 ERROR 404: Not Found.

--2009-08-11 14:27:04--  https://www.energyguide.com/customercare/global.css
Reusing existing connection to www.energyguide.com:443.
HTTP request sent, awaiting response... 405 Method Not Allowed
2009-08-11 14:27:04 ERROR 405: Method Not Allowed.

FINISHED --2009-08-11 14:27:04--
Downloaded: 1 files, 1.4K in 0s (158 MB/s)

```

I'm not sure where exactly this is breaking down. The items listed in --post-data are the form items which I believe are required for proper submission of the form which leads to the downloaded file, but I'm not 100% sure. It's funky because the site uses javascript (using __doPostBack($eventtarget,$eventarguement)) to submit the form, so It's not entirely clear to me what I need to do. Any suggestions would be greatly appreciated.

---

### Post by DaithiF on 2009-08-11
Hi,
the output below doesn't reveal much really, other than BillHistory.aspx doesn't like something about the request and raises a redirect to the error page.  Does the content of the error page offer anything useful?

If not, the next avenue of enquiry I would try would be to take a look at the VIEWSTATE parameter -- looks suspiciously like something generated on the fly by the site each time, and so you're probably sending an old stale one that it doesn't recognise.  

When you are logged in to the site 'manually' check the value of VIEWSTATE a few times -- is it changing for each request you make?

---

### Post by maino82 on 2009-08-12
Ahhh... good call. The VIEWSTATE variable does change every time, so I guess I'm going to have to wget the page each time and then parse out the VIEWSTATE variable and insert that into another wget --post-info statement. 

I miss the good 'ole days when everything on the internet was just flat text files...

---

### Post by DaithiF on 2009-08-12
yep, something like that.  you could also tackle it in something like python -- libraries like urllib make thinks like this quite easy, so if you're struggling with wget then may be worth investing some time in a more flexlble tool.

good luck
d

---

