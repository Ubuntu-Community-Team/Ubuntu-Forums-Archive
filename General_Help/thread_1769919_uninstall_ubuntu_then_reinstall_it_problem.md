---
title: "uninstall ubuntu then reinstall it problem"
date: 2011-05-28
forum: General Help
---

### Post by andypearce on 2011-05-28
Here is the problem.
My daughter's partner has leant me his toshiba equium laptop to get going. It has ubuntu 9.10 on it and he has not used it for a while. It gives an option to upgrade to 10.04LTS on update manager but needs an administrative password,which he has forgotten, to get it running. I also have a cd of 10.04LTS but when I try to run it, it also demands the administrative password. 
So far I have searched how to change this password and tried several suggestions through recovery mode and have attempted to change the password which I thought each time I had done. I have not managed it. In fact I have found other passwords that I thought were it and changed those to the same... no idea what they were now...It does not work for me. I think the best option would be to start again.

I know this laptop had windows xp on it originally but was effectively got rid of during the partition process at the beginning of the ubuntu installation so I assume it only has ubuntu on it. 

The question is how do I get rid of the ubuntu 9.10 that is on it and install the 10.04 LTS from the cd so I can make sure it is a clean, new intall with simple passwords.

I have been using ubuntu for a while and can do the simple stuff but really struggle with this one and the threads I have searched come from the angle that windows is on there as well, also the language/jargon used makes it all very complicated.

Anyone suggest anything?
Ta Andy

---

### Post by linuxinstalledfromhdd on 2011-05-28
[LEFT]Here is a really handy walkthrough for a fresh installation of 10.10:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

You shouldn't have any problems after that. 
[/LEFT]

---

### Post by andypearce on 2011-05-28
So you suggest I go on that page.. choose [http://ftp.ucsb.edu/pub/mirrors/linux/ubuntu/10.10/](http://ftp.ucsb.edu/pub/mirrors/linux/ubuntu/10.10/)
 then choose  ubuntu-10.10-alternate-i386.iso      07-Oct-2010 08:49  693M 
is that right? I chose the first one from that list that looked right. So if I down-load that will I then have 10.10 running... will I be able at that point to choose new administrative passwords so I can do the updates?

---

### Post by andypearce on 2011-05-28
I will go away and come back on tomorrow and see if there is a reply/suggestions.:D
thanks
Andy

---

### Post by holadebob on 2011-05-28
If you're going to use the computer as a tool instead of a challenge, I would stick with rock stable 10.04lts.

Download the 10.04 ISO file, burn it on a cd (or buy it from one of the Linux distributors) and install Ubuntu 10.04 from scratch. That's the best way. Upgrades seem to end up with iffy problems.

Download the updates, programs you want and you are on your way.

---

### Post by wildmanne39 on 2011-05-28
> **andypearce said:**
> I will go away and come back on tomorrow and see if there is a reply/suggestions.:D
thanks
AndyHi, this should help you reset the password. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by andypearce on 2011-05-29
Holadebob, thanks for that suggestion. I have got the 10.04lts cd and when I put it in it will not autorun, it tells me this and I cannot work out what to do about it.I also have the option of upgrading on update but it says the upgrade is not supported... so am a bit stuck.

Wildmanne39, thanks for the that suggestion as well. I tried this route before I posted the thread and although it appeared to work, in fact it did not, the new password does not seem to work.

If I put in a windows xp disc will I be able to delete ubuntu 9.10 from the hard drive using the partition. Then reinstall from the ubuntu 10.04 lts disc I have.... this is a stab in the dark for me.

---

### Post by Irihapeti on 2011-05-29
You should be able to boot the computer using the LTS livecd. Then you can either:

a) remove the existing partition using the partition editor or disk utility and then install

or

b) just install over the top of the existing installation and "choose entire disk" when you are asked where you want to install.

---

### Post by linuxinstalledfromhdd on 2011-05-29
> **andypearce said:**
> So you suggest I go on that page.. choose [http://ftp.ucsb.edu/pub/mirrors/linux/ubuntu/10.10/](http://ftp.ucsb.edu/pub/mirrors/linux/ubuntu/10.10/)
 then choose  ubuntu-10.10-alternate-i386.iso      07-Oct-2010 08:49  693M 
is that right? I chose the first one from that list that looked right. So if I down-load that will I then have 10.10 running... will I be able at that point to choose new administrative passwords so I can do the updates?

You can use any of those links. I suggest you download the 

ubuntu-10.10-desktop-i386.iso

Go ahead and burn that to a disc. And then boot your computer from that disc. 

There will be an icon on the desktop to install everything.  Just follow the prompts and you should be all set in a short time. 

When you are done installing Ubuntu 10.10 on your computer, go to the step-by-step walk-through guide:

[http://cinderbox.net/2010/12/23/to-d...erick-meerkat/]("http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/")

---

### Post by andypearce on 2011-05-29
Irihapeti, thanks for the suggestion. Obvious really but only if you know enough to spot the obvious so thanks again for the suggestion.:D I installed the cd over the existing ubuntu and chose to delete it when asked. All is now fine, new passwords etc.
I will mark as solved.
Hooray... 
Andy

---

### Post by Irihapeti on 2011-05-29
You're welcome. Glad it worked.

---

