---
title: "How do I free the CLI after I start an application from it?"
date: 2011-02-24
forum: General Help
---

### Post by Mojo McCracken on 2011-02-24
When I run an application from the CLI, the CLI is bound to the respective application until I shut it (the application) down.

Is there a command to bypass this?

---

### Post by Habitual on 2011-02-24
```
commmand &
```
will background it.

---

### Post by Mojo McCracken on 2011-02-24
Thank you very much and have a nice day!

---

### Post by Mojo McCracken on 2011-02-24
Wait... Apparently this doesn't work with anything other than Firefox, and not at all when executed as an alias...

---

### Post by Vaphell on 2011-02-24
> Wait... Apparently this doesn't work with anything other than Firefox
i beg to differ

> and not at all when executed as an alias...
care to provide an example? because it works just fine: ```
ll &
```ll is an alias to ls --color=auto -alF

---

### Post by Habitual on 2011-02-24
Why on God's Earth do people NOT tell you the whole truth when they post is beyond me.

"application" vs. "alias"

**It works with applications AND aliases**:

```
alias masterdb
alias masterdb='ssh -qi /home/jj/.ssh/Tjoa/id_tjoa_c9_east root@x.x.x.x'

masterdb &
[2] 16322

C:\home\jj>fg
ssh -qi /home/jj/.ssh/Tjoa/id_tjoa_c9_east root@x.x.x.x
Last login: Thu Feb 24 06:30:15 2011 from x.x.x.x
     ___   _        __   __   ____            __    
    / _ \ (_)___ _ / /  / /_ / __/____ ___ _ / /___ 
   / , _// // _ `// _ \/ __/_\ \ / __// _ `// // -_)
  /_/|_|/_/ \_, //_//_/\__//___/ \__/ \_,_//_/ \__/ 
           /___/                                                 
                                              
Welcome to a public Amazon EC2 image brought to you by RightScale!

********************************************************************
********************************************************************
***       Your EC2 Instance is now operational.                  ***
***       All of the configuration has completed.                ***
***       Please check /var/log/install for details.             ***
********************************************************************
********************************************************************
[root@domU-12-31-39-16-C4-24 ~]# 
```

---

### Post by Mojo McCracken on 2011-02-24
I'm sorry, guys. Had my head up my ***. Accidentally wrote 

```
command & firefox
```

Works. Thanks for the help.

---

### Post by WorMzy on 2011-02-24
You can also background running tasks with Ctrl+Z

```
wormzy@sakura[pts/2]:~$ vim
[COLOR="Red"]#(Pressed CTRL+Z)[/COLOR]
zsh: suspended  vim
wormzy@sakura[pts/2]:~$ vim
[COLOR="Red"]#(Pressed CTRL+Z)[/COLOR]
zsh: suspended  vim
wormzy@sakura[pts/2]:~$ jobs
[1]  - suspended  vim
[2]  + suspended  vim

```

At this point, I can recall either job with the fg command.
e.g.
```
fg
[COLOR="Red"]#Recall last backgrounded task[/COLOR]
```
```
fg %1
[COLOR="Red"]#Recall job number 1[/COLOR]
```

However, this isn't very useful for GUI apps. You can't use an application while it is suspended.

---

