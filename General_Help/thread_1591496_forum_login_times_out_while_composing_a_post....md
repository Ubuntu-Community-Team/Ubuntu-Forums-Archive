---
title: "forum login times out while composing a post..."
date: 2010-10-09
forum: General Help
---

### Post by jtwdyp on 2010-10-09
Hi, I've used the forums infrequently, being more of a mailing list kind of guy. But I'm currently tinkering with an old laptop I got as a "gift" which doesn't have an ethernet port, And if I wanted to use my cable modems usb connection to apt-get etc for the installed Ubuntu Lucid, I had to disconnect my router. This pc  isn't yet configured with my mail client etc... So I thought I'd try the forum again...

I noticed that using: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.3) Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3 Which has not been modified yet (except to add the scroogle search bar) I keep timing out. IE
I logged in to ubuntu forums, found an existing thread related to something I'd like to do with it. clicked on quote, and began composing a followup. When I was ready to preview the thread I got an error that said I wasn't logged in. and suggested I use some included form to try again. The form looked like it wanted my username and password but wouldn't let me enter the required info into the blank fields... I had to simply log in again with the login link at the top of the forum page, and use the back button (alt+leftarrow) several times until my reply was recovered so that I could preview, fix typos & submit...

I searched the forum for "forum login timeout" and found one relevant post which appeared to say the only reason it's OP had a problem was do to making changes to his copy of firefox but that it was fixed ([solved]) without saying how he fixed it. There was a reference to using about:config which is beyond my skill level...

How does one keep the from login session from timing out while one's browser still has an open window to what was a logged in forum page anyway??? 

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

### Post by Zimmer on 2010-10-09
When logging on tick the box that says 'Remember me'

---

### Post by jtwdyp on 2010-10-10
> **Zimmer said:**
> When logging on tick the box that says 'Remember me'

But doesn't that cause my browser to hold my forum password in its files so that if, while I'm making a quick trip to the head, some joker got to my PC  before the screensaver kicked in they could pretend to be me???

I know it's not likely. But my paranoia settings preclude letting any of my software remember any of my passwords between sessions. Ah well At least when I'm using opera from my desktop I can type my login data into the provided form and get redirected back into the post I'm in the middle of preview/post(ing)...

Thanks anyway!

---

### Post by sendblink23 on 2010-10-10
> **jtwdyp said:**
> But doesn't that cause my browser to hold my forum password in its files so that if, while I'm making a quick trip to the head, some joker got to my PC  before the screensaver kicked in they could pretend to be me???

I know it's not likely. But my paranoia settings preclude letting any of my software remember any of my passwords between sessions. Ah well At least when I'm using opera from my desktop I can type my login data into the provided form and get redirected back into the post I'm in the middle of preview/post(ing)...

Thanks anyway!


Have you tested another web browser to see if it still occurs?

---

### Post by yetiman64 on 2010-10-10
> **jtwdyp said:**
> But doesn't that cause my browser to hold my forum password in its files so that if, while I'm making a quick trip to the head, some joker got to my PC  before the screensaver kicked in they could pretend to be me???...

Use the "lock screen" button on the "Indicator Applet Session" button as you are about to leave the workstation and you won't have to worry about the waiting for the screensaver to come on.

Also when composing a reply that takes a bit of time to put together, consider using copy and paste from the editor window to a blank document on your desktop to act as a buffer to the timeouts (normal function of the forum - although occasionally a PITA). 

Or if a "submit reply" button press results in a "log in" screen, immediately use the back button on your browser to get back to the editor window and copy and paste the contents as described above, and then re-login and copy/paste back to a new reply window.

I don't think the remember me button on the site actually remembers your password as such, just sticks a cookie in the browser cache as far as I understand it, and ticking it has never seemed to stop the normal site timeouts for me.

---

### Post by jtwdyp on 2010-10-12
> **sendblink23 said:**
> Have you tested another web browser to see if it still occurs?

I get this timeout with both opera AND firefox. I'm thinking that it's just the way this forum works... I can live with it cause the people here are exceptional, making this forum worth the minor aggravation of what to me is an unnecessarily rapid timeout.  

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

### Post by jtwdyp on 2010-10-12
It would appear that on Oct 10 yetiman64 said:
> Use the "lock screen" button on the "Indicator Applet Session" button as you are about to leave the workstation and you won't have to worry about the waiting for the screensaver to come on.Actually I only used that scenario to illustrate the concept of why I don't let my software store passwords. 

