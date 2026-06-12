---
title: "Problems running Firefox 1.0.1"
date: 2005-03-06
forum: General Help
---

### Post by neotool on 2005-03-06
Hello, I'm new here and I'm having some problems with Firefox. I've installed Firefox 1.0.1 using the sudo command into /usr/local/firefox but it won't let me run Firefox unless I run it as root. However if I install it as a regular user into my home directory I can run it with no problems, why is this? Am I missing something? Thanks for any help.

---

### Post by bored2k on 2005-03-06
[QUOTE=neotool]Hello, I'm new here and I'm having some problems with Firefox. I've installed Firefox 1.0.1 using the sudo command into /usr/local/firefox but it won't let me run Firefox unless I run it as root. However if I install it as a regular user into my home directory I can run it with no problems, why is this? Am I missing something? Thanks for any help.[/QUOTE]
 That's because its installed with root only privileges.
If you want to use with ur normal user, type this down to change its properties to yours:
> $sudo chown -R neotool /usr/local/firefox; sudo chgrp -R neotool /usr/local/firefox

after that you should be able to open it as the user "neotool"

---

### Post by neotool on 2005-03-06
Thank you, that worked like a charm. I also ran this so I wouldn't have to create a new profile.> sudo chown -R user /home/user/.mozilla; sudo chgrp -R user /home/user/.mozilla

---

