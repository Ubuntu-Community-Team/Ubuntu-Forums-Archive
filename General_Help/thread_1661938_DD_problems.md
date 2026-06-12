---
title: "DD problems"
date: 2011-01-07
forum: General Help
---

### Post by silverfire675 on 2011-01-07
I'm running dd simultaneously across 3 - 4 hard drives.  I have it set to zero them out.

My problem is that some of the hard drives are finishing too soon.  For instance

The 400gb drive finished at  162gbs copied

The 120gb hard drive finished at 80gbs copied

What's going on with DD why won't it finish?

btw the command I'm using is

```
"dd if=/dev/zero of=/dev/sdb"
```and I'm using this to watch progress

```
"watch -n 15 kill -USR1 'process-id'"
```Any help is appreciated.  Thanks.

Silver

---

### Post by Grenage on 2011-01-07
> **silverfire675 said:**
> I'm running dd simultaneously across 3 - 4 hard drives.  I have it set to zero them out.

My problem is that some of the hard drives are finishing too soon.  For instance

The 400gb drive finished at  162gbs copied

The 120gb hard drive finished at 80gbs copied

What's going on with DD why won't it finish?

btw the command I'm using is

```
"dd if=/dev/zero of=/dev/sdb"
```and I'm using this to watch progress

```
"watch -n 15 kill -USR1 'process-id'"
```Any help is appreciated.  Thanks.

Silver

I can't imagine why it would stop, unless there was an error on the sector it was writing to.  Try this:

```
d if=/dev/zero of=/dev/sdb bs=2048 conv=noerror,sync
```

Edit: The bs=2048 is the block size, so if it can't write to a small chunk of that 2048, it will ignore the whole 2048.  You can leave that command out if the data is really sensitive, but it does make it a lot faster.

---

### Post by silverfire675 on 2011-01-07
You rock bro :guitar:

edit:  testing it out right now...hopefully it completes it this time :P

---

### Post by Grenage on 2011-01-07
Good luck ;)

---

### Post by psusi on 2011-01-07
Why would it stop?  Well you'd have to ask dd.  What does it SAY when it stops?

---

### Post by silverfire675 on 2011-01-07
No error messages.  It's working a bit faster, but I'm still getting the issue.

The 120gb stopped at 60gbs.  It stops exactly like it would if it made it to 120gbs....this is rly weird.

---

### Post by psusi on 2011-01-07
dd prints output to stderr when it stops... you must be missing it.

You might also want to check your dmesg for errors.

---

### Post by dcstar on 2011-01-07
> **silverfire675 said:**
> I'm running dd simultaneously across 3 - 4 hard drives.  I have it set to zero them out.
..........

If you want to "zero" drives then use the proper Secure Erase commands built into the drives themselves and accessed via hdparm:

```
hdparm --security-help
```

---

