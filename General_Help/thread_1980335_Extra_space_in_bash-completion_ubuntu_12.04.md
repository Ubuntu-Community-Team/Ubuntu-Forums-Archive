---
title: "Extra space in bash-completion ubuntu 12.04"
date: 2012-05-15
forum: General Help
---

### Post by New00Folder on 2012-05-15
Hi!

In ubuntu 10.10 hitting tab after typing "ls Dow" would autocomplete to "ls Downloads/". When I installed 12.04, first thing I checked was bash-completion. It was working correctly then. Then after I installed the updates I found that "ls Dow" autocompletes to "ls Downloads ". Same is the case of ln and g++ commands. It was working correctly for cd & chmod though.

Then I found [this]("http://askubuntu.com/questions/41707/bash-auto-completion-with-added-spaces-why-and-how-to-fix") fix of changing "default" to "filenames" in line 1587 of /etc/bash_completion.

Now ls & ln commands autocomplete correctly but g++ does not.

What I'd like to do is to either fix this version (1.3) of bash-completion or install the older version which was included in the Live CD.

If you have any ideas, please share.

Thanks.

---

### Post by codemaniac on 2012-05-15
installing auto-complete-el may fix your issue . ```
 sudo apt-get install auto-complete-el 
```

---

### Post by markbl on 2012-05-15
All I can say is that I have an up to date 12.04 system which was originally a clean install and "ls Dow" completes to "ls Downloads/" for me. I haven't done anything special and I don't have that "auto-complete-el" package installed as mentioned above.

---

### Post by New00Folder on 2012-05-15
I booted with ubuntu 12.04 and mint 12 live cds and found that both had bash-completion working correctly. Both had release 1.3 and both had "default" in line 1587 of /etc/bash_completion. None had the package auto-complete-el.

There is a deb file for bash-completion in /var/cache/apt/archive which tells me that bash-completion was updated during updates since I didn't try to install/re-install it or anything. So I feel like it was the updates that ruined it. Also it was working correctly in the freshly installed system.

I compared the contents of /etc/bash_completion.d of my installed system and of the same directory while booting from live cd. Only difference is that the installed system has an extra "acroread.sh".

One more strange thing I observed is that when I type meaningless commands (like "very wrong /us" & hit tab) I get a slash and no space while for real commands (like "chown root:root /us"), I get a space.

@markbl: Have you tried commands where file path isn't the first argument (like type "chown root:root /us" and press tab)? What about any other program that you installed manually?

---

### Post by markbl on 2012-05-15
I clean installed 12.04 on 23-Apr and at that time bash-completion 1.3-1ubuntu8 was installed in my default desktop. For my system, there has been no update of that package since (and I update every day).

My /etc/bash_completion has "have $i && complete -F _longopt -o default $i" in line 1587.

I get the slash completing on "chown root:root Dow" and also "crap_command root:root Dow".

Like most, I have installed quite a lot of programs but I can't think of anything that may affect this.

Check your ~/.bashrc and make sure it is sourcing /etc/bash_completion correctly. See /etc/skel/.bashrc for how it should be done. Sorry, not helping you much other than saying "it works for me" .. :(

---

### Post by New00Folder on 2012-05-16
I just uninstalled bash-completion and now auto-complete seems to work perfectly. There's no /etc/bash_completion now but somehow it's working; even after restarting the system. How about that!

---

### Post by thirdender on 2012-07-12
Thanks to @New00Folder for providing the missing piece for me :P I realized after reading his post that I'd also just installed Adobe's Reader software (I needed their fonts installed to render a design properly…). The program had added a symbolic link from /etc/bash_completion.d/acroread.sh -> /opt/Adobe/Reader9/Resource/Shell/acroread_tab. After removing the symbolic link and starting a new bash shell, things were back to normal. However, my problem was sporadic before, so I'm hoping this is a permanent fix. I'm assuming this file was the problem… the situation resolved immediately after the file was removed, and both @New00Folder and myself had the file in question in the bash_completion.d folder. We'll see if it stays fixed…

---

### Post by New00Folder on 2012-07-12
Well thirdender, you're welcome but I still have the acroread.sh link and my auto-complete is working fine.

---

### Post by lethalfang on 2012-07-29
> **New00Folder said:**
> I just uninstalled bash-completion and now auto-complete seems to work perfectly. There's no /etc/bash_completion now but somehow it's working; even after restarting the system. How about that!

Yeah, I've kinda lived with it for 2 months and it's finally driven me crazy enough to seek a solution. I don't know what's the problem, but that problem only occurs on one of my 3 computers. 
I removed bash-completion and it worked.

---

### Post by 4levels on 2012-08-06
Hi,

First I tried changing the /etc/bash_completion script and it worked only in my home folder.  Removing the symlink from Acroread did the trick here too!  Seems like that one is the culprit.

So I just did ```
sudo rm /etc/bash_completion.d/acroread.sh
```

---

