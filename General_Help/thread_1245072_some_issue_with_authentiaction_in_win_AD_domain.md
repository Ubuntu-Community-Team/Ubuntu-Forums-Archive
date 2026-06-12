---
title: "some issue with authentiaction in win AD domain"
date: 2009-08-20
forum: General Help
---

### Post by ubuscout on 2009-08-20
Hi people,

I'm just finish to follow
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

..and I've got my (virtualbox) ubuntu in my AD windows domain. Also my login authentication seem doing fine, I perform it with 'MYDOMAIN\myuser" without problem.

So it seem everithing is going fine :) ?!? ...almost... :P

When I browsing my network and clikking on my server share (please note it is a linux samba server) it show me a prompt asking me a password ?!? :(
But...  I think, I am just authenticated in domain ! ...why am I prompted to insert password again ?!? (Please note, of course if I insert password I get my share without problem... but I think I must not need do it too isn't it ?)


The command 'klist' give me this output:
----
Default principal: myuser@MYDOMAIN

Valid starting     Expires            Service principal
08/20/09 10:58:20  08/20/09 20:58:20  krbtgt/MYDOMAIN@MYDOMAIN
	renew until 08/27/09 10:58:20
08/20/09 10:58:20  08/20/09 20:58:20  UBUDESK$@MYDOMAIN
	renew until 08/27/09 10:58:20


Kerberos 4 ticket cache: /tmp/tkt0
----

thx in advance

---

### Post by ubuscout on 2009-08-21
...a polite toc toc..., anyone could help me to clarify this issue ?!?

thx

---

