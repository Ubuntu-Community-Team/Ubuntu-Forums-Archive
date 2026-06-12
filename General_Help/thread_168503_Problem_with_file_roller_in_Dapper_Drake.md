---
title: "Problem with file roller in Dapper Drake"
date: 2006-04-30
forum: General Help
---

### Post by stojan on 2006-04-30
Sorry for noob question, but I've installed Dapper Drake 6.06 Beta, I've my system up-to-date and when I want to extract some .rar files in File-roller, there will pop-up an error message from file roller: "Unable to extract file.Unsupported filetype." (I've slovak version of Dapper,so this is free translation to english ;) ) When I tried to unpack the same file in Breezy or Windows, there was no problem.
Any suggestions how to solve this problem? Thanx.

---

### Post by Ramses de Norre on 2006-04-30
sudo apt-get install rar-nonfree

---

### Post by stojan on 2006-04-30
Thanks You Very Much..I'll try..But anyone know about some repository where this package is? System did'nt found it in anyone of my repos.. ](*,)

---

### Post by Ramses de Norre on 2006-04-30
It's in multiverse, you can also install rar-free which is in universe but doesn't feature the latest rar formats.

---

### Post by Ramses de Norre on 2006-04-30
Ow, huge "typo" it's unrar-[free/nonfree] instead of rar.

---

### Post by stojan on 2006-04-30
Yeah.. :) I've downloaded universe package (free) but it didn't solved my problem :(
I wasn't able to download that multiverse one. Maybe I've not added good multiverse repository or what...:rolleyes: Can you tell me what repo to add? ;)

---

### Post by Ramses de Norre on 2006-04-30
It's [here]("http://packages.ubuntu.com/breezy/utils/unrar-nonfree"). It should be in the normal multiverse repo too ```
deb http://archive.ubuntu.com/ubuntu breezy multiverse

```

---

### Post by stojan on 2006-04-30
OMG! I'm so dump! 8) The main problem was that I hadn't checked multiverse as active repos.. :D That was default setting and I didn't changed it :D But now, it's working perfectly...Thanks You, now, the problem is solved.:mrgreen:

---

