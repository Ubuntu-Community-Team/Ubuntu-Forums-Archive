---
title: "Website backing"
date: 2012-02-13
forum: General Help
---

### Post by oskarh on 2012-02-13
I recently downloaded a website using wget (requested by the author), and I'd like to ask if there's some way to automatically update my offline version of the website whenever the online version does. Some sort of "check for updates" script would also work.

Thank you and sorry for any inconvenience.

---

### Post by Lars Noodén on 2012-02-13
[s]I'm just taking a guess here.  HTTP 1.1 allows an [If-Modified-Since](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.25) request header and using wget's [--header=](http://manpages.ubuntu.com/manpages/oneiric/en/man1/wget.1.html) plus any other mirroring options, that might work.  That would also depend on your web server being HTTP compliant, if it's Apache, Lighttpd, or nginx it should be no problem.[/s]

Never mind.  Go with timestamping as suggested below by Khayyam.

---

### Post by Khayyam on 2012-02-13
> **oskarh said:**
> I recently downloaded a website using wget (requested by the author), and I'd like to ask if there's some way to automatically update my offline version of the website whenever the online version does.

Yes, using the -N (--timestamping) option.

From the [Wget Manual]("http://www.gnu.org/software/wget/manual/wget.html")

> The time-stamping in GNU Wget is turned on using &#8216;--timestamping&#8217; (&#8216;-N&#8217;) option, or through timestamping = on directive in .wgetrc.  With this option, for each file it intends to download, Wget will check whether a local file of the same name exists.  If it does, and the remote file is not newer, Wget will not download it.

HTH ...

---

### Post by CharlesA on 2012-02-13
Wouldn't rsync do the same thing? Only difference is that you would need ssh access to the web server.

EDIT: In this case, wget with the timestamp switch would probably be the best thing to do.

---

### Post by SeijiSensei on 2012-02-13
I presume this is a site with reasonably static content?  If it's a dynamic site with content generated on the fly from a database, it may always be different enough that every page will update all the time.

Also you need to make sure that the developer hasn't turned off browser caching.  That might make a site look "new" all the time as well.

---

### Post by oskarh on 2012-02-16
Thank you very much for the help everyone. I'll look at time-stamping, which sounds exactly like what I need. Consider it solved :)

---

### Post by Khayyam on 2012-02-16
> **oskarh said:**
> Thank you very much for the help everyone. I'll look at time-stamping, which sounds exactly like what I need. Consider it solved

Your welcome .. all you need to now is [mark this thread as [SOLVED]](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

best .. khay

---

