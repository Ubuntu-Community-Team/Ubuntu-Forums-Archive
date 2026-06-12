---
title: "tor config failed cannot start problem"
date: 2011-07-19
forum: General Help
---

### Post by BBfanatic on 2011-07-19
Hi, I installed tor with this :-

```

sudo apt-get install tor

```

And After installation, When I ran from vidalia , it gave me error :-
```

Jul 19 21:35:32.089 [Notice] Tor v0.2.2.30-rc (git-c697952fdbaa5a9f). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jul 19 21:35:32.102 [Notice] We were compiled with headers from version 1.4.13-stable of Libevent, but we're using a Libevent library that says it's version 1.4.14b-stable.
Jul 19 21:35:32.103 [Notice] Initialized libevent version 1.4.14b-stable using method epoll. Good.
Jul 19 21:35:32.103 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 19 21:35:32.103 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jul 19 21:35:32.103 [Notice] Opening Control listener on 127.0.0.1:9051
Jul 19 21:35:32.103 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Jul 19 21:35:32.103 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jul 19 21:35:32.103 [Error] Reading config failed--see warnings above.

```

I get the same error when I ran tor from command line :-
```

sudo /etc/init.d/privoxy start
sudo /etc/init.d/tor start

```

How to Solve this ?

Thanks

---

### Post by BBfanatic on 2011-07-19
It says, port 9050 is already in use, But when i see from canyouseeme.org and check if port 9050 is running than it gives me error, with connection time out.

Even When I check from this
```

top

```

I cannot see port 9050 running.

---

### Post by BBfanatic on 2011-07-20
No one knows the answer. ?

---

### Post by Calerid on 2011-11-05
Bump? having the same error with not solution yet.

---

### Post by theophiles on 2011-12-01
This works
[http://ubuntuforums.org/showpost.php?p=9226418&postcount=3](http://ubuntuforums.org/showpost.php?p=9226418&postcount=3)

---

