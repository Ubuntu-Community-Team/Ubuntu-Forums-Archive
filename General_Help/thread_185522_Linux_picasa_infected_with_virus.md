---
title: "Linux picasa infected with virus?"
date: 2006-05-31
forum: General Help
---

### Post by loell on 2006-05-31
i thought i'd just tag it like tux.. for ubuntu + picasa users to know

[http://tuxmachines.org/node/7270]("http://tuxmachines.org/node/7270")

---

### Post by xinix on 2006-05-31
hmm maybe you could provide a little more info for others to see if the virus is found on their machines.  What anti-virus, any installation tricks and stuff like that.  I couldn't get Picasa to work.  All it did was load a thingy into the system tray which I guess is for digital cameras. I never got anything out of it.

---

### Post by loell on 2006-05-31
i'll just post the link of the blog

[http://web.mac.com/unicycler/iWeb/ramblings/Blog/08DE6CD1-6B83-4D33-9CFB-5EA404354397.html]("http://web.mac.com/unicycler/iWeb/ramblings/Blog/08DE6CD1-6B83-4D33-9CFB-5EA404354397.html")

apparently he installed aegis anti virus and scan his system 

then eventually aegis found w32/magistr.a@MM virus on picasa wine directory

[IMG]http://web.mac.com/unicycler/iWeb/ramblings/Images/virus%20on%20Linux.jpg[/IMG]

---

### Post by xinix on 2006-05-31
Well, I just installed Aegis-virus-scanner (from the repos) along with Picasa freshly downloaded from Google.  I have the same result.  I won't bother with a screenshot since it would be exactly like the one already posted. Considering that I've never had Windows I'm pretty sure that this came from the installer.

---

### Post by Travisty on 2006-06-01
Has anyone tried scanning with a differnt AV then aegis?

---

### Post by dmb on 2006-06-01
That is a bug in the virus system for aegis anti virus. It will report a virus also for any xulrunner for windows or seamonkey installation for windows/wine.  No need to panic. THIS IS NO VIRUS. Also, clamav reports no virus. Appshell.dll is a part of mozilla, even open source, check lxr.mozilla.org for more info.

---

### Post by wzzrd on 2006-06-02
[QUOTE=dmb]That is a bug in the virus system for aegis anti virus. It will report a virus also for any xulrunner for windows or seamonkey installation for windows/wine.  No need to panic. THIS IS NO VIRUS. Also, clamav reports no virus. Appshell.dll is a part of mozilla, even open source, check lxr.mozilla.org for more info.[/QUOTE]

I scanned with several other tools too. Check my [blog]("http://www.wzzrd.com/articles/2006/05/31/wonderful-though-inaccurate-story") for more info.

---

### Post by Travisty on 2006-06-02
That makes me fwwl better. It was bothering me to think that Google would bundle a virus into their installer. Thanx wzzrd.

---

### Post by RAV TUX on 2006-12-10
glad this is documented I was getting worried.

---

