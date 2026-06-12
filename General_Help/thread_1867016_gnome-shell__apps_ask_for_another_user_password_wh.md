---
title: "gnome-shell : apps ask for another user password when admin rights are needed"
date: 2011-10-22
forum: General Help
---

### Post by Sisyphe on 2011-10-22
Hello,

I upgraded to ubuntu 11.10.
This machine has two users named *ubuntu* and *eddy*. 
Both are in the admin group.

If an app (synaptic, e.g.) asks for admin rights, *eddy*'s password is rejected : the apps asks for *ubuntu*'s password.
If user *eddy* gives *ubuntu*'s password then it is accepted.

But the problem happens only when I use the gnome-shell interface. 
With unity, I can choose which user's password to enter.
In gnome-shell, I have no such choice : user eddy is always asked for user ubuntu's password.

I tried suppressing eddy's account and deleting his home then recreated it but there was no change. 
I even tried creating it using the useradd command instead of the system configuration gui app.

It is not a permission problem per se : sudo, gksudo and gksu all work perfectly for user eddy using his own password.
It seems more like a gnome3 problem asking for the password of someone else.

It is a real problem : for eddy to use apps which require admin rights, he musts start them
from a terminal using gksu(do) or use the unity interface. 

I haven't been able to find a solution so any help is appreciated.

Thanks

---

### Post by dcstar on 2011-10-22
> **Sisyphe said:**
> Hello,

I upgraded to ubuntu 11.10.
This machine has two users named *ubuntu* and *eddy*. 
Both are in the admin group.

If an app (synaptic, e.g.) asks for admin rights, *eddy*'s password is rejected : the apps asks for *ubuntu*'s password.
If user *eddy* gives *ubuntu*'s password then it is accepted.

But the problem happens only when I use the gnome-shell interface. 
With unity, I can choose which user's password to enter.
In gnome-shell, I have no such choice : user eddy is always asked for user ubuntu's password.
..........
I haven't been able to find a solution so any help is appreciated.

Thanks

I think that I have seen at least one other post with this exact problem, you may want to try and search it out and see if a bug has been reported.

---

### Post by Sisyphe on 2011-10-23
> **dcstar said:**
> I think that I have seen at least one other post with this exact problem, you may want to try and search it out and see if a bug has been reported.

Thanks for your reply.


Of course I should have mentioned that I searched (in this forum and pretty much everywhere) for more than a week before posting here.

The closest I found to my problem is
[http://ubuntuforums.org/showthread.php?t=1847749&](http://ubuntuforums.org/showthread.php?t=1847749&)
and it doesn't apply to me since my user eddy is in the admin group.

I also saw another one about gconf-editor to make sure that gksu is in sudo mode but that is also already the case.

---

### Post by Sisyphe on 2011-11-05
After all this time no solution was found.

I finally deleted user ubuntu from the console
```
sudo deluser --remove-all-files ubuntu
```
and the problem has disappeared.

I insist on « disappeared » and not « solved » since nobody is able to understand what happened and deleting users is not always an option.

By the way, this is only one of the many bugs I met after upgrading to 11.10
What a waste of time. Thanks to Debian, I don't use ubuntu for production, just for wasting time when I need to procrastinate.

---

### Post by Flo12 on 2011-11-29
Hello,
I have exactly the same problem, and I would like to find another solution that deleting the other account ! I have already posted on the French forum where I found someone with the same problem but also no solution.
The problem appeared after upgrading to ubuntu 11.10 and installing gnome-shell from Synaptic.
Anyone got any ideas?
Thanks in advance.

---

