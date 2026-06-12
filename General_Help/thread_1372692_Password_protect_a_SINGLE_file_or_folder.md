---
title: "Password protect a SINGLE file or folder?"
date: 2010-01-04
forum: General Help
---

### Post by GTerrik on 2010-01-04
So here's my problem:  A lot of people use my computer, I like that, I don't want it to change.  I also don't want my mother or little cousins to see love letters and my massive collection of Barbara Streisand porn.  (Is he kidding?  No one knows...) 

Is there a way I can make it so that a single file or folder in Unbuntu requires you to type a password EVERY time it's opened, regardless of whether or not you are an administrator?

I am not looking for encryption here (I don't think) I just want to password protect the files so that they can't be opened when a sibling plops down at my laptop for 5 minutes to check email and the like.

Thanks,
Greg

---

### Post by bodhi.zazen on 2010-01-04
Not without changing how you use your computer.

The preferred method is to create a unique account for each user, or at least use the guest account on Ubuntu. This will not restrict an administrative user (root), for that you need encryption.

Your second option is therefore Encryption.

If you want to try a graphical tool for encryption see CryptKeeper (it is in the repositories).

[http://tom.noflag.org.uk/cryptkeeper.html](http://tom.noflag.org.uk/cryptkeeper.html)

Be sure to unmount the directory when you are finished playing with it.

---

### Post by jamesisin on 2010-01-04
1. Lock your machine when you walk away.  They can sign in using a guest account or their own account, but they will not be using your profile.  (Usually you can lock your machine with alt-ctrl-l.)

2. Use an encrypted folder by following these very simple instructions:

[http://www.soundunreason.com/InkWell/?p=1185](http://www.soundunreason.com/InkWell/?p=1185)

3. Share that Barbara Streisand porn!  (Woa! what?)

---

### Post by dark_omega on 2010-01-04
Not a password but.. 

A even more complicated procedure is to use chown and chmod. Chown the file/folder to root and then chmod it to 700. You would need to run any application needing to access these files as root though. Secondly, anyone who knows about 'sudo' and your password could get back in.

That should work as well but I'm still a Linux newbie. There might be an unforseen issue with that method I am unaware of.

---

### Post by bodhi.zazen on 2010-01-04
> **dark_omega said:**
> Not a password but.. 

A even more complicated procedure is to use chown and chmod. Chmod the file/folder to root and then chmod it to 700. You would need to run any application needing to access these files as root though. Secondly, anyone who knows about 'sudo' and your password could get back in.

That should work as well but I'm still a Linux newbie. There might be an unforseen issue with that method I am unaware of.

That method will not work to protect the content form the administrative user (as requested by the OP) or a live CD. You need to use encryption.

---

### Post by dcstar on 2010-01-05
> **bodhi.zazen said:**
> Not without changing how you use your computer.

**The preferred method is to create a unique account for each user**, or at least use the guest account on Ubuntu. This will not restrict an administrative user (root), for that you need encryption.
......

Yes, using the multi-user features for **exactly** the purpose they exist for would work.

---

### Post by sTpny on 2012-05-28
just compress it with a password... its what you want.  You can still use the archive as though it were the file/folder using your archive manager, and your sibs wont be able to open it.

---

### Post by overdrank on 2012-05-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

