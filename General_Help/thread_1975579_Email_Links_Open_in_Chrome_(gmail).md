---
title: "Email Links Open in Chrome (gmail)"
date: 2012-05-07
forum: General Help
---

### Post by Rocket J Squirrel on 2012-05-07
Until a couple weeks ago, when I clicked on an email link, either in a received email, or on a web page, it opened a Compose window in Thunderbird. Now it opens a new tab in Chrome and loads the gmail web page. 

I'm using 10.10, "Maverick."

---

### Post by scouser73 on 2012-05-07
When you were in your Gmail account last, did a message at the top of the screen ask for Gmail to handle email links?, if the answer is yes then you only need to delete the Gmail cookie from within Google Chrome by going to:

*Click on the Wrench icon & then do the following.*

1 - Click **Settings**

2 - Click on **Under The Bonnet** or **Under The Hood**

3 - Click on **All Cookies & Site Data**

4 - Enter *Google* into the Search Field & delete that cookie

---

### Post by Rocket J Squirrel on 2012-05-07
Thank you. I can't recall whether I brain-farted and told Chrome to let gmail handle emails. But I want to check for that cookie anyway.

I'm using Chrome Version 19.0.1084.36 beta

I find 23 sites with the word "Google" in them. Such as "docs.google.com," and "sites.google.com" and so on. 

Under plain-vanilla "google.com" there are 37 cookies. None with a useful name like "gmail."

Delete 'em all?

---

### Post by scouser73 on 2012-05-07
Yeah, you can delete them all. Then sign back into Gmail and if that message appears click no.

---

### Post by Rocket J Squirrel on 2012-05-07
Thank you. I deleted all cookies with the word "google."

I opened gmail.com in Chrome and it didn't ask if I wanted my mail handled by gmail. I closed the page. I went to another page and clicked on the mailto: link. A new tab opened in Chrome and gmail started loading again.

Several months ago I added an extension to Chrome, "Email this page (by Google) 1.2.5" which gives a little icon on the Chrome bar that, when clicked, /used/ to bring up a mail composition window using Thunderbird. 

This extension has two options: 

[INDENT]Select provider to use when emailing a web page address: 

(x) Your default mail handler
( ) Gmail[/INDENT]

My default mail handler is still selected. I've tried toggling that extension back and forth, and it looks like it thinks that gmail via Chrome is my default mail handler. 

I have confirmed (I think) that the O/S's default mail handler is still Thunderbird by composing an email address in OpenOffice Writer and clicking on it. It opens Thunderbird.

It looks like the problem is localized to Chrome.

---

