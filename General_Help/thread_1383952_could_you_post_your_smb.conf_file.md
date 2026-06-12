---
title: "could you post your smb.conf file"
date: 2010-01-17
forum: General Help
---

### Post by titanicmusic14 on 2010-01-17
I'm trying to set up a samba server that gives me the ability to manipulate the files from my computer in the house through my regular usernames but doesnt allow my roommates with whom I share files to make any changes yet still view view their respective usernames and passwords. IF you have a similar setup could you tell me how you set up the permissions or post your .conf file.

---

### Post by jamesisin on 2010-01-17
Are you also using the Samba share?

If you are not, you can merely allow guest access with read-only permissions and be done with it.

Here is my favorite threads for Samba issues:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Hope that helps you get rolling.

---

### Post by titanicmusic14 on 2010-01-17
> **jamesisin said:**
> Are you also using the Samba share?

If you are not, you can merely allow guest access with read-only permissions and be done with it.

Here is my favorite threads for Samba issues:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Hope that helps you get rolling.

Thanks but that wasn't what I was looking for.

---

### Post by jamesisin on 2010-01-17
Maybe you could tell me what you are looking for then?

---

### Post by titanicmusic14 on 2010-01-18
> **jamesisin said:**
> Maybe you could tell me what you are looking for then?

Thanks. Somehow by creating a new share and getting rid of the lines of the old share and then just moving the files over worked. For some reason the permissions just were acting funny. I created a new file within the area that I wanted previously, wrote a few lines in the smb.conf and then magically I was able to copy files into it from xp while my other users only could read from it. Thats what I wanted.

---

### Post by jamesisin on 2010-01-18
I like magic.

Mark as SOLVED?

---

