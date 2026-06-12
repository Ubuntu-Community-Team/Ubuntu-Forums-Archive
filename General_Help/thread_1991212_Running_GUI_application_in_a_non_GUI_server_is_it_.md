---
title: "Running GUI application in a non GUI server is it possible?"
date: 2012-05-30
forum: General Help
---

### Post by shaikzubair on 2012-05-30
Hello,

I use Windows 7 and Ubuntu-Server with GUI desktop. I am planning to completely remove GUI in Ubuntu and work with non-gui environment. 

I was wondering if there is a way to access GUI application in a NON-GUI server.

Regards

Zubair.

---

### Post by CharlesA on 2012-05-30
Forward X over SSH.

```
ssh -X user@host
```

If you are using Windows, you would need an xserver like XMing or Cygwin.

---

### Post by shaikzubair on 2012-05-30
> **CharlesA said:**
> Forward X over SSH.

```
ssh -X user@host
```If you are using Windows, you would need an xserver like XMing or Cygwin.

ssh -X doesnot work in non-GUI platform.

---

### Post by CharlesA on 2012-05-30
> **shaikzubair said:**
> ssh -X doesnot work in non-GUI platform.
Yes it does.

You need a GUI application installed, of course.

If you are using putty, you would need to enable X11 forwarding.

EDIT: For some reason, I was not able to get X forwarding to work via putty and XMing, but going Ubuntu server --> Ubuntu desktop worked fine.

---

