---
title: "Superuser"
date: 2011-05-25
forum: General Help
---

### Post by .psd on 2011-05-25
I like how Android works. I am the SU. Everything which wants superuser rights asks me first. There is an application that remembers the decision and then allows me to manage the whitelist. I have complete read/write access to files without the need for a terminal. Everyone realizes this is achieved by turning security OFF, and we are all aware of the dangers that implies.

OK.

I want the same abilities with Ubuntu. How can I accomplish this?

My goal is to avoid using the terminal or typing in passwords ever (I want a very Windows-with-all-security-off type of experience). I am aware of the dangers this implies and the community's reluctance to explain how to achieve this.

---

### Post by .psd on 2011-05-25
Wow you're good.

Just making sure this is supposed to accomplish everything I asked (specifically, enabling superuser privileges for the current user), or will it simply make it so I don't have to type a password here and there?

Will I be able to read/write files freely using Nautilus file explorer, even to restricted locations, without needing the terminal?

Assuming the user account is "abc" no quotes, what would I type in the terminal to give abc superuser privileges?

---

### Post by uRock on 2011-05-25
You may want to check out the following link  for setting your account as root.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Another important link, [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by .psd on 2011-05-25
Wow that was incredibly complicated, and now I'm even more lost. But it sounded like what I'm looking for is very possible, and even better it seems it can be enabled temporarily. So how about this:

How can I read/write all files/locations without restriction? If possible, what command makes this possible, which I can then reverse once I'm done? I would not like to log in or out at any time (with the exception of the original login, which I would also like to eliminate by the way. Only my wife and I use the computer).

---

### Post by uRock on 2011-05-25
**gksu nautilus** will open nautilus as root and therefor can see all subdirectories on the system, unless those directories have been encrypted.

---

### Post by seawolf167 on 2011-05-25
Running as root or with root privileges all the time is ***very highly ***not recommended. That said, you can enable the root account via [this section here]("https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account"). Enable the account, set your password, then log in as root. ***Please note ***the big warning on that page.

If you want to have unrestricted GUI access to your folders/files, you can open your file manager with root privileges by:

```
gksu nautilus
```

---

### Post by Joe of loath on 2011-05-25
You can create a link on the desktop for a nautilus window with root privileges. However, after some time using Linux, it's rare you have to do so. I do most root stuff through the terminal now (But I am an Arch :lol:).

---

### Post by .psd on 2011-05-25
OK but then I lose all my Places. I don't know how to navigate to my home folder or anywhere else.

I understand you guys are supposed to recommend the best/secure ways to do things, but I'm trying to explain that for my needs, I literally prefer security off. Now if I can turn security off temporarily that's best, but I'm not trying to learn Ubuntu inside and out, I just want full read/write access when I want it. In other words, I would like hacker access to my own stuff, without having to hack (a la the windows experience, yes it's unsafe and insecure. I get it).

It's 100% OK if everyone that touches my computer has full access as well, and it would be ideal if I never had to login in or use a password.

---

### Post by uRock on 2011-05-25
Click Filesystem to the left, then double click Home to open the Home directory(ies)

---

### Post by Joe of loath on 2011-05-25
That's not possible by default in Ubuntu.

And really, I'd consider rethinking that attitude. That's the whole reason Windows is so insecure ;)

---

### Post by .psd on 2011-05-25
Thank you uRock!! That should handle my needs for now :)
> **Joe of loath said:**
> That's not possible by default in Ubuntu.

And really, I'd consider rethinking that attitude. That's the whole reason Windows is so insecure :wink:
I know it's not default, that's why I have to learn how to accomplish it, and I've said I know that's why windows is so insecure. I grew up on Windows, and always turn firewall, defender, uav, antivirus, ALL OF IT OFF, upnp on, etc. as unsafe as it gets I'm used to it. It's unsafety is also the reason it's user-friendly. My needs are all user right now, just myself and my wife occasionally (she has her own windows machine) there's really no network or risk of compromising the system.

---

### Post by oldos2er on 2011-05-25
> **.psd said:**
> How can I read/write all files/locations without restriction? If possible, what command makes this possible, which I can then reverse once I'm done? 


**sudo -i**

When done, type **exit**

---

### Post by seawolf167 on 2011-05-25
You can see the items from another users' home directories per uRocks post above.

My last word is: have a backup in case something goes wrong! I highly recommend imaging your drive with [Clonezilla]("http://www.clonezilla.org")

---

### Post by .psd on 2011-05-25
> **oldos2er said:**
> **sudo -i**

When done, type **exit**
That would be PERFECT!! If it made me root temporarily instead of making the terminal root temporarily. The reason I need root is to avoid using the terminal...

---

### Post by Dave_L on 2011-05-25
I think someone already suggested this, but you could enable root login, and then login as root.  That will let you do whatever you want with no restrictions.  (I'm not recommending this, but it should solve your problem.)

---

### Post by .psd on 2011-05-25
> **Dave_L said:**
> I think someone already suggested this, but you could enable root login, and then login as root.  That will let you do whatever you want with no restrictions.  (I'm not recommending this, but it should solve your problem.)
Thanks for the response, but the idea is to reduce the number of steps required to read/write files/folders.

Can I enable root login, and then delete all other accounts, and then delete the login manager so I never have to log in? That way I could still have a root password, but since nobody would ever have to log in, nobody would therefore need to know it. Then I can chmod the files/locations I don't want others to access, since they won't know the root password. I know this is perfectly opposite of the security design of Ubuntu.

---

### Post by LordNeo on 2011-05-25
By default you can decide wich user will log in automatically each time.
System->Logon Screen (or something like that)

By enabling root login and setting the default account to log to root, then you will automatically log in as root and have full rights over all the files and programs.
If you want your bookmarks and stuff, copy those files from your old /home directory over the root home (/root).
To share files just have to set the "guest access" so your wife in the other computer will have access to the files without having to know the root password.

Best regards and good luck

PD: I don't know if it's posible to chmod all the filesystem to your user... probably will break a lot of stuff...

---

