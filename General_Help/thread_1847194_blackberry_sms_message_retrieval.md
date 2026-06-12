---
title: "blackberry sms message retrieval"
date: 2011-09-20
forum: General Help
---

### Post by maclenin on 2011-09-20
Is it possible - using the command line, perhaps - to access a blackberry's database files?

1. I have a blackberry bold tethered to my natty desktop via usb.
2. I am able to charge the blackberry and enjoy a limited view of the blackberry media files and a few other file types via mass storage mode.

What I'd like to be able to do is "find" the blackberry database files so that I can extract / back-up sms / text messages.

Is this possible without installing 3pas including Barry and others?

Thanks for any insight!

---

### Post by maclenin on 2011-09-25
**Update:** I am giving Barry a whirl - to backup my BlackBerry's "SMS Messages" database to the PC - seems refreshingly straight-fwd, thus far.

However, once I have downloaded the SMS archive, I can't seem to find a way to "read" the archived files (on my PC) - defeating, essentially, the point of my particular exercise (as I don't intend to restore the database to another BlackBerry)....

If I try to open - for perusal - any of the many individual Barry-retrieved SMS files (listed in the archive manager as type "unknown") with Gnumeric or Mousepad, all I see is a single **[COLOR="DarkOrange"]@[/COLOR]**

Any thoughts? 

Thanks.

---

### Post by maclenin on 2012-01-23
This [[COLOR="DarkOrange"]golden link[/COLOR]]("http://www.progweb.com/en/2010/12/utilisation-de-barry/#toc-introduction") SOLVED the blackberry (curve / bold) sms retrieval / backup issue (in natty / oneiric) for me - with ferocious aplomb.

**NB:** My post does not address the barrybackup-gui package nor the retrieval / backup of blackberry messenger (BBM) texts, as I have yet to discover a terminal-based method for extracting BBMs. Feel free to post a BBM solution if you've got one! 

In sum:

1. Install barry "utilities" via the terminal (this will install both **barry-util** and **libarry0** packages. I use(d) aptitude. apt-get should work, as well):
```
sudo aptitude install barry-util
```

2. Connect your blackberry to your computer via usb (no need to activate mass storage mode).

2.a. [OPTIONAL] Run the following in the terminal to identify the blackberry connected to your computer.
```
bidentify
```

3. Run the following in the terminal to dump ALL SMS texts on your blackberry to the terminal window (NB: The -d option is for load and dump database not "delete" - but do a **man btool** from the terminal to see a full list of btool options):
```
btool -d 'SMS Messages'
```

3.a. [OPTIONAL] I have set up a pair of scripts to handle my SMS backup process. script1 generates a date stamp and runs the SMS dump. script2 acts as the log, to capture and direct the dump output (error and standard) to both the terminal and a separate date-stamped backup file. script2 is the "on switch" for the backup process. I wouldn't execute script1 independently of script2 - for the purposes of this backup.

script1: bb_sms.sh
```
#!/bin/bash
echo $(date)
btool -d 'SMS Messages'
```

script2: bb_sms_log.sh
```
#!/bin/bash
bb_sms.sh 2>&1 | tee bb_sms_backup_$(date +"%m%d%Y_%H%M")
```

That's it!

To thank, reiterate, and in sum, here are the two indispensable links, which put (the SMS dump aspect of) barry all together for me:

[**using barry**]("http://www.progweb.com/en/2010/12/utilisation-de-barry/#toc-introduction")
[**barry application**]("http://www.netdirect.ca/software/packages/barry")

Hope this helps others!

---

### Post by CK000 on 2012-06-21
[FONT=Garamond][SIZE=2]Thank you very much for such a useful set of posts, I have been wanting a way to do this for some considerable time.[/SIZE][/FONT]

---

