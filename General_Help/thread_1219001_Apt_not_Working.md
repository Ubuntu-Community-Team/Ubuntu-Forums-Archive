---
title: "Apt not Working"
date: 2009-07-21
forum: General Help
---

### Post by Mmarzex on 2009-07-21
I was trying to install e17 through some instructions didn't work so now when I try to install anything or use apt-get update or apt-get install I recieve this error I don't know what to do 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by bacil on 2009-07-21
are you running it as root or with sudo like this ?

```

sudo apt-get update

```

---

### Post by credobyte on 2009-07-21
Take a look at this post ( links in it ) : [http://ubuntuforums.org/showpost.php?p=4505783&postcount=4](http://ubuntuforums.org/showpost.php?p=4505783&postcount=4) !

---

### Post by wojox on 2009-07-21
Did you have Synaptic open when you where running those terminal commands?

Close any package managers before running those in terminal.

use the top command in terminal to see if processes are running.

---

### Post by Mmarzex on 2009-07-21
> **credobyte said:**
> Take a look at this post ( links in it ) : [http://ubuntuforums.org/showpost.php?p=4505783&postcount=4](http://ubuntuforums.org/showpost.php?p=4505783&postcount=4) !
It was fixed the problem seems to have been it kept trying to installing a script that wasn't actually there

---

