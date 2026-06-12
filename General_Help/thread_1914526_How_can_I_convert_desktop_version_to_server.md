---
title: "How can I convert desktop version to server?"
date: 2012-01-24
forum: General Help
---

### Post by tnsmart on 2012-01-24
I have an Ubuntu system running the normal Desktop version of Ubuntu.  I need to convert it to the Server version so that I can follow these directions: [http://letitknow.wordpress.com/2011/05/05/how-to-install-asterisk-1-8-on-ubuntu-server-11-04/](http://letitknow.wordpress.com/2011/05/05/how-to-install-asterisk-1-8-on-ubuntu-server-11-04/).  They say that you should start with an Ubuntu Server.

Are there certain packages that I can install to correctly do this?

Thanks.

---

### Post by ubudog on 2012-01-24
You could install the packages on a regular desktop version of Ubuntu, however this may cause security issues.

---

### Post by JKyleOKC on 2012-01-24
Those instructions should work equally well with the desktop edition; the major difference between the desktop edition and the server edition is that the server has no GUI. It's command-line only. In addition, certain parameters within the kernel are tweaked for the server edition, but they should not impact the operation of the PBX.

Because there's no GUI, the server edition has no graphical programs. This means no Flash, Firefox, Opera, and so on. There are how-to threads in the "Tutorials" forum here that tell how to do the conversion, but the simplest way is to just back up any critical files you have, wipe the drive clean, and install the server edition from scratch! Just be sure that's really what you want to do...

---

### Post by ubudog on 2012-01-24
> **jkyleokc said:**
> those instructions should work equally well with the desktop edition; the major difference between the desktop edition and the server edition is that the server has no gui. It's command-line only. In addition, certain parameters within the kernel are tweaked for the server edition, but they should not impact the operation of the pbx.

Because there's no gui, the server edition has no graphical programs. This means no flash, firefox, opera, and so on. There are how-to threads in the "tutorials" forum here that tell how to do the conversion, but the simplest way is to just back up any critical files you have, wipe the drive clean, and install the server edition from scratch! Just be sure that's really what you want to do...
+1

---

### Post by tnsmart on 2012-01-24
--Deleted--

---

### Post by tnsmart on 2012-01-24
Thanks for all the replies.  I went ahead and installed Asterisk 1.8 (without worrying about converting it to a "server") following the directions listed in my original post.  Now, I could use some help configuring Asterisk.  All of the directions that I can find, including the ones at that link, don't make much sense to me.

I would like to setup the browser interface so that I can configure the system from there.  How do I do that?  And will I be able to do all of my configuration from there?

The computer has a static IP of 10.10.10.151.
I'd like to setup several users with usernames like 101, 102, 102, 201, 202, 203, etc., some listen only and some listen and talk.  The users will also have passwords.
I'd like to allow multiple users to be able to dial 1 to get to one conversation, dial 2 to get to a separate conversation, etc.

Can anyone help me with this?
Thanks so much.

---

### Post by ubudog on 2012-01-24
> **tnsmart said:**
> Thanks for all the replies.  I went ahead and installed Asterisk 1.8 (without worrying about converting it to a "server") following the directions listed in my original post.  Now, I could use some help configuring Asterisk.  All of the directions that I can find, including the ones at that link, don't make much sense to me.

I would like to setup the browser interface so that I can configure the system from there.  How do I do that?  And will I be able to do all of my configuration from there?

The computer has a static IP of 10.10.10.151.
I'd like to setup several users with usernames like 101, 102, 102, 201, 202, 203, etc., some listen only and some listen and talk.  The users will also have passwords.
I'd like to allow multiple users to be able to dial 1 to get to one conversation, dial 2 to get to a separate conversation, etc.

Can anyone help me with this?
Thanks so much.

Glad to hear that.  You might want to create a new thread for that question, because people looking for an answer will probably not click on this thread.  :)

---

### Post by tnsmart on 2012-01-24
> **ubudog said:**
> Glad to hear that.  You might want to create a new thread for that question, because people looking for an answer will probably not click on this thread.  :)

Ok.  I wasn't sure if I should or not.  My new thread is here: [http://ubuntuforums.org/showthread.php?p=11637911](http://ubuntuforums.org/showthread.php?p=11637911).

Thanks again!

---

