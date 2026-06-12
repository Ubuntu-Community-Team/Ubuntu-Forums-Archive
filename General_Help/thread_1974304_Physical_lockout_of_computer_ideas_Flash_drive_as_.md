---
title: "Physical lockout of computer ideas? Flash drive as a key?"
date: 2012-05-05
forum: General Help
---

### Post by jamesbeat on 2012-05-05
I'm trying to come up with a way to lock out a computer unless there is a physical key present.
I thought of a key switch in series with the power button, but I thought maybe a flash drive with something essential on it might be more elegant.

My wife caught our ten year old son playing Club Penguin on his computer way after bedtime, so (besides grounding the little tyke) I thought that it might be a good idea to have a way if mechanically preventing him from using his computer if we need to.
He used to have a laptop, so it was easy to simply confiscate it, but he now has a tower.

I thought of simply confiscating the mouse, but (apart from thinking it's a good idea to play Ckub Penguin at 1am) he's a smart kid and would get around that problem.

Is there a way to set the machine up so that it can't boot without a flash drive containing some key files, short of using the flash drive to actually hold the entire OS?

It's important that he is able to boot the machine on his own, so simply using a login password won't do the trick

I'm open to other ideas too, there are probably loads of ingenious ways of accomplishing this...

---

### Post by zombifier25 on 2012-05-05
(your son better not know that this thread exists :P )
You can set a BIOS password. That way the computer is locked **the moment the power key is pressed**. Just enter the BIOS config and set it.
Of course, if your son is techie enough, he can remove the CMOS battery and the password is wiped. However, it's a very challenging task (it may not even be possible on certain mainboard). If you're still paranoid, lock the CPU case. BUT, some BIOS has this darned default password, which works no matter what password is set in your BIOS. Better hope your son doesn't know this.
But the most effective way is lock the Power Key, preventing the computer from being turned on in the first place.

---

### Post by cryptotheslow on 2012-05-05
You can encrypt his home directory or the entire ubuntu partitions and put the keyfile on a USB key or other removable storage device. They would be unmountable without the physical key.

I found an archive thread discussing it here: [http://ubuntuforums.org/archive/index.php/t-1552192.html](http://ubuntuforums.org/archive/index.php/t-1552192.html)

That said, I think you are fighting a losing battle on that road in this scenario - no amount of encryption and requisite keys on removable things is going to stop him booting the machine if he has physical access to it. He just needs to create a bootable USB, CD, DVD etc. and the plan fails. Don't underestimate a curious 10 year old's ability to find these solutions, it's only a quick search away.

Only real answer is to preclude physical access to the hardware or time related power removal from the tyke's room.

Another totally off-topic suggestion - rather than try to bar this activity outright by draconian means, perhaps you should encourage it into more productive channels that suit his inquisitivity....  introduce him to simple programming stuff. See if you can get hold of a Pi and sit down together and get it to do something useful. Who knows, he might me graduating at 14 and go on to be the next big genius. :D Deflection of attention rather than outright parental NO can be a good strategy ;)

---

### Post by jamesbeat on 2012-05-05
I did think of passwords, but as I say, I'd rather him be able to use the computer on his own without me or my wife having to authorize it, but I'd like to arrange things so we can take the computer away if necessary.

I'll put a key switch on the machine if it's going to be too difficult to do it with a flash drive, but I think the flash drive method would be cooler :D

---

### Post by billyseth on 2012-05-05
There is an article here

[http://linuxconfig.org/linux-authentication-login-with-usb-device](http://linuxconfig.org/linux-authentication-login-with-usb-device)

explaining how to set up a USB key, and some different things you could do with it

---

### Post by jamesbeat on 2012-05-05
I quite agree about the method being draconian, but sometimes a kid just needs to be grounded the old fashioned way.
He's actually a very good kid, and my expectation is that if he knows I can take his computer away easily, I'll never have to actually do it!

I'm already giving him what I hope is a good grounding in IT. 
The computer in question was built by him (well, I took it apart and presented it to him in pieces.
He assembled the machine with my guidance, and he knows what each of the components is and does.
He installed the OS himself too, and I've also guided him through some command line stuff.

I grew up in the age of the home micro, and it saddens me that kids don't have to learn any computer science in order to use a computer nowadays.

I'm already on the mailing list for the Raspberry Pi. I'm pretty excited about the hardware, but I'm much more excited about the programming culture that will hopefully spring up around it.

---

### Post by eanema on 2012-05-05
If your looking to take away computer privileges then I would suggest that you look into a removable hard drive bay.
for example: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6256819&CatId=285](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6256819&CatId=285)

This way if the little guy decides to sneak in an extra hour of screen time you can just yoink his hard drive.

Of course there is always the ability to run off USB or CD but still, your definitely not making it easy...

---

### Post by jamesbeat on 2012-05-05
> **billyseth said:**
> There is an article here

[http://linuxconfig.org/linux-authentication-login-with-usb-device](http://linuxconfig.org/linux-authentication-login-with-usb-device)

explaining how to set up a USB key, and some different things you could do with it

Thank you, that is EXACTLY what I had in mind!

I'm going to call this one solved! :D

---

### Post by eanema on 2012-05-05
and if you really want to get low tech, just take away the power cord... no electricity = no game time

---

### Post by billyseth on 2012-05-05
awesome, glad we could help!

---

### Post by cryptotheslow on 2012-05-05
IMO - you can't just plop a 10 y/o in front of an internet connected computer and leave them to it unsupervised. In that scenario, curfew times are irrelevant, "bad" stuff won't respect your imposed son's curfews.

Actually that is getting way O/T and not what you asked at all.

You need to stop the tyke powering up out of hours. Get an electrician to put his room on a separate ring and pull the RCB for that ring when going to bed.

Doesn't stop him creeping out and plugging in an extension lead to the landing socket of course... kids are devious like that.

Honestly I think you are more dealing with a precocious child behaviour thing than a tech related one. So you are looking for a solution in the wrong place.

If you really want to go old school on it - catch him out again and sell his desktop as punishment and leave him with nothing tech wise for a month or two.

Your choice which road to go as the dad :)

---

### Post by jonnyboysmithy on 2012-05-06
When I decide that the boys play too much computer on my tower pc I just take the ram out of the machine. If we didn't have extra powercords I'd taking them instead. You could take the monitor cable? or the harddrive cable. Typically when mum is upset at how much the boys are on the computer she just walks away with the monitor. ;)

---

### Post by jonnyboysmithy on 2012-05-06
> **cryptotheslow said:**
> IMO - **you can't just plop a 10 y/o in front of an internet connected computer and leave them to it unsupervised.** In that scenario, curfew times are irrelevant, "bad" stuff won't respect your imposed son's curfews.

Actually that is getting way O/T and not what you asked at all.

You need to stop the tyke powering up out of hours. Get an electrician to put his room on a separate ring and pull the RCB for that ring when going to bed.

Doesn't stop him creeping out and plugging in an extension lead to the landing socket of course... kids are devious like that.

**Honestly I think you are more dealing with a precocious child behaviour thing than a tech related one. So you are looking for a solution in the wrong place.**

If you really want to go old school on it - catch him out again and sell his desktop as punishment and leave him with nothing tech wise for a month or two.

Your choice which road to go as the dad :)Thumbs up to that.

---

### Post by jamesbeat on 2012-05-06
He's not allowed unrestricted, unsupervised internet access.
He's allowed on about five sites on his bedroom computer (Club Penguin et al.) and only with his door open so we can see what's on his screen, which is a 40" TV. He knows that if he visits other sites on that machine, or tampers with the history, he loses the computer permanently. Parental controls are installed and activated.
I've shown him that I can ftp into the router at any time and see what site he's on, and what sites he's been on.
If he wants to visit any sites not on the list, he must do it on my laptop in the living room under close scrutiny.

Thanks for the unsolicited parenting advice though.

---

### Post by iranai on 2012-05-06
In case somebody wants yet again a different idea, this is what my dad did to us children on our TV. Our old CRT type TV didn't have a removable cable, so first hide all the extra power cables you have. Cut the power cable in the middle and install a key switch there.  Remove the key at night or when he's in trouble/grounded/procrastinates on taking a bath/homework etc.

---

