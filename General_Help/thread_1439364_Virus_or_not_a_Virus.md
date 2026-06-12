---
title: "Virus or not a Virus"
date: 2010-03-26
forum: General Help
---

### Post by Quarkrad on 2010-03-26
Clam has just found two virus files - both **Trojan.JS.Selace-1**   The files are **iceteaplugin/cache/http/boomarrow.com/xxs/piu.bin** and **iceteaplugin/cache/http/boomarrow.com/xxs/piu.bin.gz**  Are these meaningless in terms of nasty virus?

---

### Post by cong06 on 2010-03-26
You know what nasty things you've been doing with your browser better then we do...

It sounds like a chance you'll have to take.
Either that or google "boomarrow.com" to see if there's any news.

Of course you also know that [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm")...

---

### Post by balaknair on 2010-03-26
You could try uploading the files to Virustotal to check.
They scan the files with around 30 different antivirus engines and show you the results and relevant links/info.

[http://www.virustotal.com/](http://www.virustotal.com/)

---

### Post by Kevbert on 2010-03-26
Seems that boomarrow.com is an unsafe place to go according to reports elsewhere on the web. It looks like a trojan and might affect java. There's a report on another linux forum [[COLOR="Red"]here[/COLOR]]("http://forums.opensuse.org/applications/433376-windows-trojan-found-icedtea-cache-any-danger.html"). If you google boomarrow.com you'll find that it appears in a few Security websites including McAfee and Norton. 
How to get rig of it ? now that's a good question.
Must run AV now.

---

### Post by 3rdalbum on 2010-03-26
They don't seem to be a threat to Linux.

---

### Post by Kevbert on 2010-03-26
Just run BitDefender and found this:
Object '/home/kevin/Desktop/clearos-enterprise-5.1.iso=>System/RPMS/clearsdn-content-filter-5.1-20091203.2120.noarch.rpm=>clearsdn-content-filter-5.1-20091203.2120.gz=>(gzip)=>./var/lib/suva/services/content-filter/blacklists/cleaning/domains' is infected with 'Generic.Qhost.A69FDA0A'
May be a false positive. Will try clamav now, just to be sure.

---

