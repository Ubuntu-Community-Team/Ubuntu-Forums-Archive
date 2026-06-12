---
title: "Nautilus - trivial for any program to get root privileges"
date: 2012-01-22
forum: General Help
---

### Post by ivan15 on 2012-01-22
Hello,

I have noticed one strange thing. I have downloaded unetbootin and checked "Allow execute as program" on "Permissions tab". Then I have double-clicked on it and program have been running with root privileges (because it could get acces to /root/).

If I run the program from terminal, it normally asks me for password. But when I double click on it in Nautilus, it does not ask me for any password, just run with root privileges.

I am usigin Ubuntu 10.04 LTS (and have all patches installed).

Please, is it normal behaviour? How can I make Nautilus to ask me for password too?

Thanks, Ivan

---

### Post by searchfgold6789 on 2012-01-22
Just install it with Synaptic or Software Center. Then you won't have to worry about any of that.

---

### Post by snowpine on 2012-01-22
My guess why you are seeing this behavior is that your system has a 15-minute timeout for the sudo password, and you had already entered your password within the 15 minutes. If you reboot (or wait a while) then unetbootin should ask for your password as you'd expect.

If you want to edit the timeout, the Ubuntu wiki explains how: [https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

Again, that is just a guess without knowing more details. :)

---

### Post by ivan15 on 2012-01-22
> **snowpine said:**
> My guess why you are seeing this behavior is that your system has a 15-minute timeout for the sudo password, and you had already entered your password within the 15 minutes. If you reboot (or wait a while) then unetbootin should ask for your password as you'd expect.

If you want to edit the timeout, the Ubuntu wiki explains how: [https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

Again, that is just a guess without knowing more details. :)

Yes, that was the problem. Thanks ;)

---

### Post by snowpine on 2012-01-22
Neat, I [just read]("https://help.ubuntu.com/community/RootSudo#Reset_sudo_timeout") that you can reset the time out (for example if you are walking away from your desk) with:

```
sudo -k
```

---

