---
title: "ssh Server Broken"
date: 2011-01-21
forum: General Help
---

### Post by weijiajun on 2011-01-21
So I am using 10.04 and was trying to get gitosis working on my machine so that I could use it over ssh.  Anyways I'm not sure what happened (as I did this a month ago) but ssh isn't working now.  When I try to ssh on the box (ssh localhost) I get the below error. 

PTY allocation request failed on channel 0
bash: gitosis-serve: command not found 
Connection to localhost closed.

First I know that gitosis-serve was incorrect anyways, but what I can't figure out is where that command is being called from.  When I run a terminal from the box I don't get the error so it seems to be only ssh.

Anyone have a suggestion as to locations I can look at to check this out?

---

### Post by weijiajun on 2011-01-22
Well in case anyone else runs into this problem it was a key that was leftover from when I setup gitosis, so after cleaning out the ~/.ssh directory of the invalid key everything worked.

---

