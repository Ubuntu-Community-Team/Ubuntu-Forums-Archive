---
title: "Firefox 3.6.6 Crashing"
date: 2010-07-02
forum: General Help
---

### Post by justin10054 on 2010-07-02
Updated firefox to 3.6.6 yesterday and now it crashes whenever flash is involved. gmail, youtube, etc. it never did this before. is there any way i can fix this? it's very frustrating.

---

### Post by -humanaut- on 2010-07-02
What arch is your operating system x86 or Amd64?

---

### Post by justin10054 on 2010-07-02
x86

---

### Post by x1a4 on 2010-07-02
Hi,

Does it crash in full screen mode or the moment flash loads?  Try disabling hardware acceleration.  Reinstalling flash might help.

---

### Post by -humanaut- on 2010-07-02
I'd recommend reinstalling flash as well.

---

### Post by reptil on 2010-07-02
Well I never can run firefox after upgrade to 10.4, but now I ran firefox in debbug mode, so this is the trace

Starting program: /usr/lib/firefox-3.6.6/firefox-bin 
[Thread debugging using libthread_db enabled]
[New Thread 0xb5461b70 (LWP 1911)]
[New Thread 0xb4affb70 (LWP 1912)]
[New Thread 0xb42feb70 (LWP 1913)]
[New Thread 0xb37ffb70 (LWP 1914)]
[New Thread 0xb2ffeb70 (LWP 1915)]
[New Thread 0xb25ffb70 (LWP 1916)]
[Thread 0xb25ffb70 (LWP 1916) exited]
[New Thread 0xb25ffb70 (LWP 1917)]
Attempting to load the system libmoon 

Program received signal SIGSEGV, Segmentation fault.
0xae5bf79c in ?? ()
   from /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so

and trying to run it on safe mode, this is the result:

$ firefox -safe-mode
Attempting to load the system libmoon 
Segmentation fault
 

any suggestion ?

---

### Post by reptil on 2010-07-02
Hey after did the right question google helps me

[http://linux.ittoolbox.com/groups/technical-functional/ubuntu-l/ubuntu-1004-install-broke-firefox-and-sunbird-3490720](http://linux.ittoolbox.com/groups/technical-functional/ubuntu-l/ubuntu-1004-install-broke-firefox-and-sunbird-3490720)

it works for me! 

best regards

saludos

---

### Post by justin10054 on 2010-07-02
> **x1a4 said:**
> Hi,

Does it crash in full screen mode or the moment flash loads?  Try disabling hardware acceleration.  Reinstalling flash might help.

it's instantly upon flash loading. i've already reinstalled flash. how do i disable hardware acceleration?

---

### Post by justin10054 on 2010-07-02
i should also mention that flash is working fine in galleon.

---

### Post by sgthomas80 on 2010-07-03
Yes, I get the same problem. I am on ubuntu 8.04 (Hardy Heron). But when I installed firefox update together with someother updates recommended by the update manager (among them was apturl, yelp and other updates just a few days ago), I noticed that it started crashing firefox 3.6.6 as well as the older version of firefox that was working perfectly fine until then! I have not been able to identify the problem - but it could be flash since it occurs only on pages with flash content. It even affected epiphany browser; but seamonkey seems to work fine strangely. I reverted since to firefox 2 to be able to use firefox.

---

### Post by SephSki on 2010-07-17
> **sgthomas80 said:**
> Yes, I get the same problem. I am on ubuntu 8.04 (Hardy Heron). But when I installed firefox update together with someother updates recommended by the update manager (among them was apturl, yelp and other updates just a few days ago), I noticed that it started crashing firefox 3.6.6...

I'm in the same boat.  I'm running Ubuntu 8.04, I ran the recommended firefox updates for version 3.6.6, and it's been crashing ever since.  

It could be flash that's crashing it, but it seems to me it's more of a slow-response problem, as I can load flash content just fine sometimes but it does tend to crash when I open too many tabs too quickly.  Firefox grays out then, and it might appear to come back but will be completely unresponsive.  They only way I've been able to recover is kill the firefox process and restart it.  

I've read that the big news with firefox 3.6.6 is crash protection, which I'm finding kind of ironic.  But it sure looks to me as if that's where the problem is, given that it seems to happen when pages don't load quick enough.  

I haven't found a solution yet, but then, I'm not terribly techie either.  I've been stalling on wiping out firefox and doing a clean install, but I think that's my next step unless anyone else has any ideas.

---

### Post by x1a4 on 2010-07-23
Which flash package do you have installed?  The GPL'ed one or Adobe? If Adobe's which package: **flashplugin-nonfree** or **adobe-flashplugin**?  If **flashplugin-nonfree** then remove it and install **adobe-flashplugin**.

---

### Post by SephSki on 2010-07-24
I have adobe-flashplugin, version 10.1.53.64-1.

---

### Post by sgthomas80 on 2010-08-14
> **SephSki said:**
> I'm in the same boat.  I'm running Ubuntu 8.04, I ran the recommended firefox updates for version 3.6.6, and it's been crashing ever since.  

It could be flash that's crashing it, but it seems to me it's more of a slow-response problem, as I can load flash content just fine sometimes but it does tend to crash when I open too many tabs too quickly.  Firefox grays out then, and it might appear to come back but will be completely unresponsive.  They only way I've been able to recover is kill the firefox process and restart it.  

I've read that the big news with firefox 3.6.6 is crash protection, which I'm finding kind of ironic.  But it sure looks to me as if that's where the problem is, given that it seems to happen when pages don't load quick enough.  

I haven't found a solution yet, but then, I'm not terribly techie either.  I've been stalling on wiping out firefox and doing a clean install, but I think that's my next step unless anyone else has any ideas.
I resolveed at least part of the problem by uninstalling nspluginwrapper and flashplayer-nonfree and installing adobes flash plugin library for amd64 (somewhat unofficial version...since their official site states that they've temporarily closed down their 64 bit work). Here's the link I used: 

[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

Now atleast the firefox gmail problem is resolved. In other words, now, when I log into gmail, when firefox tries to load my list of contacts for the embedded chat service (in gmail), it doesn't freeze firefox to the point where I would have to force quit it, like before. Everything (including the embedded chat) works great. At the same time, even sites such as youtube, etc. that display flash content seems to work fine. 

But, alas, its never perfect, is it? Epiphany still doesn't work. In other words doing the exact same thing in epiphany still crashes (yes, crashes, not freezes) epiphany in a split second. I think this must be epiphany's problem. In any case...let me know if this helps any of you guys and if you know how to fix the epiphany problem.

---

### Post by SephSki on 2010-08-14
Since posting, I ran updates that brought me to Firefox 3.6.8, and things got a ton worse.

So I finally bit the bullet and renamed my .mozilla directory, then started Firefox fresh.  The clean start had me without my add-ons and toolbars, but I've been slowly been putting those back.  Eventually I'll go dig out my bookmarks too.

That did the trick though.  I haven't had any non-recoverable crashes since.  In fact, there was just one time where everything grayed out and I feared I'd have to kill it, but I waited a few seconds and firefox recovered on it's own, just like it's supposed to.

So far, so good.  [knock-on-wood]

---

