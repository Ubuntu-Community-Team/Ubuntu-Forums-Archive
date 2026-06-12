---
title: "VMWare stopped working"
date: 2006-03-16
forum: General Help
---

### Post by bender unit on 2006-03-16
Hello folks,

I have a strange problem: my installation of VMware stopped working a few days ago and I have no idea what could have caused this. Now, when I try to run either VMWare or the VMPlayer, both programs just freeze right after starting up. There's nothing I can do other than killing the programs. When I run either of them from gnome-terminal, I get the following message:

```

/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
*** attempt to put segment in horiz list twice

```

I remember there was a kernel upgrade recently, but running vmware-config.pl again doesn't make any difference at all. Now what can I do to fix this problem? So far I've found no answer in the forums...

Update: ok, sorry, I've searched with the wrong terms. Now I've found some posts about the same issue, but none of the contained a solution to the problem. Running vmware-config.pl with CC=/usr/bin/gcc-3.4 doesn't do the trick. Also, other than in the posts I've found, VMware (at least the player) was working before on my machine. It just suddently doesn't work anymore, and there's nothing I can do about it. Reinstallation didn't help, either. Any more ideas?

---

### Post by joshuapurcell on 2006-03-16
Do you get any errors or other messages when running vmware-config.pl? This file should be run after using a different kernel like you are attempting to do, but it should give some feedback as well.

---

### Post by bender unit on 2006-03-17
Well, I'm not at home right now so I can't say exactly what the output was, but AFAIR it went through everything normally. I didn't abort at some point with an error message, if that's what you mean. And it was also able to load the kernel module, saying "the module loads perfectly into the running kernel" and restarted the /etc/init.d/vmware script without problems. So I don't think it has to do with broken kernel modules. And like I said, I tried running vmware-config.pl with both gcc 4.0 and 3.4, and both times I get the same error. Rebooting inbetween these steps didn't help, either.

Any other ideas?

---

### Post by bender unit on 2006-03-21
Ok, dunno if anyone is interested in this at all, because obviously I'm getting no answers, but I'll post this now anyways, since I've found a solution and there were other posts about the same issue, too, none of which contained any solutions.

So, the first solution I've found in the official VMware forums. If you have the same issue as I have, you can just run "VMWARE_USE_SHIPPED_GTK=force vmware" (or vmplayer) and it'll work (at least it does for me). Problem with that, though, is that it doesn't use your GTK2 theme anymore but the default ugly gray one.

The other solution is even simpler (and almost obvious, but I just discovered it this very moment): the problem seems to be SCIM (again!). If you run SCIM, VMware will just crash on you. (Or at least that's what I think because the only big change I made was installing SCIM and it causes problems with other apps, too). Well, the solution is the same as for the other non-working programs: just run "GTK_IM_MODULE=xim vmware" and the problem is gone!

Hope someone can use this information!

---

### Post by xavierh on 2006-03-21
What version of VMWare you are running? Try runnign the vmware-any-any patch to configure the vmwware. also make sure that you have the appropriate permissions to run it.

---

### Post by bender unit on 2006-03-21
[QUOTE=xavierh]What version of VMWare you are running? Try runnign the vmware-any-any patch to configure the vmwware. also make sure that you have the appropriate permissions to run it.[/QUOTE]
Hm? Didn't you read my last post? I've got the problem solved already. And BTW, I read that this vmware-any-any was only needed for versions up to 5.0 and it's discouraged to use it with 5.5 and higher (or doesn't even work at all).

---

### Post by Hellaxe on 2006-03-29
Try this one. It works for me always after the kernel is upgraded.
```
EDIT TO ADD: I forgot that you have to set the CC variable to the gcc version you want to use: Code:

# export CC=/usr/bin/gcc-3.4 # ./runme.pl 
```

---

### Post by antivert on 2006-06-15
Fixed my vmware problem! Thank you bender!

scim is a huge pain! ugh.

---

