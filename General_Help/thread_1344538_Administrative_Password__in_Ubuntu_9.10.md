---
title: "Administrative Password  in Ubuntu 9.10 ??"
date: 2009-12-03
forum: General Help
---

### Post by latimerio on 2009-12-03
Many system settings require root privileges.
  Gnome GUIs then pop up a dialog box asking for the administrative password.
  But Ubuntu has no root password by default (which I think is a good idea)

  I have activated my account in /etc/sudoers and I am also member of the admin group.
  *latimer   ALL = (ALL)  ALL*
  *admin:x:115:latimer*
  On the command line I can sudo to do my tasks but if for example I go to
  System -> Administration -> Bootup-Manager   I can not authenticate with my password.
  I googled around to find a solution but without success.
 Am I missing something important here?

---

### Post by akakingess on 2009-12-03
> **latimerio said:**
> Many system settings require root privileges.
  Gnome GUIs then pop up a dialog box asking for the administrative password.
  But Ubuntu has no root password by default (which I think is a good idea)

  I have activated my account in /etc/sudoers and I am also member of the admin group.
  *latimer   ALL = (ALL)  ALL*
  *admin:x:115:latimer*
  On the command line I can sudo to do my tasks but if for example I go to
  System -> Administration -> Bootup-Manager   I can not authenticate with my password.
  I googled around to find a solution but without success.
 Am I missing something important here?

First of all, I am not sure what you mean by "Boot-up Manager" so maybe that's why I am confused, but could you let us know of some more (if there are any) situations in which your password will not Authenticate?  Also, although I am 99.9% sure it has nothing to do with it, your user is part of the "root" group as well, correct?

---

### Post by latimerio on 2009-12-03
> **akakingess said:**
> First of all, I am not sure what you mean by "Boot-up Manager" 

In Karmic Koala there is a menu entry as I stated
  System -> Administration -> Bootup-Manager 
  The tooltip says: graphical runleve configuration tool
  alacarte gives the command line: su-to-root -X -c bum

And yes I am in the root group too.
I have not tested all other items but some do work when I enter my password others just come back with the authentication dialog.
E.g.  Synaptic Package Manager  does not work
whereas  Time And Date does work

BTW. The authentication dialog says "*Enter the administrative password*" which is confusing because there is no root password. It should better say just "enter your password" .
It would be desireable if there was a help button on each and every dialog that asks for authentication which then explains what must be done to get the authentication working.

---

### Post by lisati on 2009-12-03
> **latimerio said:**
> 
BTW. The authentication dialog says "*Enter the administrative password*" which is confusing because there is no root password. It should better say just "enter your password" .
It would be desireable if there was a help button on each and every dialog that asks for authentication which then explains what must be done to get the authentication working.

Isn't it possible in Karmic to set up users that *don't* have admin privileges?

---

### Post by akakingess on 2009-12-03
> **latimerio said:**
> In Karmic Koala there is a menu entry as I stated
  System -> Administration -> Bootup-Manager 
  The tooltip says: graphical runleve configuration tool
  alacarte gives the command line: su-to-root -X -c bum

And yes I am in the root group too.
I have not tested all other items but some do work when I enter my password others just come back with the authentication dialog.
E.g.  Synaptic Package Manager  does not work
whereas  Time And Date does work

BTW. The authentication dialog says "*Enter the administrative password*" which is confusing because there is no root password. It should better say just "enter your password" .
It would be desireable if there was a help button on each and every dialog that asks for authentication which then explains what must be done to get the authentication working.
I'm on Karmic 9.10, maybe that was something that you added or maybe you are using KDE instead of Gnome? Either way, it's hard to narrow down what's causing the problem or difference (depending on how you look at it) without knowing which ones work and which ones don't. If you are using Gnome, under the Applications menu, do you have the "Ubuntu Software Center" at the bottom of that menu, and if so, does it allow you to enter with your password? If it does, than that would be very odd, as it is the same as Synaptic Package Manager. I'll sit back and see if someone else can chime in with some more information, because I haven't seen or heard of this issue, and maybe you are using Kubuntu, I just don't know. I will try to help if I think I would be of assistance. Good luck, and if you could answer some of my questions maybe that would help me sort it out a little bit.;)

