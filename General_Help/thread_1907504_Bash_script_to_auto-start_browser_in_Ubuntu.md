---
title: "Bash script to auto-start browser in Ubuntu"
date: 2012-01-11
forum: General Help
---

### Post by cwscribner on 2012-01-11
Hi all.

I've been tasked with setting up a thin client to do the following:
[LIST=1]
[*]Boot to a desktop without a login
[*]Open Google Chrome
[*]Navigate to a particular URL
[/LIST]

I'm assuming this would have to be done with a bash script but I don't know where to start.  Setting up the first item is pretty easy and I'm assuming that I can just enter a commandline item in the script to start Chrome.  However, I'm not sure how to send the URL as an argument.  Any help is much appreciated.

---

### Post by pr3zident on 2012-01-11
> **cwscribner said:**
> Hi all.

I've been tasked with setting up a thin client to do the following:
[LIST=1]
[*]Boot to a desktop without a login
[*]Open Google Chrome
[*]Navigate to a particular URL
[/LIST]

I'm assuming this would have to be done with a bash script but I don't know where to start.  Setting up the first item is pretty easy and I'm assuming that I can just enter a commandline item in the script to start Chrome.  However, I'm not sure how to send the URL as an argument.  Any help is much appreciated.

You can do this ```
google-chrome "www.google.com"
``` and that should open up the browser with the link ...

---

