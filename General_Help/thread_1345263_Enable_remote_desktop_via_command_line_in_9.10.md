---
title: "Enable remote desktop via command line in 9.10"
date: 2009-12-03
forum: General Help
---

### Post by markrmcs on 2009-12-03
I've searched the internet and forums to solve this issue and have not been successful.

Specifically my issue is:

I am running 9.10 with compiz turned off. I want to be able to ssh into the machine and turn on remote desktop and then turn it off again before I terminate the ssh session.  When I am logged in locally to my machine I am able to enable and disable remote desktop via the command line using the following command:

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled (false/true)
```

If I ssh into the machine via vpn I can execute the command with no errors returned but it does not affect the state of remote desktop.

I have looked for a log that tells me what is happening but have not been successful.

If someone could point me to a source that will help me resolve this issue it would be appreciated.

Thanks in advance for any help.

Mark

---

