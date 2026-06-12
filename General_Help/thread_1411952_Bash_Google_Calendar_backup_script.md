---
title: "Bash Google Calendar backup script"
date: 2010-02-20
forum: General Help
---

### Post by mrkazoodle on 2010-02-20
Hi

I recently started using Google Calender because it is (as far as I know) the easiest way to keep my calendar (Sunbird) up to date. However I am a little concerned about backing it up; "What if I can't get Internet access?".
So I thought making a script which downloads my calendar would be an easy solution, it turned out a little bit harder than I thought.
This is what I've got so far, and it ain't workin'.

```
#!/bin/sh
wget --http-user=USERNAME@gmail.com --http-password=PASSWORD http://www.google.com/calendar/ical/UESRNAME@gmail.com/public/basic.ics
```

And this is the ouput I got (translated as much as possible)
```
Herleiden van www.google.com... 209.85.227.106, 209.85.227.147, 209.85.227.99, ...
Connecting to www.google.com|209.85.227.106|:80... connected.
HTTP-request is sent; waiting for answer... 404 Not Found
2010-02-20 21:51:20 Error 404: Not Found.

```

anyone who can help me out?

---

### Post by lukekurtis on 2010-03-02
I like your idea.  I'd like to be able to do the same thing.  Too bad no one has replied with more ideas yet--have you had any more luck?

I've been working on a similar project for backing up my Google Docs.

---

### Post by guren on 2010-03-02
I was trying this out

```

#!/bin/sh

USERNAME=''
PASSWORD=''

wget --http-user=$USERNAME@gmail.com --http-password=$PASSWORD https://www.google.com/calendar/dav?
wget http://www.google.com/calendar/ical/$USERNAME@gmail.com/private/basic.ics?

```

but I'm getting

```

Connecting to www.google.com|74.125.19.147|:443... failed: Connection refused.
Connecting to www.google.com|74.125.19.99|:443... failed: Connection refused.
Connecting to www.google.com|74.125.19.103|:443... failed: Connection refused.
Connecting to www.google.com|74.125.19.104|:443... failed: Connection refused.
Connecting to www.google.com|74.125.19.105|:443... failed: Connection refused.
Connecting to www.google.com|74.125.19.106|:443... failed: Connection refused.
401 Authorization required
Authorization failed.

```

The idea is to login first in [https://www.google.com/calendar/dav?](https://www.google.com/calendar/dav?)
then once logged in, download the ics file

The reason for ? at the end is to skip any caching.

Problem is I couldn't login. I'm not sure if google is blocking wget. I already tried putting user agent headers

---

### Post by steveroot on 2010-09-05
From your calendar, there's a private URL you can use to get an XML feed of the calendar entries.
 
EG: [https://www.google.com/calendar/feeds/steve%40yourdomain.co.uk/private-01234abcd56789etc/composite](https://www.google.com/calendar/feeds/steve%40yourdomain.co.uk/private-01234abcd56789etc/composite)
 
or [https://...../basic](https://...../basic) for simpler version. From memory, I think there's a /full too, though I only use the composite, and the basic link is the default from calendar setttings > settings > [your calendar name] (again from memory, so not exactly that). There are two groups of three links at the bottom of the page. Public feeds for XML, HTML and I can't remember (CSV?), and Private feeds for the same.  Your calendar is probably private, so use the private feed. There will only be content in your public feed if your calendar can be viewed by the world (not a good idea).
 
The feed includes something like 25 most recent new entries or updated entries.  If you're running a script to download the file, you'll have multiple files with the same content.  
 
I had to do the same for work, so wrote a small ruby application to get the feed every hour and add any new or updated entries to a mysql database.  Not quite up to the task of restoring things, but at least we can see what an appointment contained before it was amended or accidentally deleted.
 
The code is at: [http://github.com/steveroot/Google-Calendar-Backup](http://github.com/steveroot/Google-Calendar-Backup) if you want to try, but it needs work and you'll need ruby (not as quick to use as a script).
 
Hope that helps
Steve

---

