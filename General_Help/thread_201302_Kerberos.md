---
title: "Kerberos"
date: 2006-06-21
forum: General Help
---

### Post by killernurd on 2006-06-21
I've been working on integrating a Linux server into an Active Directory for about a week now, and one thing has always come up that's moderately annoying.

I installed MIT Kerberos and it works just fine doing what it's supposed to do, and the machine integrates nicely... until I reboot, or the Kerberos ticket expires. I've investigated automated Kerberos ticket-refreshing, but this always requires a keytab file.

This is where I'm thrown off - I think I grasp what the keytab is, but how the heck to I create one!?

Whenever I just 'touch krb5.keytab' to create it, Kerberos utils start segfaulting on me, and nothing I've found in these forums (or through Google; probably because my Google fu is weak) has helped. I can't figure out how to create a keytab to save my life, not even pouring over the MIT Kerberos documentation has helped.

Like I said, there isn't a problem with Kerberos, except that automation requires a keytab.

If anyone can help, I would hugely appreciate it!

---

### Post by krunkite on 2006-06-23
I'm interested in this area too. I've noticed the issue with expired tickets before.

I haven't reached the stage of carrying out my Ubuntu integration into MS 2003 AD yet, but I will soon.

Try this link. I find that HP can be useful at times. Sometimes it helps to think out the box and infer......

[http://docs.hp.com/en/J4269-90037/ch04s11.html]("http://docs.hp.com/en/J4269-90037/ch04s11.html")

Hope it's useful to you! Keep us posted.

---

### Post by killernurd on 2006-06-23
Actually, I'd figured that part out :)

I've integrated the machine fine - it works perfectly, except that when the Kerberos ticket expires, I have to manually get another one.

However, in reviewing my post, I discovered that I hadn't made my point quite clear enough; sorry :(
What I'm having trouble with is the actual *generation* of the keytab (which HP conveniently provides instructions for: [http://docs.hp.com/en/J4269-90037/ch02s05.html](http://docs.hp.com/en/J4269-90037/ch02s05.html) )

I appreciate your input, though :) It lead me to HP's page that I mentioned, and it confirmed that the other sources I've been using were correct; it's the AD server here that's misconfigured.

---

### Post by krunkite on 2006-07-03
> ..... sorry What I'm having trouble with is the actual generation of the keytab (which HP conveniently provides instructions for: 

[http://docs.hp.com/en/J4269-90037/ch02s05.html](http://docs.hp.com/en/J4269-90037/ch02s05.html) )

I appreciate your input, though It lead me to HP's page that I mentioned, and it confirmed that the other sources I've been using were correct; it's the AD server here that's misconfigured.

Dude, without your question I wouldn't have become that little bit wiser. 

1) Your keytab issue led me to investigate whether I had the MS services for Unix running on the W2k3 server. I didn't.

2) I has allowed me to look more thoroughly into my AD integration. Looking at the up side and the downside of keytab creation.

Now you're probably way ahead of me on the AD integration, but I hope I can prove of some use to you with these 2 links:

[http://www.webservertalk.com/message1503363.html]("http://www.webservertalk.com/message1503363.html")

This shows how to generate a keytab for a machine account using ktpass.exe;

[http://wiki.ethereal.com/Kerberos]("http://wiki.ethereal.com/Kerberos")

This second one is particularly useful. Look at the section on the 'ktexport utlity'. I guess if you are using RC4 keys it may be of some use!

Let me know how you've gotten on with your set up so far.

I've only just gotten round to creating my PosixAccounts, took a fair while to download SFU3.5, we don't enjoy big bandwidth/low price structures here so things are slower!:neutral:

---

### Post by killernurd on 2006-07-04
Ah-HAH!

Thanks for the tip off! It just saved my implementation - I don't *need* to generate a keytab server-side! All I need to know are the username and password! XD

I am in heaven!

I'll implement it as soon as I get into work tomorrow!

**EDIT:** Err... bugger. It didn't work.

Keytab list:

```
slot KVNO Principal
---- ---- ---------------------------------------------------------------------
   1    1  Administrator/ndac.bah.com@NDAC.BAH.COM
```

Error output:

```
root@isplinux:~# kinit -k -t /etc/krb5.keytab
kinit(v5): Client not found in Kerberos database while getting initial credentials
```

---

