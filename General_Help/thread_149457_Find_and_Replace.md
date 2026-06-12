---
title: "Find and Replace"
date: 2006-03-23
forum: General Help
---

### Post by mlissner on 2006-03-23
Ok, this isn't exactly ubuntu specific, but I've had great results here before, so I thought I'd give it a whirl.

I have this website, and on every page of it I have the number of dollars that I have fundraised. Whenever I would raise more money, I would simply open Dreamweaver, open the local version of the site, and do a global find and replace, replacing the old quanitity with the new one.

Now that I'm running Linux, I don't have dreamweaver, and doing this kind of thing is beyond me. 

Somewhere, I found this bit of knowledge a while back:
perl -pi -w -e 's/5036\.420/5036\.20/g;' *.htm

Which will search a certain folder and replace 5036.420 with 5036.20.

The problem is that I want to do that recursively within all the subfolders that are my site.

Anybody know perl well enough to educate me, or does anybody know a native linux function that will do this? I feel like grep might work, but I read the manual and found nothing for replace...any ideas, or clarifications?

Thanks in advance.

---

### Post by jrib on 2006-03-23
I don't know enough perl to understand all the switches in your command up there without looking them up.  Here is how I would do it though:

```
find /path/to/directory -name '*.htm' -exec sed -i 's/5036\.420/5036\.20/g' '{}' \;
```

I think that works...

---

### Post by mlissner on 2006-03-24
Incredible. You just saved me hours of work, and all I had to do was ask!

Thank you so much for this help, it's already done wonders...

If you want to see the satisfying fruits of your labor, [http://www.aidshike.org]("http://www.aidshike.org"). You'll see a new updated number in the quantity donated section. This project had been something I'd been putting off for ages.

Thanks again. This is great.

---

