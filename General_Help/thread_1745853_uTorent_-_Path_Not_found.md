---
title: "uTorent - Path Not found"
date: 2011-05-01
forum: General Help
---

### Post by Fritz The Rat on 2011-05-01
I'm trying to get utorrent to load torrent when downloaded and run from Firefox. When I do, I get a Path not Found error. I have no freaking idea what path is not found as it doesn't tell you. I'm lost, please help.

I did find this which says it solves the problem but it has only served to confuse me even more. -

[B]"sorry for not updating before...

i found a solution when discussing this problem at utorrent forum[/B] [B]
the script i use is:

#!/bin/sh[/B] [B]
wine /home/{Your_User_Name}/.wine/drive_c/Program\ Files/uTorrent/uTorrent.exe "z:$*"

puted in a file called utorrent placed at path: /usr/bin[/B] [B]

and then granted runing permissions using the command:[/B] [B]

sudo chmod a+x /usr/bin/utorrent[/B] [B]

now pointing firefox to that file when downloading .torrent files will start utorrent"[/B] 

1. I have no idea what - **"puted in a file called utorrent placed at path: /usr/bin**" means.

2. When I try to grant running permissions I get  a no such file or directory error[B].

[/B]If someone could translate the above post for me I think that would solve my problem.

Thanks.

---

