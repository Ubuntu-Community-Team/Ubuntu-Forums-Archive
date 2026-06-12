---
title: "iSCSI problem in 10.04"
date: 2010-08-14
forum: General Help
---

### Post by ZoombyWoof on 2010-08-14
Hi all. I have run the iscsitarget daemon on my 9.04 server (64-bit) for some time and it has worked very well. Yesterday I upgraded the server to 10.04 (64-bit) and now the ietd process gets into a loop, using 100% cpu forever when the client connects, and I get a Target error on the initiator (win7). Nothing is being logged except some starting messages about initiators.deny file is being obsoleted in the next release and that the configfile will be moved to /etc/iet, but nothing else.

Anyone has any idea of what may have gone wrong here ? I first upgraded 9.04 to 9.10 using do-release-upgrade, all worked well. Then I did a do-release-upgrade again to get the server to 10.04 and now it doesnt work so well....iSCSI is just 1 out of several things that got broken, like MySQL and Postgresql.... not a very stable version it seems....

any help appreciated. Thanx

/zw

---

### Post by ZoombyWoof on 2010-08-28
Hi, Solved it. I needed to re-install the iscsitarget package. Something in the upgrade procedure broke it...well... now it works anyway.
/zw

---

### Post by derek654 on 2010-09-22
I am having the same problem.  I have done apt-get remove iscsitarget and reinstalled multiple times.  I am still getting the issue with the file /usr/sbin/ietd using 100% of the processor and the issue with the client as well.  The exact same issue you have.  What exactly did you do to fix it?

I have also used the --purge command.

thanks,
Derek

---

### Post by dewblue on 2011-01-19
Yep, very infuriating. I'm having the same trouble with a clean install of 10.04.1, 64-bit. Samee win7 errors, and ietd eating 100% CPU.
 
A lot of important things seem to be broken in this release--including installation on a raid 1 mirror. Samba also randomly crashes the entire server, requiring a physical reset. 
 
After 4 years, I'm seriously contemplating moving away from Ubuntu :-(

---

### Post by dewblue on 2011-01-19
iscsitarget appears to be working OK under 10.04.1 32bit, though...

---

### Post by dewblue on 2011-01-19
iscsitarget appears to be working OK under 10.04.1 32bit, though...

---

### Post by dewblue on 2011-01-19
iscsitarget appears to be working OK under 10.04.1 32bit, though...

---

