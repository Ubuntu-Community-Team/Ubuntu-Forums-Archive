---
title: "Need help seting up svn"
date: 2009-10-18
forum: General Help
---

### Post by xxarthur33xx on 2009-10-18
Hi, I'm not really sure where to post this, but this looks like the best place.

I have been going over TONS of guides explaining how to setup a svn for local & remote access. I had it working fine at first, then I added a test file or two, then 2 new directories to it, and now I cant get it to work at all.
I've had errors in firefox either saying I had an error talking about non-human something, then I had it where it said I didnt have svn. I have 2 diff user groups with me in it, one also has www-data in it.
Ive edited my dav_svn.conf a bunch and restored it to it original, so that shouldnt be a problem.

If you need more info, just ask. If you have the ultimate guide that I can't find, PLEASE post it.

ps, I need my friend to be able to access the svn (hes in the uk, im in usa)

Thanks. :\

---

### Post by Lars Noodén on 2009-10-19
Which guides have you found so far?

---

### Post by xxarthur33xx on 2009-10-19
**I got it to work. I had to edit my dav_svn.conf to direct to my svn. I forgot I had to change it to my new directory.**

Ive used this one about 4-5 times, and cant get it working..
[http://odyniec.net/articles/ubuntu-subversion-server/]("http://odyniec.net/articles/ubuntu-subversion-server/")

I get this error at the moment.
```
<D:error>
<C:error/>
<m:human-readable errcode="2">
Could not open the requested SVN filesystem
</m:human-readable>
</D:error>
```

Right now I have the svn made in the highest directory (idk what its called) and I try to access it through [http://127.0.0.1/svn](http://127.0.0.1/svn)

---

