---
title: "irssi auto-close window"
date: 2009-12-04
forum: General Help
---

### Post by fluffman86 on 2009-12-04
So last night I started playing with the irssi CLI IRC client.  I like it so far, and have everything configured nicely--autojoin my favorite networks and #channels, auto-/msg nickserv identify <password>, etc.

The problem is that once I /msg nickserv, it creates a new query window, which I then have to /wc to close.  I've tried /ignore-ing nickserv, and I've tried adding to the auto-join /msg command a "wait 2000; /wc" to automatically close the query from nickserv, but none of this works.

Any ideas?  Thanks in advance!

---

### Post by andrew.46 on 2009-12-05
Hi fluffman,

> **fluffman86 said:**
> The problem is that once I /msg nickserv, it creates a new query window, which I then have to /wc to close.  I've tried /ignore-ing nickserv, and I've tried adding to the auto-join /msg command a "wait 2000; /wc" to automatically close the query from nickserv, but none of this works.

Any ideas?  Thanks in advance!

It is a little ugly but the following works on my system:

```
  Freenode = {
    type = "IRC";
    nick = "xxxxxxxx";
    **[COLOR="Red"]autosendcmd = "/msg nickserv identify xxxxxx;wait 2000;/window 2; /wc";[/COLOR]**
  };

```

with this section:

```
/window 2; /wc";
```

simply changing to the *second* window, which by default will be the nickserv window, and then closing it. A little ugly but it seems to achieve what you are after? Your syntax failed because you need to be *in* the active window to close it in this fashion :).

All the best,

Andrew

---

### Post by fluffman86 on 2009-12-05
awesome! thanks!

Took some playing since I connect to 2 separate windows.  Here's the relevant section in case anyone else stumbles upon this:
```

  rizon = {
    type = "IRC";
    autosendcmd = "/msg nickserv identify xxxxx;wait 2000;/window 3;/wc";
  };
  freenode = {
    type = "IRC";
    autosendcmd = "wait 5000;/msg nickserv identify xxxxx;wait 2000;/window 3;/wc";
  };
```

Window 2 is reserved for my autojoin chatroom, and sometimes one network would connect sooner than another, which means that sometimes freenode's nickserv would be 3, and rizon would be 4, or sometimes it would be switched.  

So now, when rizon connects, it opens a new window with the /msg, waits for authorization from the server, then closes the /msg.  Freenode waits 5 seconds before identifying, which ensures that it too opens on window 3.

---

### Post by andrew.46 on 2009-12-05
Hi fluffman86,

I see that you are right on top of this now :). I have found a slightly more elegant way that does not rely on guessing window numbers which might fit your situation better. Try using:

```
window goto nickserv;/wc";
```

and this should work a little more cleanly.

Andrew

---

### Post by fluffman86 on 2009-12-05
Awesome! That works perfectly and allows me to identify faster...both at the same time, in fact.  Thanks!

---

### Post by andrew.46 on 2009-12-05
Hi fluffman,

> **fluffman86 said:**
> Awesome! That works perfectly and allows me to identify faster...both at the same time, in fact.  Thanks!

No problems, this exchange has allowed me to learn a little more about irssi as well :).

All the best,

Andrew

---

