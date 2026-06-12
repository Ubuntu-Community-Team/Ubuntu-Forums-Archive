---
title: "Wget questions"
date: 2009-08-03
forum: General Help
---

### Post by kg84 on 2009-08-03
Hi guys...

Last night I attempted to d/l a .pdf file from a website using wget. Each time the request was met by a 403.  Downloading the pdf via the website itself (ie through the browser) was fine.

Q1. Can a website be set up to reject wget requests? Is they can, then why would they do this?

I was looking at d/l a number of pdf's from another website via wget. This time it worked. I could get each document individually or I could manually add several url's for each pdf to wget and get a few this way. I understand that wget has a 'glob' facility that allows you to get all files of a specified type - ie telling wget to get all *.pdf files linked on a web page.

This, as far as I know only works for FTP.

Q2. Is there an http equivalent for glob?

Cheers.

---

### Post by Volt9000 on 2009-08-03
Did you need to log into the website somewhere to access the PDF? If so, you need to specify this login info to wget, with the options

```

--http-user=USER
--http-password=PASS

```

If not, it's likely the website blocked you based on the user-agent string. By default, according to wget, is "Wget/VERSION". Change this with

```

--user-agent=AGENT

```

to Firefox or IE or whatever you want.
A list of user agent strings can be found [here](http://www.useragentstring.com/pages/useragentstring.php).

All this information can be found by looking at the man page, or even invoking wget with --help.

As for globbing, I don't believe there's an option for that, since AFAIK, the HTTP protocol doesn't support directory listing like FTP does.

---

### Post by kg84 on 2009-08-04
> **Volt9000 said:**
> Did you need to log into the website somewhere to access the PDF? If so, you need to specify this login info to wget, with the options

```

--http-user=USER
--http-password=PASS

```If not, it's likely the website blocked you based on the user-agent string. By default, according to wget, is "Wget/VERSION". Change this with

```

--user-agent=AGENT

```to Firefox or IE or whatever you want.
A list of user agent strings can be found [here]("http://www.useragentstring.com/pages/useragentstring.php").

All this information can be found by looking at the man page, or even invoking wget with --help.

As for globbing, I don't believe there's an option for that, since AFAIK, the HTTP protocol doesn't support directory listing like FTP does.

Thanks for the reply Volt9000.

First up, no login was required for the initial website's query. I did note on another page of the website concerned there was a statement  regarding bots siphoning up docs from this website and wget was mentioned in this. However, there was nothing to state that wget might be prohibited. But (from what you have said) I guess it is ;) 

Thanks for the advice re. User Agent. I'll give this a go.

And thanks re. globbing.

Cheers.

---

### Post by kg84 on 2009-08-04
```
wget --user-agent=firefox <url>
```

This works fine - thanks again Volt9000.

It seems that I have to add this each time for this particular website. I wonder if there is a way of permanently setting the user agent in wget... :)

---

### Post by nikhilk on 2009-08-04
> **kg84 said:**
> It seems that I have to add this each time for this particular website. I wonder if there is a way of permanently setting the user agent in wget... :)

The use of --user-agent is discouraged. So I don't think there is a setting for it in .wgetrc, to set it permanently.

---

### Post by kg84 on 2009-08-04
> **nikhilk said:**
> The use of --user-agent is discouraged. So I don't think there is a setting for it in .wgetrc, to set it permanently.


Okie-doke. Noted :)

I take it is discouraged for reasons that I hinted at above - to stop people siphoning websites etc?

---

### Post by nikhilk on 2009-08-04
> **kg84 said:**
> Okie-doke. Noted :)

I take it is discouraged for reasons that I hinted at above - to stop people siphoning websites etc?

Basically yes. It could be used to subvert some mechanisms of a website, with probably malicious intent. In some cases that might constitute violating terms and conditions of the use of a website etc, so it should be used carefully.

---

### Post by kg84 on 2009-08-04
> **nikhilk said:**
> Basically yes. It could be used to subvert some mechanisms of a website, with probably malicious intent. In some cases that might constitute violating terms and conditions of the use of a website etc, so it should be used carefully.

No problem - thanks for that. I have no real need for overuse of wget, am just in the process of learning how to drive it.

Cheers.

---

### Post by TideMan on 2009-08-04
I recently had to restrict access to a site for a client in local government who was worried that the info I had on the site would cause him grief with his tax payers.  I did it by simply editing .htaccess to exclude all but his and my IP adresses.  Everybody else gets a 403 error.

I suspect there are ways around this, but the client was happy because when he tried from home he couldn't get in.  Blissful ignorance!!

Anyway, if you're getting 403 errors, this could be the reason.

---

### Post by Volt9000 on 2009-08-04
Well, you *could* make things easier by creating a script that invokes wget using that option and any other option you specify.

Create a file with the following contents:

```

#!/bin/sh
wget --user-agent=firefox $*

```

Save this file as something like wget-ff, chmod +x it, and throw it into /usr/bin. Then you just invoke wget-ff instead of wget, pass it whatever parameters you want, and voila!

---

### Post by martinbaselier on 2009-08-04
Alias is better for this purpose:
**alias wget="wget --user-agent=firefox"**

if you add it to ~/.bashrc it will be permanent.

---

### Post by finch127 on 2009-08-04
Or you could set an alias for the command, so that wget --user-agent is simply awget. Every time you type it in from then on, wget --user-agent would be equivalent to awget then, or whatever you set it to.

Tutorial here:

[http://www.hypexr.org/bash_tutorial.php#alias](http://www.hypexr.org/bash_tutorial.php#alias)

---

### Post by kg84 on 2009-08-04
> **Volt9000 said:**
> Well, you *could* make things easier by creating a script that invokes wget using that option and any other option you specify.

Create a file with the following contents:

```

#!/bin/sh
wget --user-agent=firefox $*

```Save this file as something like wget-ff, chmod +x it, and throw it into /usr/bin. Then you just invoke wget-ff instead of wget, pass it whatever parameters you want, and voila!

Sweet - worked like a charm :)

Will give the alias method a try shortly.

Thanks for the tips guys :)

---

### Post by andrew.46 on 2009-08-05
Hi kg84,

> **kg84 said:**
> Thanks for the tips guys :)

If you have some concerns about spoofing the remote server by impersonating another browser it looks like there is an alternative which *may* work. Try

```
wget --user-agent="" <url>
```

and this should instruct wget not to use the User-Agent header at all. If it works with your files it may be a slightly 'cleaner' way of doing things :-).

Andrew

---

### Post by kg84 on 2009-08-05
> **andrew.46 said:**
> Hi kg84,



If you have some concerns about spoofing the remote server by impersonating another browser it looks like there is an alternative which *may* work. Try

```
wget --user-agent="" <url>
```and this should instruct wget not to use the User-Agent header at all. If it works with your files it may be a slightly 'cleaner' way of doing things :-).

Andrew


Thanks Andrew - that seems to work just fine. :)

---

