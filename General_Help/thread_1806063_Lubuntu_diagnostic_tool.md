---
title: "Lubuntu diagnostic tool?"
date: 2011-07-17
forum: General Help
---

### Post by hoodlum77 on 2011-07-17
Hold on, hold on, it's not that easy. I'm a Linux noob using the Lubuntu for a few days. Long story short: stupid me started playing around with chmod to get a specific folder password protected. /home is involved.

It ended up with cleared desktop and basically no access to the whole system... and then me using bunch of solutions. 

One of the solutions ([link]("http://ubuntuforums.org/showpost.php?p=6138880&postcount=1")) worked and it all seems fine now, just like it was before. 

But now I'm wondering ... it was really a mess what I did. Maybe it looks ok now, but inside the system it really isn't...

So I have two pretty simple questions:

1. Is there some diagnostic tool for ubuntu or a way to check if everything is fine, secure and healthy?

2. Not much connected, but do you have some guide on how to reinstall/install ubuntu? In my case I have Windows + Lubuntu and maybe in the future (specially if I screw the system up) would like to have Windows + Ubuntu. Some step by step guide would help.

Well, thanks!


[SIZE="1"]
FULL STORY [not "a must" I guess]
It all started when I wanted to protect one of my folders with a password. I searched a bit and found that "chmod 700" command should work with this. So I tried it a couple times - didn't work. Well, I gave my final try and rebooted. 

The blue screen showed up saying that lubuntu was checking if everything is all right with my drives. 

My typical paranoia started to work so when the checking proccess finished I quickly checked the chmod command on Google (after the fact - stupid me). There were some stuff about not using the chmod command on /home ... which I did. So I started to be impulsive and even though I didn't know if something was wrong (lubuntu test was alright I guess) I started to use some solutions (mostly from this forum & legit people) and type even more commands. 

After the reboot ... well, my lubuntu desktop got totally cleared, nothing really worked and I couldn't open (through File Manager) /home/myusername cause it gave me an error saying "Access denied". 

So once again I landed on forums, using some commands through CTRL+ALT+F1 . I tried to do it one by one, like 1 solution > reboot > check. I'm sure that those solutions were coming from a legit people, but it didn't really work. I decided it's a time for a last try. I've used this: [link]("http://ubuntuforums.org/showpost.php?p=6138880&postcount=1") > reboot. Amazing, but after all this mess, it worked. My desktop is back, everything look and work just like before the accident. But it was really a chaotic proccess, it seems ok now but maybe inside the system it isn't. That's why I have 2 questions [check above][/SIZE]

---

### Post by SteveDee on 2011-07-18
> **hoodlum77 said:**
> 

2. ...but do you have some guide on how to reinstall/install ubuntu?....


You might find this useful: [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

