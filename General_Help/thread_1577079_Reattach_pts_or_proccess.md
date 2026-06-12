---
title: "Reattach pts or proccess"
date: 2010-09-18
forum: General Help
---

### Post by Tucznak on 2010-09-18
Hi, I was googling a lot, but i dont think so there is any solution of this situation.

So, there were a ssh session, but client side crashed and after reconnect, here is still pseudo terminal and process attached to it.
Is there any way how to reattach the pts or reattach process to another terminal?
(Please ignore screen or another terminal multiplexer, as long as I'm just curios if there is any solution of this situation, cause i use screen)

Thanks in advanced

---

### Post by CharlesA on 2010-09-18
what's the output of:

```
screen -ls
```

---

### Post by Tucznak on 2010-09-18
> **CharlesA said:**
> what's the output of:

```
screen -ls
```

I think we don't understand each other, I tried to avoid hints as "use screen" etc.

The thing is, here is process attached to pts, but pts is tombstone of crashed ssh session.

---

### Post by CharlesA on 2010-09-18
If you weren't using something like screen or whatnot, then the only way you can deal with it is to find the PID using ***ps aux | grep (whatever)*** and kill that process.

I actually had to do that with one of my ssh sessions when my network connection dropped.

---

### Post by Tucznak on 2010-09-18
So, there is no way how to reattach pts to another terminal?

---

### Post by CharlesA on 2010-09-18
> **Tucznak said:**
> So, there is no way how to reattach pts to another terminal?
The only way I know of to reattach a session after it's crashed is to when you are using screen.

Check [here]("http://kb.iu.edu/data/ahrm.html") for some info.

---

### Post by Tucznak on 2010-09-18
I was thinking about it, but I can't figure out if I can access pseudo terminal stdout or stdin, if so, I shall be able to redirect them to any other terminal, right?

---

### Post by CharlesA on 2010-09-18
> **Tucznak said:**
> I was thinking about it, but I can't figure out if I can access pseudo terminal stdout or stdin, if so, I shall be able to redirect them to any other terminal, right?
That I don't know. I doubt it tho.

It would be easier just to kill it and restart whatever was running on it.

---

### Post by Tucznak on 2010-09-20
Yes, that is definitely easier, but I can imagine situation, which really happened to my co-worker who has quite important process connected to his xserver on Windows, but windows said goodbye with BSOD.

So, It is not possible.

Well, is there something like screen for X server session?

---

