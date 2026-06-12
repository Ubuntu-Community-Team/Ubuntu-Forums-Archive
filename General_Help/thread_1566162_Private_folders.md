---
title: "Private folders"
date: 2010-09-02
forum: General Help
---

### Post by komitaltrade on 2010-09-02
What is the best way to create private folders?

Network from PC (all PC clients are with HDD), but also with server.

All PC users are logged on same (one one PC) GNOME session (and they are not logged always on same PC), but I need private folders created for PC users.

---

### Post by Joe of loath on 2010-09-02
What's wrong with the user's /home directory? It's pretty private :p

---

### Post by Rubi1200 on 2010-09-02
Why not set folder permissions for each user?

Look here as a starting point:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by komitaltrade on 2010-09-02
Maybe I wasn't clear enough.

All PC users using same GNOME session. PC have just one GNOME desktop users session (administrator GNOME session is hidden).

So, it is not possible to set in home directory different permissions (for different PC users) for same GNOME user.

---

### Post by DeMus on 2010-09-02
> **komitaltrade said:**
> Maybe I wasn't clear enough.

All PC users using same GNOME session. PC have just one GNOME desktop users session (administrator GNOME session is hidden).

So, it is not possible to set in home directory different permissions (for different PC users) for same GNOME user.

In other words: you have 1 user account with 1 home folder.
Why?
Why not let everyone have his/her own account with matching home folder? So much easier.

---

### Post by limestone on 2010-09-02
As long as you don't have different users you cant do that i think...

---

### Post by scorp123 on 2010-09-02
> **komitaltrade said:**
>  All PC users using same GNOME session. Linux is a multi-user system ):P

You should really give everyone their own account. Problem solved. There really is absolutely no necessity to have everyone (auto-?) login into the same account. This will just create trouble.

---

### Post by komitaltrade on 2010-09-02
All of you are wrong.

i will give you example with Cyber Cafe. 

There is impossible to create user account (GNOME session) for every user, at least because any cyber control software don't support logout. But, most of the cyber have memberships (where is desired option to create private space for every member).

Example is Softvision Explorer where every user dont have ANY access (like user, not like application) to local disk. His disk (lets to say Home) is created on server disk. 

For me is acceptable (ideal) to make it same (except how they have windows server and I have Ubuntu server and I don't need it for Cyber Cafe).

---

### Post by scorp123 on 2010-09-02
> **komitaltrade said:**
>  i will give you example with Cyber Cafe.  Different topic entirely, you're comparing apples and oranges. In a Cyber Cafe you'd create a kiosk mode .. done. Everytime the session is logged out the account resets to a pre-defined default, nothing the user does to his session is persistent.

That's not what you asked though in the first posting. If you want a kiosk-like setup then say so. Other than that letting everyone into the same desktop session is wrong, wrong, wrong.

---

### Post by komitaltrade on 2010-09-02
This is a little embarrassing for me, but, please read what I asked.

You (scorp123) wrote "*In a Cyber Cafe you'd create a kiosk mode .. done.*".

I didn't ask that (I know to do it).

I asked opposite.

In Softvision Explorer manual pages is written:

"*[COLOR=Red]**User   drive**[/COLOR][COLOR=Red] : Normally the user drive is created   on the server in the shared "\\ServerName\Softvision Explorer Data"   folder. The items in this group can be used to save the user drive data   in a different network position[/COLOR] or request the drive to be directly created   on the computer client. However, in this case, on logging out the user   could lose all his/her saved data.*"

I wrote how "I don't need it for Cyber Cafe", but I need same solution like in Softvision Explorer (now underlined with red color, to be 100% clear what I want).

Example - students using same PC and same GNOME user session, but _**[COLOR=Red]they need they own user drive data [/COLOR]**_(in a different network position or in server HDD).

So, put out Cyber and Kiosk ideas (opposite), I used Cyber example to exp&#314;ain what I need ([COLOR=Red]**public PC with private user drive data**[/COLOR]).

---

### Post by Joe of loath on 2010-09-02
A USB stick?

---

### Post by Vaphell on 2010-09-02
and how exactly you make sure that the person using shared desktop doesn't leave his data accessible to the next user in that app you talk about? imo this is nothing more than an ugly hack.

---

### Post by komitaltrade on 2010-09-02
Why USB stick when it is plenty of HDD on network???

Why hack, I don't get it???

More close example.

TrueCrypt let us to make virtual encrypted drives (on entire network if samba is installed).

I just asked for more elegant solution, like Softvision Explorer, where this encrypted drive is created when user account is created (inside the GNOME session) and drive is mounted when user is logged and unmounted when user is logged out.

---

### Post by scorp123 on 2010-09-03
> **komitaltrade said:**
> This is a little embarrassing for me, but, please read what I asked.

You asked this:
***What is the best way to create private folders?***

... and you already received an answer for that. Give each user their own account + password and encrypted home directory. Done.

> **komitaltrade said:**
>  In Softvision Explorer manual pages is written:  Then please use that software, be happy and stop bugging us? ):P

> **komitaltrade said:**
>  (now underlined with red color, to be 100% clear what I want). And you assume that underlining it with red color will help because of .... what exactly?

We're Linux users here. We don't use Windows software 

> **komitaltrade said:**
>  Example - students using same PC and same GNOME user session, but _**[COLOR=Red]they need they own user drive data [/COLOR]**_(in a different network position or in server HDD). LOL, that's where you'd use LDAP + NFS (or SAMBA) and not this stupid and dirty hack of your's. Each student has their own account and their home directory gets mounted via the server. Result: they can login wherever they want and always have their files. And having it centrally on the server also makes backups easier.

> **komitaltrade said:**
>  I need ([COLOR=Red]**public PC with private user drive data**[/COLOR]). Give each user their own account + password. End of story.

I think we're done here. If you can't let go of your "Windows thinking" ... well, not my problem ):P

---

### Post by Chikitulfo on 2010-09-03
@Komitaltrade:
I think you came here to ask a question, but already having a vague idea of the solution you want for it.
People here are pointing out varied solutions for that problem that are pretty useful and I'm sure would work. But you already have your preconceived notion of what you want, and it is none of what you get.

The problem is: **What you really are asking for is a way to get what you want.** And you didn't ask that.

So if you want a solution you need to post the question really well explained of what exactly you are looking for, with a close example of the use you need for it. And with an accurate question, you'll get a close, accurate answer.

But please, don't ask vague things and then say we are not understanding you, because you are not making yourself clear.

You don't want a way to get private folders, you want *this* specific way to have private folders. And we still don't know what *that* specific way is...

---

### Post by dulbirakan on 2010-09-03
@scorp123: Dont you think that is a bit harsh?

And on a related note, I too think creating a seperate user for everyone is the cleanest solution... I dont see why this would not work. If your users are unknown atm. Then use a script for creating users on the go...

---

