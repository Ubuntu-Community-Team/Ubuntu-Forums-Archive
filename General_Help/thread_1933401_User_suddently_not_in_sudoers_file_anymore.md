---
title: "User suddently not in sudoers file anymore"
date: 2012-02-29
forum: General Help
---

### Post by slikkemand on 2012-02-29
Hi (this refers to ubuntu 11.04)

Yesterday I did a lot of user and group management of the fileserver i've set up with samba. Today, my user is suddenly not in the sudoers file anymore (why I have no root).

I'm absolutely confident that I used sudo with this user yesterday, but I can't do that anymore.

How did this happen, and how do I use the user as root once again? (remember I have no other users with sudo-privileges),

Sincerly A

---

### Post by winh8r on 2012-02-29
Take a look here and you can work through resolving your issue:

[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

hope this helps you

---

### Post by slikkemand on 2012-02-29
Thanks for the reply. This is a server, and I have only ssh-access

---

### Post by winh8r on 2012-02-29
Try this link for a possible solution:

[http://askubuntu.com/questions/73864/how-to-modify-a-invalid-etc-sudoers-file-it-throws-out-anderror-and-not-allowi]("http://askubuntu.com/questions/73864/how-to-modify-a-invalid-etc-sudoers-file-it-throws-out-anderror-and-not-allowi")

Hope this works for you.

---

### Post by joshuarowley42 on 2013-03-01
Hey guys, thanks for the tips.

This just happened to me, I am slightly concerned as to how this happened? Is this a known bug or caused by some security issue? 

Josh

---

### Post by efflandt on 2013-03-01
Make sure that your user is in group **sudo** (ie, in list when you type **groups**) Then if something upgrades/changes something related to sudo, you should still be able to use it, even if you have to use your password when you previously had it configured to not need an sudo password for something.

---

### Post by rnerwein on 2013-03-02
hi
i just see that two people got the same problem. try first to figure out where it comes from. 
run in a terminal:
grep admin /etc/group   ( is there a new user in it)
ls -l /etc/group (is the modification date possible)
ls -l /etc/sudoers ( are the permissions: -r--r----- 1 root root 778 Dez 22 15:43 /etc/sudoers )
did you made some installs in the last time and you don't try sudo since then.
i think to fix the problem is only a fake - the problem will come back (and may be in the next secons ! ).  if there is a bug ?!
important is: who was the initiator.
ciao

---

### Post by joshuarowley42 on 2013-03-02
Well mine are; 

rowley@lx42-x60:~$ grep admin /etc/group
lpadmin:x:105:
admin:x:119:
rowley@lx42-x60:~$ ls -ls /etc/group
4 -rw-r--r-- 1 root root 839 2013-02-26 19:13 /etc/group <I added myself to www-data, and this may have actually been the cause for this problem thinking about it!...?>
rowley@lx42-x60:~$ ls -ls /etc/sudoers
4 -r--r----- 1 root root 609 2012-03-13 22:06 /etc/sudoers

---

### Post by schragge on 2013-03-02
@**joshuarowley42**
Check your group membership:
```
groups
```
If *sudo* is not in the list, try
```
pkexec adduser $USER sudo
```

[highlight]Edit.[/highlight]
> **joshuarowley42 said:**
> I added myself to www-data, and this may  have actually been the cause for this problem thinking about  it!...?Please post the output of
```
cat /etc/group
```to see if you accidentally messed up the syntax of the file.

And please use
[noparse]```

text pasted from terminal

```[/noparse]
when posting it.

For the future, the right way to add a user to some group on Ubuntu is either ```
sudo adduser user group
``` as shown above or using *Users and Groups* GUI applet ([uhelp]community/AddUsersHowto[/uhelp])

---

### Post by joshuarowley42 on 2013-03-02
Thanks for all your help guys, everything is now sorted.. 

The problem was that I used "usermod -G www-data" not "usermod -aG www-data" - displacing all my other groups.. Thanks for the explanation on how to do it properly.. 

I feel very embarrassed suggesting a bug - self.RTFM! :P

Thanks,
Josh

Edit: amusing coincidence that this was posted yesterday.. [http://www.xkcd.com/1180/](http://www.xkcd.com/1180/)

---

