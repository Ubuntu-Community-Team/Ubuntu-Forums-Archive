---
title: "Adobe reader installed but useless"
date: 2010-04-30
forum: General Help
---

### Post by arashiko28 on 2010-04-30
I had this post on the development area but now it's closed and in-concluded.
I have now only 10.04 installed, 64-bit and adobe reader installed but does not work, I did exactly the same thing as when on 9.10 to download and install which was:
> sudo dpkg -i --force-architecture AdbeRdr9.3.2-1_i386linux_enu.deb 

And when try to run it... nothing, so I went to terminal and got this message

> exec: 691: /opt/Adobe/Reader9/Reader/intellinux/bin/acroread: not found

I really need it, please help!

---

### Post by user333 on 2010-04-30
I personally hate adobe reader, just because it is so slow and has crazy errors. What about using foxit? That seems to work just fine on linux.

---

### Post by nanog on 2010-04-30
remove in synaptic or by issuing dpkg -r  and install via the official canonical repo:

[https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=thirdpartydefault2.png](https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=thirdpartydefault2.png)

or 

```
sudo echo 'deb http://archive.canonical.com/ubuntu' >> /etc/apt/sources.list
```

```
sudo apt-get install acroread
```

---

### Post by arashiko28 on 2010-04-30
> **user333 said:**
> I personally hate adobe reader, just because it is so slow and has crazy errors. What about using foxit? That seems to work just fine on linux.

I have never had any sort of problems with it, I'll try it, but still need adobe.

---

### Post by arashiko28 on 2010-04-30
> **nanog said:**
> remove in synaptic or by issuing dpkg -r  and install via the official canonical repo:

[https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=thirdpartydefault2.png](https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=thirdpartydefault2.png)

or 

```
sudo echo 'deb http://archive.canonical.com/ubuntu' >> /etc/apt/sources.list
```

```
sudo apt-get install acroread
```

Thanks, it worked like a charm!

---

