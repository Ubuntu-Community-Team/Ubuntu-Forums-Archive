---
title: "Crontab update&amp;&amp;dist-upgrade"
date: 2011-11-08
forum: General Help
---

### Post by amhainen on 2011-11-08
I have about five Ubuntu machines I used at least once a week. Whenever I SSH into them, I'm usually greeted with the number of updates. Having lingering updates bugs me, so I made a script (attached):

```

#!/bin/bash
/usr/bin/sudo apt-get -y update
/usr/bin/sudo apt-get -y dist-upgrade

```

I know a lot of people strongly recommend checking all updates and only applying the desired, but I've just run update and then dist-upgrade for years now with no problems. I'd like to put this into Crontab, but I've read two things regarding this:

[LIST=1]
[*]Running a "sudo" operation in Crontab might be a problem as far as requiring a password.
[*]Running a "sudo" operation in Crontab is a bad idea.
[/LIST]

Can someone give me some insight? Like I said, whenever I log on I usually just run:

```
. ~/.update
```

Which is my above script. (In fact, I might even make an alias "upd" now that I think about it). Anyway, insight to why this is bad or a solution to the crontab sudo password problem would be great help. Thanks!

---

### Post by amhainen on 2011-11-08
Nevermind, I figured it out:

```
sudo crontab -e -u root
```

Then I added the line:

```
0 0 * * * /usr/bin/sudo apt-get -y update && /usr/bin/sudo apt-get -y dist-upgrade && echo "Updated on $(date)" >> /home/user/.updatelog
```

Feel free to let me know if this is still b ad. Thanks.

---

