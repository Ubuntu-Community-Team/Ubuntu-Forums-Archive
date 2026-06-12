---
title: "gcompris help"
date: 2006-06-14
forum: General Help
---

### Post by forrestcupp on 2006-06-14
I have a 2 1/2 year old boy who loves gcompris.  The problem is that some of the things in it are too advanced for him.  So I want to use the administration tool that comes with it, but it doesn't work.  It won't allow me to do anything.  If I click classes/users, it doesn't give me the option to do anything.  There are none in the list.  If I click "groups," it says to select a class, and there are none in the list.  If I click "profiles," it has the option to add, but nothing happens when I click on it.  When I click the "boards" button, there is nothing in the list.  It would be nice to be able to use this tool.  Can anyone help me figure this out?

---

### Post by az on 2006-06-14
I have used (okay, my two little girls) gcompris, but I never used the gcompris editor.  I will look at that.  

Another app which is great and somewhat similar is childsplay.  Be sure to install the childsplay plugins too, or else it is pretty boring.  There are a few activities there that are more suited to a smaller child.

---

### Post by johnc4510 on 2006-06-14
Here is their homepage, it has documentation listed:
[http://gcompris.net/-en-](http://gcompris.net/-en-)

---

### Post by az on 2006-06-15
[https://launchpad.net/distros/ubuntu/+source/gcompris/+bug/49840](https://launchpad.net/distros/ubuntu/+source/gcompris/+bug/49840)

I filed a bug.  Please add to it.

---

### Post by Rui Pais on 2006-06-15
[QUOTE=azz][https://launchpad.net/distros/ubuntu/+source/gcompris/+bug/49840](https://launchpad.net/distros/ubuntu/+source/gcompris/+bug/49840)

I filed a bug.  Please add to it.[/QUOTE]
Hi, i'm interested in this too. 
Please, what do you mean by add to it?

Rui

---

### Post by az on 2006-06-15
[QUOTE=Rui Pais]Hi, i'm interested in this too. 
Please, what do you mean by add to it?

Rui[/QUOTE]
Confirm it or add details to it.

---

### Post by Rui Pais on 2006-06-15
Ah, i get it (i was not shure)

Done it.

---

### Post by forrestcupp on 2006-06-15
[QUOTE=johnc4510]Here is their homepage, it has documentation listed:
[http://gcompris.net/-en-](http://gcompris.net/-en-)[/QUOTE]

Thank you, but I have already read through the documentation, and they don't even mention the administration tool.

And Azz, my boy uses Childsplay also, and he likes it a lot.

---

### Post by Rui Pais on 2006-06-15
[QUOTE=forrestcupp]Thank you, but I have already read through the documentation, and they don't even mention the administration tool.

And Azz, my boy uses Childsplay also, and he likes it a lot.[/QUOTE]

Hi, this a recent thing. Older versions allow definition of level directly on options of gcompris. I think they didn't update the documentation, or at least to cover this topic.

I'm planning on compiling from code on my test ubuntu installation and check if the problems persists or if its an ubuntu specific bug.

---

### Post by Rui Pais on 2006-06-15
hi, just add the following to bug report:
When launched from a terminal, gcompris -a and in profiles select Add here what i got:
> starting profiles panel
Traceback (most recent call last):
  File "/usr/share/gcompris/python/administration.py", line 180, in select_event module.start(self.panel_area)
  File "/usr/share/gcompris/python/admin/module_profiles.py", line 79, in start
    profile_list.Profile_list(frame, self.con, self.cur)
  File "/usr/share/gcompris/python/admin/profile_list.py", line 135, in __init__ self.current_profile_id)
  File "/usr/share/gcompris/python/admin/profile_group_list.py", line 67, in __init__
    self.reload(self.profile_id)
  File "/usr/share/gcompris/python/admin/profile_group_list.py", line 106, in reload
    (self.profile_id, ))
pysqlite2.dbapi2.OperationalError: no such table: groups
Traceback (most recent call last):
  File "/usr/share/gcompris/python/admin/profile_list.py", line 222, in on_add_profile_clicked
    profile_id = constants.get_next_profile_id(self.con, self.cur)
  File "/usr/share/gcompris/python/admin/constants.py", line 74, in get_next_profile_id
    cur.execute('select max(profile_id) from profiles')
pysqlite2.dbapi2.OperationalError: no such table: profiles

---

### Post by Rui Pais on 2006-06-15
Hi again, sorry to post 3 times in a row, i'm been very active :)

I tried the repo suggested in gcompris site:
[http://thomas.enix.org/DebianRepository]("http://thomas.enix.org/DebianRepository")
and it **works! **
It have as an "extra-bonus" being the 7.4, instead of 7.2, that is much more organized and well conceived (the main app for accessing modules, i mean)

If someone wants to try just add to sources.list:
deb [http://thomas.enix.org/pub/debian/packages/](http://thomas.enix.org/pub/debian/packages/) dapper main

the public keys are available at Thomas site (link above).



***Edit:*** I deleted the 7.4 (not purging and keeping config files) and reinstalled the 7.2 and then 7.2 worked normally... This seems to be, after all, just a missing default config file at 7.2 package. 
I like the 7.4 more anyway.

---

### Post by forrestcupp on 2006-06-17
I used the new repo and upgraded to 7.4, and I got administration tool to work, too.  I was able to set up classes, users, and edit the boards.  The problem is, I can't figure out how to get it to load up with the edited boards.  Has anyone figured this out?

edit:

I just figured out that you have to change your command to  ```
gcompris -p NameOfProfile
```  where NameOfProfile is whatever you named your profile.  If you don't know, either go to administration tools to find out, or type 

```
gcompris --profile-list
```

---

### Post by Rui Pais on 2006-06-17
Hi,
I just edit the default profile. 
Defaults is everything modules turned on, so it's easy to go back the the inicial state :)...

---

