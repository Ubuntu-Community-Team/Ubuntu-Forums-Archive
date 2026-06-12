---
title: "amarok annoyance"
date: 2010-10-08
forum: General Help
---

### Post by hawthornso23 on 2010-10-08
I'm not one of these people who has music playing all the time. But sometimes I do play music. When I do, Amarok puts an icon in the indicator applet - which is fine and good.

However when I have finished playing music that blasted grinning wolfhead refuses to go away and just sits there - even after I've quit from Amarok. If you click on it, it just shows you an empty menu. At that point it is a total waste of space and I wish it would go away. But our notoriously unconfigurable indicator applet provides no mechanism for killing this thing. It is one of those niggles things that just never stops annoying.

I don''t necessarily want to stop Amarok using the indicator applet area altogether because when Amarok is running it is useful and functional. But when I've stopped running Amarok, how can I tell it to go away.

---

### Post by mc4man on 2010-10-08
It's quite possible that amarok hasn't actually exited, one way to see is to open System Monitor and see if amarok is still shown (amarok, possibly amarokapp

If so installing this should resolve the unclean shutdown of amarok  (i'd do a restart after installing

```
sudo apt-get install mysql-server-core-5.1
```

---

### Post by hawthornso23 on 2010-10-08
Thanks for the tip about system monitor. It does indeed look like amarok is still around as system monitor reports it to be merely `sleeping'.

Could you please explain why you think installing a database server will help with this problem? Normally I can see the reasoning behind the advice given on this forum, but this has me stumped.

---

### Post by hawthornso23 on 2010-10-08
Well I still have no idea why this should work. However it most definitely DOES work. So thankyou! Now I can listen to music and be calmed and uplifted rather than annoyed.

---

### Post by mc4man on 2010-10-08
> explain why you think installing a database server will help 
I believe it has something to do w/ amarok not being able to complete parsing your local music collection, so it hangs.
This has been around since lucid development though I figured it had been fixed by now in lucid. 
(a number of recent posts similar to yours indicates differently

In testing maverick, which I upped to as soon as was possible, it does seem resolved.

orig. bug report (notice "Triaged", which often means don't hold your breath on a fix (though I did suggest simply making the server package a dep..?
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269)

---

