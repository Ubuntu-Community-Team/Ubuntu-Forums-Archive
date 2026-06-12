---
title: "Ubuntu 9.04, accidentally lost admin privileges"
date: 2011-01-09
forum: General Help
---

### Post by Schuby007 on 2011-01-09
Hi,

I'm new to Linux. I installed Ubuntu 9.04LTS and in an attempt to make my account more secure I went in under my user and unchecked all privileges and restarted. I figured this would make it so that it would ask for my password before I try to do anything advanced. Instead when I go to something "advanced" it asks for my password, I supply it and then an error message comes up saying I don't have rights or something like that.

Can someone explain how to get admin privileges back. I thought I might sign into root but I set my user account to automatically sign in on system start so I'm not sure how to gain root access.

Thank you,
Schuby
P.S. I'm not sure why they call it Long Term Support when they've stopped supporting 9.04 after less than 3 years. Microsoft is still supporting Windows XP after over 5!

---

### Post by Kljuka on 2011-01-09
Hey Schuby,
you should follow the standard way of recovering password: 
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

About Long term support:
Ubuntu 9.04 is NOT long term support. The ones that are: 8.04 LTS, 10.04 LTS. So basically every 2 years, there comes a release with long term support. The last one was 10.04 (which came in April 2010) and will be supported until:
April 2015 - Server version
April 2013 - Desktop version

So 5 years. You can check it also here:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by Schuby007 on 2011-01-10
Hi Kljuka,

Thank you for the quick reply and for the clarification on the Ubuntu Long Term Support editions.

I know what my password is, I just don't think it's working because I disabled the "System Administration" privilege from my user account. Is there any way to boot up in the root account and go back and enable "System Administration" for my other account? This would mean running in the gui because I have no idea what I'm doing at a cli.

Thank you,
Schuby
P.S. Could I use the **SHIFT or Esc** at the grub prompt to get to root@something and from there could I activate the desktop? Like start x server?

---

### Post by Schuby007 on 2011-01-11
Is it possible to login as root via SSH? I've setup SSH on the computer before I lost admin privileges and I'm able to connect to it by remote using my account but when I try to login as root it asks for a password and I don't know what that is. I don't recall being asked to supply a root password during Ubuntu setup.

Thanks,
Schuby

---

### Post by Elfy on 2011-01-11
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

This should help you.

You are I think a "Case 1: If you'd removed your last admin user from the admin group, then type"

---

### Post by Elfy on 2011-01-11
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

That should help you sort the admin out.

You'll need to boot into recovery mode to deal with it.

---

### Post by Schuby007 on 2011-01-12
Hey forestpiskie,

Thanks for your reply. That is my exact problem! That website has a solution that will fix it for me. However after some more research I think once I get into Recovery Mode and "drop to root shell" I'm gonna run:
```
sudo passwd root
```

to enable the root account. Because I like to administer the system by remote and it would be much easier to simply log into root and that way I can keep the extra security on my regular account.

In reality I didn't really set it up right. During installation I should have created an admin account and then created my lower privilege account that I share with others.

Thanks again for the help. I just wish there was a way I could do this without having to go into the boot menu because my usb keyboard won't work on that level so I need to find a ps/2 one lol

---

