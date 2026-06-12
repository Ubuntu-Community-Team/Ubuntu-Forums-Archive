---
title: "networkin with linux and windows 7"
date: 2012-01-20
forum: General Help
---

### Post by ewaynec on 2012-01-20
OK, here is a Windows Question from a Linux user. I have a Windows 7 problem.

  I have a home network with 2 computers and 4 media devices. The media devices are Direct tv receivers. The computers are my wifes with Windows 7, mine with Windows XP and Linux (dual boot). I just had a minor catastrophe and had to re-install XP and Linux on my PC. When I got everything working, (Windows first, so the dual boot in Linux would go smoothly) Windows 7 saw the XP and said aha we want a "homegroup", so being the good W7 that does your thinking for you it set up a homegroup for the 2 Windows computers. OK now, I install Linux it sets up the network connection, and I see the Windows 7 computer, but the Windows 7 computer will not see the Linux, (because "homegroup" is windows only). If I boot to XP it will see it, and the connection is fine both ways.

  My question is how do I un-do the homegroup and get back to the mshome network. It was working with mshome before "the event".

  I know very little about Windows 7, but I love my wife, so any help would be greatly appreciated.

---

### Post by smurphy_it on 2012-01-20
I haven't used Win7 in quite some time (only have to for family members).  If it was me, I'd remove Windows off every machine in the house ;-)

Anyways, here is an article on sharing Windows 7 networking.  You should be able to change any aspect of it via control panel, networking ...

[http://www.pcworld.com/businesscenter/article/172268/a_guide_to_windows_7_networking.html]("http://www.pcworld.com/businesscenter/article/172268/a_guide_to_windows_7_networking.html")

---

### Post by ewaynec on 2012-01-20
Please, do not misunderstand me. I am not looking for a way to set up a homegroup, or shareing. I have a homegroup set up now. That is my problem, I want to get rid of it. A homegroup will ONLY allow Windows. I want 1 windows and 1 linux.

---

### Post by Mark Phelps on 2012-01-20
Actually, "homegroup" is new to, and unique to, Windows 7.  Even Vista and XP machines can't participate in a "homegroup".

The older "workgroup" is understood by all three.

---

### Post by satanselbow on 2012-01-20
Bit of a shot in the dark but: have you got your linux box in the same workgroup (/etc/samba/smb.conf). I've got a mix of OS in the house myself and it always plays nice out the box - but it is always the linux machine workgroup that causes a hiccup :D

---

### Post by Morbius1 on 2012-01-20
Setting up Win7 file sharing from a Linux Samba user's perspective:
[http://opensuse.swerdna.org/susesambawin7.html](http://opensuse.swerdna.org/susesambawin7.html)

The Linux references are all SuSE specific so I would ignore all that but the Win7 part may be of some use to you.

---

### Post by ewaynec on 2012-01-20
Mark Phelps;
  "Homegroup" is new in Window7, but it is not unique. It will work with XP, and Vista, as well as W-7, but, and a big BUT, it will not work with Linux, It only works with Windows. 
  Your mission, should you decide to accept it, is; to help me get rid of homegroup so I can set up a workgroup that I can use with with Linux.

satanselbow; I am not in a workgroup, that is the problem.

Morbius1; Shareing and naming is not a problem.

  If someone can just tell me how change the Homegroup to workgroup I can handle everything else.
  Thanks

---

### Post by stevennlv on 2012-01-20
Two links that may help:

[Microsoft]("http://windows.microsoft.com/en-US/windows7/Networking-home-computers-running-different-versions-of-Windows")

[Win7 Forums]("http://windows7forums.com/windows-7-networking/2516-homegroup-workgroup-solved-me-least.html")

You fail to mention which version of 7 that you have. If you have Ultimate or Pro then the Local Group Policy Editor is always a useful place to start for these kinds of problems. 

I have Homegroups completely turned off in the LPGE. But, if you are not familiar with the LGPE then do some reasearch before you start to play with it or you can end up making things even worse. (BTW you'll have to log directly in to the admin account on your system to use the LGPE, it will not run properly if you try to elevate permissions from inside a user account.)

If you don't have Ultimate or Pro then you can still shut off HomeGroups in a couple of ways: 

1) Control Panel / HomeGroups
2) Control Panel / Admin Tools / Services (either logged in as admin or elevated to admin) / HomeGroup Provider = disabled / Reboot.

Personally I'd do both, just to be sure.

Theoretically on reboot other networking protocols may then try to run and the problem could be just that simple to solve? But, I'm not sure. When I read about HomeGroups I disabled it as I was configuring my box and before I tried to connect to anything.

If just turning it off doesn't work then try the links above. The one from the win7 forums has a ton of trouble shooting tips in it.

---

### Post by ewaynec on 2012-01-21
stevennlv;
  That was a big help, I did get rid of "homegroup". It is now a member of "Workgroup" as is the Linux box. From the Linux I see the W-7 and can access the shared folders, but from the W-7 box I cannot see the Linux. I see all the directtv devices and they work. 

I can boot to windows XP on the Linux box and there is a both way connection, everything works as it should.

The only help in W-7 and the MS website says, just plug it in and it will work. (what do you do when magic fails?)
  Any thoughts?

---

### Post by Morbius1 on 2012-01-21
Possibilities:

[1] Services on the server (Ubuntu) aren't running.

So start them:
```
sudo service smbd start
sudo service nmbd start
```[2] Firewalls are in the way.
If you haven't done anything to your firewalls then you're fine. If you  have done something with it disable them. We can fix it later.

[3] Your hostname is too long.

Run the following command and count the number of characters:
```
hostname
```If it's 15 characters or less then you're good to  go. If it's 16 characters or more then here's how to fix it:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```In the [global] section - right under the workgroup line - add the following line:
```
netbios name = something
```[COLOR=Blue]*"something" has to be 15 characters or less in length*[/COLOR]

[4] Rearrange the order of how samba resolves names to ip addresses by  putting the only method that works by default first. Again in the  [global] section add the following line:
```
name resolve order = bcast host lmhosts wins
```After you do [3] or [4] restart the samba services:
```
sudo service smbd restart
sudo service nmbd restart
```Wait 5 minutes - no kidding - and then  see if your client can access the server's shares.

---

### Post by ewaynec on 2012-01-21
I have it working, not 100% yet but the rest is just tweaking. I want to thank stevennlv, for helping me get rid of the homegroup. Also to Morbius1, his plagiarized instructions (yes I read the article you copied it from), I figured what the hell I have tried everything else, although the instructions were for "Linux Mint". It got samba so screwed up that I had to re-install it, and that fixed it.
  So after getting the workgroup set up and re-install samba I will call this solved.
  Thanks to all for your effort

---

### Post by imachavel on 2012-01-21
> **ewaynec said:**
> Please, do not misunderstand me. I am not looking for a way to set up a homegroup, or shareing. I have a homegroup set up now. That is my problem, I want to get rid of it. A homegroup will ONLY allow Windows. I want 1 windows and 1 linux.

exactly

---

