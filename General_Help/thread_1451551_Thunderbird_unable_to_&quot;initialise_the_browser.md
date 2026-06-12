---
title: "Thunderbird unable to &quot;initialise the browser's security component&quot;"
date: 2010-04-10
forum: General Help
---

### Post by napzilla on 2010-04-10
I am encountering an irritating problem with Thunderbird, and *nothing* I've tried has done a thing to help. I'm using Firefox 3.5.9, Thunderbird 2.0.0.24 with Ubuntu Karmic. When I launch Thunderbird, I get a message telling me that it "Could not initialize the browser's security component..." followed by some suggested remedies. Then, Thunderbird tells me it cannot connect securely to any of my email accounts because the SSL protocol has been disabled.

This failure started shortly after I let Firefox update, but Firefox works fine, and has no trouble using SSL or any other protocols. The only application having any issues is Thunderbird.

The first resource I found was on the [Mozilla Support Site]("http://support.mozilla.com/en-US/kb/Could+not+initialize+the+browser+security+component"), but none of their suggestions worked. I've continued searching for help on this problem all afternoon, but nothing has worked so far.

Here's the full list of the solutions that I've attempted so far:
[LIST]
[*]I have plenty of disk space
[*]There's no read/write restrictions on files in my profile
[*]I tried removing all three *.db files
[*]I tried creating a new profile
[*]I tried removing my Thunderbird profile
[*]I tried removing my Thunderbird, Firefox, and Sunbird profiles just for the hell of it
[*]I tried removing the Thunderbird directory from my home directory and removing it with apt-get purge, followed by a fresh install
[*]I checked, and ss3 is enabled
[*]I tried reinstalling libnss3-1d
[*]I tried sacrificing 13 virgins during a full moon
[/LIST]
As I said, not one of these has done me a bit of good. This is problematic, because it essentially means that I have to go through a web interface to access each of my email accounts (I was managing 10 or so accounts with Thunderbird, including my school account, a Gmail account, a Yahoo! account, and several others). People are going to start getting pissed at me if I don't start writing them back...
](*,)
I've run out of possible solutions. Does anybody have any other ideas? Should I just give up on Thunderbird altogether and try Evolution or some other mail client? Any help would be greatly appreciated. I'm going to go bash my head against a wall for a little bit to see if that helps anything.

---

### Post by yourcelf on 2010-04-10
Hey Napzilla,

it's this bug:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/559881](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/559881)

A simple fix is to remove libnss3-0d, with:

    apt-get remove libnss3-0d

It's marked as critical, so it ought to be fixed soon.

---

### Post by napzilla on 2010-04-10
Awesome! That fixed it. Thank you very much!

---

### Post by rbyrne on 2010-04-11
This is awesome! I had exactly the same problem, but this soution solved it straight away. 

Thanks yourcelf. (Now I'm going to have to find another use these virgins I got:P)

---

### Post by Brynderw on 2010-04-11
> **yourcelf said:**
> Hey Napzilla,

it's this bug:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/559881](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/559881)

A simple fix is to remove libnss3-0d, with:

    apt-get remove libnss3-0d

It's marked as critical, so it ought to be fixed soon.

Hi yourcelf
Unfortunately your fix does not work for me. I get the following message from terminal when  I use the apt command: E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Would be grateful for any further ideas.

---

### Post by mike55 on 2010-04-11
Thanks a lot guys, tried to find a fix for this yesterday and removing libnss3-0d did the trick.

Brynderw, are you using sudo? The command should be:

# sudo apt-get remove libnss3-0d

and then enter your password. That worked for me anyway.

---

### Post by Brynderw on 2010-04-11
mike55 you were absolutely correct, I had failed to use sudo. I'm not a frequent user of Terminal. This has also solved the problem for me. Many thanks to you and yourcelf for sorting this.

---

### Post by Satanister on 2010-04-11
Thanks a lot bro...
Did the trick for me...

p.s. do I need libnss3-0d

---

### Post by noleti on 2010-04-11
had the same problem, and it could fix it using the described method, thanks!

---

### Post by drysdam on 2010-04-11
oh sweet baby jebus THANK YOU.  I've been banging my head on this for an hour.

---

### Post by simontaylor on 2010-04-12
worked for me too. Thanks.

---

### Post by yourcelf on 2010-04-12
Ubuntu has now pushed a fix for this as a security update for Karmic Koala (9.10).  So you should be able to fix it now just  by running Update Manager.

---

### Post by eudemus on 2010-04-21
This did not fix it for me, as I did not have libnss3-0d installed in teh first place.

Any other ideas?

---

### Post by mfdc1969 on 2010-07-24
I don't have this "libnss3-0d" installed either ... yet I also have the problem but only when I try to send a link from inside Firefox, using T-bird.

It only started this morning ... I installed libnss3-0d" and the problem happened so I removed it and it seems to have disappeared for the meantime. Go figure eh?!

---

### Post by comsparks on 2010-07-28
I had the same problem and after a lot of research I found someone who tried something and it worked for him so I tried it and it fixed everything. I simply upgraded to Thunderbird 3.1 and got rid of that Thunderbird 2.0 and everything is now working perfectly. I'm using Firefox 3.6.8 and Thunderbird 3.1 under Ubuntu 9.04. I googled Deb file for Thunderbird 3.1 found it and it loaded right up. Make sure you save your Email files or your going to re-enter them manually.

Enjoy!

---

