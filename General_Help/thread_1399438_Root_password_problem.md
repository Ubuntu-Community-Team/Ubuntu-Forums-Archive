---
title: "Root password problem"
date: 2010-02-05
forum: General Help
---

### Post by bamdl001 on 2010-02-05
Hi everyone

After finally figuring out how to bring up a terminal window in Karmic Koala (obviously a new user) to attempt configure a nVidia issue, it asked for a root password.. I have no idea what the root password is. Is it a generic password or some Linux command???? Could some help with this please.

Cheers :)

---

### Post by llawwehttam on 2010-02-05
erm, did you run the command with sudo? The root is like a super administrator that can do anything but no-body uses it in ubuntu unless they are superusers or administrators.

---

### Post by NertSkull on 2010-02-05
I'm pretty sure the root password should be the same password of the primary account.  The account you set up linux with, unless you've changed things, try that.

---

### Post by bamdl001 on 2010-02-05
Thaks for the reply... The only reason I went to the terminal is to try and fix my screen resolution issue. I got the info from a forum. My screen resolution resets itself each time I boot up. I set it to 1200x780 with 60Hz refresh rate and when I fire up the PC it's back to the highest setting with Auto refresh rate again... very puzzling!!!
 
Thanks

---

### Post by bamdl001 on 2010-02-06
> **NertSkull said:**
> I'm pretty sure the root password should be the same password of the primary account.  The account you set up linux with, unless you've changed things, try that.

Yeah, that's what I thought but it didn't make any difference, said password was invalid?? and I know I didn't change the password coz I have to use it to log in.

---

### Post by ppb1701 on 2010-02-06
you should be able to set the password for root as you if you use sudo passwd root.
you'll get sudo pw prompt then ask for new pw and  confirm
had to do that to get vpn in running for work.

---

### Post by bamdl001 on 2010-02-06
> **ppb1701 said:**
> you should be able to set the password for root as you if you use sudo passwd root.
you'll get sudo pw prompt then ask for new pw and  confirm
had to do that to get vpn in running for work.

Thanks for all the help, but your talking to a novice so one step at a time... are you saying that at the prompt I need to type in sudo pw prompt "or" new pw?? sorry you will have to show me what to actually type. Sorry about this

Cheers

---

### Post by ppb1701 on 2010-02-06
> **bamdl001 said:**
> Thanks for all the help, but your talking to a novice so one step at a time... are you saying that at the prompt I need to type in sudo pw prompt "or" new pw?? sorry you will have to show me what to actually type. Sorry about this

Cheers
no worries, the command is
sudo passwd root

type it in a terminal, that will ask you for your username's password, then prompt  for a new password for root and then to confirm it.

replace root for another username to do the same to it.

then use the pw you gave it at the nvidia prompt

---

### Post by mushwars on 2010-02-06
> **ppb1701 said:**
> no worries, the command is
sudo passwd root
was just about to post that. 

for some reason ubuntu has a scrambled root password.

---

### Post by bamdl001 on 2010-02-06
> **llawwehttam said:**
> erm, did you run the command with sudo? The root is like a super administrator that can do anything but no-body uses it in ubuntu unless they are superusers or administrators.

I took your advice and went to the link you posted here and read your article "Linus is NOT Windows" I couldn't agree more. In fact I did come to Linux with an open mind even after being a Windows user for years. I knew always kept in the back of my mind that the change from Windows to Linux was not going to be straightforward and that there may be a huge range of issues to wade through. However, I have come away with confidence that my Linux experience will be for the better even though it may take some time to get used too. I have found that the Linux community is the most incredible bunch of people ready and willing to help with any problems that arise for newbies like me. So with this in mind I have resolved to become a Linux convert. I have been using KK 9.10 on my desktop for a couple of weeks and I've got to say "why didn't I use Linux years ago?"

Your article is most informative and brings reality into the picture. Thanks!

Cheers

---

