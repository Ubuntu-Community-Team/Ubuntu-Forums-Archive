---
title: "How to enable java script in chromium &amp; FF?"
date: 2011-06-24
forum: General Help
---

### Post by ssreddy555 on 2011-06-24
Recently, while trying to do a bank transaction using chromium browser, I had to abandon it midway because I was told that java script was not enabled. 

Got the same message in FF as well. Then, I went back to Windows & completed the job using IE.  

How to enable the java script on chromium? Can anybody advise? I don't find an option in the browser's settings.

Edit: I found later that java script was in fact enabled in FF; but the Bank page still popped out the message that it was not enabled.

---

### Post by pqwoerituytrueiwoq on 2011-06-24
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```that should get you the official java installed (multiverse must be enabled under software sources)
java is not javascript
if you don't want any license agreement use icetea (go to the software manager) instead but some java stuff does not like it or have poor performance

---

### Post by idoitprone on 2011-06-24
> **ssreddy555 said:**
> Recently, while trying to do a bank transaction using chromium browser, I had to abandon it midway because I was told that java script was not enabled. 

Got the same message in FF as well. Then, I went back to Windows & completed the job using IE.  

How to enable the java script on chromium? Can anybody advise? I don't find an option in the browser's settings.

Edit: I found later that java script was in fact enabled in FF; but the Bank page still popped out the message that it was not enabled. 

javascript should be on by default on both browser. In fact those cocky developers for chromium cannot turn off javascript. They believe it is the most secure browser on the web with the sandbox model and all.

java plugin is not the same as javascript. This is a common confusion amoung the populous.

You might need to change browser identification, if the website just sucks.

---

### Post by ssreddy555 on 2011-06-25
I have already installed sun java from the software center. But it did not help. 
 
I have installed sun java browser plugin as well but still I am getting the same message.
 
Is it possible to change the browser identification in chromium? If so, how to do it?
 
Also, I am gettting this at the bottom of the page on some other sites as well:
 
javascript void (0). What does it mean?

---

### Post by lovinglinux on 2011-06-25
> **ssreddy555 said:**
> I have already installed sun java from the software center. But it did not help. 
 
I have installed sun java browser plugin as well but still I am getting the same message.
 
Is it possible to change the browser identification in chromium? If so, how to do it?
 
Also, I am gettting this at the bottom of the page on some other sites as well:
 
javascript void (0). What does it mean?

It is a javascript problem not Java, probably due to a poorly designed web site. Can you post a link so we can look at it?

You can change the browser user agent with [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59/") in Firefox.

For Chrome, you can use this:

[https://chrome.google.com/webstore/detail/aafciojnlamllgpkpdkbamkfgbofhgcj](https://chrome.google.com/webstore/detail/aafciojnlamllgpkpdkbamkfgbofhgcj)

I haven't tested it, because I use Firefox, but there are some comments stating the add-on doesn't work.

---

### Post by ssreddy555 on 2011-06-25
Installed in chromium through the link u have provided.

Will see how it works, next time when I use that page.

Thank u.

---

