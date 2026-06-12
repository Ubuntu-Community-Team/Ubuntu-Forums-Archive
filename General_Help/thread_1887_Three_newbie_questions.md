---
title: "Three newbie questions"
date: 2004-10-24
forum: General Help
---

### Post by Horn on 2004-10-24
I just installed ubuntu and everything seems to be working pretty well but I have a few questions.

First one is where are the gtk libraries located, or more specifically where can I find gtk-config?  I'm trying to build wxWindows and ./configure dies trying to find gtk-config.  

Is there a list of packages that I can download?  I'm coming from Gentoo which has an online searchable list and I'm wondering if theres one for Ubuntu that I missed.

Is there a way to check my CPU speed?  I'm on a laptop and its running a bit slow.  I'm wondering if the CPU is being scaled back for some reason.  Or better yet does Ubuntu have some built in CPU scaling software that is turned on by default?

Thanks!

---

### Post by beesee on 2004-10-24
[QUOTE=Horn]First one is where are the gtk libraries located, or more specifically where can I find gtk-config?  I'm trying to build wxWindows and ./configure dies trying to find gtk-config.[/QUOTE]
You're probably gonna need to install the dev package (e.g. libgtk1.2-dev)

---

### Post by Horn on 2004-10-24
[QUOTE=beesee]You're probably gonna need to install the dev package (e.g. libgtk1.2-dev)[/QUOTE]


Thanks!  I figured out how to get Synaptic to search other places which was why I couldn't find it before.  

Anyone got any answers for the others?

---

### Post by mark on 2004-10-24
[QUOTE=Horn]Thanks!  I figured out how to get Synaptic to search other places which was why I couldn't find it before.  
  
  Anyone got any answers for the others?[/QUOTE]Re: the CPU speed issue, do a search in *Synaptic* for *gkrellm* & install.  It's a comprehensive monitoring utility.

---

### Post by oddabe19 on 2004-10-25
Yeah, but how do i enable say the Xmms plugin for that? or any of the other ones for that matter, I've never used gkrellm before.

---

### Post by shufla on 2004-10-25
Hello,

[QUOTE=Horn]I just installed ubuntu and everything seems to be working pretty well but I have a few questions.[/quote]

Great :)

[QUOTE=Horn]
First one is where are the gtk libraries located, or more specifically where can I find gtk-config?  I'm trying to build wxWindows and ./configure dies trying to find gtk-config. 
[/QUOTE]

Well, I'd like to inform you that wxwindows libraries, -dev files, and other usefull tools are in `universe' repository. You can enable it in synaptic, then push 'Refresh' button.

If you need any application first try `universe' repo, than `multiverse'. They are not supported by Ubuntu, but they works fine - I suppose better, that installing it from sources. :)

[QUOTE=Horn]
Is there a list of packages that I can download?  I'm coming from Gentoo which has an online searchable list and I'm wondering if theres one for Ubuntu that I missed.
[/QUOTE]

Huh... Repositories can be searched by Synaptic or command line tools like apt-cache. Try man apt-cache - it is very nice tool. Searches in Synaptic aren't powerfull, but usefull.

Best regads,
Lukasz Nowak

---

### Post by oddabe19 on 2004-10-25
[QUOTE=oddabe19]Yeah, but how do i enable say the Xmms plugin for that? or any of the other ones for that matter, I've never used gkrellm before.[/QUOTE]

Noone?

---

