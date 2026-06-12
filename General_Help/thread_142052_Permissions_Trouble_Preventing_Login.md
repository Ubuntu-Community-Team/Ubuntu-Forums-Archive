---
title: "Permissions Trouble Preventing Login"
date: 2006-03-09
forum: General Help
---

### Post by astrofrank128 on 2006-03-09
Hello,

One of my friends, who has my password, decided to "help me out", since I'm relatively new to the Linux scene. As a result, I am left unable to login. He typed the following into a terminal:

```
sudo chmod -R 775 /
```

So now all of my permissions are set to 775. When I attempt to login, I get a message telling me that my $HOME/.dmrc file has the wrong permissions and should be set to 644. Also, I get an error that says I am unable to login and gives me a few possible reasons (something about an administration or access file unable to be read?). I went into recovery mode, logged in as root, and typed:

```
chmod 644 $HOME/.dmrc
```

Which did nothing (I may be typing it wrong). Of course, even if that did work, I'm afraid that many of my permissions are messed up now. I'm hoping that the solution for this isn't unbelievably complicated, as it was pretty easy to do in the first place. Needless to say, I'm changing my password after this gets fixed...

---

### Post by Sutekh on 2006-03-09
```
sudo chmod -R 775 /
```
is not good.  

So I would try this command on your filesystem
```
sudo chmod -R 755 /
```

---

### Post by Mustard on 2006-03-09
Seriously, I think your 'friend' has just totally borked your system.

---

### Post by lamego on 2006-03-09
Never, but never do a -R / command on your system unless you know what you are doing (which was not the case).
If have set the same permissions (775) to all files on your system,  now it is unsafe a nd a lot of things may not work.
Reinstall your system and next time get for some help here first :)

---

### Post by astrofrank128 on 2006-03-13
Thank you guys for your help, and also for your quick responses! I have re-installed the system and blacklisted Sid the computer frier from within 10 feet of my computer.

---

