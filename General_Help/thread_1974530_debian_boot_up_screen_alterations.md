---
title: "debian boot up screen alterations"
date: 2012-05-06
forum: General Help
---

### Post by kolo-01 on 2012-05-06
hi,

i currently dual boot windows and ubuntu, however on the debian boot up screen there are around 7 options which include safe modes and system tests and a lot of other things which i do not use, what am i looking to do is change the screen to make just two options- has anyone been in this situation and found a solution to this?
any help appreciated, thanks

---

### Post by llamabr on 2012-05-06
[http://www.howtoforge.com/working_with_the_grub_menu](http://www.howtoforge.com/working_with_the_grub_menu)

However, just because you don't use them doesn't mean that you won't someday need them.  Safe modes and older kernel images may come in handy.

---

### Post by L3ct3rIII on 2012-05-06
You could use [StartUp Manager]("http://packages.debian.org/source/sid/startupmanager"). On Debian, if you don't have it already there, you can install it with the following command on terminal:

```
apt-get install startupmanager
```You will find the options you need on the "Advanced" tag. You can use [this tutorial]("http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html") to learn how to use it.

Hope it will be useful.

See ya.

---

### Post by kolo-01 on 2012-05-06
> **llamabr said:**
> [http://www.howtoforge.com/working_with_the_grub_menu](http://www.howtoforge.com/working_with_the_grub_menu)

However, just because you don't use them doesn't mean that you won't someday need them.  Safe modes and older kernel images may come in handy.

I understand that I may use them some time in the future, I was going to put this in the original post as extra, but there is little point them being there all the time and having to scroll down 7 times if ever i need to launch windows.

---

