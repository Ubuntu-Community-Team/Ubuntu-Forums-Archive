---
title: "add-apt command missing in terminal"
date: 2012-03-20
forum: General Help
---

### Post by KennyJack on 2012-03-20
$sudo add-apt repository...
add-apt command not found

The command has worked up until now and I have no clue as to why it's gone or how to get it back.  I even tried sudo su, then ran add-apt... still, command not found.  

I can install ppa's through update manager->settings->third party but it's much more convenient to do so from terminal.

Any suggestions for this minor yet highly annoying issue?

Thanks

---

### Post by claracc on 2012-03-20
See this thread: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I think the correct  command line order is :

sudo add-apt-repository ppa:user/ppa-name

Replace 'ppa:user/ppa-name' with the PPA's location that you noted above.

---

### Post by KennyJack on 2012-03-20
Yes, I realize what the full command line is to add a repository from terminal.  The "..." was meant to be whatever comes after the command.  My bad for not being clear enough.  Fact is, when I put the full ppa path it says "command not found" and won't add the repository.  Strange and annoying.  Thanks for the help, through.

---

### Post by mcduck on 2012-03-20
> **KennyJack said:**
> Yes, I realize what the full command line is to add a repository from terminal.  The "..." was meant to be whatever comes after the command.  My bad for not being clear enough.  Fact is, when I put the full ppa path it says "command not found" and won't add the repository.  Strange and annoying.  Thanks for the help, through.

The problem is the missing dash in your command.

So the correct command would be this:
```
sudo add-apt-repository ...
```

instead of:
```
sudo add-apt repository ...
```

---

### Post by mnrbig on 2012-03-20
removed

---

### Post by oldos2er on 2012-03-20
After you type 'sudo add-apt' hit the Tab key and it will autocomplete for you. Good way to avoid typos.

---

