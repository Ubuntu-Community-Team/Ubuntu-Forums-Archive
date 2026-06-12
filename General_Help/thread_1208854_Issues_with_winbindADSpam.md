---
title: "Issues with winbind/ADS/pam"
date: 2009-07-09
forum: General Help
---

### Post by T3kn0m0nk3Y on 2009-07-09
I've gotten winbind with samba and kerb5 working so that I joined my 8.04 server to a windows 2008 server domain. works great, i can "wbinfo -u/-g" and get the right user/group lists

I can even login (sort of) with my domain admin account, but it gives me some errors before I ever get to a desktop.

First time I tried to login with my domain account, it said I had no home directory (/home/DOMAIN/username) was missing bla bla

So I created it. Now when i try to login it gives me the following:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writeable by other users"

if I click ok, it gives me another error:

"The system administrator has disabled your account."

I loged in as normal with a unix account and checked the dir permissions. Its listed as root:root, but whats weird is i can't chown to domainuser:domainuser so I'm not sure what the solution is?

---

