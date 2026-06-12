---
title: "catfish problem while using locate"
date: 2010-02-06
forum: General Help
---

### Post by chitresh4u on 2010-02-06
I have noticed following issues related to catfish. I am using only locate with catfish and found these.

1. whenever the file size of my search results increases more than 1.5 GB, the location and Last modified columns are empty. Size column shows 0B. refer  screenshot 1 for details. That file is 2.4 GB in size.

2. whenever the search with terms having space in between, nothing shows in the results. If just says "Fatal error: search was aborted. refer screenshot 2

[IMG]http://xs.to/image-3456_4B6D1370.jpg[/IMG]

[IMG]http://xs.to/image-90F7_4B6D1404.jpg[/IMG]

---

### Post by chitresh4u on 2010-02-09
no one knows any solution or no one faces this problem ???? :o

---

### Post by sashoalm on 2010-10-06
Well, I'm having problems where catfish doesn't find a file that locate finds.

---

### Post by Rytron on 2012-03-07
> **chitresh4u said:**
> whenever the search with terms having space in between, nothing shows in the results. If just says "Fatal error: search was aborted. refer screenshot 2

I've noticed this too. **Locate** in catfish wont search for spaces in searches. E.g. It&#65279; will look for **[COLOR="Red"]top[/COLOR]** but not **[COLOR="Indigo"]top cat[/COLOR]**. Any workaround yet?

---

### Post by usp8riot on 2012-08-12
I had the same problems also. The newest version fixed the problem. It's pretty slick and closer to what Everything Search on Windows does. You can get it [here]("http://bazaar.launchpad.net/~smd-seandavis/catfish-search/trunk/revision/86"). And being a python app, you can just run the .py file from the directory, no need to install.

I just made a ctrl+alt+f keyboard shortcut to "catfish" and it's like I'm right back in Windows using Everything.

---

### Post by Rytron on 2012-08-12
> **usp8riot said:**
> I had the same problems also. The newest version fixed the problem. It's pretty slick and closer to what Everything Search on Windows does. You can get it [here]("http://bazaar.launchpad.net/~smd-seandavis/catfish-search/trunk/revision/86"). And being a python app, you can just run the .py file from the directory, no need to install.

I just made a ctrl+alt+f keyboard shortcut to "catfish" and it's like I'm right back in Windows using Everything.

Nice one. Thank you usp8riot.

---

### Post by ads52 on 2012-08-12
I am perhaps a little old fashioned but I still believe that time learning to use *find *itself is time very well spent. There is a nice introductory guide on the Ubuntu Community Wiki:

[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

which is well worth looking at...

---

