---
title: "First install, first problems"
date: 2009-08-04
forum: General Help
---

### Post by J V on 2009-08-04
Switch user while both logged on means no-one can get in until the user actually switches cause all buttons except unblock are disabled.

Can´t find way to get logo to show up on login form, although its set right in settings, it still shows the ubuntu logo on the login form.

Cant find hardware stats (got a gnome-dxdiag or something?) that will let me find out what video drivers I need.

Any idea how to fix these?

---

### Post by coldReactive on 2009-08-04
> **J V said:**
> Cant find hardware stats (got a gnome-dxdiag or something?) that will let me find out what video drivers I need.

There is no DirectX Support for Linux. (Not sure about Wine, it might use some translation or faking method.)

If you need to know how much RAM you have, open up System Monitor under System > Administration. But if you need to know how much VIDEO RAM you have... well, you'll have to wait for someone to answer that (If you have Intel, it's most likely you won't be able to know.)

---

### Post by credobyte on 2009-08-04
For hardware information, install hardinfo:
```
sudo apt-get install hardinfo
```

---

### Post by wojox on 2009-08-04
```
sudo lshw
```
Shows hardware specs

---

### Post by harry2006 on 2009-08-04
running lswd should be enough to give you details of all your hardwares...

---

### Post by J V on 2009-08-04
Thanks for the lshw/lswd tips, I didn't want to have to download a new program, and my use of dxdiag was pureley analogic ;)

Any advice on the switch user thing? (Its the necessary one atm)

---

### Post by J V on 2009-08-05
Is there any way to bump these things other than spamming?

---

### Post by J V on 2009-08-05
By the way, if you want to look at some of the ubuntu source, how the hell do you find the package?

I mean, if I were to want to look at the source for the login screen for example, how do I find it? Its not like they are descriptively named...

---

### Post by nothingspecial on 2009-08-05
Ok, I`m not sure what your first post means exactly.

You are having some problem with the user switcher applet.

Can you elaborate?

---

### Post by J V on 2009-08-05
Well when I have 2 users and they are both logged on (8.04 btw) and I switch from one to the other, through the switch user menu that is enabled by defaul, it goes straight to the lock screen menu, and the only button that works is the "Unlock" button which requires a password.

Effectivley meaning if that user doesn't actually switch then no-one can get on.

---

### Post by J V on 2009-08-05
Bump for #1, #7, #8...

---

### Post by J V on 2009-08-06
I'm gonna set up a cron to bump this :D

---

### Post by J V on 2009-08-06
bump... how many in a row now?

---

### Post by J V on 2009-08-07
The majority of my posts are bumps for this thread, this is starting to look like payed support actually has a purpose!

bump...

---

### Post by P4man on 2009-08-07
not sure about 8.04, but in jaunty, I just have to press escape. Then it asks me for the user name, and i can just enter the username of the "first" user, and type his password to get back to his session.

edit: btw, bumping may work contra productive. I noticed the thread, but saw a lot of replies, so i figured your issue was being taken care off, so i ignored it.

---

### Post by J V on 2009-08-07
I see, thanks...

any suggestions on the bump issue? Just make a new thread for every bump? :o

---

### Post by P4man on 2009-08-07
You probably won't need to bump if you would use a more meaningful post title, and post 1 thread per issue.

---

### Post by J V on 2009-08-07
Ah yes, I tend to make that mistake a lot lol ](*,)

---

