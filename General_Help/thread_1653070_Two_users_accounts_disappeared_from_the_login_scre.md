---
title: "Two users accounts disappeared from the login screen."
date: 2010-12-26
forum: General Help
---

### Post by Cotopaxi on 2010-12-26
Hi I upgraded from Kubuntu 9.04 to 9.10 and everything went fine except that the upgrade eliminated Wicd and substituted it with Knetwork-manager. 

I managed to install Wicd via terminal, but in that process it asked me to authorize two Client users (my elder & my younger son) to use Wicd. When I was trying to find out how to authorize them both (I was still in terminal) the installation went on, WITHOUT any of these two Client users getting authorized.

Once Kubuntu starts up, the only user that appears in the login screen is the superuser (me).

Also I am not able to make any updates or upgrades.

Can anyone give me a helping hand please?

Thanks!

---

### Post by Cotopaxi on 2010-12-26
I just found out that the two Home folders of these Client users still exist and the User Management also recognizes both Client users, but there is no way they can log into their accounts.

Any hint?

Thanks!

---

### Post by Cotopaxi on 2010-12-26
no chance somebody gives me a hint? ;)

---

### Post by vangop on 2010-12-26
All I know regarding showing users in the login screen is that if UID>1000 - the user is shown, hidden otherwise.

---

### Post by Cotopaxi on 2010-12-26
Vangop:

Thanks for your reply, both users have UID 1001 and 1002 respectively.

What I am thinking about:

If I do a clean install from CD, without formatting the Home directory, will I be able to link the new users to their existing Home folders?

Again thanks for your help! :D

---

### Post by Cotopaxi on 2010-12-26
Bad news:

I don't know what the hell I did, but there is no home directory in this installation.

Hell, things are starting to get nasty:confused:!

---

### Post by Cotopaxi on 2010-12-26
Ok, I managed to solve it partially:
Originally, in the login screen the different users could be clicked and the user only had to type the password. These "clicable" users disappeared.

Now every user has to type in his name and the correspondent password.

If anybody knows how to make reappear the "clickable" users in the login screen, that would be great!

---

### Post by vangop on 2010-12-27
Hi!
System->Administration->Login screen.
Here you can setup this.

---

### Post by Cotopaxi on 2010-12-27
Vangop,

Thanks for that one, I will try it out, once I am back home! :popcorn:

---

### Post by Cotopaxi on 2010-12-31
Ok, I found the solution:

It looks like on 10.04 and 10.10 the login screen with "clickable" user disappeared.

But at the login screen settings I could download more themes for the login screen and that did the trick!

Vangop, thanks again for your help! :popcorn:

---

