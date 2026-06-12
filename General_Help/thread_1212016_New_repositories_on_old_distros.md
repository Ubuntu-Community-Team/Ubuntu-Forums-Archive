---
title: "New repositories on old distros?"
date: 2009-07-13
forum: General Help
---

### Post by 696f6e6963 on 2009-07-13
I am using Ubuntu 8.04 (upgrading is not an option), and the repositories don't have software I need, but the 9.04 repositories do. Can I just add those to my sources.list file and grab the software or will there be issues?

---

### Post by csabo2 on 2009-07-13
Yes you can, however do not do a system upgrade with the 9.04 repos in place, put everything back how it was as SOON as you finish the application install.

---

### Post by snowpine on 2009-07-13
Bad idea.

A better idea is to install only the applications you need. [http://www.getdeb.net/](http://www.getdeb.net/) is a good source, as is the application developer's website. (For example, if you want the new OpenOffice, go to [http://www.openoffice.org/](http://www.openoffice.org/) it's not rocket science!)

---

### Post by 696f6e6963 on 2009-07-13
[csabo2]("http://ubuntuforums.org/member.php?u=871490"), upgrade as in sudo apt-get upgrade? Is sudo apt-get update fine?

[snowpine]("http://ubuntuforums.org/member.php?u=479885"), I tried getting the deb from the application developers site, it didn't seem to work. Should I take that as a compatibility issue and a reason for it not being in the older repositories?

Thanks!

---

### Post by csabo2 on 2009-07-13
Yes you can do an update, just not an upgrade :) 

Again, once you finish installing the software put your repos back, do an "apt-get clean all" and then run an update again to make sure you have clean data.


 snowpine is right its not recommended, but recommended and "in the field" are two different things, I've done this a few times and didn't have any issues.

---

### Post by j7%&lt;RmUg on 2009-07-13
If the above ideas dont work:

Which application are you trying to get the .deb for? I will help you find a download link for it.

---

### Post by snowpine on 2009-07-13
> **696f6e6963 said:**
> 
[snowpine]("http://ubuntuforums.org/member.php?u=479885"), I tried getting the deb from the application developers site, it didn't seem to work. Should I take that as a compatibility issue and a reason for it not being in the older repositories?


Try installing the .deb from the command line ('sudo dpkg -i whatever.deb') and post the output here. Usually, the error messages are very informative (for example something like "package x depends on package y, but package y cannot be installed").

ps Do you know about the "backports" repository? It is designed for exactly your situation: People who want to stick with their current release version, but need newer versions of applications: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by 696f6e6963 on 2009-07-13
Ah! Yes it was very descriptive - wrong architecture...

Can I repackage? If someone knows where I could find likewise-open5 deb for lpia (dell mini) that would be awesome. The manufacture only provides i386 and x64.

---

### Post by snowpine on 2009-07-13
Ah, I did not realize you were using a Dell Mini---I have one too (though I have upgraded to 9.04). :)

I think you will find this thread very useful: [http://ubuntuforums.org/showthread.php?t=962835](http://ubuntuforums.org/showthread.php?t=962835)

ps your plan of using the 9.04 repositories won't work anyway with the Dell remix because 8.04 is their newest release. :)

---

