---
title: "Transmission and Peer Guardian"
date: 2010-10-01
forum: General Help
---

### Post by bumder on 2010-10-01
Hey,

Is it possible to import the block lists from say , Peer Guardian, into Transmission?

I'm not au fait with what Transmission can do, maybe it has a block list capability anyway.

Cheers!

---

### Post by cchhrriiss121212 on 2010-10-01
It does have one built in, see Edit>preferences>privacy. I don't know how it compares to PG but I like how you can just turn it on and forget it is there.

---

### Post by Charles Kerr on 2010-10-01
Transmission and PG both use the bluetack blocklist, so the results should be equivalent.

---

### Post by uriel1998 on 2010-11-18
With Transmission 2.12 (11412), you can specify the URL to the blocklist.  The blocklist that used to be downloaded is:

[http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)

There are more paranoid blocklists at Bluetack's website (you want the eMule version with the .gz extension).  Each is updated weekly.

Normal IP Filter:  [http://www.bluetack.co.uk/config/nipfilter.dat.gz](http://www.bluetack.co.uk/config/nipfilter.dat.gz)

Paranoid:  [http://www.bluetack.co.uk/config/pipfilter.dat.gz](http://www.bluetack.co.uk/config/pipfilter.dat.gz)

Sources:
[https://forum.transmissionbt.com/viewtopic.php?f=4&p=50358](https://forum.transmissionbt.com/viewtopic.php?f=4&p=50358)

[http://www.bluetack.co.uk/forums/index.php?CODE=02&autocom=faq&qid=17](http://www.bluetack.co.uk/forums/index.php?CODE=02&autocom=faq&qid=17)

---

### Post by fbugnon on 2011-03-29
Sorry for bringing this post back to life, but I thought my experience could help others.

Not sure if there is a problem with the server today, but following this post advice, I couldn't use the Normal IP Filter - Transmission didn't recognize the url (above-mentioned) as a valid Block List.

After a little search, I've came across this site: [http://www.iblocklist.com/lists.php](http://www.iblocklist.com/lists.php)

Which provides a sort of regular backup for Bluetack lists as well as other lists.  I'm not advertising for it, nor have I any interest on the services provided by iBlocklist - use at your own discretion.

I'm currently using [http://list.iblocklist.com/?list=bt_level1](http://list.iblocklist.com/?list=bt_level1) with Transmission 2.22, with 220.114 IP blocked as of today.

---

### Post by vedovatti on 2011-03-31
Thank you for the last one, fbugnon. It was driving me crazy that I couldnt download it! But you url works

Thanks

---

