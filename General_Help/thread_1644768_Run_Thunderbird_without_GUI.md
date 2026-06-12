---
title: "Run Thunderbird without GUI?"
date: 2010-12-13
forum: General Help
---

### Post by Hack.The.Pow. on 2010-12-13
Hello all!

I just recently configured Thunderbird to work in the Messaging Applet via this tutorial.

[http://www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/](http://www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/)

It works great and is very convenient.  However the entry in the applet disappears after I close Thunderbird's window.  I was wondering if there was a way to run Thunderbird without the gui so all I would have is the indicator in the messaging applet.

When I get an email then it would notify me and I would click on it and it would reopen the Thunderbird window.  

Does anybody know how to do something like this?  It would be very much appreciated.

---

### Post by Krytarik on 2010-12-13
I'm running Tb with this extension, which you may have already installed following the guide you posted: [Indicators for Thunderbird - Add-ons for Thunderbird]("https://addons.mozilla.org/en-US/thunderbird/addon/223374/")

Additionally I also tried this one (and it worked): [MinimizeToTray Plus :: Add-ons for Tb & Fx]("https://addons.mozilla.org/en-US/thunderbird/addon/2831/")

Greetings.

---

### Post by Hack.The.Pow. on 2010-12-13
thanks for the reply.  The first one you linked to is indeed the one I already have installed.  The second one works pretty good too but I feel that its kind-of redundant with both of them.

---

### Post by Krytarik on 2010-12-13
> **Hack.The.Pow. said:**
> thanks for the reply.  The first one you linked to is indeed the one I already have installed.  The second one works pretty good too but I feel that its kind-of redundant with both of them.
You said:
> **I was wondering if there was a way to run Thunderbird without the gui...**
Or do you actually want to NOT run Tb until you get notified about a new message?

Then instead look at this post: [http://ubuntuforums.org/showpost.php?p=10225100&postcount=10](http://ubuntuforums.org/showpost.php?p=10225100&postcount=10)

I haven't tried it, because for me it really doesn't matter if Tb is running or not, even with a 9-year-old machine.;)

---

### Post by Hack.The.Pow. on 2010-12-13
I'm sorry if that sounded weird.  I want thunderbird to be running in the background because then the message indicator applet will work.  However I don't want to have the window open.  I don't even want it to be minimized into the tray.  I just want thunderbird to be "running"(no window) so that the thunderbird message indicator still works in the messaging applet.

That post does look promising though.  I will look into it when I get some time

---

### Post by Krytarik on 2010-12-14
> **Hack.The.Pow. said:**
> I'm sorry if that sounded weird.  I want thunderbird to be running in the background because then the message indicator applet will work.  However I don't want to have the window open.  I don't even want it to be minimized into the tray.  I just want thunderbird to be "running"(no window) so that the thunderbird message indicator still works in the messaging applet.

That post does look promising though.  I will look into it when I get some time
I just yet read a bit more detailed article about CloudSN:
[http://www.associatedcontent.com/article/6002040/cloudsn_cloud_services_notifications.html](http://www.associatedcontent.com/article/6002040/cloudsn_cloud_services_notifications.html)

Actually it sounds good, if one also uses some other services CloudSN supports. As I mentioned, you don't have to have Tb running to get notified about new mails, but once you open Tb through it, Tb is "a window", after checking your mail you could only close it by exiting Tb at all. The next time a new mail arrives and you want to check it, Tb gets started again. You see the pattern?!

---

### Post by Hack.The.Pow. on 2010-12-14
Wow that is pretty much what I wanted.  Thanks!  One problem though.

When I try to connect to my imap mail account I get this error. 

> NO [CLIENTBUG] Plaintext authentication disallowed on non-secure (SSL/TLS) 
connections.

I checked my thunderbird settings and it says I'm using STARTTLS for connection security.  I see that the only option cloudsn has for security is SSL and when I tried that it failed again.

Does this just mean I'll have to wait until CloudSn supports STARTTLS?

If so thats a bummer.  O well

---

### Post by Krytarik on 2010-12-14
> Does this just mean I'll have to wait until CloudSn supports STARTTLS?

If so thats a bummer.  O well

I think so. Because obviously your provider doesn't support SSL connections. Does none-secure work?

---

### Post by Hack.The.Pow. on 2010-12-14
Wow I'm retarted.  Just check my universities site and it turns out they do support ssl.  Just had to change the port to the correct one.  

Thanks for the help!

---

