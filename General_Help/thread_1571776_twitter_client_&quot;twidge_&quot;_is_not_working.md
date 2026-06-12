---
title: "twitter client &quot;twidge &quot; is not working??"
date: 2010-09-10
forum: General Help
---

### Post by abhilashm86 on 2010-09-10
I use command line twidge for twitter, it gives a strange error on terminal, i don't understand. I tried to update, but nothing happens .
Has anyone using twidge faced a problem??

```
abhilash@abhilash:~$ twidge lsrecent
curl: (22) The requested URL returned error: 401
twidge: user error (("curl",["-A","twidge v1.0.0; Haskell; GHC","-s","-S","-L","-y","60","-Y","1","--retry","2","-f","--user","abhilashm86:","https://twitter.com/statuses/friends_timeline.xml?page=1"]): exited with code 22)

```

It was working fine from starting, is anything problem with updates/ program?

---

### Post by rahul8590 on 2010-10-08
even i am facing the same issue , , dunno wats wrong in there

```

curl: (22) The requested URL returned error: 401
twidge: user error (("curl",["-A","twidge v1.0.0; Haskell; GHC","-s","-S","-L","-y","60","-Y","1","--retry","2","-f","--user","username:password","https://twitter.com/statuses/friends_timeline.xml?page=1"]): exited with code 22)

```

---

### Post by aos101 on 2010-10-08
It's because of changes Twitter has made to it's API, and the version of twidge in the repositories for Ubuntu (for versions before 10.10) hasn't been updated to work with the API changes:

[https://bugs.launchpad.net/ubuntu/+source/twidge/+bug/628725](https://bugs.launchpad.net/ubuntu/+source/twidge/+bug/628725)

I think the easiest solution at the moment is to grab the appropriate twidge binary from their website and use that, as it's the latest version which has been updated to work with the Twitter API changes:

[http://github.com/jgoerzen/twidge/wiki](http://github.com/jgoerzen/twidge/wiki)

---

### Post by abhilashm86 on 2010-11-08
Yes aos!! I was struggling with GUI Gwibber for twitter, now i'll try latest binary. Cheers!! :)

---

