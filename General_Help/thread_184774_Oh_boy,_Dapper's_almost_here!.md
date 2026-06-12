---
title: "Oh boy, Dapper's almost here!"
date: 2006-05-30
forum: General Help
---

### Post by hajk on 2006-05-30
A couple more days and I'll be replacing Breezy on my main computer for 64-bit Dapper. Been playing around with Dapper on an old computer for a while now, and all I can say is wow! Can't wait, feel like a kid on Christmas eve...

Just wanted to say hello and thank you to all of you Breezy experts who have helped me get going in Ubuntu the past half year. May be seeing some of you in the Dapper forums before long. :cool:

---

### Post by AirRaven on 2006-05-30
Why not dist-upgrade now? Why wait?

---

### Post by bruce89 on 2006-05-30
It's only 2 days, mind you when it comes out, the servers will be really slow, so maybe it would be better to upgrade now - ```
gksu "update-manager -d"
```

---

### Post by rado_london on 2006-05-30
By upgrading now you dont get the final piece of work. Many things are outstanding and I still wait for solution. So I think its worthy waiting 3 days more rather tan upgrading a RC version.

---

### Post by henriquemaia on 2006-05-30
[quote=rado_london]By upgrading now you dont get the final piece of work. Many things are outstanding and I still wait for solution. So I think its worthy waiting 3 days more rather tan upgrading a RC version.[/quote]

Even so, if we keep updating, things will be corrected through the updates. There are just small issues to iron out now, I guess.

---

### Post by Zdravko on 2006-05-30
> feel like a kid on Christmas eve
Absolutely! I can hardly wait 2 days more!

---

### Post by bruce89 on 2006-05-30
Dapper is only one command away then - ```
gksu "update-manager -d"
```

---

### Post by Zdravko on 2006-05-30
[bruce89]("http://ubuntuforums.org/member.php?u=13616"), you don't understand. The creampie tastes better when you look at it for a while.

---

### Post by hajk on 2006-05-30
Sure, I could upgrade now, but you know, it's got to be perfect this time. Also want to make a new partition table to allow me to triple boot Dapper-386, -AMD64 and some experimental version of Efty: /dev/hda{1,2,3} each 64MB ext2 for mounting the respective /boot directories; /dev/hda5 1GB swap; and /dev/hda{6,7,8} each about 80GB jfs for the respective / trees.

Yes, it will be busy at the servers Thursday, but then I'll be downloading only a torrent seed file, using the torrents to get the rest (and to give it back as well).

Oh boy!

---

### Post by Ameet on 2006-05-30
[QUOTE=bruce89]Dapper is only one command away then -
gksu "update-manager -d"[/QUOTE]

I tried this and get a dialog box stating the following:

> To run the program "update-manager -d" you need to enter the root password: _____

I entered my root password (the same one I use for sudo and synaptic manager, etc.), then get: 

> Error: Failed to run update-manager -d: Wrong password.

The first time I got a request for a "keyring" password.  I entered my root password again that time and was denied.  Subsequent times I don't even get asked for that.

What is wrong here?  I am a medium-newbie at Linux so please adjust the responses accordingly.

---

### Post by ubuntu27 on 2006-05-30
[QUOTE=hajk]A couple more days and I'll be replacing Breezy on my main computer for 64-bit Dapper. Been playing around with Dapper on an old computer for a while now, and all I can say is wow! Can't wait, feel like a kid on Christmas eve...
[/QUOTE]

[QUOTE=Zdravko]Absolutely! I can hardly wait 2 days more![/QUOTE]


\\:D/ \\:D/  Yeah, two mroe days to go! :D :D :D \\:D/ 


[QUOTE=hajk]A couple more days and I'll be replacing Breezy on my main computer for **64-bit Dapper**. Been playing around with Dapper on an old computer for a while now, and all I can say is wow! ....[/QUOTE]

Is your 64-bit Dapper Test machien working alright? 
I've always heard from many OS such as WIndows, UBuntu (and other Distros) that the 64-bit is not "ready yet" Too much problem.

---

### Post by mark2741 on 2006-05-30
I'm a newbie to Ubuntu, having installed it a few days ago. So far I feel like I have found the best OS on the planet for me. I'm using Breezy and am now intrigued with maybe moving up to Dapper, so long as it is fairly painless.

So if I just run the command mentioned: gksu "update-manager -d"

...then I'll be good to go? And updates, as they are released (Thursday and in the future) will be cumulative so that I won't always be running a pre-release version? 

Most importantly - will all of my installed packages and programs work? I just installed VmWare Server Beta last night and got WinXP running virtually (I'm down to needing only one Win app - MS Money....) and it is awesome. Will I have to reinstall that and the other apps I've installed? Or will everything just work?

---

### Post by jonnyfive on 2006-05-30
I upgraded to the beta of Dapper Drake and it seems to have given me alot of troubles, I will try updating to the official release but if the problems persist (wifi no longer works in dapper, sound issues, among others) I'm afriad I may have to give up on ubuntu on this laptop. Sadly.:confused:

---

### Post by ubuntu27 on 2006-05-30
If the upgrade fails.  You should install Dapper with a Clean Install that is using the Install CD (or Live CD) to install and overwrite your current Install (Breeezy or Broken Dapper)

---

### Post by ubuntu27 on 2006-05-30
[QUOTE=Ameet]I tried this and get a dialog box stating the following:



I entered my root password (the same one I use for sudo and synaptic manager, etc.), then get: 



The first time I got a request for a "keyring" password.  I entered my root password again that time and was denied.  Subsequent times I don't even get asked for that.

What is wrong here?  I am a medium-newbie at Linux so please adjust the responses accordingly.[/QUOTE]


Did you try to Install Dapper using the CD? :(

---

### Post by Ameet on 2006-05-30
[QUOTE=ubuntu27]Did you try to Install Dapper using the CD? :([/QUOTE]

I should clarify.  I have Breezy (5.10).  I started a terminal window.  Then I typed the text in at the command prompt.  That's when I got asked for the password and the "keyring password".  

I don't have Dapper at all, just Breezy.  I am gathering that if I run "update-manager -d" that it will upgrade me online, without needing an install CD?  Is that right?  That was my whole motivation for trying out the command.

I am having trouble burning CDs from ISOs on Breezy.  I think the last time I did that, I got a CD with a file in it with an .iso extension -- rather than the CD being burned with the mirror image itself.  So I don't know how to do that either. ](*,) 

Otherwise I can just wait 4-6 weeks till Shipit sends me a new CD of Dapper, but I'd rather not wait.

Thanks.

---

### Post by styven on 2006-05-30
[QUOTE=Ameet]
I am having trouble burning CDs from ISOs on Breezy.  I think the last time I did that, I got a CD with a file in it with an .iso extension -- rather than the CD being burned with the mirror image itself.  So I don't know how to do that either. ](*,) 

Thanks.[/QUOTE]

Hi,

Not sure which cd writing programme you are using, I use K3b to burn iso's.
On the pretext that have installed it, go to....... tools, burn cd image, browse for the iso and burn. 
If you have not insatlled it then use "sudo apt-get install k3b"

Hope that helps....steve

---

### Post by WoodyMahan on 2006-05-30
instead oof gksu use gksudo

Then it will run.

---

### Post by ubuntu27 on 2006-05-30
[QUOTE=Ameet]I should clarify.  I have Breezy (5.10).  I started a terminal window.  Then I typed the text in at the command prompt.  That's when I got asked for the password and the "keyring password".  

I don't have Dapper at all, just Breezy.  I am gathering that if I run "update-manager -d" that it will upgrade me online, without needing an install CD?  Is that right?  That was my whole motivation for trying out the command.

I am having trouble burning CDs from ISOs on Breezy.  I think the last time I did that, I got a CD with a file in it with an .iso extension -- rather than the CD being burned with the mirror image itself.  So I don't know how to do that either. ](*,) 

Otherwise I can just wait 4-6 weeks till Shipit sends me a new CD of Dapper, but I'd rather not wait.

Thanks.[/QUOTE]

About ISO Burning in Ubuntu:  Just download the iso file, right click on the iso, and select “"Write to Disc..."  and you're good to go.


----------------------------------------------------------------------------------------------

Sorry I am still a nob (two or three months using Ubuntu).

You should create a NEW thread for your problem. 

The helpful knowledgeable ones are ignoring because of the Thread title "Oh boy, Dapper's almost here!" which suggest that the thread is about people getting exited about the upcoming release, and not people wanting help.

---

### Post by Joetheodd on 2006-05-31
[QUOTE=Ameet]I tried this and get a dialog box stating the following:



I entered my root password (the same one I use for sudo and synaptic manager, etc.), then get: 



The first time I got a request for a "keyring" password.  I entered my root password again that time and was denied.  Subsequent times I don't even get asked for that.

What is wrong here?  I am a medium-newbie at Linux so please adjust the responses accordingly.[/QUOTE]

I think it wants the root password, not your sudo'er password.

Assume your password is foo and the root password you want is bar:

$ sudo passwd root
Password: foo
New UNIX password: bar
Confirm: bar
$

Then enter bar as the password.


I'm pretty psyched about dapper.. but not so psyched about the 400MB download on dial-up. But the upside to that, the servers won't seem slow to me. =)

---

