---
title: "unable to install packages"
date: 2010-06-20
forum: General Help
---

### Post by Velencoyy on 2010-06-20
Hey every time I try to install Ubuntu upgrade I get errors 

Failed to fetch [http://us.archive.Ubuntu.com/Ubuntu/pool/universe/c/cups/cupsys-bsd_1.3.9-17ubuntu3.7_all.deb](http://us.archive.Ubuntu.com/Ubuntu/pool/universe/c/cups/cupsys-bsd_1.3.9-17ubuntu3.7_all.deb). could not resolve "us.archive.Ubuntu.Com" 

And many more similar to this one I'm using my android to type so I can't copy all of them.

My log in screen is black with a cursor it started when my update failed to install properly.

I'm hoping if I can fix installing package issue I can run repair commands.

If any more info is needed ill try my best to get.

I use an Intel procceser, 512mb ram, intergrated Intel video card, 1.6ghz And uh 80gb harddrive.

---

### Post by wojox on 2010-06-20
> **Velencoyy said:**
> 
Failed to fetch [http://us.archive.Ubuntu.com/Ubuntu/pool/universe/c/cups/cupsys-bsd_1.3.9-17ubuntu3.7_all.deb](http://us.archive.Ubuntu.com/Ubuntu/pool/universe/c/cups/cupsys-bsd_1.3.9-17ubuntu3.7_all.deb). could not resolve "us.archive.Ubuntu.Com" 

Change it to this [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-bsd_1.3.9-17ubuntu3.7_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys-bsd_1.3.9-17ubuntu3.7_all.deb)

---

### Post by Velencoyy on 2010-06-20
Its every update listed I get an error similar to this I've tried everything how do I check where I download from?  

I'm really bad with Ubuntu atm

---

### Post by CharlesA on 2010-06-20
It sounds like a problem with DNS.

What happens if you run this:

```
dig -t A us.archive.ubuntu.com
```

---

### Post by Velencoyy on 2010-06-20
> **CharlesA said:**
> It sounds like a problem with DNS.

What happens if you run this:

```
dig -t A us.archive.ubuntu.com
```

; <<>> DiG 9.4.2-p2 <<>> -t us.archive.Ubuntu.com 
;; GLOBAL options: printcmd 
;; Connection timed out; no server could be reached 

That's what I get when I put it

---

### Post by CharlesA on 2010-06-20
Hrm, it looks like it cannot even get to that server. Do you have any problems with other sites?

You should have gotten something like this:

```
charles@thor:~$ dig -t A us.archive.ubuntu.com

; <<>> DiG 9.7.0-P1 <<>> -t A us.archive.ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47603
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;us.archive.ubuntu.com.         IN      A

;; ANSWER SECTION:
us.archive.ubuntu.com.  347     IN      A       91.189.88.46
us.archive.ubuntu.com.  347     IN      A       91.189.88.40
us.archive.ubuntu.com.  347     IN      A       91.189.92.166
us.archive.ubuntu.com.  347     IN      A       91.189.88.30
us.archive.ubuntu.com.  347     IN      A       91.189.88.45

;; Query time: 0 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Jun 20 16:45:39 2010
;; MSG SIZE  rcvd: 119

```

---

### Post by Velencoyy on 2010-06-20
Yeah 

W: failed to fetch [http://dl.Google.com/Linux/deb/dists/stable/main/i18n/translation-en_US.bz2](http://dl.Google.com/Linux/deb/dists/stable/main/i18n/translation-en_US.bz2) could not resolve dl.google.com

Edit;

W: failed to fetch [http://security.Ubuntu.com/Ubuntu/dists/jaunty-security/multiverse/i18n/translation-en_US.bz2](http://security.Ubuntu.com/Ubuntu/dists/jaunty-security/multiverse/i18n/translation-en_US.bz2) could not resolve security.Ubuntu.com

---

### Post by CharlesA on 2010-06-20
Are you able to wget it using the ip address instead of the hostname?

---

### Post by wojox on 2010-06-20
You need to change the letters in your hyper-links. It;s all lower case.

---

### Post by Velencoyy on 2010-06-20
> **CharlesA said:**
> Are you able to wget it using the ip address instead of the hostname?

How do I use wget >> I'm a noobie 

And letters are all lower case on my laptop my phone automatically corrects my words in every sentence when I type Ubuntu the u always ends up capital I don't know why

---

### Post by CharlesA on 2010-06-20
```
wget URL
```

Run that from a terminal.

---

