---
title: "Error Report Apt Update Issue"
date: 2010-11-18
forum: General Help
---

### Post by JoeFriday49 on 2010-11-18
When the update manager runs on my Acer notebook I have got this little message that pops up in a window:
<snip>
Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".
<end>

When I run the the update manager again and hit check it just tells me the system is up to date...  Since I have no Proxy server I don't understand what it is trying to tell me...  Am I in trouble, or is just a quirk?

---

### Post by Kljuka on 2010-11-18
This probably means that your update program couldn't verify the identity of update servers (whatever the reason of that might be). You could also be behind a firewall.

---

### Post by JoeFriday49 on 2010-11-20
I thought about the firewall, but I haven't changed anything here and certainly haven't installed one...  It always works fine when I run it manually...

---

### Post by daqron on 2010-11-25
Since about a week ago this has started happening to me after every update. I have tried solutions offered in various older threads about this topic (see [here]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1441622"), and [here]("http://ubuntuforums.org/showthread.php?t=827823")) but the problem resurfaces after the next update. Seems to be a very old problem without a good solution.

---

### Post by Hippytaff on 2010-11-25
looks like you have added a repository to your system that doesn't have a corresponding authentication key.

Do you have any third party repositories? if so you need to add the authentication key too, or remove the repository and add it again like this
```

sudo add-apt-repository ppa:[I]name of repository

```
[/I]then the key should also be added. There is another way to fix this but it involves finding out the keyserver and the hash of the repositry :-)

---

