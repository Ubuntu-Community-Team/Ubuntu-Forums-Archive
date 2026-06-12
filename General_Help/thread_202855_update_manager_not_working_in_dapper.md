---
title: "update manager not working in dapper"
date: 2006-06-24
forum: General Help
---

### Post by eplans on 2006-06-24
I went headlong into dapper, simply because it was available as an update, so I didn't take any precautionary steps beforehand.

It upgraded beautifully, and everything works fine and more sparkly than in breezy.

The only thing is, when I try to get fresh updates, and click on install, I get this:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060614_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060614_all.deb)
  Could not connect to 10.0.0.2:8080 (10.0.0.2). - connect (111 Connection refused)

I think it's looking in the wrong place for the downloads, but I don't know where to change the settings.  I'm sure this is a simple problem, but I've been scouring the ubuntu forums, and I don't think I really know what I'm looking for.

Many thanx,
e.

---

### Post by JoshHendo on 2006-06-24
That file seems to exist, so I don't know why it can't find it.

I don't think it is a problem with Dapper or anything, because it says connection refused. Try again now and see what happens.

If you can't seem to fix it like that, check the following.

Try typing the following into the terminal:
```

sudo gedit /etc/apt/sources.list

```
and check that it says dapper, not breezy.

That is all I can think of for now.

---

### Post by eplans on 2006-06-24
[QUOTE=JoshHendo]

Try typing the following into the terminal:
```

sudo gedit /etc/apt/sources.list

```
and check that it says dapper, not breezy.

That is all I can think of for now.[/QUOTE]

Thanks for getting back so quick.  I did go and have a really good check, but the only reference to breezy is definitely commented out.

I might go and play with my router, maybe it has some sort of firewall that is blocking the connection, though odd that it worked with breezy, and not since dapper.

Many thanks again.

---

### Post by lamego on 2006-06-24
**"10.0.0.2:8080"** <- This is clearly a proxy address, your own local proxy I guess.
The problem is that it is not able to connect to that proxy...

---

### Post by eplans on 2006-06-24
<quote> lamego 	"10.0.0.2:8080" <- This is clearly a proxy address, your own local proxy I guess.
The problem is that it is not able to connect to that proxy... </quote>

You're right, that is our router's address.  I've tried going into synaptic and entering that as the proxy address, but that hasn't helped.  

I can ping 10.0.0.2 fine, and obviously internet access is fine.   Is there something other than ping I can use to try to connect to 10.0.0.2, and specify a port, ie 8080.  I'm way out of my depth in terms of network troubleshooting here.  I can ftp just fine to my own website etc.

Is there anything Dapper does differently in terms of auto-updates that Breezy didn't do?

thanks again.

---

