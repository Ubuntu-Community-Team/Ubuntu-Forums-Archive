---
title: "Password not recongised?"
date: 2012-01-03
forum: General Help
---

### Post by helliewm on 2012-01-03
This my is really weird I have used Ubuntu for the past 6 years and have always used the same password for logging in/sudo.

Last week I had numerous things open and whilst I was in working in Chrome my Ubuntu password was asked for. Not thinking I typed it in as it looked like Ubuntu wanted to download some updates. However ever since then I cannot log into Ubuntu? I did at the time wonder why I was being asked for it but did not think too much to it.

I am accessing Ubuntu by the guest account? Fortunately I have a separate Home Folder so I shall reinstall Ubuntu and use another password.

Have I been hacked or is it a case of me doing something stupid without realising it?

Yes it is definitely the correct password I am using. 

Helen

---

### Post by sanderd17 on 2012-01-03
Maybe you get the wrong keyboard configuration when you log in.

Try to open a terminal and do 
```

su username

```

where username is your user name. I hope it works, I'm not sure though.

Then it should ask you to enter the password.

If it works, try to look if the keyboard settings in the login screen are OK, or if you have multiple layouts installed (while you use only one layout).

---

