---
title: "Side-effects of changing admin username"
date: 2011-08-09
forum: General Help
---

### Post by gornelas on 2011-08-09
Hello All,

I installed ubuntu and created my username as the first user - thus I'm the "admin" user.  I wanted to change this user name to "administrator".  

I know I can use usermod to change a username - as in "usermod -l administrator <myusername>"

My question is if this will be ok to run with the admin username.  Wil everything translate automatically or is there anything additional I should do.

Thank you very much for your time.

s.g.

---

### Post by haqking on 2011-08-09
> **gornelas said:**
> Hello All,

I installed ubuntu and created my username as the first user - thus I'm the "admin" user.  I wanted to change this user name to "administrator".  

I know I can use usermod to change a username - as in "usermod -l administrator <myusername>"

My question is if this will be ok to run with the admin username.  Wil everything translate automatically or is there anything additional I should do.

Thank you very much for your time.

s.g.

Actually you are a user with admin priveleges belonging to the admin group and allowed to perform sudo operations by providing your credentials for elevatd priveleges.

and you should NEVER name an account with admin priveleges or the admin account as Administrator.
as it broadcasts to everyone what account can perform some admin actions and is one less thing for someone to find out

---

### Post by gornelas on 2011-08-09
Hello haqking,

I can see your point.  Now, the same question applies if I want to change it to 'tommy'.

If my current username with admin privileges is 'johnny', would a simple 

usermod -l tommy johnny     do the trick?  would johnny now behave like tommy did?

Thanks for the prompt response.

---

### Post by haqking on 2011-08-09
> **gornelas said:**
> Hello haqking,

I can see your point.  Now, the same question applies if I want to change it to 'tommy'.

If my current username with admin privileges is 'johnny', would a simple 

usermod -l tommy johnny     do the trick?  would johnny now behave like tommy did?

Thanks for the prompt response.

see here:

[http://ubuntuforums.org/showthread.php?t=967404](http://ubuntuforums.org/showthread.php?t=967404)

---

### Post by gornelas on 2011-08-09
Ok.  What would happen if I just change my username to the new username?

Could I get into a situation where I make a mistake and lock myself out of sudo rights?

Not trying to be a smart-aleck just want to understand if there is any reason I should not do what I am suggesting.

Thanks.

---

### Post by sisco311 on 2011-08-09
> **gornelas said:**
> Hello All,

I installed ubuntu and created my username as the first user - thus I'm the "admin" user.  I wanted to change this user name to "administrator".  

I know I can use usermod to change a username - as in "usermod -l administrator <myusername>"

My question is if this will be ok to run with the admin username.  Wil everything translate automatically or is there anything additional I should do.

Thank you very much for your time.

s.g.

From `man usermod'
> 
       -l, --login NEW_LOGIN
           The name of the user will be changed from LOGIN to NEW_LOGIN.
           **Nothing else is changed**. In particular, the users home directory
           name should probably be changed manually to reflect the new login
           name.


By default, in Ubuntu, `foo' user's primary group is `foo' and its home directory is /home/foo.

So you might want to change those as well.

Some applications, like firefox, hardcode the location of the home directory in their config files, so if you rename your home directory, you will have to manually adjust the locations in the config files.

IMO, it's much easier to create a new account(with admin rights; add it to the admin group), copy the config files from the the old one to the new and when you're absolutely sure that everything works well, delete the old one.

> **haqking said:**
> Actually you are a user with admin priveleges belonging to the admin group and allowed to perform sudo operations by providing your credentials for elevatd priveleges.

and you should NEVER name an account with admin priveleges or the admin account as Administrator.
as it broadcasts to everyone what account can perform some admin actions and is one less thing for someone to find out

True if one allows remote access to the computer, or more precisely to the admin account on the computer. Otherwise the passwd and group files are world readable for local users.

---

### Post by SoFl W on 2011-08-09
Why not create a new user called whateveryouwant and give that new user admin privileges?  If you have to copy files over to the new home folder you can. This would avoid your worries.

---

### Post by sisco311 on 2011-08-09
> **sofl w said:**
> why not create a new user called whateveryouwant and give that new user admin privileges?  If you have to copy files over to the new home folder you can. This would avoid your worries.

+1 ;)

---

### Post by haqking on 2011-08-09
> **gornelas said:**
> Ok.  What would happen if I just change my username to the new username?

Could I get into a situation where I make a mistake and lock myself out of sudo rights?

Not trying to be a smart-aleck just want to understand if there is any reason I should not do what I am suggesting.

Thanks.

yes you could get into a situation if you are not careful.

Best to delete and recreate as outlined in the link.

You can change name but there might issues such as renaming home folder, files external to the home folder, mail issues etc.

knock on effects are often unseen until later.

remember have a back up before making any such changes

---

### Post by gornelas on 2011-08-09
Awesome responses.  Thanks sisco311, haqking, and SoFiW.  Now I know more about why you should and shouldn't do it.  

I had read the man page for usermod -l, but I didn't know if the stated 'Nothing else is changed' maybe didn't apply to the admin user.

I will go the route of creating the new user and giving it admin privileges.

Thanks again.

s.g.

---

