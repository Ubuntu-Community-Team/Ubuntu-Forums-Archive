---
title: "Ubuntu Updates without Password"
date: 2011-02-05
forum: General Help
---

### Post by SNYP40A1 on 2011-02-05
I plan to install Ubuntu on an older laptop for my grandmother.  Is there a way to allow Ubuntu system updates without having to enter a password?  I don't want her to run as root, I plan not to tell her the root password so that she doesn't accidentally do something bad.

---

### Post by cogier on 2011-02-05
Linux security, to some extent, relies on the password to help prevent security issues.

You seem to have been on the Ubuntu Forum for some time so I am a little surprised that you are referring to a **root** password.

You will need a password for your grandmother whatever you do, why not pick something she knows like her birth date or her phone number. 

Perhaps you mean to a login password?

If you want the system to boot up without requiring her to log in then there is an install option to remove this. You can also do this post installation using **System>Administration>Users and Groups.**

Hope that helps.

---

### Post by TeoBigusGeekus on 2011-02-05
What about sshing into her laptop every week or so and updating it yourself?

---

### Post by psycho5 on 2011-02-05
How about you just edit the sudoers file?

create an alias for your grandma's user name.

create an alias for updates such as RUN_UPDATE = /sbin/apt-get upgrade

then give her permission to do that

<username> ALL=(ALL) NOPASSWD: RUN_UPDATE

actually, that's not entirely what you need to do, you also need to add 
<username> ALL=(ALL) RUN_UPDATE 

under the members of admin groups that may gain root privilages, so that she will be allowed only to run updates without entering passwords. just for that command.

---

### Post by cprofitt on 2011-02-05
There is a GUI way to ensure that security updates are installed w/o user intervention of the use of the admin password.

**System > Administration > Update Manager** 

Click the** settings** button

select "install security updates without confirmation"

See the attached image.

---

### Post by SNYP40A1 on 2011-02-05
> **cprofitt said:**
> There is a GUI way to ensure that security updates are installed w/o user intervention of the use of the admin password.

**System > Administration > Update Manager** 

Click the** settings** button

select "install security updates without confirmation"

See the attached image.

I think that's what I'm looking for...thanks cprofitt.

cogier, I might not know the terminology...I'm just trying to setup a system that my 91 year old grandmother can use without having to enter a long password for everything.  Keep things as simple as possible.

---

