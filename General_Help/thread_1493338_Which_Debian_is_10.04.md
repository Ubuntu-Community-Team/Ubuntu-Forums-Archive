---
title: "Which Debian is 10.04?"
date: 2010-05-25
forum: General Help
---

### Post by jamesisin on 2010-05-25
Yep, I just want to know which version of Debian was used for Ubuntu 10.04.  I tried to find some sort of chart which displayed versioning between the two distributions, but I didn't have any luck.

---

### Post by 2hot6ft2 on 2010-05-25
I'm pretty sure it's sid.
:popcorn:

---

### Post by Arand on 2010-05-25
10.04 was based on Debian testing: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

 - Arand

---

### Post by jamesisin on 2010-05-25
Hmmm... Perhaps I should elaborate.

I am trying to add the correct Opera repository for Ubuntu 10.04:

[http://deb.opera.com/](http://deb.opera.com/)

Which repository would be most appropriate?

---

### Post by WorMzy on 2010-05-25
I'm using ```
http://deb.opera.com/opera/ stable non-free
``` it was automatically added when I downloaded and installed the Ubuntu .deb from the Opera download page.

---

### Post by jamesisin on 2010-05-25
Which specific version of Opera does that give you?

---

### Post by WorMzy on 2010-05-26
10.10.4742

---

### Post by Phrea on 2010-05-26
By default, it will also add /opera-beta/ but that is generally disabled.
```

http://deb.opera.com/opera-beta/ stable non-free 

```
That will give you the latest [10.53b I believe].

A handy link: [http://www.opera.com/browser/next/](http://www.opera.com/browser/next/)
It provides you with a time line for the 10.5x final release of Opera for Linux [it finally will come in the beginning of June]

---

### Post by jamesisin on 2010-05-26
Using this one:

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) sid non-free

I get a message when I open Opera saying there is a newer version available. Are you seeing this as well?

---

### Post by jamesisin on 2010-05-26
Check it out.  Here is the message I get when I first open Opera:

[ATTACH]158387[/ATTACH]

Then I checked the download version here:

[ATTACH]158388[/ATTACH]

and here:

[ATTACH]158389[/ATTACH]

And finally I double-checked my version:

[ATTACH]158390[/ATTACH]

There you have it.

---

### Post by WorMzy on 2010-05-27
No message like that here. I even ran "check for updates" from the help menu, and got the "You are running the latest version" in response.

[[img]http://www.ubuntu-pics.de/thumb/71596/about_opera___opera_029_044Dgv.png[/img]](http://www.ubuntu-pics.de/bild/71596/about_opera___opera_029_044Dgv.png)

The only difference I can see is you're using i386, while I'm using AMD64. That might make a difference, but I doubt it.

---

