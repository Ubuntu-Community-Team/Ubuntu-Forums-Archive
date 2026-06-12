---
title: "RM Protection:"
date: 2006-04-28
forum: General Help
---

### Post by klepto on 2006-04-28
Does anyone have a script that will make sure that when you delete
items it shows what you are deleting and it moves it to the /tmp folder.
I made an alias to use rm -i whenever I rm'd but i rm -rf by habit. 

I deleted 8 gigs of data that I needed by one simple typo.

---

### Post by Ensnared on 2006-04-28
Using rm -v (for verbose) will show what is being deleted. If you need it to be moved instead of deleted I guess you could set up an alias that moves it all to /tmp/ like this:```
alias rm='mv -v $* /tmp/'
```

This will show two lines of output for each file (again, thanks to the -v switch), like this:```
'filename' -> '/tmp/filename'
removed 'filename'
```

If you want this done permanently for all users, you add the alias to /etc/bash.bashrc - if you only want it for yourself, add it to your ~/.bashrc file.

I've only tested this quickly right now, so I can't guarantee it will work perfectly. and if you specify "rm -rf" it might generate an error, since "mv" doesn't have an -r switch... there might be more sophisticated ways of dealing with this, like filter out any switches given to "rm" before passing the rest of the command line to the mv-command.

However, I strongly reccomend you don't use anything like this, as it might give you some rather nasty surprises when you're suddenly sitting on a system without such an alias (i.e. any system other than your own). It's better to chalk this mistake up to experience and start thinking twice before using rm - it won't take long to break the habit of using the -rf switches, all you have to do is get started ;)

---

