---
title: "ubuntu single sign-on"
date: 2011-07-20
forum: General Help
---

### Post by mokrates on 2011-07-20
I don't quite know, where to go with this 'bugreport'.

I have a problem with ubuntu's single sign-on (also related to signing on to this forum):

I use pwdhash (pwdhash.com). what pwdhash does (for those, who don't know) is to take the first two parts of a domain right-hand-side (so login.ubuntu.com and one.ubuntu.com both yield 'ubuntu.com') AND a password, and it generates a password (by means of a hash) for that website. (so 'ubuntu.com' and 'g0d' yield 's3Cur1T4', or sth. ;) )

my problem now is the following: why do launchpad.net and ubuntu.com share my login-credentials. I kinda don't like that. Credentials should be singular for exactly one website. (i understand credential-security that way) If launchpad wants to log me in via ubuntu.com, it should redirect me there, or other way round.
especially with pwdhash, i have the problem that, when i create my password for ubuntu.com, i cannot log in on launchpad, or the other way round. that sucks.

greetz,

mo

---

