---
title: "Weird 10.04 and samba issue"
date: 2010-05-03
forum: General Help
---

### Post by paped on 2010-05-03
OK I am a bit stuck with this problem so any ideas/help appreciated, as I cannot find anything in the forum/google about this.

I have had Samba running on an 8.04LTS Ubuntu server for the past 2 years and before that on a 6.06LTS server, after the initial set-up it has just worked with both XP and recently Ubuntu clients.

This weekend though I upgraded to 10.04 desktop on the client machines and I have a weird problem basically all users can read and copy/save i.e. write to the drives as before. But if I try to rename a file or copy a file within the share it errors saying that I do not have permission, the only user that can do any changes is the admin account on the server, if I login with its credentials everything works as it did. All files in the shares are owned by "user" (the server admin user) and in the group "users" as they have been for the last x years, I have not changed my smb.conf file so in theory it should still work.
I have even now upgraded my server to 10.04LTS to see if it was some sort of version mismatch but I still have the issue so I am baffled.

I am assuming that it is some sort of permissions issue or how 10.04 applies the permissions maybe but it certainly seems to be somehow related to the upgrade to 10.04 - worked before but not after the upgrades??

---

### Post by randumnumber on 2010-05-04
im having problems with getting it to connect at all, i have 10.04 on my server and cannot connect with my 9.04 machine, lots of people are having issues, ive seen 6 threads about this, hell i posted one, if you find something that works let me know.

---

### Post by Sciamano on 2010-05-04
Same here. Can't connect to shared folders on my Lucid PC, samba keeps asking for username and password.

---

### Post by paped on 2010-05-05
Well I can connect to all of mine fine it seems to be a user/permissions issues for me. But one thing I did notice on my clients is that none of the shares would show up in "network" until I edited that smb.conf even though this is on the client which does not run Samba as such its the client?

I have had to do this in the past on other Ubuntu and Linux versions after upgrades but I always thought it was something to do with my network set-up. The edit I made was: 

(open file "/etc/samba/smb.conf" in gedit/nano under sudo)
Change the workgroup/domain name (near the top of the document) from WORKGROUP to whatever you use as your workgroup/domain name in your network.

Then reboot - after reboot the shares magically show up..... 

Not sure if this is your problem but hope this helps..

---

