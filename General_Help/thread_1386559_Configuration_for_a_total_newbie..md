---
title: "Configuration for a total newbie."
date: 2010-01-20
forum: General Help
---

### Post by rhynes on 2010-01-20
I'm not the newbie but my mother is asking for another computer and the timing is great to introduce her to linux - very basic user on internet, email and the occasional word doc. I'm getting tired of repairing her XP OS and removing the occasional virus she gets. 

Running karmic 9.10.

Trying to configure the box for as little change as possible - and I know the desktop switching feature will freak her out. How can I lock it so there is only one desktop? I know there will be a finger slip and she'll be calling me about her programs disappearing. Not so easy to explain over the phone with her. 

Anything else I should be doing to it that anyone can think of? She's on the other side of the country so deskside support is out of the question. She's not one to play with settings and will always call first.

I'm sure there's alot of her friends that will make the switch to ubuntu once they see it :D I love ubuntu personally and i'm sure she's going to as well.

 
Thanks.

Rob.

---

### Post by drpjkurian on 2010-01-20
Hi
Try ubuntu with default Gnome desktop. Put the launchers for her regular programmes like mozilla and open office in desktop. Switching of the desktop should never be a problem.

---

### Post by rhynes on 2010-01-20
Yeah, I have all the launchers on the desktop. Just hoping i'm not forgetting anything as it's being shipped tomorrow.

---

### Post by hemimaniac on 2010-01-20
"How can I lock it so there is only one desktop?"

in 9.04 in the simple compiz settings there was settings there pertaining to the "desktop wall/cube"

if they still there you can turn that all the way down to 1 then lock it up

---

### Post by dr_alejandro on 2010-01-20
To have only one desktop you can right click on the Workspace Switcher, select preferences and set it to one row and on column (instead of the default 4 workspaces (2x2)).

---

### Post by jamesisin on 2010-01-20
As to your question, dr_alejandro has it exactly correct.  I just wanted to say that you should look into desktop support options as well.  It'll be easier and safer for you to support this machine from afar than any Windows box.  You could ssh into the machine and run updates for her, even while she is on the box.

---

### Post by rogue_0111 on 2010-01-20
As for your tech support issues how about [logmein.com]("https://secure.logmein.com/US/labs/") with their new linux browser plugin.

Good luck

---

### Post by hemimaniac on 2010-01-24
for you support, in addition to logmein i came across [whizhelp]("http://www.wizhelp.com") , it has worked flawless for me so far.

---

### Post by efflandt on 2010-01-26
But is there anything like logmein or whizhelp for 64-bit Linux client (both of those are i386).  Actually whizhelp does not list anything for Win7, so that would not help me help a friend anyway.

I tried --force-architecture install of logmein-client and adding it to nspluginwrapper used for 32-bit flashplugin, and it sort of half worked.  64-bit Firefox then recognized it as a plugin, and when I tried to connect it came up with the menus on the left, but the desktop was blank white and mouse movements did not happen on the remote.  So maybe it needs something else 32-bit (like java?).

The logmein-client did work fine in 32-bit Ubuntu 9.10.

---

### Post by jamesisin on 2010-01-26
I suppose you could keep a 32 bit VM around for just that purpose.

---

### Post by hemimaniac on 2010-01-26
> **efflandt said:**
> But is there anything like logmein or whizhelp for 64-bit Linux client (both of those are i386).  Actually whizhelp does not list anything for Win7, so that would not help me help a friend anyway.

I tried --force-architecture install of logmein-client and adding it to nspluginwrapper used for 32-bit flashplugin, and it sort of half worked.  64-bit Firefox then recognized it as a plugin, and when I tried to connect it came up with the menus on the left, but the desktop was blank white and mouse movements did not happen on the remote.  So maybe it needs something else 32-bit (like java?).

The logmein-client did work fine in 32-bit Ubuntu 9.10.

wiz help will pretty much run anywhere there is java, i have used it on many os's that aren't listed on their page, also on the home page of wizhelp, it informs you that it will likely fail on first run in linux, also i found 64 bit java will fail more often then work in FF so [here ]("http://www.psychocats.net/ubuntu/nonfree")is a fix for that.

---

