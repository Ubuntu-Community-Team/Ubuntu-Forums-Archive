---
title: "Help me, please. I want ubuntu to NOT see some folders."
date: 2011-01-21
forum: General Help
---

### Post by dmdevotee on 2011-01-21
Hi all.

I have a network with:

- A windows 2003 server promoted to domain controller. It has a folder named "Profiles$" and another folder named "Shared"

- Some windows xp clients in a domain.

- a ubuntu 10.10 client.


I want to have a specific user from my domain to have acces to both "Profiles$" and "Shared" if it does login on a windows xp machine, but i want to only have acces to "Shared" when that user login on a ubuntu machine.



The question is: this is possible to block a folder to ubuntu machines, or ubuntu it's a beast that can see all that windows xp (for example) can see??

---

### Post by 3Miro on 2011-01-21
A network is designed to be agnostic with respect to an OS. There should be no way to distinguish an Ubuntu machine from an XP machine.

On a network, machines recognize one another via IP. You can give different IP to Windows and Linux and then there should be a way to restrict access for certain IP addresses.

---

### Post by dmdevotee on 2011-01-21
> **3Miro said:**
> A network is designed to be agnostic with respect to an OS. There should be no way to distinguish an Ubuntu machine from an XP machine.

On a network, machines recognize one another via IP. You can give different IP to Windows and Linux and then there should be a way to restrict access for certain IP addresses.



  but if i restrict a certain IP adress... i can't distinguish when that IP address wants to access to a "forbidden" folder from a "shared" folder...

---

### Post by 3Miro on 2011-01-21
Can you not setup IP per folder. I know you can do that with NFS (the Linux file sharing protocol), there should be a way to set IP x.x.x.x can see folder Y but not folder Z.

---

### Post by dmdevotee on 2011-01-21
> **3Miro said:**
> Can you not setup IP per folder. I know you can do that with NFS (the Linux file sharing protocol), there should be a way to set IP x.x.x.x can see folder Y but not folder Z.

the problem is: the folder is on windows, not on ubuntu

---

### Post by SeijiSensei on 2011-01-21
> **dmdevotee said:**
> the problem is: the folder is on windows, not on ubuntu

Then enforce a username/password on the share in Windows.

---

### Post by dmdevotee on 2011-01-21
> **SeijiSensei said:**
> Then enforce a username/password on the share in Windows.

and how can a username/password distinguish a user with linux from a user with xp?

---

### Post by psusi on 2011-01-21
Why would you want to do that?

Also "haves" is not a word.  The third person singular is he, she, or it *has* a folder.  The plural forms of have are still have, as in we have a car.

---

### Post by SeijiSensei on 2011-01-21
Well, you could have different user names on the Linux machine, so that XP user charlie has to log in as user charles on the Linux box.

But I agree with psusi.  Why should someone have different access rights depending on the client's platform?

---

### Post by dmdevotee on 2011-01-21
> **SeijiSensei said:**
> 

But I agree with psusi.  Why should someone have different access rights depending on the client's platform?

because if the user makes, in ubuntu, a new folder , or a new file, into the profile folder it will make the profile unavailable to update  (i tried it with virtual machines) (the profile folder is the folder on the sever where the windows xp clients store their windowx config (desktp, my documents, my images, etc))

---

### Post by psusi on 2011-01-22
> **dmdevotee said:**
> because if the user makes, in ubuntu, a new folder , or a new file, into the profile folder it will make the profile unavailable to update  (i tried it with virtual machines) (the profile folder is the folder on the sever where the windows xp clients store their windowx config (desktp, my documents, my images, etc))

So tell people not to do that.  Not that anyone is likely to try in the first place.

---

### Post by dmdevotee on 2011-01-22
> **psusi said:**
> So tell people not to do that.  Not that anyone is likely to try in the first place.

sorry but this is not a solution. 

anyway, this is made with virtual machines, for a classwork.

and maybe this is a windows concern more than ubuntu concern.

windows has a "windows services for unix" module, but i can't see the solution anyway.

---

### Post by psusi on 2011-01-22
What makes you think someone is going to go mess with the files in their profile from a Linux machine?  This really seems to be a complete non issue.

---

### Post by dmdevotee on 2011-01-22
> **psusi said:**
> What makes you think someone is going to go mess with the files in their profile from a Linux machine?  This really seems to be a complete non issue.

a good system adminitrator needs to find a solution for every chance to have a problem with pcs, in my opinion

---

### Post by psusi on 2011-01-22
> **dmdevotee said:**
> a good system adminitrator needs to find a solution for every chance to have a problem with pcs, in my opinion

You can't prevent stupid.  Every time you try to make things more idiot proof, they come up with a better idiot.  Sometimes, you just have to leave it at "well don't do that".  Especially when the likelihood of someone doing it is about a million to one.

---

### Post by dcstar on 2011-01-22
> **dmdevotee said:**
> because if the user makes, in ubuntu, a new folder , or a new file, into the profile folder it will make the profile unavailable to update  (i tried it with virtual machines) (the profile folder is the folder on the sever where the windows xp clients store their windowx config (desktp, my documents, my images, etc))

Users should **not ever** have permissions to access their Windows profile folders directly.

If this is allowed then **you **have bypassed normal Windows security and deserve any consequences for doing something so stupid.

---

### Post by psusi on 2011-01-22
> **dcstar said:**
> Users should **not ever** have permissions to access their Windows profile folders directly.

If this is allowed then **you **have bypassed normal Windows security and deserve any consequences for doing something so stupid.

They kind of have to, or they can't log in.

---

### Post by dmdevotee on 2011-01-22
> **dcstar said:**
> Users should **not ever** have permissions to access their Windows profile folders directly.

If this is allowed then **you **have bypassed normal Windows security and deserve any consequences for doing something so stupid.


> **psusi said:**
> They kind of have to, or they can't log in.


if i am not wrong, both of you are right.

users must have permissions to log in. but the shouldn't can access to their profile folder directly. that's why the path to the file folder is "e:/Profiles$/username". the "$" character at the end of the folder's name, is making it **invisible** but **not inaccesible** to the users.

so, if the users **know** that the path is //Profiles$/username, they could access directly. but they wouldn't know that path, so no problem

---

