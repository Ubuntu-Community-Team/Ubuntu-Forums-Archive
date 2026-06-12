---
title: "Problem in Mozilla Firefox. UBUNTU 10.10"
date: 2010-12-02
forum: General Help
---

### Post by sundarapandian on 2010-12-02
Using mozilla firefox 3.6.10
ubuntu 10..10


i"m getting CSS error for a particular website only(ie. the color and indentation of the website is very different)... 

But when i use windows seven the website looks correct .

I don't know why this happend?
It's an issue with ubuntu??? or mozilla??
when is use Chromium Browser the same error i got...:(



Thanks...........

---

### Post by lovinglinux on 2010-12-02
Possibly their fault.

If the site doesn't contain personal information and you are fine sharing it, please do so we can test it.

---

### Post by sundarapandian on 2010-12-02
The Screenshot.png is on firefox,the other one is on chromium....

---

### Post by lovinglinux on 2010-12-02
Looks like a really badly designed site.

Open Firefox Error Console and see what CSS errors you get.

---

### Post by lovinglinux on 2010-12-02
I tested it on Opera, Firefox and Chrome. It is a really badly designed site. Besides...

> It is recommended to use Internet Explorer 8 for Safe & Secure Browsing. You may download Internet Explorer 8 by clicking on &#8220;Logo&#8221; 	 
 For Safety tips and guidelines on secure browsing through IE 8, please visit : [http://www.microsoft.com/windows/internet-explorer/features/safer.aspx](http://www.microsoft.com/windows/internet-explorer/features/safer.aspx)

---

### Post by sundarapandian on 2010-12-02
Ya worst design.... But in Win7 it's working fine...

---

### Post by searchfgold6789 on 2010-12-02
Some sites are just designed to be used with IE (such as poorly designed ones).
The answer my friend is WINE (sudo apt-get install wine)

---

### Post by sundarapandian on 2010-12-02
Bu tin windows seven this website works fine in FIREFOX.

---

### Post by lovinglinux on 2010-12-02
Someone should tell their web designer that just putting the w3c icons in the page doesn't make it valid: [http://validator.w3.org/check?uri=http%3A%2F%2Fbankofindia.com&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Fbankofindia.com&charset=%28detect+automatically%29&doctype=Inline&group=0)

---

### Post by sundarapandian on 2010-12-02
thnks friends...
any other way  other than IE8?

---

### Post by sundarapandian on 2010-12-02
I used Ubuntu Live CD it worked fine.....
I'm confused:

---

### Post by lovinglinux on 2010-12-02
> **sundarapandian said:**
> thnks friends...
any other way  other than IE8?

I wouldn't use that service even if it looked right. It doesn't inspire confidence on the service they are providing.

---

### Post by lovinglinux on 2010-12-02
I was able to test the baking page and it looks "fine" too.

Perhaps you have an extension blocking the css files.

Try to create a new Firefox profile, only for that bank. However, using the LiveCD is the most recommended method for online banking.

---

