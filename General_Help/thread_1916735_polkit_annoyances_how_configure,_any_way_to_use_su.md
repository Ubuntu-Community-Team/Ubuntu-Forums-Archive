---
title: "polkit annoyances: how configure, any way to use sudo instead?"
date: 2012-01-28
forum: General Help
---

### Post by fitzhugh on 2012-01-28
Is there any way to switch from polkit to sudo? 

I know there are valid reasons for using polkit, but in my case it causes more problems than it solves, and I doubt I'm alone in this.

Like requirements to use difficult, long, and secure passwords that end up being written down on a post-it on the monitor, this is such a wonderfully secure hassle that I am desperite to defeat it entirely.

I do use a super long password, makes entering it over and over a real pain. I change my system and reinstal it often enough that this drives me crazy.

My computer is safe from meddling when I'm logged in, and is locked when I'm not using it. I only worry about someone accessing it after stealing it. I have the drive encrypted and will probably add an encrypted folder (tried both drive and home ... just crawled)*. Sudo set to not timeout or use NOPASSWD:ALL was ideal.


I read a post somewhere here that showed how the timeout for auth_admin_keep and auth_self_keep are hardcoded at 5 minutes, and while the earlier policykit had auth_self_once (or something like that) the new version doesn't recognize it. 

So, as asked above, what can I do to remove it? 

Thanks!

*actually, I guess I live a very boring life. They wouldn't get anything of interest even if they had full access, but I like to pretend I'm important enough that someone would actually care about my crap, and that my crap consists of all VITAL SECRETS. Oh well. I couldn't come up with a real reason to encrypt, but not admitting the truth was reason enough to accept the performance hit of encrypting. And using a long password.

---

