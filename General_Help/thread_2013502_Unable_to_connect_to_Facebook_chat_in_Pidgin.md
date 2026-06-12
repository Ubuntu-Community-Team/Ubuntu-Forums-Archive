---
title: "Unable to connect to Facebook chat in Pidgin"
date: 2012-06-30
forum: General Help
---

### Post by viperdvman on 2012-06-30
This just happened about a half hour ago. I get kicked out of Facebook chat in Pidgin. I try to log on, and it says I've logged on from another location. So I kill every possible connection from my Facebook account and change my password.

Now, when I try to log onto my Facebook chat, with new password, it shows "Undefined condition"

Is anyone else getting this problem?

---

### Post by viperdvman on 2012-06-30
Don't know how I did it, but it's working now.

[I]edit:
Just kicked me off again, and got "Undefined Condition"[/I]

---

### Post by MrHotsauce on 2012-10-11
I'm also having the same sort of the same issue. For the past almost year I have been able to use facebook chat though pidgin (using the Facebook(XMPP)) plugin, but the past week any time I try and log in I get the following 

[IMG]http://i.imgur.com/LAgs3.png[/IMG]

and the following IM shows up from facebook

```
(12:11:33 AM) chat.facebook.com: Your account is temporarily unavailable. Regain access by logging into your account from your computer's web browser: http://www.facebook.com/
```

I have tried numerous times logging in logging out even went so far as to deactivate and reactivate my facebook but to no avail am I able to get it to work.

Should probably be stated I'm using Xubuntu 12.04 and Pidgin 2.10.6

EDIT - I just noticed I've brought back a thread from 4 months ago I'm terribly sorry for that.

---

### Post by freakalad on 2013-02-13
I've been struggling with the same issue now for more than a week.

I'm trying to connect to the chat service via XMPP clients, but I'm unable to connect.
The authentication goes through OK, but (in Adium at least) I get a "Resource Conflict" error (other clients are a bit more cryptic in their responses).
I've also tried different XMPP clients, including the one now included with the latest version(s) of ThunderBird (config'd as detailed @ [https://www.facebook.com/sitetour/chat.php](https://www.facebook.com/sitetour/chat.php)).

I've recently enabled 2FA & generated a unique password/hash for every connecting client - similarly as I do for my google chat connections.

I can see the authentication going through OK (i.e. a different message than if I entered an incorrect password), but then the connection is terminated with the the following message returned:
"Your account is temporarily unavailable. Regain access by logging into your account from your computer's web browser: http://www.facebook.com/"

I've tried logging off *all* my clients, including my mobile & reconnecting with a single XMPP client only, but the problem persists.

This has happening for little over a week now & I find it deeply frustrating, as I rely on my various IM services to stay in contact with friends, family & colleagues. 

I believe that this is an issue at FB server-side, and not the client, as I've tried this with multiple different clients from different connections.

If anyone has any insights into this, that would be a *great* help

---

### Post by momo321 on 2013-05-19
Hi !

I experienced the same error :  "[COLOR="#FF0000"]***Undefined Condition***[/COLOR]"  (on linux mint 14 / Ubuntu 12.04 with Pidgin 2.10.6).

The fix is to allow applications to connect to Facebook outside a browser :
On facebook.com :
– account > settings
– **apps** 
– **apps you use** and set it to "on"
[IMG]https://lh6.googleusercontent.com/-pSTvRUXlzYE/UZijbapgDCI/AAAAAAAAAdU/yLtmnRllgQM/w834-h378-no/Capture.png[/IMG]

I hope this helps.

---

### Post by freakalad on 2013-05-19
Thanks for the info, but unfortunately I can still not get this to work.
The setting was on for me (with some rather restrictive controls), so I tried turning the option off & back on again, but problem persists.

Can you please provide some additional info?

---