---

### Post by akakingess on 2009-12-03
> **lisati said:**
> Isn't it possible in Karmic to set up users that *don't* have admin privileges?

Yes, that's why I didn't even address that issue, sorry, if my kids were on this machine and attempted to do something that required authentication, then entering their passwords would do nothing, however, they could enter mine and we could do whatever it was they were trying that required admin/root privileges.

---

### Post by latimerio on 2009-12-03
> **akakingess said:**
> ..they could enter mine and we could do whatever it was they were trying that required admin/root privileges.

The authorization dialog from Ubuntu Software Center allows to pick a user and enter the admin password of that user.
In contrast to that the dialog box from System -> Administration -> ...  does not offer any user selection

Coming back to your questions:
Yes, I am using the standard gnome desktop
and yes, I can install packages through Applications -> Ubuntu Software Center.
The software center does only check for authentication when I pick a package whereas System -> Administration -> Synaptic Package Center asks for authorization right away.
The command line for the latter is:
[I]gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic 
[/I]and it does not accept my authentication no matter if I invoke it using the gui nor if I type it in a terminal window.

---

### Post by latimerio on 2009-12-07
Add-On:
When I set a root passwd in /etc/shadow the auth dialog from System > Administration > Synaptic Package Center works as expected.
I also tried with a 9.04 Ubuntu Gnome installation and there it works as expected when I use my user password.
So I assume that somehow the sudo mechanism in 9.10 is not implemented properly through all GUI tools.
Neither  su-to-root -X -c /usr/sbin/synaptic  nor gksu /usr/sbin/synaptic  work with my user password even though I am member of groups *root adm dialout cdrom floppy sudo audio video plugdev lpadmin admin sambashare* and my account is setup in sudoers with* ALL=(ALL) ALL*.

---

### Post by latimerio on 2009-12-08
Problem tracked down:

Today I found out that  running *gksudo /usr/sbin/synaptic *works perfectly.
Obviously there is a difference between  gksu  and gksudo which is not taken fully into account.
Especially the script  su-to-root  only makes use of gksu  which leads to the effect that a root password is required instead of the sudo mechanism.
Also *gksu *should be replaced by  gksudo in all Administration menu items and in /usr/sbin/su-to-root.

---

### Post by Iwillsurvive on 2009-12-20
> **latimerio said:**
> Problem tracked down:

Today I found out that  running *gksudo /usr/sbin/synaptic *works perfectly.
Obviously there is a difference between  gksu  and gksudo which is not taken fully into account.
Especially the script  su-to-root  only makes use of gksu  which leads to the effect that a root password is required instead of the sudo mechanism.
Also *gksu *should be replaced by  gksudo in all Administration menu items and in /usr/sbin/su-to-root.




I have the same problem.
How is it that you replace gksu with gksudo where and how?




                                         sign

                                          Iwillsurvive

---

### Post by latimerio on 2009-12-20
In the meantime I have filed bug 493961 at ubuntu for that. It is found at [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/493961](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/493961) and it describes the misery in full. If you register with launchpad bug tracking you can add yourself to  the bug by clicking on this affects me too. BTW. You can report bugs through the command ubuntu-bug.

---

### Post by cdt1334 on 2009-12-24
> **Iwillsurvive said:**
> I have the same problem.
How is it that you replace gksu with gksudo where and how?

Yes, do tell how you fixed the issue.  I am having that issue as well - I can enter in my password when I use sudo and it works fine.

However, when I try to install Opera, it wants my password and it keeps saying it's wrong.

-cdt-

---

### Post by Iwillsurvive on 2009-12-27
Yes I have fixed the issue sudo as part of login name unlocks the system.

---

### Post by Dougga on 2012-04-27
I believe I know what's going on here.

The authors of the BUM package (Boot Up Manager) do not follow any reasonable protocol of security. 

What they are asking for is the Administrative Password for the machine.

Ubuntu users generally have no idea what this password is.

I suspect if you set the root password with 'sudo passwd root' then run BUM using the new password, it will work.

[I'll try it now]

Yes, this works.  We Ubuntu users are simply unfamiliar with being asked for the root password.  It's an antiquated security practice.

I hope this helps.

Cheers!

---

