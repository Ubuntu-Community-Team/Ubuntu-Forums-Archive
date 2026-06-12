---
title: "Add account in Thunderbird Shredder"
date: 2009-12-17
forum: General Help
---

### Post by DeMus on 2009-12-17
I just added a PPA in my sources list and installed Thunderbird 3, codename Shredder.
How can I set up my Gmail mailaccount and import all my mail, Addressbook and settings?
When I try to create an account, in the window next to my username I see this rotating symbol and that's it. Nothing happens. And believe me I tried it several times, and also waited a very long time to see if anything would happen.

How hard can it be to add an account? Happily Vs 2 is still functioning so I think I will stick to that. Once again: New is not always better.

---

### Post by scouser73 on 2009-12-17
Hi DeMus, I'm not sure why you're unable to add an account; as you know these things are very easy to do, sometimes anyway lol.

I'd like to give you my instructions fot setting up the tar.bz2 file from Mozilla.

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by DeMus on 2009-12-17
Thanks for your info about installing the program. That part I managed. I just can not add an account, which is, as you also wrote, an easy thing to do. Normally.
I give up and will continue to use T'bird 2. At least that one is working for me.

I did read several other posts here where people complain about Vs3. What's wrong with the software writers? Ubuntu comes with 9.10 which is a disaster, now Mozilla comes with Thunderbird 3 which is not much better.
Are they trying too hard to beat MS? This way it won't work, that's for sure.

---

### Post by scouser73 on 2009-12-17
Have you seen if it's a problem with your profile? I would suggest setting up a new profile (whilst keeping the original) using the instructions set out here: [[COLOR="Red"]**Mozilla Thunderbird Help**[/COLOR]]("http://www.mozilla.org/support/thunderbird/profile")

---

### Post by DeMus on 2009-12-17
> **scouser73 said:**
> Have you seen if it's a problem with your profile? I would suggest setting up a new profile (whilst keeping the original) using the instructions set out here: [[COLOR="Red"]**Mozilla Thunderbird Help**[/COLOR]]("http://www.mozilla.org/support/thunderbird/profile")

Thanks for your help. I did what you wrote, well what was written in the link you wrote, and still it didn't work.
I deleted everything belonging to T'bird 3 and continue using Vs2. 
I give up.

Thanks again.

---

