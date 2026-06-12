---
title: "itunes or iphone app in linux?"
date: 2012-06-25
forum: General Help
---

### Post by qwertyjjj on 2012-06-25
Is there an app in Linux that I can use to backup my iPhone?
Can it manage existing music already bought through iTunes or will it not be ableto copy those contents over?

---

### Post by sibin xavier on 2012-06-25
Install Wine or PlayOnLinux.After that install itunes for Windows using Wine

---

### Post by qwertyjjj on 2012-06-25
> **sibin xavier said:**
> Install Wine or PlayOnLinux.After that install itunes for Windows using Wine

It doesn;t work well on wine

---

### Post by Habitual on 2012-06-25
> **qwertyjjj said:**
> It doesn;t work well on wine

Virtualbox or dual-boot with Windows.

---

### Post by qwertyjjj on 2012-06-26
> **Habitual said:**
> Virtualbox or dual-boot with Windows.

Isn't there an app in Linux that can manage the phone?
Like Amarok? I also saw libimobiledevice but I am not sure if that works on 11.10 yet?

---

### Post by qwertyjjj on 2012-06-26
How can I install libimobiledevice on 11.10?

---

### Post by rubylaser on 2012-06-26
Google turned [this]("http://www.tekkidd.com/2011/11/libimobiledevice-now-supports-ios5.html") up.  That PPA now contains a version for Natty (11.04), so I'd try that first.  Although this may work, the comments don't seem too encouraging, the virtualbox or dual boot Windows is probably the most reliable way to do this.

---

### Post by qwertyjjj on 2012-06-26
> **rubylaser said:**
> Google turned [this]("http://www.tekkidd.com/2011/11/libimobiledevice-now-supports-ios5.html") up.  That PPA now contains a version for Natty (11.04), so I'd try that first.  Although this may work, the comments don't seem too encouraging, the virtualbox or dual boot Windows is probably the most reliable way to do this.

I added the repo but it said 404 not found in the update.
So, I went to update ther sources but the ppa wasn't in there.

?

---

### Post by rubylaser on 2012-06-26
I don't use 11.10 since there is a stable release out (12.04).  I'd read through some of those comments and see if anyone else had the same issue.  You can manually browse that PPA and the package does appear to be there, so I'm not sure what the issue is.

---

### Post by qwertyjjj on 2012-06-27
Tried using Banshee and it uploads music to the iPhone but you can't actually see it on the iPhone even though the storage space is reduced.
When will Linux sort out links to Apple products?!

---

### Post by evilsoup on 2012-06-27
> **qwertyjjj said:**
> When will Linux sort out links to Apple products?!

Well there's two main groups of Linux developers: those who do it unpaid, and those who work for companies like Canonical and Red Hat.

The unpaid guys seem mostly to be committed to the whole 'open-source' ideal, or they are hobbyists who enjoy hacking their equipment: either way, they are unlikely to go for the locked-down Apple ecosystem.

The paid guys, on the other hand, are mostly working for companies targeting enterprise customers... for whom putting music on an iPhone is not a high priority.

So probably never, sorry :V

---

### Post by qwertyjjj on 2012-06-28
> **evilsoup said:**
> Well there's two main groups of Linux developers: those who do it unpaid, and those who work for companies like Canonical and Red Hat.

The unpaid guys seem mostly to be committed to the whole 'open-source' ideal, or they are hobbyists who enjoy hacking their equipment: either way, they are unlikely to go for the locked-down Apple ecosystem.

The paid guys, on the other hand, are mostly working for companies targeting enterprise customers... for whom putting music on an iPhone is not a high priority.

So probably never, sorry :V

If there was a good alternative to the iPhone then I would use it but there isn't yet...

---

### Post by blennox on 2012-06-28
I think until gtkpod is updated for 12.04, your best bet is running iTunes in a virtual windows environment I'm afraid, that's what I'm having to do, spent quite a bit of time trying to get Banshee to work with no success.

---

### Post by coldjeanz on 2012-07-09
I can use Banshee music play to add or remove music from my iPod touch. It's not ideal and sometimes doesn't work but it's better than nothing.

---

### Post by lolpenguin on 2012-07-09
> **qwertyjjj said:**
> Tried using Banshee and it uploads music to the iPhone but you can't actually see it on the iPhone even though the storage space is reduced.
When will Linux sort out links to Apple products?!

Not until someone actually finds a way past Apple's proprietary framework (impossible?)

---

### Post by Lampang on 2012-07-09
After a fair amount of hunting around and trying various solutions, I ended up:

(a) using iTunes on XP running under VirtualBox.
(b) swearing on everything which is holy that I will never again buy anything made by Apple.

---

### Post by Topsiho on 2012-07-09
Googling with ipod ubuntu 12.04 I found:

[http://modifyubuntu.com/#programs](http://modifyubuntu.com/#programs)

and searching in this page with iPod some information is given that may (or may not) help.

Topsiho

---

### Post by scouser73 on 2012-07-09
> **qwertyjjj said:**
> Tried using Banshee and it uploads music to the iPhone but you can't actually see it on the iPhone even though the storage space is reduced.
When will Linux sort out links to Apple products?!

When Apple allows the use of iTunes to work on Linux without having to install WINE (which doesn't really fix the issue).

---

### Post by coldjeanz on 2012-07-10
> **lolpenguin said:**
> Not until someone actually finds a way past Apple's proprietary framework (impossible?)

It works (although slightly buggy). I can also use Beatbox to add music although right now it's not possible to remove music.

---

### Post by lolpenguin on 2012-07-10
> **scouser73 said:**
> When Apple allows the use of iTunes to work on Linux without having to install WINE (which doesn't really fix the issue).

Which will never happen, unless Apple really gets a change of heart. Steve Jobs elected Tim Cook as the new CEO beacuse of their similarities. <<<--- Note similarities.

---

