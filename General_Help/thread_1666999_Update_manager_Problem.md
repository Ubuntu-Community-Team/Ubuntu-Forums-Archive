---
title: "Update manager Problem"
date: 2011-01-14
forum: General Help
---

### Post by Brolyfanatic777 on 2011-01-14
Hello! =]

I'll start by saying that Linux is GREAT!!!! I'm on Linux mint 32-bit, I love it! My Sony vaio Flys now!

My issue is this, every time I go to the Update manager and manually check for new updates this dialogue box appears.

 
[IMG]http://c4.ac-images.myspacecdn.com/images02/141/l_f1db24221d004cc5ac4d0804a6ecf35b.png[/IMG]


What to do? I haven't a clue!

I almost forgot, yesterday i found out that one of my favourite programs (handbrake) finally updated, so I went to their site ([www.handbrake.fr]("http://www.handbrake.fr")) to see if they made it available for linux again. they did, and they provided a 3rd party PPL. I'm wondering if this somehow changed the default ppl for the update manager

Please Advise.

---

### Post by Habeouscorpus on 2011-01-14
You have to take those sources out of your source file. They're broken. The problem, I'm guessing, isn't with you or with Handbrake. The ppas probably got deleted.

Go to /etc/apt/sources.list (sudo gedit /etc/apt/sources.list), and edit the file so that you take out those web links. This way, your computer will not try to hit them for packages. Don't forget to save!

---

### Post by Habeouscorpus on 2011-01-14
You have to take those sources out of your source file. They're broken. The problem, I'm guessing, isn't with you or with Handbrake. The ppas probably got deleted.

Go to /etc/apt/sources.list (sudo gedit /etc/apt/sources.list), and edit the file so that you take out those web links. This way, your computer will not try to hit them for packages. Don't forget to save!

---

### Post by Brolyfanatic777 on 2011-01-14
I'm sorry, I'm a bit of a newb, could you recommend a good tutorial? Or maybe walk me through it?

---

### Post by Brolyfanatic777 on 2011-01-16
is there anything else I can try?

---

### Post by plucky on 2011-01-17
> **Brolyfanatic777 said:**
> is there anything else I can try?

Open **Applications > Ubuntu Software Centre > Edit >Software Sources > Other Software** and un-tick the PPA as a Source and then exit.It will ask you to reload.Do so.

See if you still have errors.

If you do, please post output from a terminal of ```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

Good Luck

---

### Post by Brolyfanatic777 on 2011-01-17
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free

# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb games

---

### Post by Brolyfanatic777 on 2011-01-17
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free

# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb games

---

### Post by Brolyfanatic777 on 2011-01-17
total 16
-rw-r--r-- 1 root root  48 2011-01-17 08:27 local-repository.list
-rw-r--r-- 1 root root  48 2011-01-17 08:27 local-repository.list.save
-rw-r--r-- 1 root root 132 2011-01-17 08:27 user-ppa-name-maverick.list
-rw-r--r-- 1 root root 132 2011-01-17 08:27 user-ppa-name-maverick.list.save
 
No luck, Here are the requested terminal outputs

---

### Post by plucky on 2011-01-17
> -rw-r--r-- 1 root root 48 2011-01-17 08:27 local-repository.list
-rw-r--r-- 1 root root 48 2011-01-17 08:27 local-repository.list.save

Not sure what that is so post output of ```
cat /etc/apt/sources.list.d/local-repository.list
```

The other one is what is causing the error shown at the beginning.
So delete that list as it is not valid.

```
sudo rm /etc/apt/sources.list.d/user-ppa-name-maverick.list
```

Good Luck

---

### Post by Brolyfanatic777 on 2011-01-17
deb file:///usr/share/local-repository binary/

---

### Post by Brolyfanatic777 on 2011-01-17
The problem seems to have been resolved by me entering the second line you told me to enter. I no longer get the error message. I'll post back should any other problems arise.

Many Many many thanks

Jim

---

### Post by plucky on 2011-01-17
> **Brolyfanatic777 said:**
> deb file:///usr/share/local-repository binary/

That means nothing to me.Can you remember why you are using that as a source?

If you still have a problem I would disable it by putting a # in front of the line,so it looks like ```
#deb file:///usr/share/local-repository binary/
```

Good Luck

---

