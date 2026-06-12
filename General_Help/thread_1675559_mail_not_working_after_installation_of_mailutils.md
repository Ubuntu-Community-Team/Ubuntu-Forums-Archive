---
title: "mail not working after installation of mailutils"
date: 2011-01-25
forum: General Help
---

### Post by awclemen on 2011-01-25
Hello forum folks,

I recently upgrade my server from Jaunty to Lucid.  The mail command no longer works for my scripts, so I installed mailutils.  However, when I try to run mail, it doesn't seem to find it:

```
/home/frank# apt-get install mailutils
Reading package lists... Done
Building dependency tree
Reading state information... Done
mailutils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
/home/frank# mail
The program 'mail' can be found in the following packages:
 * heirloom-mailx
 * mailutils
Try: apt-get install <selected package>
```

This has worked before for my other servers in previous weeks, but for some reason that the two servers that I updated this week can't find mail.

Any ideas?

Thanks is advance for your help.

--Andy

---

### Post by SeijiSensei on 2011-01-26
I don't know what "heirloom-mailx" is, but I've installed the "[bsd-mailx]("http://packages.ubuntu.com/lucid/bsd-mailx")" package to get the command-line mail program.

---

### Post by awclemen on 2011-01-26
Thanks for your reply, SeijiSensei.

I actually just uninstalled and reinstalled mailutils and now, mail/mailx just works.... not sure what happened on the first install...

```
apt-get remove mailutils
apt-get install mailutils
```

---

