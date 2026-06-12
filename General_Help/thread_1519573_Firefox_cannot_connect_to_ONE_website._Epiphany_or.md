---
title: "Firefox cannot connect to ONE website. Epiphany or Chromium does."
date: 2010-06-28
forum: General Help
---

### Post by cudjoe on 2010-06-28
Hi all.
I face a very strange problem.

Firefox cannot connect to only ONE website ([http://www.djangoproject.com/]("http://www.djangoproject.com/"))
whereas I never had any problem with the thousands of pages I browse everyday.

Epiphany or Chromium loads it without any problem.

I tried to start a new Firefox profile from scratch, and it worked ! Two days after, the problem occured again.

Do you have any idea ? What could cause this ?

Thank you in advance for your suggestions...

---

### Post by lovinglinux on 2010-06-28
Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

For more Firefox tweaks and tips see [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)
For additional support see [Firefox Optimization and Troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by cudjoe on 2010-06-29
Thank you for your reply.

But I already had IPv6 disabled and all !

---

### Post by CTBuckweed on 2010-06-29
> **cudjoe said:**
> Hi all.
I face a very strange problem.

Firefox cannot connect to only ONE website ([http://www.djangoproject.com/]("http://www.djangoproject.com/"))
whereas I never had any problem with the thousands of pages I browse everyday.

Epiphany or Chromium loads it without any problem.

I tried to start a new Firefox profile from scratch, and it worked ! Two days after, the problem occured again.

Do you have any idea ? What could cause this ?

Thank you in advance for your suggestions...
I am running Firefox 3.6.3 on my 64 bit Lucid Lynx 10.04. I can get to [http://www.djangoproject.com/](http://www.djangoproject.com/) just fine. I have never enabled IPv6. Is your DNS server blocking this site for some reason? Try pinging that address. I could ping it also.

---

### Post by lovinglinux on 2010-06-29
Try to clear Firefox cache.

BTW, I can open it here.

---

### Post by jupeter on 2010-07-02
I have the same problem on all pages in "djangoproject.com" and all subdomains of this domain (ex.docs.djangoproject.com). 

There is no problem to open page in other web browsers like Chrome or Opera. 

I have latest Firefox 3.6.6 from ubuntu packages with disabled all extensions. 

Disable ipv6 and clear cache didn't resolve problem.

Thank you in advance for your suggestions.

---

### Post by lovinglinux on 2010-07-02
Can you reach the site by IP number?

---

### Post by jupeter on 2010-07-02
Thanks for answer. 

No, I cannot open this site by IP number. 

On different web browsers, server redirect from URL [http://64.207.133.18/](http://64.207.133.18/) to [http://www.64.207.133.18/](http://www.64.207.133.18/) and it's correct behavior:
```
jupeter@k13:~$ telnet 64.207.133.18 80
Trying 64.207.133.18...
Connected to 64.207.133.18.
Escape character is '^]'.
GET / HTTP/1.0
host: 64.207.133.18

HTTP/1.0 301 Moved Permanently
Date: Fri, 02 Jul 2010 13:30:46 GMT
Server: Apache
Content-Type: text/html; charset=utf-8
Location: http://www.64.207.133.18/
Content-Length: 0
Connection: close

Connection closed by foreign host.
```

On Firefox, I waiting without any answer or redirection.

Any suggestions?

---

### Post by lovinglinux on 2010-08-05
> **jupeter said:**
> Thanks for answer. 

No, I cannot open this site by IP number. 

On different web browsers, server redirect from URL [http://64.207.133.18/](http://64.207.133.18/) to [http://www.64.207.133.18/](http://www.64.207.133.18/) and it's correct behavior:
```
jupeter@k13:~$ telnet 64.207.133.18 80
Trying 64.207.133.18...
Connected to 64.207.133.18.
Escape character is '^]'.
GET / HTTP/1.0
host: 64.207.133.18

HTTP/1.0 301 Moved Permanently
Date: Fri, 02 Jul 2010 13:30:46 GMT
Server: Apache
Content-Type: text/html; charset=utf-8
Location: http://www.64.207.133.18/
Content-Length: 0
Connection: close

Connection closed by foreign host.
```

On Firefox, I waiting without any answer or redirection.

Any suggestions?

Try to access it via a web proxy like [http://www.hidemyass.com](http://www.hidemyass.com) just to see if it works.

---

### Post by Haudegen22 on 2010-08-05
Try removing invalid entries from the list of preferred languages in your Firefox preferences.

-- 
Bye, Andi

---

### Post by cudjoe on 2010-08-10
> **Haudegen22 said:**
> Try removing invalid entries from the list of preferred languages in your Firefox preferences.

Thank you veru much Andi ! This is it !

At last I can get browse the django from my favorite browser !

---

