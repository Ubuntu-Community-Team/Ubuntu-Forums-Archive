---
title: "Auto-login and starting X without GDM"
date: 2009-10-27
forum: General Help
---

### Post by raptir on 2009-10-27
I've read a few posts about this, but I just wanted to clarify a few things before I do a minimal install of Ubuntu. I'm currently running Xubuntu 9.10rc, and I successfully stopped GDM from booting (commented it out in the default display manager file). I also have Xfce starting automatically when I log-in. I have two questions:

1) I currently have Xfce auto-starting by putting "startx" at the end of my ~./profile. Some posts I've read suggest having this in .bashrc, instead:

```
pgrep X &>/dev/null; [ $? = 1 ] && startx
```

What's the difference in the two commands? Also, on a somewhat related note (assuming I'm sort of understanding the difference in the commands), is there a way to not record all of the xsession error messages? I'm using an SSD, and I'd rather not have it writing to .xsession-errors every time my computer boots up. Moving the file to a different directory so I can put it on a RAM disk would be fine, as well.

2) How would I perform an auto-login without a display manager? Is it still safe to do this? I'm trying to install Ubuntu on an eee pc with a poor-performance SSD, so anything I could do to shorten boot-time would be an improvement.

---

### Post by raptir on 2009-10-28
Oh, and I was going to try SLiM, but it seems as though that's not in the repos anymore...

---

