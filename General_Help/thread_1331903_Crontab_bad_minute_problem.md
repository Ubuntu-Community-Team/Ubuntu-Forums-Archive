---
title: "Crontab bad minute problem"
date: 2009-11-19
forum: General Help
---

### Post by birdy62 on 2009-11-19
Hi,
I want to set a cron job to run every 10 min from 8 am - 2pm every saturday, every day of the year.

my crontab entry (using crontab -e) is as follows:

```
*/10 08-14 * * 6
```however upon saving  I get the "bad minute can't save" message. Also the syntax colour in the editor is showing red for the month as well. I have tested it here [http://www.hxpi.com/cron_sandbox.php](http://www.hxpi.com/cron_sandbox.php) and it comes up fine. Also it does not seem to make any difference what the minute is set at I still get a "bad minute" . I am using vim as an  editor. According to many how-tos this should be ok. Previously I have used cron in unix BSD with no problem am I missing something? 

Ubuntu 9.10 Karmic Koala

Thanks

---

### Post by blueridgedog on 2009-11-19
You may not have extended crontab, so try:

0,10,20,30,40,50 08-14 * * 6

---

### Post by birdy62 on 2009-11-19
Thanks for reply.
Your suggestion produces the same error. The minutes, whatever they are set at are still getting the "bad minute" error.

Here is the whole entry, (truncated)

  0,10.20,30 08-14 * * 6 rsync -v -P --stats -z -r -p --delete /media/Nano/Docs "server address"

0,10,20,30 and the month are shown as errors in the syntax checker before saving. Seems like crontab won't accept any minute or month entries.

---

### Post by blueridgedog on 2009-11-20
You are certain you don't have a leading space or other character?

---

### Post by Bag-O-Stuff on 2009-11-20
> **birdy62 said:**
> 

Here is the whole entry, (truncated)

  0,10.20,30 08-14 * * 6 rsync -v -P --stats -z -r -p --delete /media/Nano/Docs "server address"



Is the period between the 10 and 20 minutes a typo in your post or the crontab entry?

---

### Post by birdy62 on 2009-11-21
Thanks 

blueridgedog, no leading space or other character, it would seem to be something like that but I can't see it.

Bag O stuff, yes that is a typo.

This is very puzzling, I am using vim as my system editor, could this be a problem? I created numerous crontabs in BSD unix with no probs, is there any log files or parameters I should be looking at ? 

very mystified.

---

### Post by Bag-O-Stuff on 2009-11-21
The entry looks OK to me.  Try in Nano?

```
export EDITOR=nano
```

---

