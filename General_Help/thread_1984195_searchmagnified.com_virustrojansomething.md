---
title: "searchmagnified.com virus/trojan/something"
date: 2012-05-21
forum: General Help
---

### Post by ManiacDan on 2012-05-21
So I recently upgraded to 12.04 (against my will, but that's a whole other story).  While I hate unity and I think it's an enormous step backward, that's not my biggest problem at the moment.

Any time a DNS resolution fails, I'm redirected to searchmagnified.com.  This happens anytime the DNS lookup fails, even on the command line.

I have ClamAV running on a schedule and it hasn't found anything.  All the guides I've found online have been as simple as "clear your cookies" and other crap, but since it's at the system level, that obviously doesn't work.

How do I track down this issue and get rid of it?  This is a sensitive corporate machine, and I really don't want to format it for the second time in 2 weeks.

---

### Post by zombifier25 on 2012-05-21
Oh boy, your system is screwed up real hard. What is your DNS server? Are there anything weird in your /etc/hosts?

---

### Post by raja.genupula on 2012-05-21
[http://www.freemalwarecheck.com/malware-06/searchmagnified-com-removal.html](http://www.freemalwarecheck.com/malware-06/searchmagnified-com-removal.html)

[http://www.google.com/search?q=searchmagnified.com&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](http://www.google.com/search?q=searchmagnified.com&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs)

---

### Post by ManiacDan on 2012-05-21
Update:

resolv.conf points to 127.0.0.1 as my primary DNS server.  I have software running **as root** listening on 53:

```
maniacdan@maniacdan-laptop:~$ sudo netstat -pnl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:56524         0.0.0.0:*               LISTEN      7086/GoogleTalkPlug
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      4690/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      947/cupsd       
```

**Edit**:  I reinstalled dnsmasq and it's the real one.  The mystery deepens.

---

### Post by ManiacDan on 2012-05-21
> **zombifier25 said:**
> Oh boy, your system is screwed up real hard. What is your DNS server? Are there anything weird in your /etc/hosts?

DNS Server started out as the comcast default, then I changed it to google DNS.  Neither worked.

/etc/hosts contains nothing suspicious.

---

### Post by ManiacDan on 2012-05-21
> **raja.genupula said:**
> [http://www.freemalwarecheck.com/malware-06/searchmagnified-com-removal.html](http://www.freemalwarecheck.com/malware-06/searchmagnified-com-removal.html)

[http://www.google.com/search?q=searchmagnified.com&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](http://www.google.com/search?q=searchmagnified.com&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs)

This would be helpful if I was on windows, which I'm not.  Hence the unbutuforums.org.  Also, the first link is a scam.

---

### Post by roelforg on 2012-05-21
> **ManiacDan said:**
> Update:

resolv.conf points to 127.0.0.1 as my primary DNS server.  I have software running **as root** listening on 53:

```
maniacdan@maniacdan-laptop:~$ sudo netstat -pnl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:56524         0.0.0.0:*               LISTEN      7086/GoogleTalkPlug
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      4690/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      947/cupsd       
```

Did someone override the dns in ff itself?
Try using dig to see if it's systemwide or ff only.

---

### Post by ManiacDan on 2012-05-21
System wide, like I said in my first post.

---

### Post by roelforg on 2012-05-21
> **ManiacDan said:**
> System wide, like I said in my first post.

It's just that most people mean their browser when they say redirect and that you didn't mention the syswide detail.
Check your upstream dns and clear your dnscache, it could be that someone poisoned the upstream one.

---

### Post by ManiacDan on 2012-05-21
Not trying to fight with you, I said it happens *on the command line*.  Trying to ping a domain that doesn't exist results in a ping to this scammy search domain.

I don't have nscd installed, so there's no DNS to cache (I don't think).

---

### Post by roelforg on 2012-05-21
> **ManiacDan said:**
> Not trying to fight with you, I said it happens *on the command line*.  Trying to ping a domain that doesn't exist results in a ping to this scammy search domain.

I don't have nscd installed, so there's no DNS to cache (I don't think).

I skimmed the op, sorry.

From the dnsmasq site:
> 
Dnsmasq **caches internet addresses** (A records and AAAA records) and address-to-name mappings (PTR records), reducing the load on upstream servers and improving performance (especially on modem connections).

dnsmasq does caching.
And the upstream dns could be the problem.
Try using dig but force it to use one of the root dnsservers, that way you can see if it's more than a dns issue.

---

### Post by ManiacDan on 2012-05-21
> And the upstream dns could be the problem.
**DING DING DING**

You'd think business-class T3s for offices of 200+ people wouldn't redirect like this.

The first redirect was cached locally, which is why it seemed like a local issue.  Plus, search results seemed to back me up.  Also, at least one of the domains I was testing with is actually *owned by* searchmagnified, so that was throwing a wrench in it.

Hate.

Anyway, thank you for your responses, and sorry I was annoyed.  Mondays are not the time to think you have a virus on an OS you loathe anyway.

---

