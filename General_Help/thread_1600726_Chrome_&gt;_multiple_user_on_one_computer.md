---
title: "Chrome &gt; multiple user on one computer"
date: 2010-10-19
forum: General Help
---

### Post by pierreu1 on 2010-10-19
I have tried to look for this answer, but maybe it is my lack of knowledge on how to use users and groups in Ubuntu. I am sorry if this is an easy question for some or it has been answered before, but I am a newbie at using Linux and I did spent a lot of time (perhaps ineffectively) looking for the answer here and there (Google).

Basically, I would like to use Chrome (and other programs that did not automatically migrate to my other user's desktop (Lucid). I have tried to download the deb files like I did on the sudo/admin desktop, as I read this as a possible solution. Initially, an upgrade/update using synaptic did the trick, but then Chrome vanished from the other users' desktop/menu. Firefox installed automatically on the users though like many others! Why the discrepancy and what is the easiest way to allow a range of applications to be installed for all my users? Is using Samba the solution? This looks like an app for a server or computers and routers situation.

I would like to also know how to use properties for the different users. For instance, I think if one user belongs to a group, they can share files as long as those files have been made shareable. But, what about the different settings parameters when one click manage groups. There is a long list of different name like couchdeb and others. There is a the long list of those. I was not able to read anything about how to use these and what they all mean. BTW, did I install by mistake avahi and samba if I do not have a network of computers to configure?

Thanks for all the help and may these answers help others as well.

---

### Post by pierreu1 on 2010-10-22
Ok! Found an answer/solution.

It seems that Google does not want different users of a system to have Chrome (according to a discussion which I did not bookmark).

So, I uninstalled using the app Ubuntu software Center on my desktop or in system menu from the admin account (export the bookmarks) and then installed it in my user account, importing my bookmarks. Apparently there is a way to get a system wide download using a package, but I did not want to try it since I was not sure of the safety of the package.

Not sure if this post was put in the right forum section, but I will let admin confirm this and let me know! :)

---

### Post by sikander3786 on 2010-10-22
You want to share all installed software with all users on your computer?

All the software you install from the repositories gets installed for all the users. If you install it from .deb or source packages, it gets installed for the current user only.

If thats not the answer you were looking for, please explain a bit.

---

### Post by pierreu1 on 2010-11-08
Thanks! That worked!

---

### Post by vanangamudi on 2011-03-30
when i close chrome system hangs.

I'm using Ubuntu9.10 Karmic 

Please tell why it crashes.

---

### Post by sikander3786 on 2011-03-30
> **vanangamudi said:**
> when i close chrome system hangs.

I'm using Ubuntu9.10 Karmic 

Please tell why it crashes.
First of all, you should update your 9.10 install as it is scheduled to reach end of life in about a months time.

Secondly, we need you to start Chrome from Terminal (Applications > Accessories) by using this command.

```
chromium-browser
```

Then close it and paste the output from Terminal if possible as it might let us know more about the problem.

Alternatively, try removing and re-installing Chrome.

```
sudo apt-get remove --purge chromium-browser
```

```
sudo apt-get install chromium-browser
```

---

