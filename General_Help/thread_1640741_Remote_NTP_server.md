---
title: "Remote NTP server"
date: 2010-12-08
forum: General Help
---

### Post by ter-pierre on 2010-12-08
Hi guys!

I need to know the local time/date from a remote NTP server.
Example:
I have in my corporative network a Windows NTP server in France.
How can I check the local time/date fro that server?
In a Windows box I can use "net time \\myfrenchserver", but I dont know how to do this frm my Ubuntu box.

Help please...

---

### Post by SlugSlug on 2010-12-08
ssh into the box (if you can?)and type date

or maybe locally

ntpdate ip.of.remote.server

then date

---

### Post by sedawk on 2010-12-08
Check if 
```

ntpdate -q <ip_of_ntp_server>
#or
ntpdate -d -q <ip_of_ntp_server>

```
do the trick

---

### Post by ter-pierre on 2010-12-08
sedawk and SlugSlug,

ntpdate dont show the time/date of the NTP server, but just MY time/date using that NTP server.
I need to know the local frenc time from that NTP server.

---

### Post by anglican on 2010-12-08
> **ter-pierre said:**
> sedawk and SlugSlug,

ntpdate dont show the time/date of the NTP server, but just MY time/date using that NTP server.
I need to know the local frenc time from that NTP server.I tried:
```
ntpq -p
```
then taking the refid I.P. number (aaa.bbb.ccc.ddd):
```
ntpq -c readvar aaa.bbb.ccc.ddd
```
which seems to show what you want.

H

---

### Post by SeijiSensei on 2010-12-08
> **ter-pierre said:**
> ntpdate dont show the time/date of the NTP server, but just MY time/date using that NTP server. I need to know the local frenc time from that NTP server.

That's because your local computer has a "locale" defined that includes your time zone.  ntpdate actually reports the time in GMT which is then adjusted to your local time zone via your defined locale.  Can't you just adjust the reported time to account for the difference in time zones between you and France (+0100)?

---

### Post by ter-pierre on 2010-12-08
SeijiSensei, is very complicated to do this calcs automated. Some countries uses sumertime, others uses sumertime and wintertime. I will need to know my local time, know if is sumertime, know my local GMT, know remotetime, remote GMT, know if sumertime, or wintertime... Its a lot to know!!!

anglican
I'm triyng to use, but still no success.. :confused:
I have almost 12 NTP servers in my intranet.
I'm trying "ntpq -c readvar IP" but returns : timed out, nothing received

---

### Post by SlugSlug on 2010-12-08
why do you need 12 NTP servers?? sync em all to one or two..  can you get ssh access - it will be a lot easier

---

### Post by ter-pierre on 2010-12-08
[SlugSlug]("http://ubuntuforums.org/member.php?u=716956")
My company have a lot of remote sites. We have one NTP server on headquarter that sync with an external NTP. All other internal NTP servers, one on each site, sync with this "master".
What I need is a way to query the local time on each of this (Windows) NTP servers from a Ubuntu server box.
Inquire the strategy to use this "lot" of NTP servers... I prefer dont talk about...

---

### Post by apmcd47 on 2010-12-08
So you are not trying to sync your local clock with the remote server; you are trying to find the time in that server's region. You are using the wrong tool, in my opinion. You can probably get the time for a particular region by setting the TZ variable to that region, then running date locally, e.g.```
TZ=CET date
```which is close to SeijiSensei's solution.

So my solution for each country you wish to keep track of would be to have a series of shell scripts, functions or aliases:
```
 frenchtime() {TZ=CET date}
```(the above is for a function, obviously).

Given that all the ntp servers should be synced I don't see the need to check the time on the server itself, but if you insist the above function should probably be something like:```
 frenchtime() {TZ=CET ntpdate -q frenchserver}
```

Now just have one such function or script for each country and you should be okay.

Andrew

---

### Post by ter-pierre on 2010-12-08
:D

Thanks Andrew!!!
TZ+date solves my problem.

Excuse if I can't be clear or if I can't understood someone.
Thanks all

=D>

---

### Post by ter-pierre on 2010-12-08
Excuse, but just one more point...:confused:

TZ plus Date will able to consider DST?
Consider that in some countries the adoption of DTS don't have a fixed date, but is defined by an anual law...

---

### Post by tredegar on 2010-12-08
> TZ plus Date will able to consider DST?
Yes.
TZ rules are regularly updated if you keep your system up-to-date.

See also **cat /usr/share/doc/tzdata/README.Debian**

---

### Post by ter-pierre on 2010-12-09
tredegar

Very nice!!!

=D>=D>=D>

---

### Post by SeijiSensei on 2010-12-11
Just an observation that you need to make sure the tzdata file is updated regularly.  Countries do change their definitions of when daylight savings begins and ends remarkably often.  I can recall seeing updates to tzdata a couple of times in the past year or so.

---

