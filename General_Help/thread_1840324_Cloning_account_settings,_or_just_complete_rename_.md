---
title: "Cloning account settings, or just complete rename user account"
date: 2011-09-07
forum: General Help
---

### Post by mwade on 2011-09-07
Hello,

Is there a way to clone a user account settings (installed applications, settings etc etc) to a new account?  I have created an account and I need to change the user name to something else.  The problem is I have spent so much time configuring all the settings, installing programs etc for the account that I want to remove, or at least change the name so there is no traces of the original user name.

thanks,

---

### Post by haqking on 2011-09-07
> **mwade said:**
> Hello,

Is there a way to clone a user account settings (installed applications, settings etc etc) to a new account?  I have created an account and I need to change the user name to something else.  The problem is I have spent so much time configuring all the settings, installing programs etc for the account that I want to remove, or at least change the name so there is no traces of the original user name.

thanks,


is this what you need [http://www.rs-tek.net/wordpress/?p=1](http://www.rs-tek.net/wordpress/?p=1)

---

### Post by Habitual on 2011-09-07
```
sudo usermod -l <New Username> -d /home/<New Username> -m <Old Username>
```

NOTE: **This is a MOVE**, *not a COPY* action.

example usage:
```
sudo usermod -l mickey -d /home/pluto -m mickey
```

---

