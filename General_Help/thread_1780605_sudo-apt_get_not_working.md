---
title: "sudo-apt get not working"
date: 2011-06-12
forum: General Help
---

### Post by vanspud on 2011-06-12
Hi,

I recently installed Ubuntu 11.04 on an old Sony Vaio laptop. I was following some of the steps here....

[http://www.techdrivein.com/2011/04/12-things-i-did-after-installing-new.html](http://www.techdrivein.com/2011/04/12-things-i-did-after-installing-new.html)

The step "**Enable Full DVD Playback(Dual Layer DVD Support)**" did not finish correctly doh and now I can't use 'sudo apt-get' for anything or the software center or using the 'Update Manager' does not work.

The update manger says it may be caused by an update not finishing correctly which sounds correct as explained above. The apt-get command gives me back the following....

'Could not get lock /var/lib/dpkg/lock resource temporarily unavailable'
'unable to lock administration directory /var/lib/dpkg is another process using it?'

Is there a way for me to fix this? I tried the obvious restart but that hasn't worked. Any advice/ help is greatly appreciated. Thanks.

---

### Post by Toz on 2011-06-12
> 'Could not get lock /var/lib/dpkg/lock resource temporarily unavailable'
'unable to lock administration directory /var/lib/dpkg is another process using it?'

There is another process/program running that is connected to the database. Do you have update manager running? Is there a terminal window open with another apt-get process running?

---

### Post by Robbinski12 on 2011-06-12
If you're not running any other installation programs, you could just delete the lock yourself using the terminal and rm-command.

EDIT: execute 'man rm' for more info on the rm-command

---

### Post by vanspud on 2011-06-12
Thanks for reply guys.

I turned off laptop and turned it on again so nothing else is running.

I ran 'sudo dpkg --configure -a' and it got it working again, but whenever I try install anything it gets stuck on the screenshot and I am unable to get past it/ press anything. This is what originally stopped the process too.

---

### Post by vanspud on 2011-06-12
Ok this is major problem for me now. I thought I could work around it but I get that screenshot on everything I try install now. Just tried installing 'subversion', it starts working/ downloading, then that screenshot pops up and I can't do anything.

Please help!

---

### Post by Rocket2DMn on 2011-06-12
That screenshot is just prompting you for some configuration.  Press TAB until OK is highlighted and click Enter to navigate through that screen and any following ones.  Default configuration is probably fine if more screens like that pop up.

---

### Post by vanspud on 2011-06-12
ah, excellent!

That worked, thanks a million rocket2Dmn!!

---

