---
title: "Email other than Evolution?"
date: 2011-04-25
forum: General Help
---

### Post by cortimi on 2011-04-25
I have tried for two days to get Evolution working properly. The only account I can get functioning is gmail, hotmail and yahoo won't even bother to try and work. I have read ad nauseaum on how to try and 'configure' these to work to no avail. Any suggestions on an alternative client?

---

### Post by andymorton on 2011-04-25
You could try Thunderbird. It should configure your accounts automatically once you've entered your address and password. 

andy

P.S It's available in the software centre.

---

### Post by collisionystm on 2011-04-25
FORGET about evoluton.

Use Zimbra. It is a beast. Best thing ever for linux. Blows away Thunderbird.

```

http://www.zimbra.com/products/desktop.html

```

---

### Post by gandaran on 2011-04-25
> **cortimi said:**
> I have tried for two days to get Evolution working properly. The only account I can get functioning is gmail, hotmail and yahoo won't even bother to try and work. I have read ad nauseaum on how to try and 'configure' these to work to no avail. Any suggestions on an alternative client?
evolution or any other mail client with yahoo email? I think thats not possible with the free yahoo mail accounts, only the paid yahoo accounts have support for POP server.

---

### Post by collisionystm on 2011-04-25
Zimbra is endorsed by yahoo. 

Oh and when you install Zimbra,

Change the theme to Smoky. 

It looks much better =)

Did I mention it automatically syncs google contacts and calendar right out the box??? No more addon crap for thunderturd.

---

### Post by cortimi on 2011-04-25
Thanks everyone, Zimbra looks like EXACTLY what I am looking for! Downloading it now. =3

Edit... Well I got a tar.gz, extracted, ran the install script in terminal....nothing happens. I guess I am doing something wrong? I've only had Ubuntu for three days.

---

### Post by collisionystm on 2011-04-25
> **cortimi said:**
> Thanks everyone, Zimbra looks like EXACTLY what I am looking for! Downloading it now. =3

When you install Zimbra do this,

Extract the zimbra archive

Next,

```

cd <extractedarchive>

```

```

sudo bash

```

```

./install.pl

```

Enter to continue, A to accept
Enter ( keep defaults)

You have finished installing application files.

Would you like to continue to install data files for user: root?
------------------------------
(Y)es or (N)o [N]: 


```


NO


```

Tyoe 

```

exit

```

in your terminal to go back to non-root user

run

```


/opt/zimbra/zdesktop/linux/user-install.pl


```

Enter to keep all defaults

Run Zimbra.

Icon will be on your desktop.

---

### Post by Sirkyuubi on 2011-04-25
Forget all those!

Just use "mail" from the terminal.

J/K

---

### Post by DeMus on 2011-04-25
> **collisionystm said:**
> FORGET about evoluton.

Use Zimbra. It is a beast. Best thing ever for linux. Blows away Thunderbird.

```

http://www.zimbra.com/products/desktop.html

```

Well, each his/her own but I would not suggest to use Zimbra. What a dreadfull program. I have tried it, after reading here about it, on a Windows XP machine and I immediately un-installed it. It's slow, has a bad user interface and it takes 15 minutes to un-install. And no, I don't have a slow laptop.
I have been a Thunderbird user and will stay that way. Zimbra doesn't come close to Thunderbird.
But as I said before: each his/her own.

---

### Post by cortimi on 2011-04-25
> **collisionystm said:**
> When you install Zimbra do this,

...

Icon will be on your desktop.

Wow, I never would have figured that out, thank you!!!! Worked like a treat.


Edit...Windows Live Mail STILL refuses to work. "SMTP Timeout". I don't get it. Smtp server is set to "smtp.live.com", port 25, authentication and SSL enabled. Nothing working. This sucks. >.<

---

### Post by collisionystm on 2011-04-25
> **cortimi said:**
> Wow, I never would have figured that out, thank you!!!! Worked like a treat.


Edit...Windows Live Mail STILL refuses to work. "SMTP Timeout". I don't get it. Smtp server is set to "smtp.live.com", port 25, authentication and SSL enabled. Nothing working. This sucks. >.<

Got this from another site
> 

 [CENTER]The Short Version[/CENTER]
 Receiving: **pop3.live.com**, port **995**, **SSL**
 Sending: **smtp.live.com**, port **587** (or 25), **TLS** (or SSL)
 Use your full Hotmail email address and password for login credentials. Sending requires authentication as well.




---

### Post by cortimi on 2011-04-25
Done all of that. It just will not work.

[IMG]http://img685.imageshack.us/img685/5510/zimbra.png[/IMG]

---

### Post by collisionystm on 2011-04-25
Change your SMTP port to 587

---

### Post by moonport on 2011-04-25
> **andymorton said:**
> You could try Thunderbird. It should configure your accounts automatically once you've entered your address and password. 

andy

P.S It's available in the software centre.

Thunderbird was my choice too. Zimbra is too slow and tricky.

---

### Post by cortimi on 2011-04-25
[[IMG]http://img848.imageshack.us/img848/1839/zimba2.png[/IMG]](http://img848.imageshack.us/i/zimba2.png/)

Same thing.

---

### Post by collisionystm on 2011-04-25
Shut off your firewall and try it

---

### Post by gandaran on 2011-04-25
just to point out that unlike gmail with hotmail you have to enter the full email on the username field and choose SSL encryption on both  pop and smtp options, hotmail works fine with evolution.

---

### Post by cortimi on 2011-04-25
> **collisionystm said:**
> Shut off your firewall and try it

How do I do that? I haven't installed any firewalls, and the router is UPnP and works for everything else. Thunderbird can access the inbox to Hotmail...but no other folders. What in the $%^& is going on? Grr. Thanks for your patience by the way.

---

### Post by NertSkull on 2011-04-25
Just another note.

Zimbra doesn't (yet) support GnuPG encrypted/secure emails.  Whereas thunderbird does.

So if you ever end up wanting that support, you may want to consider thunderbird instead

(at least, last time I checked, unless zimbra has added support in the past 7 months or so)

---

### Post by gandaran on 2011-04-25
> Thunderbird can access the inbox to Hotmail...but no other folders
hotmail only supports pop so you only have access to the inbox, for the other folders you would have to have a imap server setup which hotmail doesn't support.

---

### Post by cortimi on 2011-04-25
> **gandaran said:**
> hotmail only supports pop so you only have access to the inbox, for the other folders you would have to have a imap server setup which hotmail doesn't support.

Ok, so the inbox to hotmail is the only thing I am supposed to be able to see? If something goes to the spam folder, that means I can't check it form Thunderbird?

---

### Post by collisionystm on 2011-04-25
> **cortimi said:**
> Ok, so the inbox to hotmail is the only thing I am supposed to be able to see? If something goes to the spam folder, that means I can't check it form Thunderbird?

Make a Gmail account and set your Hotmail emails to forward to it.... :)

Gmail is much better anyways.

---

### Post by gandaran on 2011-04-25
> **cortimi said:**
> Ok, so the inbox to hotmail is the only thing I am supposed to be able to see? If something goes to the spam folder, that means I can't check it form Thunderbird?
if hotmail is doing the filtering then no you wont see it, but also I don't know about thunderbird as I don't use it but evolution has spam filters and puts unsolicited mail that wasn't filtered by the email provider in a separate box where you can check it, for me evolution is better and faster than thunderbird and no problems with my hotmail account.

---

