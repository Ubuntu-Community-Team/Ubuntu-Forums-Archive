---
title: "Can Firefox co-exist with Swiftweasel?"
date: 2009-09-18
forum: General Help
---

### Post by DapperMe17 on 2009-09-18
Hi,

I have Firefox 3.0 & Swiftweasel 3.5, both on the same box.

I've installed Swiftweasel, which runs fine. However, for some reason, when I add or delete "add-ons" under either FIrefox or Swiftweasel, my toolbar positioning (icons, search bars, etc) will reset to original after a browser restart.

Everything else (settings, themes, etc) hold my changes.

Any ideas as to why this is happening?

---

### Post by lovinglinux on 2009-09-18
> **DapperMe17 said:**
> I have Firefox 3.0 & Swiftweasel 3.5, both on the same box

Yes, they can co-exist without any issues. Keep in mind that Swiftweasel uses a different directory for storing profiles, so any settings change made on Swiftweasel will not be reflected on Firefox 3.0. 

> **DapperMe17 said:**
> I've installed Swiftweasel, which runs fine. However, for some reason, when I add or delete "add-ons" under either FIrefox or Swiftweasel, my toolbar positioning (icons, search bars, etc) will reset to original after a browser restart.

Everything else (settings, themes, etc) hold my changes.

Any ideas as to why this is happening?

I don't remember if Swiftweasel copies your Firefox profiles when you first use it, but I guess it does. That would explain why the problem is occurring on both browsers. It must have copied a corrupted profile from Firefox.

Try to delete the file **localstore.rdf** from your profiles. This should reset your toolbars. Then install or remove an add-on to see if the problem persists.

Firefox profile folder is under ~/.mozilla/firefox/ while swiftweasel is under  ~/.sw35/swiftweasel/. The profile folder is usually a bunch of random numbers/letters followed by .default, unless you have created a profile with a different name.

---

### Post by DapperMe17 on 2009-09-18
Thank you!

Yes, I see the different directories...Mozilla & SW. 

I will delete both of those files & try it again. 

I reinstalled several extensions to Swiftweasel, via a FEBE backup file that was originally created with Firefox. I guess that could have an effect. 

I'll delete those two files, then uninstall the add-ons from Swift & reinstall. 

Maybe I will delete all of Swift & start anew, without importing backup files from FEBE.

---

### Post by lovinglinux on 2009-09-18
> **DapperMe17 said:**
> I reinstalled several extensions to Swiftweasel, via a FEBE backup file that was originally created with Firefox. I guess that could have an effect.

Using FEBE should not render such problems, just because the backup was created in Firefox. I believe you already had this issue in Firefox and just replicated it to Swiftweasel by using a FEBE backup.

> **DapperMe17 said:**
> Maybe I will delete all of Swift & start anew, without importing backup files from FEBE.

When things start to go weird, that's the best remedy. I use FEBE a lot and it is usually very reliable. Nevertheless, I like to start a new profile from scratch from time to time, specially when Mozilla releases a major version of Firefox.

---

### Post by DapperMe17 on 2009-09-18
Thanks.

Yes, I deleted both .rdf files just fine...Firefox & Swift.

I then deleted the entire SW35 profile folder in my home folder just fine. 

I began to add add-ons individually, restarted & had no problems with the first couple of add-ons. 

However, I added about 4 add-ons similtaneously, then hit the "restart browser" button. Swift then closed down, but didn't restart. Of course, I could manually hit the Swift icon & the browser reappeared, but without the changes. This has happened more than once. (Swiftweasel 3.5.2) 

After closing the browser, I've noticed that is stays active as a "process". When I "kill" the process & restart the browser, my new add-ons appear, but my toolbar is reset...???

I wouldn't think I can only add "1" add-on at a time & restart after every add-on is added...I could do that fine in Firefox 3.0. Maybe I need to add one extension
at a time, then restart the browser after each one in 3.5?
Hmmm...

---

### Post by lovinglinux on 2009-09-18
> **DapperMe17 said:**
> I wouldn't think I can only add "1" add-on at a time & restart after every add-on is added...I could do that fine in Firefox 3.0. Maybe I need to add one extension
at a time, then restart the browser after each one in 3.5?

Perhaps is one of your extensions that is causing this. It makes no difference if you install one or more extensions and then restart. Well, it shouldn't make any difference.

BTW, I wouldn't recommend running 3.5.2, since there are some serious security issues on this version. Unfortunately, Swiftweasel 3.5.3 is not available yet.

---

### Post by DapperMe17 on 2009-09-18
I hear you, about multiple extensions. 

Just uninstalled Firefox 3 & deleted the profile as well.

Then, I went back into Swift & deleted one add-on, then restarted browser. Toolbar was reset again. 

Yes, I can go through the extensions one-by-one. 

Would it be better to use Firefox 3.5.3 rebrand in the repository & just manually adjust the about:config settings?

---

### Post by lovinglinux on 2009-09-18
> **DapperMe17 said:**
> Would it be better to use Firefox 3.5.3 rebrand in the repository & just manually adjust the about:config settings?

Yes it would be better in regard to security, but then you loose the benefit of the optimizations provided by Swiftweasel.

I like to compile Firefox myself with the same optimizations as Swiftweasel, but I'm unable to compile 3.5.3 for some reason, so I'm using the one from Mozilla instead, while 3.6 final version doesn't come out.

---

### Post by DapperMe17 on 2009-09-18
Definitely consider 3.5.3 from Mozilla. I may install Ubuntuzilla as well.

I noticed that "Tor button" was a know conflict with Firefox. I uninstalled it & "seem" to have solved the issue. 

I have the cutting edge repository for Firefox - rebrands. There is a 3.5 & 3.6. 

Not sure if that is the same as 3.5.3 from Mozilla, so will go and investigate a bit. 

Thanks for taking the time to clear up a few things for me!

---

### Post by DapperMe17 on 2009-09-18
I also didn't suspect FEBE...it HAS been a really good extension. 

Tor button worked well for me in Firefox 3.0...not playing well with 3.5 I guess. I'll have to find another proxy extension.

I'll check out Shiretoko....

---

### Post by lovinglinux on 2009-09-18
I'm using Ubuntuzilla right now. It works like a charm, although I'm looking forward to see 3.6 final version, since 3.6.1a is really fast. It has a great performance, even when playing flash videos. Its faster than Swiftweasel 3.5.2 ;)

---

### Post by DapperMe17 on 2009-09-18
Always good to have a faster browser:)

Just installed Ubuntuzilla & ran the terminal script for install & auto update. Great deal for those of us running Hardy LTS. The best way to set up the relatives with.

I still like the idea of Swiftweasel & wonder if the security issues are galant enough to worry about for now, or is it best to run with Firefox 3.5.3?

---

### Post by lovinglinux on 2009-09-18
> **DapperMe17 said:**
> I still like the idea of Swiftweasel & wonder if the security issues are galant enough to worry about for now, or is it best to run with Firefox 3.5.3

[http://www.mozilla.com/en-US/firefox/3.5.3/releasenotes/](http://www.mozilla.com/en-US/firefox/3.5.3/releasenotes/)

---

