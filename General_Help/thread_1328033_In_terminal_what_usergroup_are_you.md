---
title: "In terminal what user/group are you?"
date: 2009-11-16
forum: General Help
---

### Post by doccpu on 2009-11-16
i change the permissions of motion.conf to root/motion  rwrwr-
i ( david) am a member of group motion
but in gui i cant read or edit motion.conf. from a terminal Gedit says i have no priviledges to read or edit it. well hell ls-l shows rw-rw-r so motion has permission i am a member of motion. why cant i edit it?
dhorner at usa tod net


the gui says i am in the motion group but am i really?
adduser says The user `david' is already a member of `motion'.
so why cant i read or edit the file?  :confused:

---

### Post by mbeach on 2009-11-16
Because the permissions are set to rw-rw-r-- and you are getting an error saying not able to read the file, something is amiss, as that final r should allow anyone to read the file.

What is the full path to the file? Check the permissions of the folder it is in maybe?

By the way, you can also type "groups" to see what groups you are in.

---

### Post by doccpu on 2009-11-16
All things said i was in the group but once again bit in the tail by an undocumented problem. If you change your group in a terminal that terminal may or may not be able to see the file but anything done in gui or other terminals remember the old groups you were in. You have to relogin to the pc/gui for ubuntu to know you are in that group.
Someone mentioned in passing that you may have to login again for it to see the changes. Yep after relog to gui it worked . This problem has been one of the reasons i have disliked ubuntu for a long time. You have to log out and in again after every group change so can use your own machine.
You can actually have better priviledges to a file in samba than you do at the machines console. a lack of an x on a directory some where will eat your lunch. And cause hair loss from pulling.
If i could get plugins, codecs, and more good software for ubuntu i would make it my main op system. I do use it for important stuff i want to run more than a day without a reboot. File and web Servers.

---

### Post by mbeach on 2009-11-23
> **doccpu said:**
>  You have to relogin to the pc/gui for ubuntu to know you are in that group.

I don't think that is all that uncommon in any os. I suppose the annoyance factor comes down to how often are you amending groups for a particular user whether or not it is a "real" issue. 

You are right, a lack of an 'x' can make sure make things difficult, but those are the specifications which are agreed upon and followed for years, and with time, experienced admins spot/troubleshoot quite quickly and with ease.

I would be suspicious of a system where the samba setup is such that access to files is more open than being at the console - would seem to indicate some potential areas for untidiness.

Good luck,
mb.

---

