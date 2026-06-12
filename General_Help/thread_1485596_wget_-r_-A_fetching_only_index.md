---
title: "wget -r -A fetching only index"
date: 2010-05-17
forum: General Help
---

### Post by rlong on 2010-05-17
Hi there,

I've been trying for a while to use wget to automate the download of podcast archives. I've checked the documentation and searched the wget mailing list archives for similar issues but haven't found anything.

I've tried multiple options on both 1.12 and 1.10.2.

My issue is that if I use just the recursive option it seems to work but when i add --accept=mp3 it downloads only the index.html and exits. When I added the --debug option I got this in the output:

```
Deciding whether to enqueue "http://pauldotcom.com/".
Already on the black list.
Decided NOT to load it.
```

and so on...

This is the complete command as I last tried it:

```

wget -r -np -U mozilla -e robots=off --random-wait --debug --accept=mp3 http://pauldotcom.com/ -H --domains=http://www.pauldotcom.com/,http://archive.pauldotcom.com/,http://media.libsyn.com/media/pauldotcom/

```

Any insights here would be appreciated. Thanks!

-R

---

### Post by sedawk on 2010-05-17
If you have something like this

base/
base/webcast1.mp3
base/webcast2.mp3
base/old/webcast3.mp3
base/old/webcast4.mp3

and you only accept mp3, then you do not allow
wget to load base/old/index.html which is the directory
listing that is needed to later download webcast3 and webcast4.
So you should also accept index.html or generally html.

---

### Post by rlong on 2010-05-17
Hi, thanks for the reply.

My understanding is that wget downloads and parses htm/html files for links automatically regardless of whether they are explicitly accepted and then deletes them after parsing if they are not accepted.

I can see all the parsed links listed when using the --debug option but I get a "The domain was not accepted. Decided NOT to load it." or "Already on the black list. Decided NOT to load it." message when wget is deciding whether to follow them. Note that I am not on any blacklist as far as the host is concerned since I am able to download everything if I use the -r option alone. It seems like something about -A is causing wget to fail to follow links.

I have been fiddling with wget off and on for a couple of days now and would be grateful for any help towards a breakthrough. Thanks.

-R

---

