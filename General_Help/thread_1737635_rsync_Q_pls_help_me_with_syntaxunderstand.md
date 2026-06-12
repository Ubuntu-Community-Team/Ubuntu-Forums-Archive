---
title: "rsync Q: pls help me with syntax/understand"
date: 2011-04-23
forum: General Help
---

### Post by fisheater on 2011-04-23
Addendum: i put this into Grsync, to my suprize it worked! Topic solved (sort of, Grsync did the syntax for me). Thanks.

Hi all,

This post comes from the misadventure of not adding &#8211;n (dry run).

Please help me make some sense of this great system - rsync.

Problem: Wanting to sync local folder to webhost, so it will be easily available to me online. Tried FileZilla &#8211; no sync option.

Solution: rsync.

This is my proposed sync:

```
rsync -avrz -e --delete -n 'ssh' * my_login@ssh.hostwebsite:/home/public/frenchfry /remomte/dir /myhomeHD/dir
```

Deconstructed into simple English:

-a - to recurse the directory copying all the files and directories and perserving things like case, permissions, and ownership on the target.
-v &#8211; verbose 
-r - recurse into directories
-z &#8211; compression

-e (not sure why, it was in a tutorial)

--delete - delete files that don't exist on the sending side (keeps my receiving directory an exact copy of my sending)

'ssh' * [email]my_login@ssh.hostwe[/email]bsite:/home/public/frenchfry - this gets me into my SSH server, and puts me in the directory /home/public/frenchfry


/remomte/dir &#8211; this this line redundant? I want it to be /home/public/frenchfry


/myhomeHD/dir &#8211; this tells which is my desktop (source) directory

Thanks for taking a look!

FE

---

