---
title: "why does PuTTy look wrong?"
date: 2012-06-25
forum: General Help
---

### Post by stupidquestion on 2012-06-25
I use PuTTy to connect to Ubuntu by SSH. Sometimes the texts are not visible unless I select them with mouse first, and sometimes I get gibberish non-English characters. This makes it difficult to understand the configuration sometimes. What can I do to make PuTTy look normal? 

Or if you don't use PuTTy, what do you use for SSH?

---

### Post by bab1 on 2012-06-25
> **stupidquestion said:**
> I use PuTTy to connect to Ubuntu by SSH. Sometimes the texts are not visible unless I select them with mouse first, and sometimes I get gibberish non-English characters. This makes it difficult to understand the configuration sometimes. What can I do to make PuTTy look normal? 

Or if you don't use PuTTy, what do you use for SSH?

You can use the standard terminal to connect to a remote host via SSH.  Just open a terminal (cntl+alt+t) and type ```
ssh <remote_host>
```
^^^ Where <remote_host> is either the hostname or IP address of the remote host.

---

### Post by deathadder on 2012-06-25
As for putty I've never had that problem, does the "reset" command help at all when it goes wrong?

Since you're using putty I'm guessing you're connecting from a Windows machine? I've used [MobaXterm]("http://mobaxterm.mobatek.net/") without any problems when I've had to use a Windows machine.

---

### Post by stupidquestion on 2012-06-25
> **bab1 said:**
> You can use the standard terminal to connect to a remote host via SSH.  Just open a terminal (cntl+alt+t) and type ```
ssh <remote_host>
```^^^ Where <remote_host> is either the hostname or IP address of the remote host.

I am connecting from Windows so I need a SSH client first.

> **deathadder said:**
> As for putty I've never had that problem, does the "reset" command help at all when it goes wrong?

Since you're using putty I'm guessing you're connecting from a Windows machine? I've used [MobaXterm]("http://mobaxterm.mobatek.net/") without any problems when I've had to use a Windows machine.

Does it support key files? I'll take a look at it. ... I don't see support for keys under Sessions -> SSH.

---

### Post by gamblor01 on 2012-06-25
Another option would be to install cygwin and use that instead.  I install it on any Windows machine I touch, though I did have some issues building a binary at work on a Windows/cygwin environment so I ultimately had to switch to building it in MinGW.  However, if all you're looking to do is SSH, cygwin is more than capable.

---

### Post by Zvlwab on 2012-06-26
If you're using Google Chrome, you can use this plugin: [https://chrome.google.com/webstore/detail/pnhechapfaindjhompbnflcldabbghjo?utm_source=chrome-ntp-icon](https://chrome.google.com/webstore/detail/pnhechapfaindjhompbnflcldabbghjo?utm_source=chrome-ntp-icon)

---

### Post by deathadder on 2012-06-26
> **stupidquestion said:**
> Does it support key files? I'll take a look at it. ... I don't see support for keys under Sessions -> SSH.
It's, as far as I know, basically cygwin wrapped around some nice tabbed terminals. The SSH command looks like it takes all of the options my Linux box does, including the -i argument.

So you should be fine with keys, the MyDocuments folder points to you "My Documents" on your Windows install, so presuming the private key file is in there you can use something like:
```
> ssh -i MyDocuments/path/to/id_rsa -l username remote_host
```

---

