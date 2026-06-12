---
title: "Alpine roles"
date: 2009-12-28
forum: General Help
---

### Post by C. M .Hughes on 2009-12-28
Hi all,
I have Alpine configured to check 2 of my (IMAP) e-mail addresses:

[email]mypersonal@gmail.com[/email]
[email]mywork@pcc.edu[/email]

I can navigate between all of the messages just fine, but the problem I have is that I can not configure it to display the correct 'From' e-mail address automatically. The default is to display 

From:mypersonal@gmail.com 

which is not what I want when writing messages from [email]mywork@pcc.edu[/email]

I have tried addressing this issue using a Role. In the 'Current Folder Type' I have choices of

() Any
() News
() Email
() Specific

If I choose 'Any', then this means that I have to choose the role for *every* e-mail that I compose/reply/forward (but at least it works); I have tried choosing 'Specific' and selecting the appropriate folder for [email]mywork@pcc.edu[/email] so that it will automatically select the appropriate 'From' address, but I can't get it to work. 

Does anyone have any ideas on things that I can change/test?

Many thanks

---

### Post by C. M .Hughes on 2010-01-04
bump

---

### Post by inkhorn on 2010-02-04
Hi,

I just wrote a [blog entry]("http://nixliving.blogspot.com/2010/02/alpine-gmail-and-ssh-how-to-make-your.html") on setting up Alpine to send emails through Gmail using roles that put whatever email address in the **From **field that you want.  

Basically, you have to change the **To pattern** under **Current Message Conditions** to match any one of the email accounts you're checking through gmail (e.g. [email]mywork@pcc.edu[/email]).  Then under **Actions Begin Here** and beside **Set From** you need to put your name and the email address that you set for the **To pattern** (e.g. C.M. Hughes <mywork@pcc.edu>).  

It's handy to set **Reply Use**, under **Actions Begin Here**, to **Without Confirmation** so that when someone sends you an email to [email]mywork@pcc.edu[/email], your reply to that email will automatically contain C.M. Hughes <mywork@pcc.edu> in the **From **field.  Also, you'll want to tell Alpine to ask for confirmation of what role you're using when you compose so that you can choose whether to send from your gmail or pcc account.

On my configuration I have the **Folder Type** set to **Email**, which I believe was the default Role setting.  It works for me!

Hope this helps,
Inkhorn

---

### Post by C. M .Hughes on 2010-02-05
Thank you so much Inkhorn, that worked great!

It is now configured so that the 'From' and 'Reply-to' fields complete automatically- woohoo!

Thanks again

---

