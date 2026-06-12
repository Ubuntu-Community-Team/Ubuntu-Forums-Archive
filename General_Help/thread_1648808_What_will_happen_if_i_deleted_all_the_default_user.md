---
title: "What will happen if i deleted all the default user groups in Ubuntu?"
date: 2010-12-19
forum: General Help
---

### Post by dokha on 2010-12-19
[http://answers.yahoo.com/question/index?qid=20101219045227AAnTifa](http://answers.yahoo.com/question/index?qid=20101219045227AAnTifa)

i am considered a power user in windows but in  ubuntu ima total noob. in the users settings, manage groups, i see like  100 groups. and thats just annoys me, all i want is to be the admin and  everything to work its not rocket science is that so hard for linux? I  DO NOT WANT TO BELONG TO A FREAKING GROUP I JUST WANT 1 SIMPLE ADMIN  ACCOUNT. someone please explain everything related to this subject. i  mean i see stupid groups like 'audio' and 'couchdb'. WTF
i dont want these useless groups to exist on my system

---

### Post by CharlesA on 2010-12-19
They are not useless groups. They are system groups, which are required by the system for it to function. If you remove them, you will break your OS.

By default the user created during install is in the admin group, and that's all you really need to know. :)

---

### Post by nothingspecial on 2010-12-19
You`d completely stuff up your system.

---

### Post by dokha on 2010-12-19
but i can go to advanced settings user privelges and check them all for one admin user. why should i need the other groups?

---

### Post by nothingspecial on 2010-12-19
> **dokha said:**
> but i can go to advanced settings user privelges and check them all for one admin user. why should i need the other groups?

Because that`s how linux works.

[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

[http://faculty.cs.byu.edu/~rodham/cs240/linux-tutorial/linuxdoc.html](http://faculty.cs.byu.edu/~rodham/cs240/linux-tutorial/linuxdoc.html)

[http://www.debianadmin.com/users-and-groups-administration-in-linux.html](http://www.debianadmin.com/users-and-groups-administration-in-linux.html)

---

### Post by dokha on 2010-12-19
they tell me this may leave files with invalid id in the system, if i delete the audio group this mean the audio will not work even though i have checked it (use audio devices) in the user privilages?
please only for pros and experianced users i need helpful info here.

---

### Post by oldos2er on 2010-12-19
Linux is not windows. [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

[http://books.google.com/books?id=JK_XhN3W-egC&pg=PA575&lpg=PA575&dq=understanding+ubuntu+linux+users+and+groups&source=bl&ots=mujmrNq3fs&sig=o_a0k3sWvxJwYD-z0DvbRLdg90w&hl=en&ei=SzsOTeflIsH58AbU_pHbDQ&sa=X&oi=book_result&ct=result&resnum=8&ved=0CE4Q6AEwBw#v=onepage&q=understanding%20ubuntu%20linux%20users%20and%20groups&f=false](http://books.google.com/books?id=JK_XhN3W-egC&pg=PA575&lpg=PA575&dq=understanding+ubuntu+linux+users+and+groups&source=bl&ots=mujmrNq3fs&sig=o_a0k3sWvxJwYD-z0DvbRLdg90w&hl=en&ei=SzsOTeflIsH58AbU_pHbDQ&sa=X&oi=book_result&ct=result&resnum=8&ved=0CE4Q6AEwBw#v=onepage&q=understanding%20ubuntu%20linux%20users%20and%20groups&f=false)

---

### Post by nothingspecial on 2010-12-19
> **dokha said:**
> 
please only for pros and experianced users i need helpful info here.

If you want more info, read the links I posted.

However, Ubuntu is set up so you don`t have to worry about these things. I suggest you ignore them.

---

### Post by dokha on 2010-12-19
just if anyone is wondering i deleted the audio group and the audio is still working so yeah..
but i created a backup new user first if anything would happen but nothing.

---

### Post by iponeverything on 2010-12-19
> **dokha said:**
> [http://answers.yahoo.com/question/index?qid=20101219045227AAnTifa](http://answers.yahoo.com/question/index?qid=20101219045227AAnTifa)

i am considered a power user in windows but in  ubuntu ima total noob. in the users settings, manage groups, i see like  100 groups. and thats just annoys me, all i want is to be the admin and  everything to work its not rocket science is that so hard for linux? I  DO NOT WANT TO BELONG TO A FREAKING GROUP I JUST WANT 1 SIMPLE ADMIN  ACCOUNT. someone please explain everything related to this subject. i  mean i see stupid groups like 'audio' and 'couchdb'. WTF
i dont want these useless groups to exist on my system

sounds like you need to create your own operating system - that way you can design it the way you like. The particular design characteristic that you don't seem to understand has been a fundamental part of UNIX design since before you were born.

---

### Post by jocko on 2010-12-19
> **dokha said:**
> they tell me this may leave files with invalid id in the system, if i delete the audio group this mean the audio will not work even though i have checked it (use audio devices) in the user privilages?
please only for pros and experianced users i need helpful info here.
Do you want to know what happens when you check the "use audio devices" box in user privileges? You make your user a member of the audio group. Without an audio group, that checkbox will do nothing. Leave the groups alone. They are there for a reason, even if you don't see it. I'm sure there's a way to give all privileges to the admin group, and then get rid of all the other groups, but that would take a lot of work and it's very likely it would have unpredictable results later on...

---

### Post by iponeverything on 2010-12-19
> **dokha said:**
> 
please only for pros and experianced users i need helpful info here.

 "What will happen if i deleted all the default user groups in Ubuntu"

Your system will break. 

It is so easy to test, I am surprised you decided to post.

---

### Post by dokha on 2010-12-19
for future newbies: DO NOT DO WHAT I JUST DID.
i deleted all the groups , for some reason some groups just came back (prob the ones that the user belonged to), and now all those privilages just disappeared, only 3 left, 'access external storage automatically' 'administer the system' 'use audio devices', (for the whole system not only the account i used) however i cant see any actual difference in useage at the moment. atleast i got my answer...and now im satisfied...  :)
lets hope i dont have to reinstall, if anyone knows how to undo wat i just did it will be appreciated..

EDIT: i discovered i cannot install anything now

---

### Post by CharlesA on 2010-12-19
You will have to reinstall. The system is hosed.

---

### Post by nothingspecial on 2010-12-19
You`ll have to reinstall.

You fubared it.

Just like all those "experi[COLOR=Red]a[/COLOR]nced"  users said you would.

---

### Post by dokha on 2010-12-19
its seemed like a good idea at the time..lol
anyway
ubuntu is probably not my type of distro i am searching for a distro targeted for desktop home single users, (is there such a thing?) i will post about that right now.
huge thanks to every one who replied u guys rock.

---

### Post by coffeecat on 2010-12-19
> **dokha said:**
> i am searching for a distro targeted for desktop home single users, (is there such a thing?)

Each Linux distro has its own strengths and weaknesses, but there are none that I can think of that are targeted for single users more or less than Ubuntu. By their very nature Linux OSs are good at running multi-user systems, but that doesn't make them bad as single user systems.

If you want to try out other distros, Fedora, Opensuse, Mepis, PCLinuxOS and Mandriva are good ones to try, but I do have one piece of advice concerning all of them....

Don't delete the default user groups! :p

---

### Post by Verbeck on 2010-12-19
> **dokha said:**
> its seemed like a good idea at the time..lol

next, try [dban]("http://www.dban.org/")
make sure you dont have a backup
:popcorn:

---

### Post by jocko on 2010-12-20
> **dokha said:**
> ...
ubuntu is probably not my type of distro i am searching for a distro targeted for desktop home single users, (is there such a thing?) i will post about that right now.
huge thanks to every one who replied u guys rock.
So exactly **what** is your problem with the groups? **How** does it make ubuntu less suited for a single user? If you have one single user that is member of all the proper groups (like the default user in ubuntu), you have a distro that is perfect for a single home desktop user... Just because the presence of groups makes it very easy to decide which users in a multi user system can have what permissions doesn't make it any more complicated to just have one single user...

---

### Post by CharlesA on 2010-12-20
> **jocko said:**
> So exactly **what** is your problem with the groups? **How** does it make ubuntu less suited for a single user? If you have one single user that is member of all the proper groups (like the default user in ubuntu), you have a distro that is perfect for a single home desktop user... Just because the presence of groups makes it very easy to decide which users in a multi user system can have what permissions doesn't make it any more complicated to just have one single user...
I'm guessing that because the OP is coming from Windows background, they expected to only have one or two groups - Users and Administrators.

That's "normal" for a standalone desktop, even tho there are a few other groups on a standalone Windows desktop.

---

