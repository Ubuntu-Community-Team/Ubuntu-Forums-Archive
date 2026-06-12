---
title: "Is it worth upgrading to 11.04 from 9.04?"
date: 2011-08-21
forum: General Help
---

### Post by lavrentis on 2011-08-21
Hello, I run a web server which has 9.04 on it and everything is running perfectly fine but I am concerned now because support has been dropped for it and I cannot update it. Is upgrading to 11.04 really that much better and will I notice anything different? 

I understand that it will take me a lot of effort to upgrade wont it? I'm fairly new with Ubuntu but there isnt just a secret command I'm missing that will install 11.04 keeping all stuff thats on the server already ?:)

Thanks

---

### Post by realzippy on 2011-08-21
Think you cannot upgrade directly to 11.04...

And isn't it better for a server to stay with LTS ? (10.04)

---

### Post by apacketofsweets on 2011-08-21
It's a lot of risk for something you might not like, 11.04 is a huge change, especially if you want a server OS. I'd suggest you stick with what you've got, afterall, if it's not broke, why fix it?

---

### Post by lavrentis on 2011-08-21
> **realzippy said:**
> Think you cannot upgrade directly to 11.04...

And isn't it better for a server to stay with LTS ? (10.04)

Yeah, I was thinking that. Is there a direct way of upgrading from 9.04 to 10.04 LTS or do I  have to fresh install?

---

### Post by apacketofsweets on 2011-08-21
The easiest way is a fresh install as far as I can gather, but there are complicated (and risky) ways of manually upgrading it. Either way you do it, make sure you make a solid back up.

---

### Post by lavrentis on 2011-08-21
> **apacketofsweets said:**
> The easiest way is a fresh install as far as I can gather, but there are complicated (and risky) ways of manually upgrading it. Either way you do it, make sure you make a solid back up.

Thanks, is the easiest way that through update-manager?

---

### Post by apacketofsweets on 2011-08-21
I'd assume so, if it's available.

---

### Post by mikewhatever on 2011-08-21
There is no update manager on the server edition, so it would be hard to use it. Try the 'sudo do-release-upgrade' command.
For more info:
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by lavrentis on 2011-08-21
> **mikewhatever said:**
> There is no update manager on the server edition, so it would be hard to use it. Try the 'sudo do-release-upgrade' command.
For more info:
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Thanks but that is only for 9.10 to 10.04, as I am on 9.04 I would have to upgrade to 9.10 first.

9.04 to 9.10 should be a lot easier right.

---

### Post by ajgreeny on 2011-08-21
9.10 has also lost its support, even for the server edition, I think, so updating 9.04 to 9.10 online would not be possible as far as I'm aware.

A fresh install seems the only real option, and I agree with others; go for the 10.04 server, the most recent LTS version.

---

### Post by mikewhatever on 2011-08-21
Here is a howto for an EOL release.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You can't directly upgrade to any Ubuntu version. 9.04 can only be upgraded to 9.10, and 9.10 to 10.04.

---

### Post by mcstat on 2011-08-21
Since it's a server it's better to upgrade it to 10.04 an LTS, support is for about 10 years.

---

### Post by lavrentis on 2011-08-21
> **mikewhatever said:**
> Here is a howto for an EOL release.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You can't directly upgrade to any Ubuntu version. 9.04 can only be upgraded to 9.10, and 9.10 to 10.04.

Thanks, is that a fresh install or will it keep my current files and setup? If it is a fresh install I might as well install 10.04 as a fresh install. If that makes any sense at all.

Sorry for all the questions like I said I'm quite new to ubuntu.

---

### Post by realzippy on 2011-08-21
..as far as programs/apps still exist in the new version,it will keep them and their configs.
Uninstall proprietary drivers before,also it is unlikely you run them on a server.

---

### Post by lavrentis on 2011-08-21
> **realzippy said:**
> ..as far as programs/apps still exist in the new version,it will keep them and their configs.
Uninstall proprietary drivers before,also it is unlikely you run them on a server.

Thanks,

Cheers all, great ubuntu community here on this website! :)

---

### Post by lavrentis on 2011-08-21
Hello, there is a problem...

> Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg'
tar: Removing leading `/' from member names

Reading cache

Checking package manager

Can not upgrade

An upgrade from 'jaunty' to 'lucid' is not supported with this tool.




What shall I do?

---

### Post by Topsiho on 2011-08-21
I think you should do a fresh install of 10.04 LTS. That's far safer than upgrade, and again upgrade. For a server 10.04 LTS is supported for ==> 5 <=== years, for the desktop 3 years. Not 10 years as someone said.

If you use it only as a server you might have a look at the server edition ([http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download)).

Topsiho

---

### Post by lavrentis on 2011-08-21
> **Topsiho said:**
> I think you should do a fresh install of 10.04 LTS. That's far safer than upgrade, and again upgrade. For a server 10.04 LTS is supported for ==> 5 <=== years, for the desktop 3 years. Not 10 years as someone said.

If you use it only as a server you might have a look at the server edition ([http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download)).

Topsiho

Ok thanks, I think that is what I will have to do.

I really think though whoever designed the upgrade thing to directly upgrade to 10.04 should make it so it knows to upgrade to 9.10. Probably easier said than done.

---

### Post by ajgreeny on 2011-08-21
As I said before, I think part of your problem is that 9.10 has also lost support, so you can not upgrade to that from 9.04, and as you can only go from one version to the next, or from one LTS to the next LTS, you have no option but to clean install, which I think is what you have now accepted as your next activity.

---

