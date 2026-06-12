---
title: "wget login form sets cookie with javascript"
date: 2010-05-06
forum: General Help
---

### Post by ecoulthard on 2010-05-06
Is there any way to get wget to work with a login form that sets a cookie with a javascript function before submission? I know wget cannot call javascript functions but if there was a way to get it to set the cookie instead that would be great.

Thanks,

Here is the form tag:
<form name="form" method="post" action="https://www.yourfavouritesite.com/login.asp" onsubmit="return SetCookie()">

Here is the javascript function:
function SetCookie() {
	var idField = document.getElementById("idField");
	var cookieName = "ID";
	var cookieValue = idField.value;
	var nDays = 30;
	var today = new Date();
	var expire = new Date();
	if (nDays==null || nDays==0) nDays=1;
	expire.setTime(today.getTime() + 3600000*24*nDays);
	document.cookie = cookieName+"="+escape(cookieValue) + ";expires="+expire.toGMTString();
	return true;
}

---

### Post by WorMzy on 2010-05-06
I don't think so. I'm not sure why you'd even want to. Wget is a downloader, it doesn't have any use for cookies. If you want a terminal based web browser, try w3m.

---

### Post by ecoulthard on 2010-05-06
> **WorMzy said:**
> I don't think so. I'm not sure why you'd even want to. Wget is a downloader, it doesn't have any use for cookies. If you want a terminal based web browser, try w3m.

I want to write an automated script to check for updates. In order to do this I need the script to be able to login on its own.

---

### Post by WorMzy on 2010-05-06
Hm, it seems I'm mistaken and wget *can* use cookies. ```
wget --no-cookies --header "Cookie: <name>=<value>"
``` Might do what you want, or alternatively generate the cookie file in a browser, then store the cookie somewhere where it won't get purged, then ```
wget --load-cookies <file>
```

---

### Post by ecoulthard on 2010-05-06
I was able to get it to work by copying the cookies from my browser but I couldn't get it to work using --header. One of the problems is that I also need to keep session values in the cookie as well so using --no-cookies may clobber them. I think I might try using curl instead.

---

### Post by WorMzy on 2010-05-06
Session cookies are stored on the server, so --no-cookies shouldn't affect them. But keep in mind that session cookies expire shortly after the connection is dropped, you would need to keep the connection between wget and the server alive to maintain the session.

---

### Post by ecoulthard on 2010-05-06
Here are the calls I am using with urls and login information changed.

wget -O /dev/null --save-cookies=cookies.txt --keep-session-cookies [http://www.myfavoritesite.com](http://www.myfavoritesite.com)

wget -O out.html --keep-session-cookies --save-cookies=cookies.txt --load-cookies=cookies.txt --header "Cookie: ID=12345;expires=Sun, 6 Jun 2010 09:09:07 UTC" --post-data "user=me&password=my_password" [https://www.myfavoritesite.com/login.asp](https://www.myfavoritesite.com/login.asp)

The page that is returned is a login page that says that my session is expired. If I use --no-cookies for the second call I get the same result except that now cookies.txt has 1 entry instead of 3.

---

### Post by ecoulthard on 2010-05-11
I figured it out. When submitting my login request I did not include the name of the submit button in my post data. The correct wget call is:

wget -O /dev/null --keep-session-cookies --save-cookies=cookies.txt --post-data "ID=myID&password=myPassword&Submit=Submit" [https://www.yourfavoritesite.com/login.asp](https://www.yourfavoritesite.com/login.asp)

where "Submit" is the name and value of the submit button. When I viewed the html for the submit button its value was set to "". So somewhere along the way the value needed to be set to "Submit".

---

### Post by ju2wheels on 2010-05-11
Use the Firefox Tamper Data plugin to see what gets sent back and forth to avoid that issue. It lets you see exactly what data is posted after javascript has done all its manipulations...

---

