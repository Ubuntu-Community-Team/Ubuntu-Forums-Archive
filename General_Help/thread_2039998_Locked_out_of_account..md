---
title: "Locked out of account."
date: 2012-08-10
forum: General Help
---

### Post by Lateralus138 on 2012-08-10
Hello I was messing around in the terminal and thought I could logout with the command
```

logout 

```
And of course that didn't work so I did "logout --help" (yes I know about "man logout") and didn't really see much and tried logout ian and ian logout and logout () and of course none of this worked so I rebooted and when I tried to log back in it would flash a black screen and go back to the login screen
I can log in as guest. I know better than to mess around like this I'm not as noob as my noob mistake sounds I was just being lazy to not Google the command or even look at MAN. Please help.

---

### Post by chadk5utc on 2012-08-10
Hello I did a quick search and found this hope it helps, I think it will.

[https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html](https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html)

---

### Post by Lateralus138 on 2012-08-10
> **chadk5utc said:**
> Hello I did a quick search and found this hope it helps, I think it will.

[https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html](https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html)
No that did not work
I get this message:
passwd: Authentication token manipulation error
passed: password unchanged

---

### Post by kostkon on 2012-08-10
> **Lateralus138 said:**
> No that did not work
I get this message:
passwd: Authentication token manipulation error
passed: password unchanged
What did you do exactly? Here's [a simpler how-to]("http://www.psychocats.net/ubuntu/resetpassword") with screenshots you can easily follow.

---

### Post by Lateralus138 on 2012-08-10
> **kostkon said:**
> What did you do exactly? Here's [a simpler how-to]("http://www.psychocats.net/ubuntu/resetpassword") with screenshots you can easily follow.
OK that let me change the password but it still does the same thing when I try to login. :confused:
It only flashes the black screen for a second but what I can read OS "could not write bytes: broken pipe"

---

### Post by steeldriver on 2012-08-10
see if you can log in at one of the virtual terminals (Ctrl-Alt-F1, Ctrl-Alt-F2 etc.) - if you can then it's likely just an xsession startup issue (possibly bad ownership on your .Xauthority file)

---

### Post by Lateralus138 on 2012-08-10
> **steeldriver said:**
> see if you can log in at one of the virtual terminals (Ctrl-Alt-F1, Ctrl-Alt-F2 etc.) - if you can then it's likely just an xsession startup issue (possibly bad ownership on your .Xauthority file)

Yeah I tried that when I first had the issue and I can login successfully.

---

### Post by Lateralus138 on 2012-08-10
That's exactly what it was change ownership of the file back to me and was able to log back in.  The owner had been changed to root. Thanks for your help problem solved.

---

### Post by steeldriver on 2012-08-10
Great - please mark the thread as 'SOLVED' using the thread tools

---

