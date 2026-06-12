---
title: "No access to recordings dir"
date: 2009-08-18
forum: General Help
---

### Post by sebrock on 2009-08-18
I have a strange issue. My recordings are located at:

```

/var/500GB/recordings

```

If i start the mythtv-backend from

```

sudo /etc/init.d/mythtv-backend start

```

I get no access to the above directory. If I however start with

```

sudo mythbackend

```

I get access to the dir and everything works. According to the init.d-script it mythtv-backend should be started user mythtv. Even setting ownership to that dir for mythtv does not work. I really can't figure out what is wrong here.

---

