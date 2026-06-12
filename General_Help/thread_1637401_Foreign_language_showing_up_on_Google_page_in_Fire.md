---
title: "Foreign language showing up on Google page in Firefox"
date: 2010-12-04
forum: General Help
---

### Post by Flipper628 on 2010-12-04
[B]The past few days, when I do a Google search in FF, I get results with a foreign language as part of the results. This language can be seen on other areas of the page, as well. I found a link at the bottom of the page where you can set the page to English, but it reverts back. Is this a hijack or something?

Below is a copy/paste of the first result when I search for Ubuntu Forum. Note the foreign character in the summary. Thanks.
[/B]



**[*Ubuntu Forums*]("http://ubuntuforums.org/")**

Welcome to the *Ubuntu Forums*,  we encourage you to REGISTER on our forums and participate in the  community. Ubuntu is a complete Linux-based operating system **...**
**ubuntuforums**.org/ - [&#5024;&#5069;&#5062;&#5058;&#5034;&#5079;]("http://webcache.googleusercontent.com/search?q=cache:ncsHT27JcrEJ:ubuntuforums.org/+ubuntu+forums&cd=1&hl=chr&ct=clnk&gl=us&client=ubuntu") - [&#5028;&#5088;&#5105;]("http://www.google.com/search?hl=chr&q=related:ubuntuforums.org/+ubuntu+forums&tbo=1&sa=X&ei=XX36TJLvE4aglAf3u6DBDA&ved=0CBYQHzAA")
[Search]("http://ubuntuforums.org/search.php")
[Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")
[Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333")
[Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")
[Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310")
[General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")
[Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334")
[Desktop Environments]("http://ubuntuforums.org/forumdisplay.php?f=329")
[&#5028;&#5034;&#5079; &#5058;&#5082;&#5045;&#5069;&#5076;&#5061;&#5026;  ubuntuforums.org »]("http://www.google.com/search?hl=chr&q=+site:ubuntuforums.org+ubuntu+forums&sa=X&ei=XX36TJLvE4aglAf3u6DBDA&ved=0CB8QrAM")

---

### Post by lovinglinux on 2010-12-05
[LIST]
[*]Go to [http://www.google.com/preferences?hl=en](http://www.google.com/preferences?hl=en)
[*]Change to English
[/LIST]

---

### Post by TFrakes on 2010-12-10
Re: Foreign language showing up on Google pages in Firefox.  I have the same problem and my preferences are already set to English.  I repeated that action and still have the problem.  It's impossible to know what I'm clicking on.  Help!   (Thanks)

---

### Post by Flipper628 on 2010-12-10
Yes, my preference is already set to English... Still getting the foreign language. I'm not even sure what the language is... It also keeps changing my location (in the left column) to Washington Heights, NY.

---

### Post by libssd on 2010-12-10
> **Flipper628 said:**
> [&#5028;&#5034;&#5079; &#5058;&#5082;&#5045;&#5069;&#5076;&#5061;&#5026;  ubuntuforums.org »]("http://www.google.com/search?hl=chr&q=+site:ubuntuforums.org+ubuntu+forums&sa=X&ei=XX36TJLvE4aglAf3u6DBDA&ved=0CB8QrAM")
That doesn't look like a foreign language to me, rather a character set problem.

Edit > Preferences > Content > **Fonts & Colors **Advanced...

What does it show as your default character encoding? It should be Western (ISO-8859-1). If it's not, change it; if it is, try another encoding, such as Unicode (UTF8 or UTF-16. If the problem persists, something else is going on. 

I take it back; I just copied your "odd" characters, and pasted them into a Google search box. See image. It looks like characters are "leaking" in from an Indic character set, plus some Greek, and Latin characters. ](*,)

Strange.

---

### Post by libssd on 2010-12-10
**More**: I'm seeing the same artifacts with Google Chrome, so this isn't a browser dependency. I think Google itself is screwing something up.

There is another thread on this: [http://ubuntuforums.org/showthread.php?t=1536811](http://ubuntuforums.org/showthread.php?t=1536811)

But, I'm not buying the solution, as my language settings in both browsers appear to be what they should be.

---

### Post by Flipper628 on 2010-12-11
I appreciate the efforts. Checked my settings and they are as they should be. Going on to read the other thread. Thanks, libssd.

---

### Post by Flipper628 on 2010-12-11
This solution worked for me that I found in the other thread:

> **mirzmaster said:**
> I've actually been seeing the same issue, but  it only appears sometimes.  I checked the Language settings of Firefox  via Edit -> Preferences -> Content -> Languages.  After you hit  the "Choose..." button, you will be shown the preferred Language  ordering of Firefox.

Oddly enough, on that Languages screen, the only language in the list was "chrome://global/locale/intl.properties"!

To rectify the problem, I added "English [en]" to the list, and moved it  above the strange entry in the ordering.  Refreshing Google now shows  the correct character set.

I had to change the order so that [en] was on top. The strange characters are now gone. Thanks, all, for the help.

---

### Post by jay76 on 2011-03-07
Thanks guys, I was having this problem just now in March 2011, looks like a bug that hasn't been fixed yet?

---

### Post by jashale on 2011-03-26
jay76.  I agree this is still an issue.  I just had to deal with it this morning.

---

### Post by libssd on 2011-03-26
Interestingly, on a Google Chrome OS notebook, all the non-Latin characters display as empty squares -- which just means that they are not in the character set. To my surprise, unicode is not a character set option with Chrome OS.

---

