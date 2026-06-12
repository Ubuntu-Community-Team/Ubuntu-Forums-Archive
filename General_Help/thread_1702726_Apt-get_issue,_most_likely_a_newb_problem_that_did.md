---
title: "Apt-get issue, most likely a newb problem that didn't exist until I touched it"
date: 2011-03-08
forum: General Help
---

### Post by SubparUserdo on 2011-03-08
Hello. I'm new to the forums.

When I try to run apt-get in any capacity, I get the following message in BASH:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

I read somewhere (another forum) to use the following command:

$ ps ax | grep apt

I don't understand a whole lot about that string. I think I'm telling it to show all auxiliary processes that have apt in the name? or some such? Anyway, I entered it, and this came up:

2632 ?        S      0:04 /usr/bin/python /usr/sbin/aptd
 2641 ?        S      0:06 /usr/lib/apt/methods/http
 2734 pts/0    S+     0:00 grep --color=auto apt


I have tried ^C, I have tried "rm" on "/lock". I got those solutions by googling the issue. I'm new to Ubuntu, and frustrated. I was simply using Google for my issues, and it was working, but this problem popped up, and I was seeing all the same solutions with no context, so I decided to join here and ask the question. I also searched ubuntuforums.org before I posted, and didn't see my problem.

](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by new_tolinux on 2011-03-08
did you also try putting "sudo" in front of your apt-get command?

Example:
```
sudo apt-get update
```

---

### Post by SubparUserdo on 2011-03-08
Oh, yes I did. I use "sudo" in front of all my apt actions. But I was just about to post again, letting you all know that it seems it was simply a matter of waiting for the processes to die on their own. I just ran

$ sudo apt-get update

Worked like a charm. Thanks for the reply, though. I may have similar problems in the future that are just as noobish. You have been warned.

---

### Post by new_tolinux on 2011-03-08
No problem, but please don't forget to mark this thread as "solved" ;)

I didn't forget my first days wit linux (and before that: DOS), although I hesitated a little before I asked the question..... but then again, "is the plug connected" solves most of the problems, so I did :P

---

### Post by SubparUserdo on 2011-03-08
I've been trying to figure out how to change the thread to "solved". No such luck D:

---

### Post by SubparUserdo on 2011-03-08
I totally just found it.

---

