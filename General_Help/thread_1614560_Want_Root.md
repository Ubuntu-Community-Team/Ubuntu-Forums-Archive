---
title: "Want Root"
date: 2010-11-05
forum: General Help
---

### Post by Data 1 on 2010-11-05
I own 8 servers, several of them I log in to as root daily.

I have my home computer, using ubuntu for the past 3 months or so.

I'm sick of not being able to see, change, alter other users files. How do I make my user into a root account on the ubuntu home conmputer?

Even when I put one of my server drives in a USB cradle I can't view the contents of folders owned by root. Root folders I created on the original server.

I'm not the sudo type, I want full control.

Thank you-

Jim

---

### Post by sisco311 on 2010-11-05
If you prefer su over sudo, then set up a root password.

[uhelp]community/RootSudo[/uhelp]

---

### Post by nl4m on 2010-11-05
> **Data 1 said:**
> I own 8 servers, several of them I log in to as root daily.

I have my home computer, using ubuntu for the past 3 months or so.

I'm sick of not being able to see, change, alter other users files. How do I make my user into a root account on the ubuntu home conmputer?

Even when I put one of my server drives in a USB cradle I can't view the contents of folders owned by root. Root folders I created on the original server.

I'm not the sudo type, I want full control.

Thank you-

Jim


I don't know if it will help, but you can try to unlock the root account. Type in the command promp <snip> without the quotation marks. ****

---

### Post by wilee-nilee on 2010-11-05
I think this site will give you some information that may be helpful.
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Data 1 on 2010-11-05
Hi and thank you all. I haven't read the article link in the latest post but so far I enabled the root account, logged in as root. Then I went to users and tried everything including adding the regular user to the root group. Still couldn't see other users files as a regular user.

Interesting stuff.... on to read the latest link.

---

### Post by sisco311 on 2010-11-05
> **Data 1 said:**
> Hi and thank you all. I haven't read the article link in the latest post but so far I enabled the root account, logged in as root. Then I went to users and tried everything including adding the regular user to the root group. Still couldn't see other users files as a regular user.

Interesting stuff.... on to read the latest link.

Oh, you have problems with file permissions, check out:
[uhelp]community/FilePermissions[/uhelp]
and
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by yetiman64 on 2010-11-05
A couple of links worth noting are,
> [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138) by bodhi.zazen  and
> [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) by aysiu.

Not just from the forum rules perspective (as important as they are) but from the a technical perspective as well (good tech info and further links etc)

Consider
> On the forums, however, in the past, before this "policy", all too often   people would simply instruct new users to set a root password to "fix"   their problems. This was done without explaining (not intended as an  exhaustive list):

1. The potential risks of setting a root PW.

2. How to lock the root account.

3. The nature of the problem and the preferred solution, ie linux  permissions, fstab, etc.

4. Setting a root PW can (or has in the past) caused new problems.

  Thus the intent of the policy is we  prefer if people educate new  users re: permissions, etc, etc, rather  then simply  instruct them to  set a root pw. I note one user has focused on permissions etc. :)

and this is also a point to consider with regard to recovery mode and a lost root password.
> *What potential problems come up for the forums when a root account is  enabled? Surely there's no problem with users enabling the root  account, right?*
Security aside, from a strictly support perspective, root logins  complicate support in a couple of ways. One situation is users enabling a  root account and forgetting their root password. It's come up more than  once that when a user has enabled the root account and forgotten her  root password, she is unable to boot into recovery mode, and then  alternate means of recovering the Ubuntu installation have to be  employed (more complicated means).As bodhi.zazen points out to gain a root shell,

> The preferred method of obtaining a root shell is :

     ```

sudo -i
``` This really negates the need to set a root password and any commands needing to be run as root can be done so very easily.

---

### Post by lisati on 2010-11-05
Closed for review.

Please read item 12 in the list of "don'ts" in [this]("http://ubuntuforums.org/showthread.php?t=885580") thread.

---

