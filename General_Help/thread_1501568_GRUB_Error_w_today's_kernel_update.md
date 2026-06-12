---
title: "GRUB Error w/ today's kernel update"
date: 2010-06-04
forum: General Help
---

### Post by UserDemos on 2010-06-04
Hello all,

This morning, I installed new kernel updates. I rebooted my computer and got the following error:

"Minimal Bash-like line editing is supported. For first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions." (There might have been more, but that's all I wrote down). 

I have no idea what to do. I got on a friend's computer and used the following way to boot into my system: [http://ubuntuforums.org/showthread.php?t=1437104](http://ubuntuforums.org/showthread.php?t=1437104)

But unfortunately, this hasn't really fixed anything. I still have to use that fix to get in. Can anyone help me? I'm not sure what to do in this case. I am using a Dell Inspiron 9300, only Ubuntu 10.04 installed. Let me know if you need any other info to help me with this problem. 

Thanks a lot (and in advance)!

---

### Post by yetiman64 on 2010-06-04
After managing to get back in did you do in a terminal

```
sudo update-grub
```?

---

### Post by UserDemos on 2010-06-04
No I didn't, I see now I must have accidentally skipped that step. I will do that now and report back the results.

---

### Post by UserDemos on 2010-06-04
Thank you for pointing out my simple mistake. The update-grub worked great! No more issues. Thank you!

---

### Post by yetiman64 on 2010-06-04
You're welcome, and could you mark the thread as solved with the thread tools drop down menu at the top of your browser window, thanks.

---

