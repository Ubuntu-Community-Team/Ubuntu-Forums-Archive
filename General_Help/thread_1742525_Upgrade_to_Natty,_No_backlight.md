---
title: "Upgrade to Natty, No backlight"
date: 2011-04-28
forum: General Help
---

### Post by Dipper on 2011-04-28
The title says it all.  I am using an Acer Aspire laptop that I upgraded from 10.10 to 11.04 today.  There is no backlight.

What's the fix?

---

### Post by Dipper on 2011-04-29
bump........

---

### Post by Dipper on 2011-04-29
........bump.............

---

### Post by Dipper on 2011-04-29
I'm sure I'm not the only one with this problem.  Using Acer Aspire 5734Z laptop.

---

### Post by Dipper on 2011-04-29
...............bump..................

---

### Post by mörgæs on 2011-04-29
Your bumping is not welcome. 

There is a lot to do in the fora these days answering questions. Please write ONCE and wait for someone to find your post.

---

### Post by docmark777 on 2011-04-29
There were numerous people complaining of the backlight problem with beta 2 and nothing was done about it. 

Now there are thousands of people staring at black laptop screens and all that can be done is ridicule someone for bumping.  

Remember, his computer no longer works due to the upgrade and he is having to use another computer every time he wants to check to see if someone responded--so, for those of us who have no idea how to fix the problem--maybe you could spend less time attacking the bumper and more time attacking the problem.

---

### Post by wgarcia on 2011-04-30
Same thing could be said on your reply, docmark777, and on mine before I say this:

This seems to be a problem with the 2.6.38 kernel, I've seen two suggestions (I haven't tried them as I don't have this problem):

1) start with an older kernel if you have it available at the grub menu (if you don't see the grub menu when you start the computer press shift right after the initial BIOS messages at start-up).

2) if at least you can see something to open a terminal and type, give the following command at a terminal:

sudo setpci -s 00:02.0 F4.B-0

If it works there is a way to make it run at start-up so that this does not need to be typed every time at start up.

---

### Post by Dipper on 2011-06-11
> **wgarcia said:**
> 

2) if at least you can see something to open a terminal and type, give the following command at a terminal:

sudo setpci -s 00:02.0 F4.B-0

If it works there is a way to make it run at start-up so that this does not need to be typed every time at start up.

I've seen this posted a few times.  And everyone seems to say that that command can be run automatically everytime at startup, but no one has ever explained how to do that. A step by step would be great, starting with how to get to the terminal on startup.  My expertise level is "user", not IT. Thanks.

---

### Post by linuxinstalledfromhdd on 2011-06-11
What is this on your sig abotu Startup Disk Creator? 

It doesn't format all drives..  only the one you select.   I would change that sig if you want to be accurate. Don't blame Ubuntu for everything you do wrong.

---

### Post by Dipper on 2011-06-14
> **linuxinstalledfromhdd said:**
> What is this on your sig abotu Startup Disk Creator? 

It doesn't format all drives..  only the one you select.   I would change that sig if you want to be accurate. Don't blame Ubuntu for everything you do wrong.

It DOES format all drives.  I selected the drive that was to be formatted and it formatted everything that was connected. I lost a lot of data and it was if my house burned down. I will change the signature when I am satisfied that the problem is resolved.

What does this have to do with my question?  What are the steps to make "sudo setpci -s 00:02.0 F4.B-0" permanent?  I am sure I am not the only Acer Aspire 5734Z user who would like to be able to upgrade to Natty (if for no other reason than to stop seeing that annoying upgrade nag every time I boot my machine).  I tried Natty but had to downgrade to Maverick because this bug is a show stopper. But Maverick will not be supported forever.

It seems that the Ubuntu team places the importance of the predictable 6-month release cycle over the importance of releasing something that doesn't contain these kind of bugs.  This is an issue that was reported during the beta testing phase (as it should have been) and wasn't corrected by the time of the official release. The release should have been delayed if there were bugs of this magnitude still unresolved.

---

### Post by euchrid on 2011-06-15
I have an Acer Aspire 5336, and just managed to fix this issue (well, sort of) yesterday. Following the advice in this thread:
[http://ubuntuforums.org/showthread.php?p=10943621](http://ubuntuforums.org/showthread.php?p=10943621)
got my backlight working on every boot. 

glococo's post is a good step-by-step, and nicely simple.

My post in the above thread allows the backlight to be re-activated after the screen turns itself off (or powers down or whatever it does), by using a keyboard shortcut.

These are only workarounds, though, and are far from satisfactory. It would seem that this is a kernel problem, but if it isn't, someone needs to look at it, because it potentially renders many computers unusable. Many users would assume hardware failure, or, like me, might assume it was a driver problem or brightness issue. 

I am guessing that there are several misdiagnosed issues out there that might actually turn out to be this backlight problem instead.

---

### Post by Dipper on 2011-07-03
I can't believe we are halfway into the Natty life cycle and there is still no fix for this MAJOR issue.  Come October when Oneiric is released, Maverick will no longer be supported and Acer users will be high and dry. 

Come on guys, please fix this.  I know you read these threads.

---

### Post by mahmoodkamal on 2011-07-19
this is post which fixed the problem for me on acer aspire 5336:

[http://ubuntuforums.org/showthread.php?t=1742352](http://ubuntuforums.org/showthread.php?t=1742352)

Although now i have to press Fn+brightness key just once and then everything is fine.

---

