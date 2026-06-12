---
title: "HTML links not opening in default browser."
date: 2011-07-07
forum: General Help
---

### Post by brad1138 on 2011-07-07
I have Chrome as my default browser, I also have FF 5 installed. If I click an html link form my desktop, or a separate program opens a web page, they always open in FF. I have seen this in older versions of Ubuntu also, 32 & 64 bit. What is the issue?

Thanks,
Brad

---

### Post by haqking on 2011-07-07
have you checked preferred applications ?

also some apps have there own preferences for file handling.

any particular app ?

---

### Post by brad1138 on 2011-07-07
> **haqking said:**
> have you checked preferred applications ?

also some apps have there own preferences for file handling.

any particular app ?

Yes, preferred apps is set to Chrome, both Chrome and FF confirm that. 

Basically any program that opens a web page, like when you click on "about" and it brings up that info in a web page.

If I drag a url to the desktop, close all browsers, then double click the url. It opens in FF, always.

---

### Post by wojox on 2011-07-07
What if you try it the old fashion way:

```
sudo update-alternatives --config x-www-browser
```

---

### Post by brad1138 on 2011-07-07
> **wojox said:**
> What if you try it the old fashion way:

```
sudo update-alternatives --config x-www-browser
```

I'll try, but what will that do?

---

### Post by brad1138 on 2011-07-07
Thanks, I tried it anyway (I get scared of running commands that might do things I don't know how to undo). 

It worked :). I changed it from Chrome auto to Chrome manual. I ran it a second time to see that the change took.

> [sudo] password for brad: 
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                    Priority   Status
------------------------------------------------------------
* 0            /usr/bin/google-chrome   200       auto mode
  1            /usr/bin/firefox         40        manual mode
  2            /usr/bin/google-chrome   200       manual mode

Press enter to keep the current choice[*], or type selection number: 2
brad@Phenom-II:~$ sudo update-alternatives --config x-www-browser
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                    Priority   Status
------------------------------------------------------------
  0            /usr/bin/google-chrome   200       auto mode
  1            /usr/bin/firefox         40        manual mode
* 2            /usr/bin/google-chrome   200       manual mode


Thanks,
Brad

---

### Post by wojox on 2011-07-07
Cool. Glad to here it. ;)

---

### Post by Virus666 on 2012-06-23
> **wojox said:**
> What if you try it the old fashion way:

```
sudo update-alternatives --config x-www-browser
```

That solved the problem. I had the opposite problem; when I clicked an URL in Skype, webpage opens in Chromium instead of Firefox while Firefox is my default browser. Making Firefox as default browser via Firefox and operating system preferences did not work. However, thanks to that code I solved the problem.

Thank you... :-)

---

