---
title: "Deleting Users"
date: 2011-07-18
forum: General Help
---

### Post by NoFriends on 2011-07-18
Hi,

I am trying to delete specific users along with their files, these are the steps i am taking, any help is appreciated.

> sudo su -

> cat /etc/passwd

> userdel user1

userdel command not found.

I am not able to remove the specified user, Does anyone know how else to remove this user.

Thanks in advance.

---

### Post by nerdy_kid on 2011-07-18
That sounds really suspicious to me, has anything strange been going on?

---

### Post by NoFriends on 2011-07-18
Nothing strange going on that I know of, How come ?

As you can see from the above quote, I was running as root.

---

### Post by haqking on 2011-07-18
> **NoFriends said:**
> Nothing strange going on that I know of, How come ?

As you can see from the above quote, I was running as root.


go to /usr/sbin

do a ls and see if userdel is present

if so do it from that directory maybe your path is messed up

---

### Post by NoFriends on 2011-07-18
I just run the below:

> cd /usr/bin

Could not find or locate the userdel there, if this is not there, is there a way to manually delete users, or another solution ?

thanks for your help

---

### Post by haqking on 2011-07-18
> **NoFriends said:**
> I just run the below:



Could not find or locate the userdel there, if this is not there, is there a way to manually delete users, or another solution ?

thanks for your help

 said sbin not bin

/usr/sbin

also you dont need to use sudo su.  you can use sudo which is preferred

and yes just go to system>administration>users & groups

depending on what version of Ubuntu you are using

---

### Post by NoFriends on 2011-07-18
Sorry never checked the post correctly.

I managed to run userdel user1 under the /usr/sbin directory and it worked successfully.

Thanks for your help.

---

### Post by haqking on 2011-07-18
> **NoFriends said:**
> Sorry never checked the post correctly.

I managed to run userdel user1 under the /usr/sbin directory and it worked successfully.

Thanks for your help.


ok then in which case it your path that is not set.

go to terminal and type

echo $PATH

and paste output here

---

