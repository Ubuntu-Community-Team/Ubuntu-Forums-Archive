---
title: "Can't access URLs with dashes?"
date: 2006-06-01
forum: General Help
---

### Post by ketsugi on 2006-06-01
Ever since I switched to Ubuntu I've been able to access certain URLs, including [http://step-.blogspot.com](http://step-.blogspot.com) and [http://dirt-.blogspot.com](http://dirt-.blogspot.com). I get a 404 in Firefox, and attempting to ping the URL in a terminal gives me an "Unknown host" error.

Removing the dashes works, but brings me to the wrong blog. I know there are blogs there behind those URLs, but Ubuntu just doesn't want to try to resolve the domain. I know it maps properly because Windows has no problem resolving it to the blogspot.com IP.

Is this a problem with the Linux kernel itself, or is it some other issue? Is it all URLs with dashes or is it only blogspot.com addresses?

This isn't really a big issue for me but my girlfriend has noticed that my Ubuntu machine can't access these sites (while her Windows laptop can) and frankly, it's not doing much for Ubuntu's reputation, or mine either. :/

---

### Post by BitTorrentBuddha on 2006-06-01
It's not a problem with the hyphens nor is it a problem with firefox. [http://ultimate-guitar.com](http://ultimate-guitar.com) works just fine and pinging those sites in a terminal results in an unknown host...

---

