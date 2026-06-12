---
title: "Light SMTP Clients"
date: 2009-09-30
forum: General Help
---

### Post by ooobooontooo on 2009-09-30
Hi,

Can anyone recommend me a light SMTP client? I need it to interface with mutt. I've tried esmtp and nbsmtp. I couldn't get esmtp to work, but nbsmtp worked pretty well, but I don't like the fact that I have to store my password in a file. I would rather enter my password in every single time I need to send an email (So, command line authentiaction as opposed to storing password in a file). Thanks.

I know I'm being paranoid, but I feel more comfortable this way...

---

### Post by andrew.46 on 2009-10-02
Hi oobooontooo,

> **ooobooontooo said:**
>  I would rather enter my password in every single time I need to send an email (So, command line authentiaction as opposed to storing password in a file).

I believe that msmtp might be your answer here. I have used it for quite some time and I will admit that I have always placed my password in the configuration file and simply changed the permissions to 0600. But I scavenged through the man pages and noted the following:

```

password [secret]
    Set  your  password  for  SMTP authentication. An empty argument
    unsets the password. Authentication must be activated  with  the
    auth  command.   If  no password is set but one is needed during
    authentication, msmtp will try to find it in ~/.netrc.  If  that
    fails, it will try to find it in SYSCONFDIR/netrc (use --version
    to find out what SYSCONFDIR is on your platform). If that fails,
    it will try to get it from a system specific keychain (if avail-
    able). [B][B][COLOR="Red"]If that fails but a controlling  terminal  is  available,
    msmtp will prompt you for it[/COLOR][/B][/B].

```

This looks like it might be what you are after?

Andrew

---

### Post by ooobooontooo on 2009-10-02
Sounds good. Thank you. I'll try it out some time soon.

---

### Post by bobblu on 2009-10-02
msmtp is an SMTP client that can be used to send mails from Mutt and probably other MUAs (mail user agents). It forwards mails to an SMTP server (for example at a free mail provider), which takes care of the final delivery. Using profiles, it can be easily configured to use different SMTP servers with different configurations, which makes it ideal for mobile clients.  This package is compiled with GSASL and TLS support. 

================================
[weddings in the maldives](http://www.bestatmaldivesholidays.co.uk/pages/honeymoons)
[buy steriod](http://legalsteroids.com)

---

### Post by ooobooontooo on 2009-10-02
Thanks.

Yeah, I didn't think to use msmtp because it said no commandline authentication was available on this page:
[http://wiki.mutt.org/?LightSMTPagents]("http://wiki.mutt.org/?LightSMTPagents")
Anyway, still haven't tried yet...I'll let you know how it goes...

---

### Post by andrew.46 on 2009-10-02
Hi oobooontooo,

> **ooobooontooo said:**
> Yeah, I didn't think to use msmtp because it said no commandline authentication was available on this page:
[http://wiki.mutt.org/?LightSMTPagents]("http://wiki.mutt.org/?LightSMTPagents")
Anyway, still haven't tried yet...I'll let you know how it goes...

Hmmm.... I could not get this to run while calling msmtp from within mutt, looks like this usage does not qualify as a 'controlling terminal' :(. Sorry for leading you astray....

Andrew

---

