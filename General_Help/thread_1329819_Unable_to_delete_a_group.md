---
title: "Unable to delete a group"
date: 2009-11-17
forum: General Help
---

### Post by sefs on 2009-11-17
I had created a group and place my main (sudo) user in it.

I removed myself from this group.

But now when I type groups in the terminal i still see this group listed as one that I am in.

I am also unable to delete this group.

How can I get rid of it?

Thanks.

---

### Post by sisco311 on 2009-11-17
> **sefs said:**
> I had created a group and place my main (sudo) user in it.

I removed myself from this group.

But now when I type groups in the terminal i still see this group listed as one that I am in.

I am also unable to delete this group.

How can I get rid of it?

Thanks.

you have to log out and log back in in order the changes take effect.

EDIT: how did you try to delete the group?

---

### Post by sefs on 2009-11-17
At this point I feel like tearing ubuntu developers limb from limb.

Sighs.

Anyhow...

The gui for users & groups seem to be not working so I was trying from the command line.  With the gui i was rebooting after each change but things did not seem to stick.

Anyhow I ended up trying to do it from the command line 

I ran this command...

```

sudo usermod -G vmnetzero myuser

```

That removed me from all groups and left me only in the vmnetzero group.

I thought ~/.bash_history would not only contain commands but also the output commands but not so ... so I cannot remember what groups I was a part of.

How can I find that out...is output to the terminal stored somewhere for a time?

Secondly ... my user is no longer part of the sudoers  so I cannot use it to do any admin.

How can I get my user back into its orginal groups and back on the sudoers list.

---

### Post by sefs on 2009-11-17
> **sisco311 said:**
> you have to log out and log back in in order the changes take effect.

EDIT: how did you try to delete the group?

I tried to delete it at first by logging into the users & groups gui.  I deleted it.  Rebooted, it was back.

I finally got it deleted by command line

sudo groupdel groupname

That was before my calamity

---

### Post by sisco311 on 2009-11-17
reboot in the Recovery Mode and add you user to the admin group:

[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")


---------------------------------------------------------------

To add a user to a group:

```
man usermod
```
```
sudo usermod -**[B]a**[/B]G vmnetzero myuser
```
-a = append = Add the user to the **supplementary **group(s). Use only with the -G option;)

or:
```
adduser username group
```
(as root (sudo adduser...) this will work in ubuntu/debian systems)

or

```
gpasswd -a username group
```
(...most linux/unix systems)

---

### Post by sefs on 2009-11-17
Thank you.  I will try this now. :)

Good old Pshycocats to the rescue again.

P.S.  .bashrc_history shows the history of what I typed.

Is there somewhere to view the history of the output that was generated from what I typed?

---

### Post by sisco311 on 2009-11-17
nm

---