> Also when composing a reply that takes a bit of time to put together, consider using copy and paste from the editor window to a blank document on your desktop to act as a buffer to the timeouts (normal function of the forum - although occasionally a PITA). Yeah, If I realize I'm going to spend that much time on it before I began typing I would usually do that... 

> Or if a "submit reply" button press results in a "log in" screen, immediately use the back button on your browser to get back to the editor window and copy and paste the contents as described above, and then re-login and copy/paste back to a new reply window.Yeah, that would work. Though except for the occasion when I started this thread, the login form at the bottom works and the action (preview or post) then proceeds normally.

> I don't think the remember me button on the site actually remembers your password as such, just sticks a cookie in the browser cache as far as I understand it, and ticking it has never seemed to stop the normal site timeouts for me.Yeah, that figures... Since I don't really want it to "remember me" on some future browser session anyway, I'm thinking theres no point in my checking that box if I'm still going to time out.
If it stopped the time out it might be worth it to me however. That is IF if only gives my browser a cookie... Because you see, my paranoid settings also automatically delete ALL cookies on browser close anyway...   

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

### Post by lovinglinux on 2010-10-12
> **yetiman64 said:**
> I don't think the remember me button on the site actually remembers your password as such, just sticks a cookie in the browser cache as far as I understand it, and ticking it has never seemed to stop the normal site timeouts for me.

That is true. is just a cookie that eventually will timeout if you not access the page frequently.

> **jtwdyp said:**
> I get this timeout with both opera AND firefox. I'm thinking that it's just the way this forum works... I can live with it cause the people here are exceptional, making this forum worth the minor aggravation of what to me is an unnecessarily rapid timeout.  

I don't get timeouts here ever. Check Firefox cookie settings.

> **jtwdyp said:**
> Yeah, that figures... Since I don't really want it to "remember me" on some future browser session anyway, I'm thinking theres no point in my checking that box if I'm still going to time out.
If it stopped the time out it might be worth it to me however. That is IF if only gives my browser a cookie... Because you see, my paranoid settings also automatically delete ALL cookies on browser close anyway...   

Check your cookie settings. It is not supposed to timeout if you click the "remember me" button. If you delete the cookies when you exit, then you will need to login and tick the "remember me" button again.

---

### Post by jtwdyp on 2010-10-16
> **lovinglinux said:**
> That is true. is just a cookie that eventually will timeout if you not access the page frequently.I'm guessing that means that the "remember me" cookie would (if I didn't delete it) stay valid for a set time frame since last forum visit with same browser, after which it will self expire...[QUOTE=lovinglinux]Check your cookie settings. It is not supposed to timeout if you click the "remember me" button. If you delete the cookies when you exit, then you will need to login and tick the "remember me" button again.[/QUOTE]I'm thinking that means that the "remember me" button feeds my browser a cookie that is designed to only expire if I spend too much time **NOT connected** to the forum. or that has a longer expiration period than you've ever been logged in... I'm thinking I'll have to experiment with it. If it keeps me from timing out while my browser still has a page open to some part of the forum. And stops remembering me every time I close my browser, then it would be worth the habit of turning it on upon initial login.

Thanks
-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

### Post by lovinglinux on 2010-10-17
> **jtwdyp said:**
> I'm guessing that means that the "remember me" cookie would (if I didn't delete it) stay valid for a set time frame since last forum visit with same browser, after which it will self expire...

Yes.

> **jtwdyp said:**
> I'm thinking that means that the "remember me" button feeds my browser a cookie that is designed to only expire if I spend too much time **NOT connected** to the forum. or that has a longer expiration period than you've ever been logged in... I'm thinking I'll have to experiment with it. If it keeps me from timing out while my browser still has a page open to some part of the forum. And stops remembering me every time I close my browser, then it would be worth the habit of turning it on upon initial login.

It shouldn't expire if you still has a forum page open.

The expiration time is in the order of days. You don't need to keep the forum open to stay logged. Visiting the forum once a day should be more than enough, as long as you don't delete the cookies when closing the browser.

---

### Post by jtwdyp on 2010-10-17
OK testing complete...  I guess for me the way to stay happy with ubuntu forum is to get in the habit of checking the "remember me" box on forum login to avoid the timeout. And I can trust that the "remembered state won't persist past cookie deletion at end of browser session. (and/or it looks like clicking on 'log out' will also delete the cookie...) In any case, Now that I understand how it's organized,  it works for me.

Thank you One and all for the explanations.

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

