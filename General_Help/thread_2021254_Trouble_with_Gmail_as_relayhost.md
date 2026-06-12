---
title: "Trouble with Gmail as relayhost"
date: 2012-07-08
forum: General Help
---

### Post by AlexBooton on 2012-07-08
I set up a relayhost using a gmail account in U12.04/postfix

It works!

BUT then I created a new gmail a/c just for this purpose and gmail won't accept the username or password.  The log says:
```
(SASL authentication failed; server smtp.gmail.com[173.194.68.109] said: 535-5.7.1 Please log in with your web browser and then try again.
```

Fine, I followed the instructions and logged in with my web browser.  That works!

But the gmail relay doesn't!

I've copied and pasted the username and password from the results of  ```
postmap -q [smtp.gmail.com]:587 /etc/postfix/sasl_passwd
``` into the web browser at gmail.com so I know there is no error there.

So why does it work with an older gmail a/c and not with a new one?  Is there delay until the gmail data is propagated to the correct server?  It's been two days so far.

Any ideas?

Thanks

---

### Post by critin on 2012-07-09
> So why does it work with an older gmail a/c and not with a new one?  I don't know the program at all, so ignore this if you know better.  It sounds like you need to have the gmail account first, before you set up the relayhost.   How difficult would it be to set up another now that you have the new addy?

Gmail forums may have the easy answer.

---

### Post by AlexBooton on 2012-07-09
I think I found the problem.

It appears you can't have ANYTHING in /etc/postfix/sasl_passwd AFTER the line with the credentials for the relay host.

Even a line with only a "#" seems to result in the wrong password being sent!

```
postfix -q ...
``` shows the correct user and password but apparently that's not what's sent to the relay host.

This was a real hair puller.

AB

---

