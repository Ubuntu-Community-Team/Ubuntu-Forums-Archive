---
title: "Thunderbird 3"
date: 2009-12-09
forum: General Help
---

### Post by dluzius on 2009-12-09
How soon will tbird3 be available thru synaptic pkg mgr?I can't wait to get it up and running on my pc.
Dave

---

### Post by Jive Turkey on 2009-12-09
It will be available as soon as you enable ppa repository for it.

See here:[https://launchpad.net/ubuntu/+source/thunderbird]("https://launchpad.net/ubuntu/+source/thunderbird")

---

### Post by t0p on 2009-12-09
> **Jive Turkey said:**
> It will be available as soon as you enable ppa repository for it.

See here:[https://launchpad.net/ubuntu/+source/thunderbird](https://launchpad.net/ubuntu/+source/thunderbird)

Yes.  Ubuntu will not officially use the new version of Thunderbird (or, indeed, any new software) until the next version of Ubuntu is released (ie 10.04).  So if you want to use it before 10.04, you'll have to enable a PPA repository that has it.

---

### Post by running_rabbit07 on 2009-12-09
I have tried to install it from the Mozilla site and it wouldn't work on Jaunty, however, it did work on Karmic. It is a shame, because it looks great.

---

### Post by cjnkns on 2009-12-09
> It will be available as soon as you enable ppa repository for it.

See here:[https://launchpad.net/ubuntu/+source/thunderbird](https://launchpad.net/ubuntu/+source/thunderbird)

I must be blind. I do not see the details I need to enable the PPA on the link you provide...

Could you please provide a bit more info for me? Thank you!

---

### Post by Jive Turkey on 2009-12-09
I found a nice guide [here]("http://www.ubuntu-inside.me/2009/08/howto-install-thunderbird-3-beta-on.html") that worked for me on 64-bit jaunty.

Once completed you will have a menu option called "shredder" which is thunderbird 3

---

### Post by cjnkns on 2009-12-09
> I found a nice guide here that worked for me on 64-bit jaunty.

Once completed you will have a menu option called "shredder" which is thunderbird 3

Thank you - I appreciate the help.

---

### Post by scouser73 on 2009-12-10
Slightly off-topic but if you wanted to install it from the Thunderbird website then follow these instructions.

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

### Post by Yfrwlf on 2009-12-17
So you can easily install (menu shortcut created for you, added to add/remove programs) TB3 STABLE in Windows, but with Ubuntu you have to wait 5 more months until the next version of everything comes out, or you have to add a PPA link which will give you the daily unstable version of both Firefox and Thunderbird?  That's not very friendly. :(

Linux still needs a package system that is cross-distro.  If you're not going to offer debs or rpms then at least offer "installers" that will do the above-mentioned things.

---

### Post by scouser73 on 2009-12-17
> **cjnkns said:**
> Thank you - I appreciate the help.

Shredder is the codename for pre releases of Thunderbird like Alphas & Betas, that codename is dropped once the final release is made public.

---

### Post by running_rabbit07 on 2009-12-17
> **scouser73 said:**
> Slightly off-topic but if you wanted to install it from the Thunderbird website then follow these instructions.

Thanks for those instructions. The only problem I had was with the **chown -R** command and I worked around that by using the gksudo nautilus to get to the folder properties and change the ownership to my user name. I had uninstalled the 2.0 version so I had to use another icon, but that is fine.

---

### Post by scouser73 on 2009-12-17
What was the problem with **chown -R**?

---

### Post by running_rabbit07 on 2009-12-17
> **scouser73 said:**
> What was the problem with **chown -R**?
  It said the same thing with every file in the folder ```
chown: changing ownership of `thunderbird/components/xultmpl.xpt': Operation not permitted
```

---

### Post by scouser73 on 2009-12-17
> **running_rabbit07 said:**
> It said the same thing with every file in the folder ```
chown: changing ownership of `thunderbird/components/xultmpl.xpt': Operation not permitted
```

That's really odd, you shouldn't have any problems with that command, anyway you've got it sorted now.

Regards,

Scouser73

---

### Post by litlfrog on 2009-12-28
So I've got a working copy of the new version of Thunderbird now. How do I import my mail and settings from Thunderbird 2? If I choose "Import," the program neither knows where to look nor gives me an option to manually choose a location.

---

### Post by DrKay on 2010-04-06
You're right about this. The good news is that this seems to be coming. I installed Google Chrome this way. I went to the web site, downloaded a file, opened the file, entered my password, and it installed like magic. It even placed an icon where it should under "Internet" in the menu. This is definitely the way to go. We can't expect normal users to add lines to their sources list, update the sources, etc. We need to use the more friendly way.

---

### Post by lidex on 2010-04-06
> **scouser73 said:**
> What was the problem with **chown -R**?
I suspect he missed the "sudo -i" part

---

### Post by lidex on 2010-04-06
> **DrKay said:**
>  We can't expect normal users to add lines to their sources list, update the sources, etc. We need to use the more friendly way.

And that will happen as soon as Mozilla makes an installer for linux.

---

