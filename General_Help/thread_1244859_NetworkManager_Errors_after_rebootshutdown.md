---
title: "NetworkManager Errors after reboot/shutdown"
date: 2009-08-19
forum: General Help
---

### Post by TheGames on 2009-08-19
Hello guys..

I installed Ubuntu 8.04.3 today. I noticed though that whenever I reboot or shutdown, it shows a bunch of NetworkManager errors. I saw NetworkManager errors when I shutdown after running the LiveCD as well. My Internet is working well and I'm connected to a wireless router.

Here is a picture of the errors:

[img]http://img29.imageshack.us/img29/8788/imgubuntu.jpg[/img]

**Is this a serious issue? What is causing these errors and how do I fix it?**

---

### Post by Zeroangel on 2009-08-19
It may look unsightly, but it's no big deal, really.

---

### Post by TheGames on 2009-08-20
> **Zeroangel said:**
> It may look unsightly, but it's no big deal, really.
Can you please explain why it's not big a deal? I appreciate it.:)

---

### Post by kibster on 2009-08-20
Upon install of the upgrade 8.04 to 9.? went well but I noticed a couple weeks ago that I have the same error... Only one line pops up  I think it says something about a script error... I went looking for the answer and found one...and it seemed complicated and i figured if it blows...the famous one liner ..... Re-install

which I'm thinking of doing anyways....I dont have any real problems other than that and once awhile it acts goofy...Ahh the browser closes and a few other things more annoying than anything and it doesnt do it all the time.. That was why I was going to reload it... 

My biggest compliant is that when I shut down I get Beeps like crazy
sometimes one  sometimes 5, 6, 7 beeps... Now that upsets me.

---

### Post by TheGames on 2009-08-21
*bump*
Can someone please tell me why I should ignore these errors? :confused:
Thank you

---

### Post by bchurchill on 2009-08-22
If it's not causing any problems before shutdown, I wouldn't worry about it in general.  However, if you're paranoid, you can replace NetworkManager with wicd.  Many, many people like wicd much more.

---

### Post by Zeroangel on 2009-08-22
Well, it looks like two different things are trying to manage your wireless card. One of them is complaining because the other one shut it down first.

But, nothing bad will happen -- because a wireless adapter isnt like a hard drive. Nothing bad happens if its shutdown improperly. -- Well the worst that will happen is that the AP that its connecting to might think that computer is still online for a little while, but thats about it.

---