### Post by medgno on 2006-06-01
Pinging from the commandline works just fine for me, and I'm on Dapper. Here's the command I typed:
```
ping ultimate-guitar.com
```
If you put in the [http://,](http://,) that would make it not work. Otherwise, I'm really not sure.

---

### Post by nanotube on 2006-06-01
you might notice the particular pattern in the urls that don't work. the hyphen is the last character of the machine name. so ultimate-guitar is not really a good test case.
and, i will note that those step- and dirt- blogs dont work for me either, and i am running breezy.

i think you just stumbled on a problem in ubuntu.

---

### Post by cleentrax on 2006-06-01
yes, step-.blogspot.com is a real page, which I can access from Windows with Firefox or IE, but not from Ubuntu, either with Opera or Firefox.

---

### Post by gmhikin03 on 2006-06-01
are you sure its not [http://step.blogspot.com](http://step.blogspot.com) and [http://dirt.blogspot.com](http://dirt.blogspot.com) without the dashes.  because both of those took me to sites.  just an idea.

---

### Post by greggh on 2006-06-01
I can access both of those sites in winxp with FF. Looks like this is an Ubuntu bug in handling urls with a - in the last position as a subdomain.

---

### Post by roger6106 on 2006-06-01
Both of them work for me with Firefox in WinXP. In Ubuntu does it work with browsers other than firefox?

---

### Post by nanotube on 2006-06-01
[QUOTE=roger6106]Both of them work for me with Firefox in WinXP. In Ubuntu does it work with browsers other than firefox?[/QUOTE]
no, it does not. i even tried elinks (text mode browser), as well as wget, and telnet to port 80. 
it seems to be a system-level thing, not browser-level. it just fails to resolve the domain.

---

### Post by nanotube on 2006-06-01
[QUOTE=gmhikin03]are you sure its not [http://step.blogspot.com](http://step.blogspot.com) and [http://dirt.blogspot.com](http://dirt.blogspot.com) without the dashes.  because both of those took me to sites.  just an idea.[/QUOTE]
according to the OP, those are /different/ blogs.

---

### Post by ketsugi on 2006-06-01
[QUOTE=nanotube]according to the OP, those are /different/ blogs.[/QUOTE]

Indeed, those are different blogs, as anyone who's tried the links in Windows can attest to.

I guess this would be a problem with the DNS resolution, which would be in the kernel, right? So where do we file the bug?

---

### Post by medgno on 2006-06-01
Well, according to [the RFCs](ftp://ftp.isi.edu/in-notes/rfc1035.txt) none of the subdomains in a domain name are allowed to begin or end with a hyphen. So according to the RFC, Windows' behavior is broken. And I doubt you'll get Ubuntu or Linux as a whole to adopt a broken implimentation.

---

### Post by ketsugi on 2006-06-01
Well if that's the case, then someone needs to tell Google about it because they're allowing those subdomains on their Blogspot service :/

---

### Post by greggh on 2006-06-01
[QUOTE=medgno]Well, according to [the RFCs](ftp://ftp.isi.edu/in-notes/rfc1035.txt) none of the subdomains in a domain name are allowed to begin or end with a hyphen. So according to the RFC, Windows' behavior is broken. And I doubt you'll get Ubuntu or Linux as a whole to adopt a broken implimentation.[/QUOTE]

Can you quote the part where it gives that restriction with regards to "subdomains". I couldn't find it. I know that you cannot register a "domain" with a - at either the biginning or end, but was not aware of any kind of rule against doing this in a subdomain.

---

### Post by ketsugi on 2006-06-01
[QUOTE=greggh]Can you quote the part where it gives that restriction with regards to "subdomains". I couldn't find it. I know that you cannot register a "domain" with a - at either the biginning or end, but was not aware of any kind of rule against doing this in a subdomain.[/QUOTE]

Under Section 2.3.1:

> <domain> ::= <subdomain> | " "

<subdomain> ::= <label> | <subdomain> "." <label>

<label> ::= <letter> [ [ <ldh-str> ] <let-dig> ]

<ldh-str> ::= <let-dig-hyp> | <let-dig-hyp> <ldh-str>

<let-dig-hyp> ::= <let-dig> | "-"

<let-dig> ::= <letter> | <digit>

<letter> ::= any one of the 52 alphabetic characters A through Z in
upper case and a through z in lower case

<digit> ::= any one of the ten digits 0 through 9

Essentially, a subdomain MUST begin with a letter, and MUST end with either a letter or a digit.

---

### Post by medgno on 2006-06-01
Whoops, ketsugi beat me to it.

---

### Post by greggh on 2006-06-01
Ok, I'm going to have to admit that I'm not smart enough to understand all that. Can you tell me what part of that means you can't have a - at the biginning or end of the subdomain? :confused:

---

### Post by roger6106 on 2006-06-01
I just made sucessfully 3 subdomains with dashes at the front, end, and both. People shouldn't even be able to make those subdomains, should they? The subdomains I made are [-fake]("http://-fake.jarpequipment.com"), [fake-]("http://fake-.jarpequipment.com"), and [-fake-]("http://-fake-.jarpequipment.com"). They should all redirect to Google. Can Ubuntu use the subdomains starting with a hyphen?

*Note: supposedly the DNS could take a while to propogate although I was able to access these immediately.*

---

### Post by roger6106 on 2006-06-01
> <label> ::= <letter> [ [ <ldh-str> ] <let-dig> ]
From my understanding the <letter> means that you can only start the subdomain with a letter, the <ldh-str> means that you can have multiple letters, digits, and hyphens, and the closing <let-dig> means the last letter of the subdomain can only be letters or digits.

---

### Post by imagine on 2006-06-01
As already pointed out: Domain names must begin and end with a letter or a digit. Therefore you cannot register such a second-level-domain (eg ubuntu-.com). Of course for subdomains it's up to the owner what they allow. It's not like as it would be a crime to set up invalid subdomain names, it's just a violation of the specifications, even though some operating systems and browsers do indeed support domain names starting and ending with various special characters.
You can try to file a bug report, but I guess it will be marked as rejected.

---

### Post by Kuprin on 2006-06-01
That's exactly it; the behaviour in Ubuntu is correct, and that of Windows and Blogspot is wrong. Somebody go stick this in Google's face, k? :p

---

### Post by ketsugi on 2006-06-02
I've filed a support request with Blogger.com regarding this issue.

Btw I checked it on my sister's Mac Mini and confirmed that Macs have no problem resolving these URLs too... which makes our case weaker, I'm afraid, even if Ubuntu IS the standards-compliant one.

---

