---
title: "Need simple solution to sync folder contents daily"
date: 2010-01-31
forum: General Help
---

### Post by jimmy the saint on 2010-01-31
I have several laptops that I need to sync basic files between.  I also have a semi-dedicated home server I can use.  I do not want to use the cloud solutions, as my connection is way too slow and unreliable for that to be a viable option.  Also, I have limited (read none) scripting/programming expertise so an application recommendation would be better than a "hey, just write a script that does this" recommendation.  

Do any of you use software to accomplish this?  What would you recommend?

Thanks

JTS

---

### Post by fisheater on 2010-01-31
Option #1:
1.It isn't totally clear what you are doing with both laptops. If you have your files in one place (desktop/server/ or one laptop) you can leave the there and access your data via a VPN/SSH setup.

I had a similar situation: 1. all my files on my desktop, 2. taking my laptop out of the house and trying to work on my files, then sync/update my desktop and hope I didnt delete an updated file (which happened).

Disclaimer: Not associated with any of the programs suggested below.

Solution: use Nx Nomachine ([http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)). Works well, easy set up, very handy. All my files stay in one spot. Best part? There is a portable windows version that will run off a USB, thus any computer anywhere will allow you access to your files – even if you dont have you laptop! 


[http://blog.galerie-cesar.com/download-portable-version-of-nxclient-for-windows/](http://blog.galerie-cesar.com/download-portable-version-of-nxclient-for-windows/)
[http://tsukasa.jidder.de/blog/2008/09/02/making-the-nx-client-portable](http://tsukasa.jidder.de/blog/2008/09/02/making-the-nx-client-portable)

Good luck

FE

Failing the that try:
[http://synkron.sourceforge.net/](http://synkron.sourceforge.net/)
[http://portableapps.com/apps/utilities/toucan](http://portableapps.com/apps/utilities/toucan)

---

### Post by t4thfavor on 2010-01-31
rsync -auv source/dir dest/dir 

I think, you could mount the server as an sshfs mount point in a script, and run it when you get home every day. 

There are alot of posts on it, search the forum for a script I wrote last week sometime. It does it all in one step.

---

### Post by Chonnawonga on 2010-08-28
Unison! It's got a simple GUI and it's fairly easy to set up. It's in the repos, so you can get it through Software Centre.

---

